<script lang="ts">
	import { onMount } from 'svelte';
	let canvas: HTMLCanvasElement;
	let amplitude = 0.25; // wave height
	let frequency = 1.5; // waves per unit
	let speed = 1.0; // wave speed
	let wireframe = false; // set true to see the mesh

	const colors = [
		'#ffb703', // golden yellow
		'#fb8500', // orange
		'#d62828' // warm red
	];

	onMount(() => {
		let dispose: (() => void) | undefined;

		// We want to run the animation client side.
		(async () => {
			const THREE = await import('three');

			const hexToVec3 = (hex: string) => {
				const color = new THREE.Color(hex);
				return new THREE.Vector3(color.r, color.g, color.b);
			};

			function generateWaveMaterial(offset: number) {
				const shaderColor = hexToVec3(colors[offset]);
				return new THREE.ShaderMaterial({
					transparent: true,
					depthWrite: false,
					uniforms: {
						uTime: { value: 0 },
						uAmp: { value: 1.0 }, // pixels
						uFreq: { value: 1.0 }, // waves across width
						uSpeed: { value: 0.2 },
						uEdgeStart: { value: 0.75 }, // start of the moving band (0=bottom,1=top)
						uEdgeEnd: { value: 1.0 }, // end of the moving band (top)
						uColor: { value: shaderColor }
					},
					vertexShader: `
                uniform float uTime, uAmp, uFreq, uSpeed, uEdgeStart, uEdgeEnd;
                varying vec2 vUv;
                void main() {
                  vUv = uv;
                  // Only move near the top using a smooth mask
                  float edge = smoothstep(uEdgeStart, uEdgeEnd, vUv.y);

                  // Wave along X (use uv.x so it scales with geometry)
                  float wave = sin((vUv.x * uFreq * 6.28318530718) + uTime * uSpeed) * uAmp;

                  vec3 pos = position;
                  pos.y += wave * edge;   // bottom remains untouched (edge ~ 0), top moves (edge ~ 1)

                  gl_Position = projectionMatrix * modelViewMatrix * vec4(pos, 1.0);
                }
              `,
					fragmentShader: `
                uniform vec3 uColor;
                void main() {
                  gl_FragColor = vec4(uColor, 1.0); // flat color
                }
              `
				});
			}

			function generateWave(offset: number) {
				const material = generateWaveMaterial(offset);
				const geometry = new THREE.PlaneGeometry(40, 6, 200, 200);
				const mesh = new THREE.Mesh(geometry, material);
				return {
					tick(elapsed: number) {
						material.uniforms.uTime.value = elapsed;
					},
					getMesh() {
						return mesh;
					},
					setMeshPositionY(y: number) {
						mesh.position.setY(y);
					},
					dispose() {
						geometry.dispose();
						material.dispose();
						mesh.remove();
					}
				};
			}

			// Renderer draws into the Svelte-bound <canvas>
			const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
			renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

			const scene = new THREE.Scene();

			const camera = new THREE.PerspectiveCamera(50, 1, 0.1, 100);
			camera.position.set(0, 0, 20);
			camera.lookAt(0, 0, 0);
			// Light
			scene.add(new THREE.AmbientLight(0xffffff, 0.6));
			const dir = new THREE.DirectionalLight(0xffffff, 1);
			dir.position.set(3, 5, 2);
			scene.add(dir);

			const waves: ReturnType<typeof generateWave>[] = [];

			for (let i = 0; i < colors.length; i++) {
				waves.push(generateWave(i));
			}

			waves.reverse().forEach((wave) => scene.add(wave.getMesh()));

			// Size to the canvas’s CSS size
			function resize() {
				const width = canvas.clientWidth;
				const height = canvas.clientHeight;

				const needResize =
					canvas.width !== Math.round(width * renderer.getPixelRatio()) ||
					canvas.height !== Math.round(height * renderer.getPixelRatio());

				if (needResize) {
					renderer.setSize(width, height, false);
					waves.forEach((wave, i) => wave.setMeshPositionY(-10 + i * 2));
				}

				camera.aspect = width / height;
				camera.updateProjectionMatrix();
			}
			window.addEventListener('resize', resize, false);
			resize();

			const clock = new THREE.Clock();
			renderer.setAnimationLoop(() => {
				waves.forEach((wave) => wave.tick(clock.getElapsedTime()));
				renderer.render(scene, camera);
			});

			dispose = () => {
				window.removeEventListener('resize', resize);
				renderer.setAnimationLoop(null as unknown as FrameRequestCallback);
				renderer.dispose();
				waves.forEach((wave) => wave.dispose());
			};
		})();

		return () => dispose?.();
	});
</script>

<canvas bind:this={canvas} class="block h-screen w-screen" {...$$restProps}></canvas>
