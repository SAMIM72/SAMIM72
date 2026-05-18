<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Code Logo Design</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
    }

    body{
      height:100vh;
      display:flex;
      justify-content:center;
      align-items:center;
      background:#0d1117;
      font-family:Arial, sans-serif;
    }

    .logo-box{
      position:relative;
      width:260px;
      height:260px;
      display:flex;
      justify-content:center;
      align-items:center;
    }

    /* Back Gray Design */
    .gray1,
    .gray2,
    .gray3,
    .gray4{
      position:absolute;
      width:70px;
      height:70px;
      background:linear-gradient(to bottom,#bdbdbd,#5c5c5c);
      border-radius:20px;
      z-index:1;
    }

    .gray1{
      top:10px;
      left:10px;
      transform:rotate(45deg);
    }

    .gray2{
      top:10px;
      right:10px;
      transform:rotate(45deg);
    }

    .gray3{
      bottom:10px;
      left:10px;
      transform:rotate(45deg);
    }

    .gray4{
      bottom:10px;
      right:10px;
      transform:rotate(45deg);
    }

    /* Yellow Layer */
    .yellow-layer{
      position:absolute;
      width:200px;
      height:200px;
      background:linear-gradient(135deg,#ffd633,#ffb300);
      transform:rotate(45deg);
      border-radius:35px;
      z-index:2;
    }

    /* Orange Main Shape */
    .main-logo{
      position:absolute;
      width:180px;
      height:180px;
      background:linear-gradient(135deg,#ff5722,#ff9800);
      transform:rotate(45deg);
      border-radius:35px;
      z-index:3;
      display:flex;
      justify-content:center;
      align-items:center;
    }

    /* White Circle */
    .circle{
      width:100px;
      height:100px;
      border:8px solid white;
      border-radius:50%;
      background:transparent;
      display:flex;
      justify-content:center;
      align-items:center;
      transform:rotate(-45deg);
    }

    /* Code Symbol */
    .code{
      color:white;
      font-size:48px;
      font-weight:bold;
    }

  </style>
</head>

<body>

  <div class="logo-box">

    <div class="gray1"></div>
    <div class="gray2"></div>
    <div class="gray3"></div>
    <div class="gray4"></div>

    <div class="yellow-layer"></div>

    <div class="main-logo">
      <div class="circle">
        <div class="code">&lt;/&gt;</div>
      </div>
    </div>

  </div>

</body>
</html>
 
