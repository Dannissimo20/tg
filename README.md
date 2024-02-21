<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Telegram</title>
  <script src="https://telegram.org/js/telegram-web-app.js"></script>
  <style>
      body {
          margin: 0;
          padding: 0;
          font-family: Arial, sans-serif;
          box-sizing: border-box;
          color: var(--tg-theme-text-color);
          background: var(--tg-theme-bg-color);
      }

      #main {
          position: relative;
          max-width: 600px;
          margin: 200px auto 0 auto;
          padding: 20px;

          img {
              position: absolute;
              top: -100px;
              left: -50px;
              height: 100px;
          }
      }

      p {
          margin: 10px 0;
          font-size: 20px;
      }
  </style>
</head>
<body>
<div id="main">
  <img src="./logo.png" alt="logo">
  <p>Запись оформлена</p>
  <p>Дата: <span id="date"></span></p>
  <p>Время: <span id="time"></span></p>
  <p>Мастер: <span id="master"></span></p>
</div>
<script src="https://telegram.org/js/telegram-web-app.js"></script>
<script>
  let tg = window.Telegram.WebApp;
  tg.expand();

  async function fetchData() {
    try {
      const response = await fetch('https://api.telegram.org/bot6678468580:AAFFzk3hF3rwz0GIuUCQIKkQk4weMqBMHGI/getMe');
      const data = await response.json();

      Обновите ваши HTML-элементы полученными данными
      document.getElementById('date').textContent = data.result.time;
      document.getElementById('time').textContent = data.result.date;
      document.getElementById('master').textContent = data.result.name;
    } catch (error) {
      console.error('Ошибка при получении данных:', error);
    }
  }

  fetchData(); // Вызовите функцию при загрузке страницы
</script>
</body>
</html>
