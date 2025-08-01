<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ສະນັບສະໜູນໂດຍການຊື້ເຄື່ອງ</title>
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      background-color: #304674;
      color: #ffffff;
    }

    h1 {
      text-align: center;
      margin: 1rem 0;
      font-size: 1.8rem;
    }

    #loading {
      text-align: center;
      padding: 2rem;
      font-size: 1.2rem;
      color: #c0d6ff;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
      gap: 1rem;
      padding: 1rem;
      max-width: 800px;
      margin: auto;
    }

    .product {
      background-color: #3e598c;
      padding: 1rem;
      border-radius: 8px;
      text-align: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }

    .product img {
      width: 100%;
      height: auto;
      max-height: 120px;
      object-fit: cover;
      border-radius: 6px;
      margin-bottom: 0.5rem;
    }

    .product h2 {
      font-size: 1rem;
      margin: 0.5rem 0 0.2rem;
      color: #ffffff;
    }

    .product p {
      margin: 0;
      color: #a5d6ff;
      font-weight: bold;
    }

    .product a {
      display: inline-block;
      margin-top: 0.5rem;
      padding: 0.4rem 0.8rem;
      background-color: #00bfa5;
      color: white;
      border-radius: 4px;
      text-decoration: none;
      font-size: 0.9rem;
    }

    .product a:hover {
      background-color: #008e76;
    }
  </style>
</head>
<body>
  <h1>ສະນັບສະໜູນໂດຍການຊື້ເຄື່ອງ</h1>
  <div id="loading">ກຳລັງໂຫລດຂໍ້ມູນ...</div>
  <div id="product-list" class="products" style="display: none;"></div>

  <script>
    const API_URL = "https://script.google.com/macros/s/AKfycbwq5awwOMzMj3wPM8WFUlqpgW4Blbtygq81PgiO0XyfN2tPXlGpHLdq6GOCE9DKrQWbhg/exec";

    fetch(API_URL)
      .then((res) => res.json())
      .then((data) => {
        document.getElementById("loading").style.display = "none";
        const productList = document.getElementById("product-list");
        productList.style.display = "grid";

        data.forEach((item) => {
          const div = document.createElement("div");
          div.className = "product";
          div.innerHTML = `
            <img src="${item.Pictures}" alt="${item.Name}" loading="lazy" />
            <h2>${item.Name}</h2>
            <p>${item.Price} ກີບ</p>
            <a href="#">🛒 ສັ່ງຊື້</a>
          `;
          productList.appendChild(div);
        });
      })
      .catch((error) => {
        document.getElementById("loading").innerText = "ໂຫລດຂໍ້ມູນຫຼົ້ມເລວ 😢";
        console.error(error);
      });
  </script>
</body>
</html>
