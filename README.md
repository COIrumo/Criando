<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>REGISTRO DE OCORRÊNCIAS</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      background-color: #e6f0fa;
      color: #003f7f;
    }
    h1 {
      text-align: center;
      color: #003366;
    }
    .ocorrencia {
      border: 2px solid #a3c2f2;
      padding: 15px;
      margin-bottom: 30px;
      border-radius: 10px;
      background-color: #ffffff;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    .form-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
    .form-group {
      display: flex;
      flex-direction: column;
      min-width: 180px;
      flex: 1;
    }
    label {
      font-weight: bold;
      margin-bottom: 5px;
      color: #004080;
    }
    input, select {
      padding: 6px;
      font-size: 14px;
      border: 1px solid #aaccee;
      border-radius: 5px;
    }
    .btn-limpar {
      margin-top: 15px;
      background-color: #0059b3;
      color: white;
      border: none;
      border-radius: 5px;
      padding: 8px 15px;
      cursor: pointer;
      font-weight: bold;
    }
    .btn-limpar:hover {
      background-color: #003d7a;
    }
  </style>
</head>
<body>
  <h1>REGISTRO DE OCORRÊNCIAS</h1>

  <div class="ocorrencia">
    <h2>Dados da Ocorrência</h2>
    <div class="form-row">
      <div class="form-group">
        <label for="sigla">Sigla</label>
        <input type="text" id="sigla" name="sigla" oninput="atualizarLocal()" />
      </div>
      <div class="form-group">
        <label for="local">Local</label>
        <input type="text" id="local" name="local" readonly />
      </div>
    </div>
    <button class="btn-limpar" onclick="document.getElementById('sigla').value='';document.getElementById('local').value=''">Limpar</button>
  </div>

  <script>
    const siglaParaLocal = {
      "AAD": "Aparecida de Goiânia",
      "ABC": "Aparecida do Taboado",
      "ADQ": "Adamantina",
      "AJB": "Américo Brasiliense",
      "ALS": "Altinópolis",
      "ANA": "Anápolis",
      "BGC": "Boa Vista",
      "BDI": "Bady Bassitt",
      "BRR": "Barretos",
      "BSA": "Botucatu",
      "CAP": "Capivari",
      "CBA": "Cuiabá",
      "CBT": "Cubatão",
      "CPS": "Campinas",
      "CRB": "Cravinhos",
      "CTA": "Curitiba",
      "FES": "Fernandópolis",
      "FRN": "Franca",
      "GOI": "Goiânia",
      "IPU": "Ipuã",
      "ITB": "Itumbiara",
      "JND": "Jundiaí",
      "LMB": "Leme",
      "MAR": "Marília",
      "MGA": "Maringá",
      "OUR": "Ourinhos",
      "PCS": "Poços de Caldas",
      "PNS": "Penápolis",
      "POA": "Porto Alegre",
      "PTG": "Pitangueiras",
      "RBE": "Ribeirão Preto",
      "REC": "Recife",
      "RJA": "Rio de Janeiro",
      "RPL": "Replan",
      "SBC": "São Bernardo do Campo",
      "SBO": "Santa Bárbara d'Oeste",
      "SOR": "Sorocaba",
      "SP": "São Paulo",
      "SZC": "Suzano",
      "TBT": "Tatuí",
      "TUP": "Tupã",
      "URU": "Uruguaiana",
      "VAR": "Varginha",
      "VCP": "Viracopos",
      "VIT": "Vitória"
    };

    function atualizarLocal() {
      const sigla = document.getElementById('sigla').value.trim().toUpperCase();
      const local = siglaParaLocal[sigla] || '';
      document.getElementById('local').value = local;
    }
  </script>
</body>
</html>
