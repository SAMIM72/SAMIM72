


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>3D Animated Scene</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family:Arial, sans-serif;
    }

    body{
      overflow:hidden;
      background:black;
    }

    canvas{
      display:block;
    }

    .text{
      position:absolute;
      top:50%;
      left:50%;
      transform:translate(-50%,-50%);
      color:#00ffff;
      text-align:center;
      z-index:10;
    }

    .text h1{
      font-size:70px;
      text-shadow:0 0 20px cyan;
    }

    .text p{
      margin-top:10px;
      font-size:20px;
      color:white;
    }
  </style>
</head>
<body>

  <div class="text">
    <h1>SAMIM</h1>
    <p>3D Animated Developer Scene</p>
  </div>

  <script type="module">
    import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.module.js';

    const scene = new THREE.Scene();

    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );

    const renderer = new THREE.WebGLRenderer({ antialias:true });

    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    // Cube
    const geometry = new THREE.BoxGeometry(2,2,2);

    const material = new THREE.MeshStandardMaterial({
      color:0x00ffff,
      emissive:0x00ffff,
      metalness:1,
      roughness:0.2
    });

    const cube = new THREE.Mesh(geometry, material);
    scene.add(cube);

    // Light
    const light = new THREE.PointLight(0xffffff,2);
    light.position.set(5,5,5);
    scene.add(light);

    // Background particles
    const particlesGeometry = new THREE.BufferGeometry();
    const particlesCount = 5000;

    const posArray = new Float32Array(particlesCount * 3);

    for(let i=0; i<particlesCount * 3; i++){
      posArray[i] = (Math.random() - 0.5) * 50;
    }

    particlesGeometry.setAttribute(
      'position',
      new THREE.BufferAttribute(posArray,3)
    );

    const particlesMaterial = new THREE.PointsMaterial({
      size:0.03,
      color:0x00ffff
    });

    const particlesMesh = new THREE.Points(
      particlesGeometry,
      particlesMaterial
    );

    scene.add(particlesMesh);

    camera.position.z = 5;

    // Animation
    function animate(){
      requestAnimationFrame(animate);

      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;

      particlesMesh.rotation.y += 0.001;

      renderer.render(scene,camera);
    }

    animate();

    // Resize
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();

      renderer.setSize(window.innerWidth, window.innerHeight);
    });
  </script>

</body>
</html>
