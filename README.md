<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Roblox Scripts Atualizados 2026</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-950 text-white min-h-screen">

  <!-- HEADER -->
  <header class="bg-gray-900 border-b border-gray-800 sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
      <h1 class="text-2xl font-bold text-green-400">Roblox Scripts Atualizados 2026</h1>

      <nav class="flex gap-6 text-sm font-semibold">
        <a href="#inicio" class="hover:text-green-400 transition">Início</a>
        <a href="#produtos" class="hover:text-green-400 transition">Scripts</a>
        <a href="#adicionar" class="hover:text-green-400 transition">Adicionar</a>
      </nav>
    </div>
  </header>

  <!-- HERO -->
  <section id="inicio" class="py-20 px-6 text-center bg-gradient-to-b from-gray-900 to-gray-950">
    <h2 class="text-5xl font-extrabold mb-6">
      Loja de Scripts Lua Roblox
    </h2>

    <p class="text-gray-300 max-w-2xl mx-auto text-lg">
      Venda e organize seus scripts Roblox em um site moderno.
      Adicione nome, descrição e código Lua diretamente na página.
    </p>

    <button onclick="document.getElementById('adicionar').scrollIntoView({behavior:'smooth'})"
      class="mt-8 bg-green-500 hover:bg-green-400 transition px-8 py-4 rounded-2xl text-black font-bold shadow-lg">
      Adicionar Novo Script
    </button>
  </section>

  <!-- FORM -->
  <section id="adicionar" class="max-w-5xl mx-auto px-6 py-14">
    <div class="bg-gray-900 rounded-3xl p-8 border border-gray-800 shadow-2xl">
      <h3 class="text-3xl font-bold mb-8 text-green-400">
        Adicionar Script
      </h3>

      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label class="block mb-2 font-semibold">Nome do Script</label>
          <input id="nome"
            type="text"
            placeholder="Ex: Auto Farm Driving Empire"
            class="w-full bg-gray-800 border border-gray-700 rounded-xl px-4 py-3 outline-none focus:border-green-400" />
        </div>

        <div>
          <label class="block mb-2 font-semibold">Preço</label>
          <input id="preco"
            type="text"
            placeholder="Ex: R$ 19,90"
            class="w-full bg-gray-800 border border-gray-700 rounded-xl px-4 py-3 outline-none focus:border-green-400" />
        </div>
      </div>

      <div class="mt-6">
        <label class="block mb-2 font-semibold">Descrição</label>
        <textarea id="descricao"
          rows="4"
          placeholder="Digite a descrição do script..."
          class="w-full bg-gray-800 border border-gray-700 rounded-xl px-4 py-3 outline-none focus:border-green-400"></textarea>
      </div>

      <div class="mt-6">
        <label class="block mb-2 font-semibold">Código Lua</label>
        <textarea id="codigo"
          rows="8"
          placeholder="Cole aqui seu script Lua Roblox"
          class="w-full bg-gray-800 border border-gray-700 rounded-xl px-4 py-3 font-mono outline-none focus:border-green-400"></textarea>
      </div>

      <button onclick="adicionarScript()"
        class="mt-8 bg-green-500 hover:bg-green-400 transition text-black font-bold px-8 py-4 rounded-2xl shadow-lg">
        Publicar Script
      </button>
    </div>
  </section>

  <!-- LISTA -->
  <section id="produtos" class="max-w-7xl mx-auto px-6 pb-20">
    <div class="flex justify-between items-center mb-8">
      <h3 class="text-4xl font-bold text-green-400">
        Scripts Publicados
      </h3>
    </div>

    <div id="listaScripts" class="grid md:grid-cols-2 xl:grid-cols-3 gap-8">
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="border-t border-gray-800 py-8 text-center text-gray-500">
    © 2026 Roblox Scripts Atualizados - Todos os direitos reservados.
  </footer>

  <script>
    const lista = document.getElementById('listaScripts');

    function adicionarScript() {
      const nome = document.getElementById('nome').value;
      const preco = document.getElementById('preco').value;
      const descricao = document.getElementById('descricao').value;
      const codigo = document.getElementById('codigo').value;

      if (!nome || !descricao || !codigo) {
        alert('Preencha todos os campos!');
        return;
      }

      const card = document.createElement('div');
      card.className = 'bg-gray-900 border border-gray-800 rounded-3xl p-6 shadow-2xl';

      card.innerHTML = `
        <div class="flex justify-between items-start gap-4">
          <h4 class="text-2xl font-bold text-green-400">${nome}</h4>
          <span class="bg-green-500 text-black px-4 py-2 rounded-xl font-bold">
            ${preco || 'GRÁTIS'}
          </span>
        </div>

        <p class="text-gray-300 mt-4 whitespace-pre-line">
          ${descricao}
        </p>

        <div class="mt-6">
          <div class="flex justify-between items-center mb-2">
            <span class="font-bold text-white">Código Lua</span>
            <button onclick="copiarCodigo(this)"
              class="bg-green-500 hover:bg-green-400 text-black px-4 py-2 rounded-xl font-bold transition">
              Copiar
            </button>
          </div>

          <pre class="bg-black rounded-2xl p-4 overflow-auto text-sm text-green-300 border border-gray-800"><code>${codigo.replace(/</g, '&lt;')}</code></pre>
        </div>
      `;

      lista.prepend(card);

      salvarLocal();

      document.getElementById('nome').value = '';
      document.getElementById('preco').value = '';
      document.getElementById('descricao').value = '';
      document.getElementById('codigo').value = '';
    }

    function copiarCodigo(botao) {
      const codigo = botao.parentElement.parentElement.querySelector('code').innerText;

      navigator.clipboard.writeText(codigo);

      botao.innerText = 'Copiado!';

      setTimeout(() => {
        botao.innerText = 'Copiar';
      }, 1500);
    }

    function salvarLocal() {
      localStorage.setItem('scriptsSalvos', lista.innerHTML);
    }

    function carregarLocal() {
      const salvos = localStorage.getItem('scriptsSalvos');

      if (salvos) {
        lista.innerHTML = salvos;
      }
    }

    carregarLocal();
  </script>

</body>
</html>
