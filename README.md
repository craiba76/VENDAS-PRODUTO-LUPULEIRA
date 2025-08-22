<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lupuleira Cervejaria</title>
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-50 font-sans">

<!-- Header -->
<header class="bg-yellow-600 text-white p-6 text-center">
  <h1 class="text-3xl font-bold">Lupuleira Cervejaria</h1>
  <p class="mt-2">Escolha sua cerveja e peça pelo WhatsApp!</p>
</header>

<!-- Produtos -->
<main class="max-w-6xl mx-auto p-6 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">

  <!-- Produto -->
  <div class="bg-white shadow rounded p-4 flex flex-col items-center">
    <img src="https://via.placeholder.com/200x200?text=IPA" alt="Lupuleira IPA" class="rounded mb-4">
    <h2 class="text-xl font-bold mb-2">Lupuleira IPA</h2>
    <p class="mb-2">Cerveja artesanal lupulada, sabor intenso.</p>
    <p class="mb-4 font-semibold">R$ 20,00</p>
    <input type="number" min="0" value="0" class="border p-1 w-16 text-center mb-2 quantity" data-name="Lupuleira IPA" data-price="20">
  </div>

  <div class="bg-white shadow rounded p-4 flex flex-col items-center">
    <img src="https://via.placeholder.com/200x200?text=Pilsen" alt="Lupuleira Pilsen" class="rounded mb-4">
    <h2 class="text-xl font-bold mb-2">Lupuleira Pilsen</h2>
    <p class="mb-2">Leve e refrescante.</p>
    <p class="mb-4 font-semibold">R$ 18,00</p>
    <input type="number" min="0" value="0" class="border p-1 w-16 text-center mb-2 quantity" data-name="Lupuleira Pilsen" data-price="18">
  </div>

  <div class="bg-white shadow rounded p-4 flex flex-col items-center">
    <img src="https://via.placeholder.com/200x200?text=Stout" alt="Lupuleira Stout" class="rounded mb-4">
    <h2 class="text-xl font-bold mb-2">Lupuleira Stout</h2>
    <p class="mb-2">Escura, encorpada e cremosa.</p>
    <p class="mb-4 font-semibold">R$ 22,00</p>
    <input type="number" min="0" value="0" class="border p-1 w-16 text-center mb-2 quantity" data-name="Lupuleira Stout" data-price="22">
  </div>

  <div class="bg-white shadow rounded p-4 flex flex-col items-center">
    <img src="https://via.placeholder.com/200x200?text=Weiss" alt="Lupuleira Weiss" class="rounded mb-4">
    <h2 class="text-xl font-bold mb-2">Lupuleira Weiss</h2>
    <p class="mb-2">Cerveja de trigo, suave.</p>
    <p class="mb-4 font-semibold">R$ 19,00</p>
    <input type="number" min="0" value="0" class="border p-1 w-16 text-center mb-2 quantity" data-name="Lupuleira Weiss" data-price="19">
  </div>

  <div class="bg-white shadow rounded p-4 flex flex-col items-center">
    <img src="https://via.placeholder.com/200x200?text=Session+IPA" alt="Lupuleira Session IPA" class="rounded mb-4">
    <h2 class="text-xl font-bold mb-2">Lupuleira Session IPA</h2>
    <p class="mb-2">Sabor marcante, baixo teor alcoólico.</p>
    <p class="mb-4 font-semibold">R$ 21,00</p>
    <input type="number" min="0" value="0" class="border p-1 w-16 text-center mb-2 quantity" data-name="Lupuleira Session IPA" data-price="21">
  </div>

</main>

<!-- Botão WhatsApp -->
<div class="fixed bottom-4 right-4">
  <button id="whatsappBtn" class="bg-green-500 text-white px-6 py-3 rounded-full shadow-lg hover:bg-green-600">
    Pedir pelo WhatsApp
  </button>
</div>

<!-- JS -->
<script>
  document.getElementById('whatsappBtn').addEventListener('click', function() {
    const quantities = document.querySelectorAll('.quantity');
    let message = "Olá, quero pedir:%0A";
    let total = 0;
    quantities.forEach(qty => {
      const value = parseInt(qty.value);
      if (value > 0) {
        const name = qty.getAttribute('data-name');
        const price = parseFloat(qty.getAttribute('data-price'));
        total += value * price;
        message += `- ${value}x ${name}%0A`;
      }
    });
    if(total === 0){
      alert("Escolha pelo menos um produto!");
      return;
    }
    message += `Valor total: R$ ${total.toFixed(2)}`;
    const phone = "559199999999"; // Substitua pelo número real do WhatsApp
    const url = `https://wa.me/${phone}?text=${message}`;
    window.open(url, "_blank");
  });
</script>

</body>
</html>
