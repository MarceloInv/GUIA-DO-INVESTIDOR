<!DOCTYPE html><html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Guia do Investidor</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f3f3f3; }
    header { background: #004d40; color: white; padding: 20px; text-align: center; }
    nav { background: #00796b; padding: 10px; text-align: center; }
    nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
    section { padding: 20px; }
    .card { background: white; border-radius: 10px; padding: 20px; margin-bottom: 20px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    footer { background: #004d40; color: white; text-align: center; padding: 10px; margin-top: 40px; }
    canvas { max-width: 100%; height: auto; }
    input { padding: 10px; margin: 5px 0; width: 100%; max-width: 300px; }
    label { display: block; margin-top: 10px; }
  </style>
</head>
<body>  <header>
    <h1>Guia do Investidor</h1>
    <p>Aprenda a investir com segurança e inteligência</p>
  </header>  <nav>
    <a href="#inicio">Início</a>
    <a href="#renda-fixa">Renda Fixa</a>
    <a href="#renda-variavel">Renda Variável</a>
    <a href="#grafico">Gráfico</a>
    <a href="#contato">Contato</a>
  </nav>  <section id="inicio">
    <div class="card">
      <h2>Comece a Investir</h2>
      <p>Investir é essencial para construir um futuro financeiro sólido. Aqui você encontrará conteúdos simples e diretos para iniciar no mundo dos investimentos.</p>
    </div>
  </section>  <section id="renda-fixa">
    <div class="card">
      <h2>Renda Fixa</h2>
      <p>Opções como Tesouro Direto, CDB, LCI e LCA são ótimas para quem busca segurança e previsibilidade.</p>
    </div>
  </section>  <section id="renda-variavel">
    <div class="card">
      <h2>Renda Variável</h2>
      <p>Ações, fundos imobiliários e criptomoedas oferecem maior potencial de retorno, mas com mais riscos. Ideal para quem busca diversificação e ganhos no longo prazo.</p>
    </div>
  </section>  <section id="grafico">
    <div class="card">
      <h2>Simulação de Crescimento do Investimento</h2>
      <label>Valor Inicial (R$):</label>
      <input type="number" id="valorInicial" value="1000">
      <label>Taxa de Juros Anual (%):</label>
      <input type="number" id="juros" value="10">
      <label>Anos:</label>
      <input type="number" id="anos" value="5">
      <button onclick="atualizarGrafico()">Simular</button>
      <canvas id="graficoInvestimento"></canvas>
    </div>
  </section>  <section id="contato">
    <div class="card">
      <h2>Fale Conosco</h2>
      <p>Envie dúvidas, sugestões ou parcerias para: <strong>contato@guiadoinvestidor.com</strong></p>
    </div>
  </section>  <footer>
    <p>&copy; 2025 Guia do Investidor. Todos os direitos reservados.</p>
  </footer>  <script>
    let chart;
    function atualizarGrafico() {
      const valorInicial = parseFloat(document.getElementById('valorInicial').value);
      const taxa = parseFloat(document.getElementById('juros').value) / 100;
      const anos = parseInt(document.getElementById('anos').value);

      let valores = [];
      let labels = [];
      let valorAtual = valorInicial;

      for (let i = 1; i <= anos; i++) {
        valorAtual *= (1 + taxa);
        valores.push(valorAtual.toFixed(2));
        labels.push(`Ano ${i}`);
      }

      if (chart) chart.destroy();

      const ctx = document.getElementById('graficoInvestimento').getContext('2d');
      chart = new Chart(ctx, {
        type: 'line',
        data: {
          labels: labels,
          datasets: [{
            label: 'Investimento (R$)',
            data: valores,
            borderColor: '#00796b',
            backgroundColor: 'rgba(0, 121, 107, 0.1)',
            fill: true,
            tension: 0.4
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: { position: 'top' },
            title: { display: true, text: 'Projeção de Crescimento' }
          }
        }
      });
    }

    window.onload = atualizarGrafico;
  </script></body>
</html>
