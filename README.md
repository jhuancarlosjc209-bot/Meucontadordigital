<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>💰 Meu Contador Digital</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="manifest" href="manifest.json">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <script>
    if ("serviceWorker" in navigator) {
      navigator.serviceWorker.register("service-worker.js");
    }
  </script>
  <style>
    :root {
      --azul: #007bff;
      --verde: #00b894;
      --azul-claro: #eaf4ec;
      --branco: #fff;
      --cinza: #f5f8fa;
      --sombra: 0 4px 16px rgba(0,0,0,0.08);
      --radius: 16px;
      --radius-sm: 8px;
      --radius-xs: 6px;
      --transition: all .2s;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background: var(--cinza);
      margin: 0;
      padding: 0;
      color: #222;
      min-height: 100vh;
    }
    header {
      background: linear-gradient(90deg, var(--azul), var(--verde) 80%);
      color: var(--branco);
      text-align: center;
      padding: 32px 16px;
      box-shadow: var(--sombra);
    }
    header h1 {
      margin: 0 0 10px 0;
      font-size: 2.1em;
      letter-spacing: .5px;
    }
    header p {
      font-size: 1.1em;
      font-weight: 500;
      opacity: .96;
      margin: 0;
    }
    main {
      max-width: 490px;
      margin: 24px auto;
      background: var(--branco);
      padding: 24px 16px 8px 16px;
      border-radius: var(--radius);
      box-shadow: var(--sombra);
    }
    h2 {
      color: var(--azul);
      border-left: 5px solid var(--verde);
      padding-left: 12px;
      font-size: 1.3em;
      margin-top: 0;
    }
    section {
      margin-bottom: 40px;
    }
    .card, .meta-card {
      background: var(--azul-claro);
      border-radius: var(--radius-sm);
      box-shadow: 0 2px 8px rgba(0,0,0,0.03);
      margin: 10px 0;
      padding: 14px 12px 11px 16px;
      transition: var(--transition);
      position: relative;
    }
    .ideias-card {
      background: #eaf0ff;
      border-radius: 10px;
      padding: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.04);
      margin: 12px 0;
      font-size: 1.07em;
      font-weight: 500;
      color: #14599e;
    }
    .card:hover, .meta-card:hover {
      transform: scale(1.017);
      background: #e2f2e9;
    }
    button, .btn {
      background: var(--verde);
      color: var(--branco);
      padding: 12px 0;
      border: none;
      border-radius: var(--radius-sm);
      cursor: pointer;
      font-weight: bold;
      font-family: inherit;
      width: 100%;
      box-shadow: 0 2px 4px rgba(0,0,0,0.07);
      font-size: 1em;
      margin-top: 8px;
      transition: var(--transition);
    }
    button:active, .btn:active, button:hover, .btn:hover {
      background: #019875;
      transform: scale(1.025);
    }
    input, select, textarea {
      width: 100%;
      padding: 11px;
      margin: 8px 0;
      border-radius: var(--radius-xs);
      border: 1px solid #d7eae0;
      font-size: 1em;
      font-family: inherit;
      box-sizing: border-box;
      background: #f7fcfa;
      outline: none;
    }
    input:focus, textarea:focus {
      border-color: var(--azul);
      box-shadow: 0 0 0 2px #b1d4f8;
    }
    label {
      font-weight: 500;
      color: #333;
      display: block;
      margin-bottom: 3px;
      margin-top: 10px;
    }
    .progress {
      background: #dfe6e9;
      border-radius: 10px;
      width: 99%;
      margin: 14px auto 0 auto;
      height: 15px;
      overflow: hidden;
    }
    .progress-bar {
      height: 100%;
      background: linear-gradient(90deg, var(--verde), var(--azul));
      width: 0%;
      transition: width 1s cubic-bezier(.54,.13,.42,.98);
    }
    .meta-list {
      margin-top: 10px;
      margin-bottom: 4px;
    }
    .meta-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 1em;
      background: #e3f2fc;
      margin-bottom: 6px;
      padding-right: 9px;
      border-left: 4px solid var(--azul);
    }
    .meta-actions button {
      background: transparent;
      color: var(--azul);
      border: none;
      font-size: 1.1em;
      margin-left: 8px;
      padding: 0;
      cursor: pointer;
      font-weight: bold;
      opacity: .9;
    }
    .meta-actions button:hover {
      color: var(--verde);
      opacity: 1;
    }
    .motivacional {
      background: #e3f7fe;
      border-left: 4px solid var(--azul);
      padding: 14px 12px;
      border-radius: var(--radius-sm);
      color: #156788;
      margin-bottom: 8px;
      font-weight: 600;
      font-size: 1.06em;
      box-shadow: 0 1px 6px rgba(0,100,255,.06);
      display: flex;
      align-items: center;
      gap: 7px;
    }
    .bonus {
      background: #fff4e1;
      color: #856404;
      border: 1px solid #ffeeba;
      padding: 10px;
      border-radius: var(--radius-sm);
      margin-top: 10px;
      font-size: 1em;
      box-shadow: 0 1px 4px rgba(255,198,80,0.05);
    }
    .sobre-block {
      background: #f2f7fd;
      border-radius: var(--radius);
      padding: 14px 13px 2px 13px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.03);
      margin-bottom: 12px;
      font-size: 1.04em;
    }
    .hide {
      display: none !important;
    }
    @media (max-width: 650px) {
      main {max-width: 99vw; padding: 12px 2vw;}
      .motivacional { font-size: 1em; }
    }
    @media (max-width: 420px) {
      header {padding: 19px 2px;}
      main {padding:8px 1vw;}
      h2 {font-size:1.13em; padding:0 0 0 8px;}
      .card,.meta-card,.motivacional{padding:9px 5px;}
      .sobre-block{padding:8px 6px;}
    }
    footer {
      background-color: var(--azul);
      color: var(--branco);
      text-align: center;
      padding: 14px;
      margin-top: 48px;
      border-top: 6px solid var(--verde);
      border-radius: var(--radius) var(--radius) 0 0;
      letter-spacing: .15px;
      font-size: 1em;
      box-shadow: 0 -2px 6px rgba(0,0,0,0.06);
      font-weight: 500;
    }
    /* ícones emojis inline fix */
    .emoji { font-style: normal; font-size: 1.22em; line-height:2; vertical-align:middle;}
    #adicionarMeta {
      padding: 8px 0 0 0;
      border-top: 1px dashed #09bb41;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <header>
    <h1>💰 Meu Contador Digital</h1>
    <p>Educação Financeira Inteligente para brasileiros.<br>Saia das dívidas, guarde dinheiro e realize seus sonhos!</p>
  </header>
  <main>
    <!-- MOTIVACIONAL -->
    <div class="motivacional" id="motivacionalFrase" style="display: none;">
      <span class="emoji">🧭</span>
      <span id="motivacionalTexto">Você está no controle do seu futuro financeiro!</span>
    </div>

    <section id="inicio">
      <h2>Comece sua jornada financeira</h2>
      <p>Transforme problemas em oportunidades.<br>
      <b>Descubra ideias fáceis para sair da dívida, guardar dinheiro e pagar tudo corretamente!</b></p>
      <button onclick="mudarSecao('perfil')">Começar agora (Grátis)</button>
    </section>

    <section id="perfil" class="hide">
      <h2>Seu Perfil Financeiro</h2>
      <form id="perfilForm" autocomplete="off">
        <label for="nome">Nome completo:</label>
        <input type="text" id="nome" required minlength="2">

        <label for="renda">Renda mensal (R$):</label>
        <input type="number" id="renda" required min="0" step="0.01">

        <label for="meta">Meta financeira inicial:</label>
        <input type="text" id="meta" placeholder="Ex: Sair da dívida, comprar notebook, pagar aluguel atrasado..." required>

        <label><input type="checkbox" id="dicas"> Desejo receber Dica Bônus Personalizada</label>
        <button type="submit">Salvar perfil</button>
      </form>
    </section>

    <section id="painel" class="hide">
      <h2>📊 Painel Financeiro</h2>
      <div class="card" id="resumo"></div>
      <div class="progress"><div class="progress-bar" id="progresso"></div></div>
      <div class="meta-list" id="metaList"></div>
      <div id="adicionarMeta">
        <form id="novaMetaForm" autocomplete="off">
          <label for="novaMeta">Nova meta financeira (dinheiro, material ou pagar alguém):</label>
          <input type="text" id="novaMeta" placeholder="Ex: Quitar dívida cartão, comprar bicicleta, pagar mecânico..." required>
          <button type="submit" class="btn">Adicionar meta</button>
        </form>
      </div>
    </section>

    <!-- IDEIAS PARA SAIR DA DÍVIDA E GUARDAR DINHEIRO -->
    <section id="ideias">
      <h2>📝 Ideias práticas para Sair da Dívida e Alcançar Metas</h2>
      <div class="ideias-card">💳 <b>Organize suas dívidas:</b> Liste todos os valores que deve, prazos e para quem. Comece pelas dívidas com juros maiores.</div>
      <div class="ideias-card">📆 <b>Negocie prazos:</b> Converse com pessoas/instituições para parcelar ou negociar valores em aberto.</div>
      <div class="ideias-card">💵 <b>Separe um valor fixo para guardar:</b> Reserve sempre um valor por semana. Mesmo R$ 5 já faz diferença com o tempo!</div>
      <div class="ideias-card">🎯 <b>Defina suas metas:</b> Seja dinheiro, bem material ou pagar alguém. Deixe claro quanto precisa e até quando quer alcançar.</div>
      <div class="ideias-card">✅ <b>Use planilhas ou apps:</b> Controle dívidas pagas, metas alcançadas e o que falta. Visualize seu progresso.</div>
      <div class="ideias-card">👨‍👩‍👧 <b>Peça ajuda/reduza despesas:</b> Envolva família, corte gastos desnecessários e foque em prioridades.</div>
      <div class="ideias-card">💡 <b>Mude hábitos aos poucos:</b> Troque pequenos gastos por sonhos maiores, assim ficará mais fácil guardar dinheiro.</div>
      <div class="ideias-card">⏳ <b>Método para pagar alguém:</b> Agende transferências, crie alertas no celular/app, e mantenha comunicação aberta.</div>
      <div class="ideias-card">📦 <b>Venda/desapegue de itens:</b> Use o dinheiro para abater dívidas ou tirar projetos do papel.</div>
    </section>

    <section id="dicas">
      <h2>💡 Dicas de Finanças</h2>
      <div class="card">📗 <b>Gaste menos do que ganha:</b> A base da saúde financeira é manter os gastos abaixo do que você recebe.</div>
      <div class="card">📘 <b>Monte sua reserva:</b> Guarde pelo menos R$50 por mês. Pequenos valores são poderosos!</div>
      <div class="card">📙 <b>Tenha metas reais:</b> Exemplo: guardar R$20 por semana durante 6 meses para X.</div>
      <div class="card">💳 <b>Evite dívidas caras:</b> Priorize quitar cartões/empréstimos com juros altos.</div>
    </section>

    <section id="sobre">
      <h2>🌍 Sobre o Projeto</h2>
      <div class="sobre-block">
        <p>O <b>Meu Contador Digital</b> ajuda brasileiros a sair das dívidas, organizar o dinheiro e conquistar metas reais — seja dinheiro, bem material ou pagar alguém importante!<br>
        Acreditamos que educação financeira acessível muda vidas. Tudo é pensado para facilitar sua jornada.<br>
        <span class="emoji">🇧🇷</span></p>
      </div>
    </section>
  </main>
  <footer>
    Meu Contador Digital © 2025 — Educação financeira para todos os brasileiros 🇧🇷
  </footer>

  <script>
    const frasesMotivacionais = [
      "Você está no controle do seu futuro financeiro!",
      "Sair da dívida é o primeiro passo para sonhar!",
      "A disciplina de hoje será o sucesso de amanhã.",
      "Cada dívidazinha paga abre espaço para conquistas maiores.",
      "Organize hoje, realize sempre!",
      "Juntos podemos transformar sua vida financeira!",
      "Meta definida, dedicação constante. Seu sonho está mais perto!",
      "Seus objetivos são possíveis com organização!"
    ];
    function mostrarFraseMotivacional() {
      const frase = frasesMotivacionais[Math.floor(Math.random()*frasesMotivacionais.length)];
      document.getElementById('motivacionalFrase').style.display = "flex";
      document.getElementById('motivacionalTexto').textContent = frase;
    }
    function mudarSecao(secao) {
      for (let s of ['inicio','perfil','painel','dicaBonus']) {
        const el = document.getElementById(s);
        if (el) el.classList.add('hide');
      }
      document.getElementById(secao).classList.remove('hide');
      if (secao !== 'perfil') mostrarFraseMotivacional();
      if (secao === 'painel') atualizarPainel();
      if (secao === 'dicaBonus') atualizarBonus();
    }
    function getPerfil() {
      const dados = localStorage.getItem('perfil');
      return dados ? JSON.parse(dados) : null;
    }
    function setPerfil(perfil) {
      localStorage.setItem('perfil', JSON.stringify(perfil));
    }
    function getMetas() {
      const metas = localStorage.getItem('metas');
      return metas ? JSON.parse(metas) : [];
    }
    function setMetas(metas) {
      localStorage.setItem('metas', JSON.stringify(metas));
    }
    function atualizarPainel() {
      const perfil = getPerfil();
      const resumo = document.getElementById('resumo');
      const progresso = document.getElementById('progresso');
      if (!perfil) {
        resumo.innerHTML = "Preencha seu perfil para ver seu resumo financeiro.";
        progresso.style.width = "0%";
        return;
      }
      resumo.innerHTML =
        `<h3>Olá, ${perfil.nome} 💰!</h3>
        <p>Sua renda mensal é de <b>R$${Number(perfil.renda).toLocaleString('pt-BR',{minimumFractionDigits:2})}</b>.</p>
        <p>Sua meta financeira inicial é: <b>${perfil.meta}</b>.</p>
        <p>Clique abaixo e adicione novas metas quando precisar <span class="emoji">📈</span>.</p>`;
      progresso.style.width = `${Math.min((parseFloat(perfil.renda)/10000)*100,100)}%`;
      atualizarMetaList();
    }
    function gerarDicaBonus(perfil) {
      let dica = "";
      if (!perfil) return "";
      if (perfil.renda < 2000) {
        dica = "💡 Dica bônus: Comece pequeno — tente guardar R$5 por dia. O importante é criar o hábito.";
      } else if (perfil.renda < 5000) {
        dica = "💡 Dica bônus: Foque em investir parte do seu salário mensal. Um fundo de emergência é essencial.";
      } else {
        dica = "💡 Dica bônus: Diversifique seus investimentos e monte uma reserva de 6 meses da renda.";
      }
      if (perfil.meta && perfil.meta.trim().toLowerCase().includes("quitar")) {
        dica += "<br><b>Lembre-se:</b> Quitar dívidas caras é prioridade!";
      }
      return dica;
    }
    function atualizarBonus() {
      const perfil = getPerfil();
      document.getElementById('bonusArea').innerHTML = gerarDicaBonus(perfil);
    }
    function atualizarMetaList() {
      const metas = getMetas();
      const ul = document.getElementById('metaList');
      if (metas.length === 0) {
        ul.innerHTML = "<div class='meta-card'>Nenhuma meta extra cadastrada ainda.</div>";
        return;
      }
      ul.innerHTML = metas.map((m, i) =>
        `<div class="meta-card">
            <span>📈 <b>${m}</b></span>
            <span class="meta-actions">
              <button title="Editar" onclick="editarMeta(${i})">✏️</button>
              <button title="Excluir" onclick="excluirMeta(${i})">🗑️</button>
            </span>
          </div>`
      ).join('');
    }
    function editarMeta(idx) {
      const metas = getMetas();
      const nova = prompt("Edite sua meta:", metas[idx]);
      if (nova && nova.trim().length > 1) {
        metas[idx] = nova.trim();
        setMetas(metas);
        atualizarMetaList();
      }
    }
    function excluirMeta(idx) {
      if (!confirm("Deseja mesmo excluir esta meta?")) return;
      const metas = getMetas();
      metas.splice(idx,1);
      setMetas(metas);
      atualizarMetaList();
    }
    document.getElementById('perfilForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const nome = document.getElementById('nome').value.trim();
      const renda = parseFloat(document.getElementById('renda').value);
      const meta = document.getElementById('meta').value.trim();
      const querDicas = document.getElementById('dicas').checked;
      setPerfil({nome, renda, meta, querDicas});
      if (querDicas) mudarSecao('dicaBonus');
      else mudarSecao('painel');
    });
    document.getElementById('novaMetaForm').addEventListener('submit', function(e){
      e.preventDefault();
      const novaMeta = document.getElementById('novaMeta').value.trim();
      if (novaMeta.length < 2) return;
      let metas = getMetas();
      metas.push(novaMeta);
      setMetas(metas);
      document.getElementById('novaMetaForm').reset();
      atualizarMetaList();
    });
    window.onload = function() {
      mostrarFraseMotivacional();
      if(getPerfil()) { mudarSecao('painel'); }
      else { mudarSecao('inicio'); }
      atualizarMetaList();
    };
  </script>
  <!-- DICA BONUS personalizada, só aparece se marcado no perfil -->
  <section id="dicaBonus" class="hide">
    <h2>💡 Dica Bônus Personalizada</h2>
    <div class="bonus" id="bonusArea"></div>
    <button onclick="mudarSecao('painel')" style="margin-top:16px;">Ir para o Painel</button>
  </section>
</body>
</html>
