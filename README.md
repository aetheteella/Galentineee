# Galentineee
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Valentine's Day Card</title>
  <link href="https://fonts.googleapis.com/css?family=Roboto|Pacifico" rel="stylesheet">
  <style>
    body {
      margin: 0;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-image: url('https://cdn.pixabay.com/photo/2021/01/15/18/58/heart-5917360_960_720.png');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }

    .envelope {
      content: url('https://assets.codepen.io/4927073/Envelope3.png');
      width: 430px;
      position: absolute;
      left: 18%;
      top: 3%;
      filter: drop-shadow(1.5px 0.75px 1.75px #4d4d4d);
      transition: width 0.3s ease-in-out;
    }

    .card {
      position: relative;
      width: 262px;
      height: 372px;
      margin: auto;
      box-shadow: inset 5px 0px 15px 0px rgba(0, 0, 0, 0.1),
        3px 0px 3px -2px rgba(0, 0, 0, 0.3);
      background-color: #fffffa;
      transform: scale(1.05);
      left: 12px;
      transform-origin: 50% 50%;
      perspective: 1000px;
      transition: all 0.5s ease-in-out;
    }

    .card .page {
      position: absolute;
      width: 100%;
      height: 100%;
      margin: -10px 0px 0px -10px;
      margin: auto;
      backface-visibility: hidden;
      transform-style: preserve-3d;
      transition: all 1.5s ease-in-out;
    }

    .card .front,
    .card .back,
    .card .page2 {
      transform: perspective(800px) rotateY(0deg);
      background-color: #fff;
      border-radius: 15px;
      overflow: hidden;
    }

    .card .front {
      background-image: url('https://cdn.pixabay.com/photo/2016/02/13/12/47/xoxo-1194444_960_720.png');
      background-size: cover;
      background-position: center;
      z-index: 1;
    }

    .card .back,
    .card .page2 {
      background-color: #f5a9b8;
      box-shadow: inset 0 0 15px rgba(0, 0, 0, 0.1);
      z-index: 2;
    }

    .card:hover .front {
      transform: perspective(800px) rotateY(-180deg);
    }

    .card:hover .back {
      transform: perspective(800px) rotateY(0deg);
    }

    .card .text-container {
      width: 80%;
      height: 80%;
      margin: auto;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Roboto', sans-serif;
      color: #fff;
      visibility: hidden;
      opacity: 0;
      transition: opacity 1s ease-in-out;
      text-align: center;
    }

    .text-container.show {
      visibility: visible;
      opacity: 1;
    }

    .text-container h1 {
      font-family: 'Pacifico', cursive;
      color: #fff;
      font-size: 2.5rem;
      text-shadow: 2px 4px 6px rgba(0, 0, 0, 0.2);
    }

    .text-container p {
      font-size: 1.25rem;
      color: #fff;
      margin: 20px 0;
    }

    @media (max-width: 1024px) {
      .envelope {
        width: 370px;
      }

      .card {
        width: 230px;
        height: 330px;
      }
    }

    @media (max-width: 675px) {
      .envelope {
        width: 320px;
      }

      .card {
        width: 200px;
        height: 290px;
      }
    }

  </style>
</head>

<body>

  <div class="envelope"></div>

  <div class="card" id="card">
    <!-- Front Page -->
    <div class="page front">
      <div class="text-container">
        <h1>Happy Valentine's Day!</h1>
        <p>Click to open the card and discover the love!</p>
      </div>
    </div>

    <!-- First Inside Page -->
    <div class="page back">
      <div class="text-container">
        <h1>Hey galentine gurl</h1>
        <p>                     "          Roses are red, Violets are blue, You're my sister, and I'm stuck with you! </p>
      </div>
    </div>

    <!-- Second Inside Page -->
    <div class="page page2">
      <div class="text-container">
        <h1>Appie valentine</h1>
        <p>""Together forever, we’ll always stay, Through thick and thin, come what may!"</p>
      </div>
    </div>

  </div>

  <script>
    let card = document.getElementById('card');
    let front = document.querySelector('.front');
    let back = document.querySelector('.back');
    let page2 = document.querySelector('.page2');

    // Card flip logic
    let currentPage = 0;
    const pages = [front, back, page2];

    card.addEventListener('click', function () {
      if (currentPage < pages.length - 1) {
        currentPage++;
      } else {
        currentPage = 0;
      }
      flipCard();
    });

    function flipCard() {
      pages.forEach((page, index) => {
        page.style.transform = `perspective(800px) rotateY(${(index - currentPage) * 180}deg)`;
        page.querySelector('.text-container').classList.toggle('show', index === currentPage);
      });
    }
  </script>

</body>
</html>

