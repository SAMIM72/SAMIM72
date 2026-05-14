html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Samim 3D Portfolio</title>

  <!-- THREE JS -->
  <script type="module" src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.module.js"></script>

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
      position:fixed;
      top:0;
      left:0;
      width:100%;
      height:100%;
      z-index:1;
    }

    /* HERO SECTION */
    .hero{
      position:absolute;
      top:50%;
      left:50%;
      transform:translate(-50%,-50%);
      text-align:center;
      z-index:10;

      animation: float 4s ease-in-out infinite;
    }

    .hero h1{
      font-size:90px;
      color:#00F7FF;

      text-shadow:
        0 0 10px #00F7FF,
        0 0 20px #00F7FF,
        0 0 40px #00F7FF,
        0 0 80px #00F7FF;
    }

    .hero p{
      color:white;
      margin-top:20px;
      font-size:24px;
      letter-spacing:4px;
    }

    /* BUTTON */
    .btn{
      display:inline-block;
      margin-top:35px;
      padding:15px 40px;

      border:2px solid #00F7FF;
      border-radius:50px;

      color:#00F7FF;
      text-decoration:none;
      font-size:18px;

      transition:0.4s;

      box-shadow:
        0 0 10px #00F7FF,
        0 0 20px #00F7FF;
    }

    .btn:hover{
      background:#00F7FF;
      color:black;

      transform:scale(1.1);

      box-shadow:
        0 0 20px #00F7FF,
        0 0 40px #00F7FF,
        0 0 80px #00F7FF;
    }

    /* FLOATING ANIMATION */
    @keyframes float{
      0%{
        transform:translate(-50%,-50%) translateY(0px);
      }

      50%{
        transform:translate(-50%,-50%) translateY(-20px);
      }

      100%{
        transform:translate(-50%,-50%) translateY(0px);
      }
    }

    /* GLOW */
    .glow{
      position:absolute;
      width:500px;
      height:500px;

      background:#00F7FF;
      border-radius:50%;

      filter:blur(200px);

      opacity:0.2;

      z-index:0;

      animation:pulse 6s infinite;
    }

    @keyframes pulse{
      0%{
        transform:scale(1);
      }

      50%{
        transform:scale(1.3);
      }

      100%{
        transform:scale(1);
      }
    }

  </style>
</head>

<body>

  <!-- Glow -->
  <div class="glow"></div>

  <!-- HERO -->
  <div class="hero">
    <h1>SAMIM</h1>

    <p>FULL STACK DEVELOPER • CYBER SECURITY</p>

    <a href="#" class="btn">Explore Portfolio</a>
  </div>

  <!-- THREE JS 3D SCENE -->
  <script type="module">

    import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.module.js';

    const scene = new THREE.Scene();

    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth/window.innerHeight,
      0.1,
      1000
    );

    const renderer = new THREE.WebGLRenderer({
      antialias:true
    });

    renderer.setSize(window.innerWidth, window.innerHeight);

    document.body.appendChild(renderer.domElement);

    // GEOMETRY
    const geometry = new THREE.TorusKnotGeometry(1,0.3,100,16);

    const material = new THREE.MeshStandardMaterial({
      color:0x00ffff,
      emissive:0x00ffff,
      metalness:1,
      roughness:0.1
    });

    const torus = new THREE.Mesh(geometry, material);

    scene.add(torus);

    // LIGHT
    const pointLight = new THREE.PointLight(0xffffff,2);

    pointLight.position.set(5,5,5);

    scene.add(pointLight);

    // PARTICLES
    const particlesGeometry = new THREE.BufferGeometry();

    const particlesCount = 6000;

    const posArray = new Float32Array(particlesCount * 3);

    for(let i=0; i<particlesCount * 3; i++){

      posArray[i] = (Math.random() - 0.5) * 100;

    }

    particlesGeometry.setAttribute(
      'position',
      new THREE.BufferAttribute(posArray,3)
    );

    const particlesMaterial = new THREE.PointsMaterial({
      size:0.02,
      color:0x00ffff
    });

    const particlesMesh = new THREE.Points(
      particlesGeometry,
      particlesMaterial
    );

    scene.add(particlesMesh);

    camera.position.z = 4;

    // ANIMATION
    function animate(){

      requestAnimationFrame(animate);

      torus.rotation.x += 0.01;
      torus.rotation.y += 0.01;

      particlesMesh.rotation.y += 0.0008;

      renderer.render(scene,camera);
    }

    animate();

    // RESPONSIVE
    window.addEventListener('resize',()=>{

      camera.aspect = window.innerWidth/window.innerHeight;

      camera.updateProjectionMatrix();

      renderer.setSize(
        window.innerWidth,
        window.innerHeight
      );

    });

  </script>

</body>
</html>


🎯 Final Look Idea
Header Animation → About Me → Skills → Stats → Snake Animation → Projects → Contact → Footer Wave
