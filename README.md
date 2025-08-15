<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>Love Animation</title>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <style>
    body {
      background: #111;
      color: white;
      font-size: 80px;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
    }
    .heart {
      opacity: 1;
    }
  </style>
</head>
<body>
  <div class="heart">❤️</div>
  <audio id="blop" src="https://www.soundjay.com/buttons/button-29.mp3"></audio>

  <script>
    const crtLoveTL = () => {
      const move = 1000;
      const boom = 200;
      const easing = "sin.inOut";
      const easingBoom = "sin.in";
      const easingOut = "sin.out";
      const opts = { duration: move, easing, opacity: 1 };
      const delta = 150;

      const el = {
        l: document.querySelector('.heart'),
        o: document.querySelector('.heart'),
        v: document.querySelector('.heart'),
        e: document.querySelector('.heart'),
        blop: document.getElementById('blop')
      };

      return new mojs.Timeline().add([
        new mojs.Tween({
          duration: move,
          onUpdate: (p) => {
            el.l.style.transform = scale(${1 + 0.5 * p});
          },
          onComplete: () => {
            [el.l, el.o, el.v, el.e].forEach((elem) => {
              elem.style.opacity = 0;
            });
            el.blop.play();
          }
        })
      ]);
    };

    const tl = crtLoveTL();
    tl.play();
  </script>
</body>
</html>
