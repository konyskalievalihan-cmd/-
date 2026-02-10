<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>💘</title>

<style>
  body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ffdde1, #ee9ca7);
    height: 100vh;
    overflow: hidden;
  }

  .box {
    position: relative;
    top: 50%;
    transform: translateY(-50%);
    margin: auto;
    background: white;
    padding: 25px;
    border-radius: 15px;
    width: 90%;
    max-width: 350px;
    text-align: center;
    z-index: 2;
  }

  h1 {
    margin-bottom: 25px;
  }

  button {
    font-size: 18px;
    padding: 10px 22px;
    margin: 10px;
    border: none;
    border-radius: 12px;
    cursor: pointer;
  }

  #yes {
    background: #ff4d6d;
    color: white;
    transition: transform 0.3s;
  }

  #no {
    background: #ddd;
    position: relative;
  }

  /* сердечки */
  .heart {
    position: absolute;
    color: #ff4d6d;
    font-size: 20px;
    animation: float 6s linear infinite;
    opacity: 0.8;
  }

  @keyframes float {
    0% {
      transform: translateY(100vh) scale(1);
      opacity: 1;
    }
    100% {
      transform: translateY(-10vh) scale(1.5);
      opacity: 0;
    }
  }
</style>
</head>

<body>

<div class="box">
  <h1>Давай погуляем 14 февраля? 💌</h1>
  <button id="yes">Да</button>
  <button id="no">Нет</button>
</div>

<script>
  const yesBtn = document.getElementById("yes");
  const noBtn = document.getElementById("no");

  let scale = 1;
  let clickCount = 0;

  const noTexts = [
    "Нет",
    "Ой…",
    "Давай погуляем",
    "Просто по Атакенту будем ходить 😅"
  ];

  noBtn.onclick = () => {
    scale += 0.2;
    yesBtn.style.transform = `scale(${scale})`;

    clickCount++;

    if (clickCount < noTexts.length) {
      noBtn.innerText = noTexts[clickCount];
    } else {
      moveNoButton();
    }
  };

  function moveNoButton() {
    const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
    const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
    noBtn.style.position = "fixed";
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  }

  yesBtn.onclick = () => {
    document.body.innerHTML = `
      <h1 style="text-align:center; margin-top:40vh;">
        Урааа ❤️<br>Тогда договорились 😉
      </h1>
    `;
  };

  // сердечки
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerText = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (16 + Math.random() * 20) + "px";
    document.body.appendChild(heart);

    setTimeout(() => heart.remove(), 6000);
  }, 300);
</script>

</body>
</html>
