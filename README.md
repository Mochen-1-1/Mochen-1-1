					new THREE.Float32BufferAttribute(positions, 3).setUsage(
						THREE.DynamicDrawUsage));


				geometry.setAttribute(
					"customColor",
					new THREE.Float32BufferAttribute(colors, 3));

				geometry.setAttribute("size", new THREE.Float32BufferAttribute(sizes, 1));

				const plane = new THREE.Points(geometry, shaderMaterial);

				plane.position.y = -8;
				scene.add(plane);
			}

			function addListners(camera, renderer, composer) {
				document.addEventListener("keydown", e => {
					const {
						x,
						y,
						z
					} = camera.position;
					console.log(`camera.position.set(${x},${y},${z})`);
					const {
						x: a,
						y: b,
						z: c
					} = camera.rotation;
					console.log(`camera.rotation.set(${a},${b},${c})`);
				});

				window.addEventListener(
					"resize",
					() => {
						const width = window.innerWidth;
						const height = window.innerHeight;

						camera.aspect = width / height;
						camera.updateProjectionMatrix();

						renderer.setSize(width, height);
						composer.setSize(width, height);
					},
					false);

			}
		</script>

	</body>

</html>
