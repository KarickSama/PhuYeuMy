# PhuYeuMy
github.com/KarickSama/PhuYeuMy
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Anh Yêu My Lắm 💖</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: black;
      overflow: hidden;
      height: 100%;
    }

    .falling-text {
      position: absolute;
      color: hotpink;
      font-size: 24px;
      font-weight: bold;
      cursor: pointer;
      animation: fall linear forwards;
      user-select: none;
    }

    @keyframes fall {
      0% {
        transform: translateY(-50px);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh);
        opacity: 0;
      }
    }

    .heart {
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: pink;
      transform: rotate(45deg);
      animation: floatUp 6s ease-in infinite;
    }

    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: pink;
      border-radius: 50%;
    }

    .heart::before {
      top: -5px;
      left: 0;
    }

    .heart::after {
      left: -5px;
      top: 0;
    }

    @keyframes floatUp {
      0% {
        bottom: -20px;
        opacity: 0;
        transform: translateX(0);
      }
      50% {
        opacity: 1;
        transform: translateX(20px);
      }
      100% {
        bottom: 100vh;
        opacity: 0;
        transform: translateX(-20px);
      }
    }

    .burst-heart {
      position: absolute;
      color: hotpink;
      font-size: 30px;
      animation: explode 1s ease-out forwards;
      pointer-events: none;
    }

    @keyframes explode {
      0% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        transform: scale(3);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

<script>
  // Chữ rơi liên tục
  setInterval(() => {
    const text = document.createElement("div");
    text.className = "falling-text";
    text.innerText = "Anh Yêu My Lắm 💖";
    text.style.left = Math.random() * window.innerWidth + "px";
    text.style.animationDuration = (3 + Math.random() * 2) + "s";

    // Khi bấm vào chữ rơi thì pháo hoa trái tim
    text.addEventListener("click", (e) => {
      for (let i = 0; i < 8; i++) {
        const burst = document.createElement("div");
        burst.className = "burst-heart";
        burst.innerText = "💖";
        burst.style.left = e.clientX + (Math.random() * 60 - 30) + "px";
        burst.style.top = e.clientY + (Math.random() * 60 - 30) + "px";
        document.body.appendChild(burst);
        setTimeout(() => burst.remove(), 1000);
      }
    });

    document.body.appendChild(text);
    setTimeout(() => text.remove(), 7000);
  }, 300);

  // Trái tim bay liên tục
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.style.left = Math.random() * window.innerWidth + "px";
    heart.style.bottom = "0px";
    heart.style.opacity = Math.random();
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 200);
</script>

</body>
</html>
