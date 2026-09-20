<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>For Lisa 💗</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #ffd6e7, #fff0f6);
    }

    .container {
      text-align: center;
      width: 90%;
      max-width: 500px;
      padding: 30px;
    }

    h1 {
      color: #ff4f91;
      font-size: 32px;
      margin-bottom: 30px;
    }

    .buttons {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 20px;
      min-height: 100px;
    }

    button {
      border: none;
      border-radius: 15px;
      padding: 14px 28px;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yes {
      background: #ff4f91;
      color: white;
    }

    #no {
      background: #777;
      color: white;
    }

    #message {
      margin-top: 25px;
      color: #ff4f91;
      font-size: 18px;
      min-height: 30px;
    }

    #success {
      display: none;
      animation: pop 0.7s ease;
    }

    .bears {
      font-size: 90px;
      margin: 20px 0;
      animation: bounce 1.5s infinite;
    }

    .hearts {
      position: fixed;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
    }

    .heart {
      position: absolute;
      bottom: -50px;
      font-size: 25px;
      animation: floatUp 4s linear forwards;
    }

    @keyframes floatUp {
      from {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }

      to {
        transform: translateY(-110vh) rotate(360deg);
        opacity: 0;
      }
    }

    @keyframes pop {
      0% {
        transform: scale(0);
      }
      80% {
        transform: scale(1.15);
      }
      100% {
        transform: scale(1);
      }
    }

    @keyframes bounce {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-12px);
      }
    }

    .love-text {
      color: #ff4f91;
      font-size: 26px;
      font-weight: bold;
    }

    .subtext {
      color: #777;
      font-size: 18px;
    }
  </style>
</head>

<body>

  <div class="hearts" id="hearts"></div>

  <div class="container" id="question">

    <h1 id="questionText">Lisa... do you love me? 🥺💗</h1>

    <div class="buttons">
      <button id="yes">YES 💗</button>
      <button id="no">NO 😭</button>
    </div>

    <div id="message"></div>

  </div>


  <div class="container" id="success">

    <div class="bears">🧸💗🧸</div>

    <div class="love-text">
      I KNEW YOU WOULD SAY YES 😭💗
    </div>

    <p class="subtext">
      I love you so much, Lisa 🥺💕
    </p>

    <div style="font-size: 35px;">
      💕 💗 💖 💞 💓
    </div>

  </div>


  <script>

    const yesButton = document.getElementById("yes");
    const noButton = document.getElementById("no");
    const message = document.getElementById("message");

    const question = document.getElementById("question");
    const success = document.getElementById("success");

    let noCount = 0;

    const messages = [
      "Are you sure? 🥺",
      "Please think twice 😭",
      "Pleeeease Lisa 🥹💗",
      "Don't do this to me 😭",
      "One more chance? 🥺",
      "The YES button looks better 👀💗",
      "PLEASEEEEE 😭💕",
      "You really want to say no?? 😭",
      "I'm gonna cry now 🥲💔",
      "Okay... think VERY carefully 😭💗"
    ];

    noButton.addEventListener("click", () => {

      noCount++;

      // Make NO smaller
      const newNoSize = Math.max(8, 20 - noCount * 2);
      noButton.style.fontSize = newNoSize + "px";

      noButton.style.padding =
        Math.max(3, 14 - noCount) + "px " +
        Math.max(6, 28 - noCount * 2) + "px";

      // Make YES bigger
      const newYesSize = 20 + noCount * 5;
      yesButton.style.fontSize = newYesSize + "px";

      yesButton.style.padding =
        (14 + noCount * 2) + "px " +
        (28 + noCount * 4) + "px";

      // Change message
      message.textContent =
        messages[Math.min(noCount - 1, messages.length - 1)];

      // Eventually make NO almost disappear
      if (noCount >= 8) {
        noButton.style.opacity = "0.3";
      }

    });


    yesButton.addEventListener("click", () => {

      question.style.display = "none";
      success.style.display = "block";

      createHearts();

    });


    function createHearts() {

      const heartContainer = document.getElementById("hearts");

      setInterval(() => {

        const heart = document.createElement("div");

        heart.classList.add("heart");

        const heartTypes = ["💗", "💕", "💖", "💘", "💓", "❤️"];

        heart.textContent =
          heartTypes[Math.floor(Math.random() * heartTypes.length)];

        heart.style.left = Math.random() * 100 + "vw";

        heart.style.fontSize =
          (20 + Math.random() * 30) + "px";

        heart.style.animationDuration =
          (3 + Math.random() * 3) + "s";

        heartContainer.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 6000);

      }, 250);

    }

  </script>

</body>
</html>
