<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Шкарпетки Nike</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.css">
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-XXXXXXXXXX');
  </script>
  <style>
    body { font-family: Arial, sans-serif; background-color: #fff; color: #333; margin: 0; padding: 0; }
    header { background-color: #111; color: #fff; padding: 20px 0; text-align: center; }
    .logo { font-size: 32px; font-weight: bold; }
    .container { padding: 20px; max-width: 800px; margin: auto; }
    .slider-container { margin-bottom: 20px; }
    .swiper-slide img { width: 100%; border-radius: 12px; object-fit: cover; height: 300px; }
    .price-block, .form-block { background: #f5f5f5; padding: 20px; border-radius: 12px; margin-top: 20px; }
    .form-block input, .form-block select, .form-block textarea { width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 8px; border: 1px solid #ccc; }
    .form-block label { display: block; margin-bottom: 5px; font-weight: bold; }
    .form-block button { width: 100%; padding: 12px; background: #111; color: #fff; border: none; border-radius: 8px; cursor: pointer; }
    .form-block button:hover { background: #444; }
    .opt-toggle, .call-request { margin-top: 10px; display: flex; justify-content: space-between; flex-wrap: wrap; gap: 10px; }
    .opt-toggle label, .call-request label { display: flex; align-items: center; gap: 5px; white-space: nowrap; }
    .footer { text-align: center; padding: 20px; background: #f5f5f5; margin-top: 40px; font-size: 14px; }
    .message { text-align: center; margin-top: 20px; color: green; font-weight: bold; display: none; }
  </style>
</head>
<body>
  <header>
    <div class="logo">Birkling Corp</div>
  </header>
  <div class="container">
    <div class="slider-container">
      <div class="swiper">
        <div class="swiper-wrapper">
          <div class="swiper-slide"><img src="https://i.imgur.com/ZtRLHZG.jpeg" alt="Шкарпетки Nike"></div>
          <div class="swiper-slide"><img src="https://i.imgur.com/9jstItx.jpeg" alt="Шкарпетки Nike"></div>
        </div>
        <div class="swiper-pagination"></div>
      </div>
    </div>
    <div class="price-block">
      <h2>Актуальні ціни</h2>
      <p><strong>Мінімальне замовлення:</strong> 12 пар</p>
      <p>1 упаковка (12 пар) – <strong>300 грн</strong></p>
      <p><strong>Оптова вартість:</strong></p>
      <ul>
        <li>240 пар – <strong>4080 грн</strong></li>
        <li>500+ пар – <strong>16 грн за пару</strong></li>
      </ul>
    </div>
    <div class="form-block">
      <form id="orderForm">
        <label for="name">ПІБ</label>
        <input type="text" name="name" required>

        <label for="email">Email</label>
        <input type="email" name="email" required>

        <label for="delivery">Служба доставки</label>
        <select name="delivery">
          <option value="Нова Пошта">Нова Пошта</option>
          <option value="Укрпошта">Укрпошта</option>
        </select>

        <label for="address">Адреса / Номер відділення</label>
        <input type="text" name="address" required>

        <label for="quantity">Кількість пар</label>
        <input type="number" name="quantity" id="quantity" value="12" step="12" min="12" required>

        <div class="opt-toggle">
          <label><input type="radio" name="opt" value="240 пар" onclick="disableQuantity(true)"> Опт 240 пар</label>
          <label><input type="radio" name="opt" value="500+ пар" onclick="disableQuantity(true)"> Опт 500+ пар</label>
          <label><input type="radio" name="opt" value="Роздріб" onclick="disableQuantity(false)" checked> Роздріб</label>
        </div>

        <div class="call-request">
          <label><input type="checkbox" name="call_request" id="call_request"> Зателефонувати мені</label>
        </div>

        <label for="comment">Коментар до замовлення (за бажанням)</label>
        <textarea name="comment" rows="3" placeholder="Напишіть, якщо є додаткові побажання..."></textarea>

        <button type="submit">Оформити замовлення</button>
      </form>
      <p class="message" id="successMessage">Ваше замовлення успішно оформлене, очікуйте повідомлення про прибуття</p>
    </div>
    <div class="price-block">
      <h3>Передоплата</h3>
      <p>Для підтвердження замовлення просимо надіслати мінімальну передоплату <strong>200 грн</strong> на картку:</p>
      <p><strong>4314 1402 1195 9843</strong></p>
      <p>Це гарантія того, що ви прийдете на пошту, і ми не сплачуватимемо доставку за власні кошти.</p>
    </div>
    <div class="footer">
      Телеграм для звʼязку: <a href="https://t.me/andrii_admin">@andrii_admin</a><br>
      Email: <a href="mailto:BirklingCorp@gmail.com">BirklingCorp@gmail.com</a><br>
      Переглядів сайту: <span id="counter">0</span>
    </div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.js"></script>
  <script>
    new Swiper('.swiper', {
      pagination: { el: '.swiper-pagination', clickable: true },
      loop: true
    });

    const form = document.getElementById('orderForm');
    const successMessage = document.getElementById('successMessage');

    form.addEventListener('submit', function (e) {
      e.preventDefault();
      const formData = new FormData(form);
      fetch('https://formspree.io/f/xkndydgp', {
        method: 'POST',
        body: formData,
        headers: { 'Accept': 'application/json' }
      }).then(response => {
        if (response.ok) {
          successMessage.style.display = 'block';
          form.reset();
        } else {
          alert('Щось пішло не так. Спробуйте ще раз.');
        }
      });
    });

    function disableQuantity(disable) {
      document.getElementById('quantity').disabled = disable;
    }

    document.addEventListener('DOMContentLoaded', () => {
      let views = localStorage.getItem('siteViews') || 0;
      views++;
      localStorage.setItem('siteViews', views);
      document.getElementById('counter').textContent = views;
    });
  </script>
</body>
</html>

