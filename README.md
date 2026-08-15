## Hi there 👋

<!--
**Farm16k/Farm16k** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
farmer-16/
├── public/
│   └── index.html
├── server.js
├── package.json
└── .env
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Farmer 16</title>

  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #eef7e9;
      color: #243024;
    }

    .app {
      max-width: 520px;
      margin: auto;
      min-height: 100vh;
      padding-bottom: 30px;
    }

    header {
      background: #4d8b3d;
      color: white;
      padding: 22px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 30px;
    }

    header p {
      margin: 7px 0 0;
    }

    .page {
      display: none;
      padding: 20px;
    }

    .page.active {
      display: block;
    }

    .hero {
      background: white;
      border-radius: 20px;
      padding: 30px 20px;
      text-align: center;
      margin-top: 20px;
      box-shadow: 0 5px 15px rgba(0,0,0,.08);
    }

    .farmer {
      font-size: 85px;
    }

    .hero h2 {
      font-size: 25px;
    }

    button {
      border: 0;
      border-radius: 13px;
      padding: 14px 18px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }

    .primary {
      background: #4d8b3d;
      color: white;
      width: 100%;
    }

    .secondary {
      background: #ddd;
      color: #222;
      width: 100%;
      margin-top: 10px;
    }

    .products {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    .product {
      background: white;
      border-radius: 18px;
      padding: 17px;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0,0,0,.07);
    }

    .product-icon {
      font-size: 45px;
    }

    .product h3 {
      margin: 8px 0;
    }

    .price {
      font-weight: bold;
      font-size: 18px;
      margin-bottom: 10px;
    }

    .cart-item {
      background: white;
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .quantity {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .quantity button {
      padding: 7px 11px;
      background: #dcebd7;
    }

    .total {
      background: white;
      border-radius: 15px;
      padding: 18px;
      margin: 15px 0;
      font-size: 20px;
      font-weight: bold;
      text-align: right;
    }

    input {
      width: 100%;
      padding: 14px;
      margin: 7px 0;
      border: 1px solid #ccc;
      border-radius: 12px;
      font-size: 16px;
    }

    textarea {
      width: 100%;
      min-height: 100px;
      padding: 14px;
      margin: 7px 0;
      border: 1px solid #ccc;
      border-radius: 12px;
      font-size: 16px;
      resize: vertical;
    }

    .success {
      text-align: center;
      background: white;
      border-radius: 20px;
      padding: 30px 20px;
    }

    .success-icon {
      font-size: 65px;
    }

    .back {
      margin-bottom: 15px;
      background: transparent;
      padding: 5px;
      color: #4d8b3d;
    }

    .empty {
      text-align: center;
      padding: 40px 10px;
    }

    .cart-button {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      width: min(480px, calc(100% - 30px));
      background: #e6a817;
      color: #fff;
      z-index: 10;
      box-shadow: 0 5px 15px rgba(0,0,0,.2);
    }

    .hidden {
      display: none !important;
    }
  </style>
</head>

<body>

<div class="app">

  <header>
    <h1>🌾 Farmer 16</h1>
    <p id="welcome">Bienvenue dans notre boutique</p>
  </header>

  <!-- ACCUEIL -->
  <section id="home" class="page active">

    <div class="hero">

      <div class="farmer">👨‍🌾</div>

      <h2>Bienvenue chez Farmer 16</h2>

      <p>
        Découvrez notre sélection de produits légaux.
      </p>

      <button class="primary" onclick="showPage('shop')">
        🛍️ Ouvrir la boutique
      </button>

    </div>

  </section>

  <!-- BOUTIQUE -->
  <section id="shop" class="page">

    <button class="back" onclick="showPage('home')">
      ← Retour
    </button>

    <h2>🛍️ Boutique</h2>

    <div class="products">

      <div class="product">
        <div class="product-icon">🌱</div>
        <h3>Produit A</h3>
        <div class="price">10 €</div>
        <button class="primary" onclick="addToCart('Produit A', 10)">
          Ajouter
        </button>
      </div>

      <div class="product">
        <div class="product-icon">🌿</div>
        <h3>Produit B</h3>
        <div class="price">20 €</div>
        <button class="primary" onclick="addToCart('Produit B', 20)">
          Ajouter
        </button>
      </div>

      <div class="product">
        <div class="product-icon">🌾</div>
        <h3>Produit C</h3>
        <div class="price">50 €</div>
        <button class="primary" onclick="addToCart('Produit C', 50)">
          Ajouter
        </button>
      </div>

      <div class="product">
        <div class="product-icon">📦</div>
        <h3>Produit D</h3>
        <div class="price">90 €</div>
        <button class="primary" onclick="addToCart('Produit D', 90)">
          Ajouter
        </button>
      </div>

    </div>

  </section>

  <!-- PANIER -->
  <section id="cart" class="page">

    <button class="back" onclick="showPage('shop')">
      ← Boutique
    </button>

    <h2>🛒 Mon panier</h2>

    <div id="cartItems"></div>

    <div id="emptyCart" class="empty hidden">
      <div style="font-size:50px">🛒</div>
      <p>Ton panier est vide.</p>
      <button class="primary" onclick="showPage('shop')">
        Voir la boutique
      </button>
    </div>

    <div id="cartBottom">

      <div class="total">
        Total : <span id="total">0.00 €</span>
      </div>

      <button class="primary" onclick="showPage('checkout')">
        Continuer la commande
      </button>

    </div>

  </section>

  <!-- FORMULAIRE -->
  <section id="checkout" class="page">

    <button class="back" onclick="showPage('cart')">
      ← Panier
    </button>

    <h2>📦 Informations de livraison</h2>

    <p>
      Renseigne les informations nécessaires à la livraison.
    </p>

    <input
      id="firstName"
      type="text"
      placeholder="Prénom"
      autocomplete="given-name"
    >

    <input
      id="lastName"
      type="text"
      placeholder="Nom"
      autocomplete="family-name"
    >

    <textarea
      id="address"
      placeholder="Adresse complète"
      autocomplete="street-address"
    ></textarea>

    <input
      id="city"
      type="text"
      placeholder="Ville"
      autocomplete="address-level2"
    >

    <input
      id="postalCode"
      type="text"
      placeholder="Code postal"
      autocomplete="postal-code"
    >

    <button class="primary" onclick="submitOrder()">
      ✅ Valider ma commande
    </button>

  </section>

  <!-- SUCCÈS -->
  <section id="success" class="page">

    <div class="success">

      <div class="success-icon">✅</div>

      <h2>Commande reçue !</h2>

      <p>
        Merci pour ta commande.
      </p>

      <p>
        Numéro de commande :
        <strong id="orderNumber"></strong>
      </p>

      <button class="primary" onclick="showPage('home')">
        Retour à l'accueil
      </button>

    </div>

  </section>

</div>

<button
  id="cartButton"
  class="cart-button hidden"
  onclick="showPage('cart')"
>
  🛒 Panier (<span id="cartCount">0</span>)
</button>


<script>

  const tg = window.Telegram?.WebApp;

  if (tg) {
    tg.ready();
    tg.expand();

    if (tg.setHeaderColor) {
      tg.setHeaderColor("#4d8b3d");
    }

    if (tg.setBackgroundColor) {
      tg.setBackgroundColor("#eef7e9");
    }

    const user = tg.initDataUnsafe?.user;

    if (user) {
      document.getElementById("welcome").textContent =
        "Bonjour " + (user.first_name || "à vous") + " 👋";
    }
  }


  let cart = [];


  function showPage(pageName) {

    document.querySelectorAll(".page").forEach(page => {
      page.classList.remove("active");
    });

    document.getElementById(pageName).classList.add("active");

    updateCart();

    window.scrollTo({
      top: 0,
      behavior: "smooth"
    });
  }


  function addToCart(name, price) {

    const existing = cart.find(
      item => item.name === name
    );

    if (existing) {
      existing.quantity++;
    } else {
      cart.push({
        name: name,
        price: price,
        quantity: 1
      });
    }

    updateCart();

    if (tg?.HapticFeedback) {
      tg.HapticFeedback.impactOccurred("light");
    }

    alert("Produit ajouté au panier.");
  }


  function removeFromCart(index) {

    cart.splice(index, 1);

    updateCart();
  }


  function changeQuantity(index, amount) {

    cart[index].quantity += amount;

    if (cart[index].quantity <= 0) {
      cart.splice(index, 1);
    }

    updateCart();
  }


  function updateCart() {

    const container =
      document.getElementById("cartItems");

    container.innerHTML = "";

    let total = 0;
    let count = 0;

    cart.forEach((item, index) => {

      total += item.price * item.quantity;
      count += item.quantity;

      const div =
        document.createElement("div");

      div.className = "cart-item";

      div.innerHTML = `
        <div>
          <strong>${escapeHtml(item.name)}</strong>
          <br>
          ${item.price.toFixed(2)} € × ${item.quantity}
        </div>

        <div class="quantity">

          <button onclick="changeQuantity(${index}, -1)">
            −
          </button>

          <strong>${item.quantity}</strong>

          <button onclick="changeQuantity(${index}, 1)">
            +
          </button>

          <button onclick="removeFromCart(${index})">
            🗑️
          </button>

        </div>
      `;

      container.appendChild(div);

    });

    document.getElementById("total").textContent =
      total.toFixed(2) + " €";

    document.getElementById("cartCount").textContent =
      count;

    const empty =
      document.getElementById("emptyCart");

    const bottom =
      document.getElementById("cartBottom");

    if (cart.length === 0) {
      empty.classList.remove("hidden");
      bottom.classList.add("hidden");
    } else {
      empty.classList.add("hidden");
      bottom.classList.remove("hidden");
    }

    const cartButton =
      document.getElementById("cartButton");

    if (count > 0) {
      cartButton.classList.remove("hidden");
    } else {
      cartButton.classList.add("hidden");
    }
  }


  async function submitOrder() {

    if (cart.length === 0) {
      alert("Ton panier est vide.");
      return;
    }

    const firstName =
      document.getElementById("firstName").value.trim();

    const lastName =
      document.getElementById("lastName").value.trim();

    const address =
      document.getElementById("address").value.trim();

    const city =
      document.getElementById("city").value.trim();

    const postalCode =
      document.getElementById("postalCode").value.trim();


    if (
      !firstName ||
      !lastName ||
      !address ||
      !city ||
      !postalCode
    ) {

      alert(
        "Merci de remplir tous les champs."
      );

      return;
    }


    const order = {

      firstName,
      lastName,
      address,
      city,
      postalCode,

      items: cart,

      total: cart.reduce(
        (sum, item) =>
          sum + item.price * item.quantity,
        0
      ),

      telegramUser:
        tg?.initDataUnsafe?.user || null

    };


    try {

      const response =
        await fetch("/api/order", {

          method: "POST",

          headers: {
            "Content-Type": "application/json"
          },

          body: JSON.stringify(order)

        });


      const result =
        await response.json();


      if (!response.ok) {
        throw new Error(
          result.error || "Erreur serveur"
        );
      }


      document.getElementById(
        "orderNumber"
      ).textContent = result.orderNumber;


      cart = [];

      updateCart();

      showPage("success");


      if (tg?.HapticFeedback) {
        tg.HapticFeedback.notificationOccurred("success");
      }

    } catch (error) {

      console.error(error);

      alert(
        "Impossible d'envoyer la commande. Réessaie."
      );

    }

  }


  function escapeHtml(value) {

    return String(value)
      .replaceAll("&", "&amp;")
      .replaceAll("<", "&lt;")
      .replaceAll(">", "&gt;")
      .replaceAll('"', "&quot;")
      .replaceAll("'", "&#039;");

  }


  updateCart();

</script>

</body>
</html>
const express = require("express");
const path = require("path");
require("dotenv").config();

const app = express();

const PORT = process.env.PORT || 3000;

const BOT_TOKEN = process.env.BOT_TOKEN;
const ADMIN_CHAT_ID = process.env.ADMIN_CHAT_ID;


if (!BOT_TOKEN || !ADMIN_CHAT_ID) {
  console.error(
    "BOT_TOKEN ou ADMIN_CHAT_ID manquant dans .env"
  );

  process.exit(1);
}


app.use(express.json());

app.use(express.static(
  path.join(__dirname, "public")
));


function escapeTelegram(text) {

  return String(text)
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;");

}


app.post("/api/order", async (req, res) => {

  try {

    const {
      firstName,
      lastName,
      address,
      city,
      postalCode,
      items,
      total,
      telegramUser
    } = req.body;


    if (
      !firstName ||
      !lastName ||
      !address ||
      !city ||
      !postalCode ||
      !Array.isArray(items) ||
      items.length === 0
    ) {

      return res.status(400).json({
        error: "Données de commande invalides."
      });

    }


    const orderNumber =
      "F16-" +
      Date.now().toString().slice(-8);


    let products = "";

    for (const item of items) {

      products +=
        `• ${escapeTelegram(item.name)} × ${item.quantity} — ` +
        `${Number(item.price * item.quantity).toFixed(2)} €\n`;

    }


    const telegramName =
      telegramUser?.first_name || "Non renseigné";


    const telegramUsername =
      telegramUser?.username
        ? "@" + telegramUser.username
        : "Non renseigné";


    const message =

      `🌾 <b>NOUVELLE COMMANDE — FARMER 16</b>\n\n` +

      `🆔 <b>Commande :</b> ${orderNumber}\n\n` +

      `👤 <b>Client</b>\n` +
      `Prénom : ${escapeTelegram(firstName)}\n` +
      `Nom : ${escapeTelegram(lastName)}\n\n` +

      `📍 <b>Adresse</b>\n` +
      `${escapeTelegram(address)}\n` +
      `${escapeTelegram(postalCode)} ${escapeTelegram(city)}\n\n` +

      `📦 <b>Produits</b>\n` +
      products +

      `\n💰 <b>Total :</b> ${Number(total).toFixed(2)} €\n\n` +

      `📱 <b>Telegram</b>\n` +
      `Prénom Telegram : ${escapeTelegram(telegramName)}\n` +
      `Compte : ${escapeTelegram(telegramUsername)}`;


    const telegramResponse =
      await fetch(
        `https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`,
        {
          method: "POST",

          headers: {
            "Content-Type": "application/json"
          },

          body: JSON.stringify({
            chat_id: ADMIN_CHAT_ID,
            text: message,
            parse_mode: "HTML"
          })
        }
      );


    const telegramResult =
      await telegramResponse.json();


    if (!telegramResponse.ok || !telegramResult.ok) {

      console.error(
        "Telegram error:",
        telegramResult
      );

      return res.status(500).json({
        error: "Impossible d'envoyer la notification Telegram."
      });

    }


    res.json({
      success: true,
      orderNumber
    });


  } catch (error) {

    console.error(error);

    res.status(500).json({
      error: "Erreur interne."
    });

  }

});


app.listen(PORT, () => {

  console.log(
    `Farmer 16 lancé sur le port ${PORT}`
  );

});
