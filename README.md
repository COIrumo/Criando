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
      position: relative;
    }
    .ocorrencia h2 {
      margin-top: 0;
      color: #003366;
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
  <script>
    const siglaParaLocal = {
    "AAD": "Aparecida de Goiânia",
    "ABC": "Aparecida do Taboado",
    "ADQ": "Adamantina",
    "AJB": "Américo Brasiliense",
    "ALS": "Altinópolis",
    "ANA": "Anápolis",
    "ATB": "Aparecida do Taboado",
    "BGC": "Boa Vista",
    "BDI": "Bady Bassitt",
    "BRR": "Barretos",
    "BRT": "Barretos",
    "BSA": "Botucatu",
    "CAC": "Cachoeira Paulista",
    "CAP": "Capivari",
    "CBA": "Cuiabá",
    "CBT": "Cubatão",
    "CPS": "Campinas",
    "CRB": "Cravinhos",
    "CTB": "Catanduva",
    "CTA": "Curitiba",
    "CUI": "Cuiabá",
    "FES": "Fernandópolis",
    "FOZ": "Foz do Iguaçu",
    "FRN": "Franca",
    "GOI": "Goiânia",
    "GRA": "Guará",
    "GUA": "Guarulhos",
    "IPU": "Ipuã",
    "ITA": "Itapeva",
    "ITB": "Itumbiara",
    "ITP": "Itapira",
    "JAC": "Jaci",
    "JND": "Jundiaí",
    "JPA": "João Pessoa",
    "LDB": "Londrina",
    "LMB": "Leme",
    "MAR": "Marília",
    "MGA": "Maringá",
    "MIR": "Mirassol",
    "MOC": "Montes Claros",
    "MTR": "Monteiro",
    "NAT": "Natal",
    "NVP": "Nova Petrópolis",
    "OUR": "Ourinhos",
    "PCS": "Poços de Caldas",
    "PGS": "Ponta Grossa",
    "PIU": "Piúma",
    "PMP": "Pompéia",
    "PNS": "Penápolis",
    "POA": "Porto Alegre",
    "PRA": "Piracicaba",
    "PRU": "Presidente Prudente",
    "PTG": "Pitangueiras",
    "RBE": "Ribeirão Preto",
    "REC": "Recife",
    "REI": "Reis",
    "RJA": "Rio de Janeiro",
    "RMN": "Rondonópolis",
    "RPL": "Replan",
    "RPS": "Raposos",
    "RRA": "Ribeirão das Neves",
    "SBC": "São Bernardo do Campo",
    "SBO": "Santa Bárbara d'Oeste",
    "SJP": "São José dos Pinhais",
    "SLZ": "São Luís",
    "SOR": "Sorocaba",
    "SP": "São Paulo",
    "SPS": "São Pedro da Serra",
    "SSB": "Santo Sebastião do Paraíso",
    "STB": "Sete Barras",
    "STP": "São Thomé das Letras",
    "SZC": "Suzano",
    "TBT": "Tatuí",
    "TNG": "Tanguá",
    "TUP": "Tupã",
    "URU": "Uruguaiana",
    "VAR": "Varginha",
    "VCP": "Viracopos",
    "VDC": "Vitória da Conquista",
    "VIT": "Vitória",
    "VLG": "Vila Gilda",
    "VLN": "Vila Natal",
    "ZZV": "Vila Natal",
    "ZZZ": "Replan",
    "ZWI": "Aldeinha",
    "ICB": "Cubatão",
"PSN": "Santa",
"PCZ": "Conceiçãozinha",
"IBA": "Ilha Barnabé",
"IPG": "Piçaguera",
"IAA": "Areais",
"ZPG": "Perequê",
"ZZV": "Vila Natal",
"ZZV": "Vila Esperança",
"ZGM": "Gladson Moraes",
"ZPT": "Paratinga",
"ZGP": "Gaspar Ricardo",
"ZWU": "Acaraú",
"ZDC": "ZDC",
"ZXW": "Pai Matias",
"ZSM": "Samaritá",
"ZMU": "Mongaguá",
"ZIH": "Itanhaem",
"ZPX": "Peruibe",
"ZXS": "Pedro de Toledo",
"ZMH": "Miracatu",
"ZJQ": "Juquia",
"ZRY": "Registro",
"ZCH": "Cajati",
"ZEZ": "Engenheiro Ferraz",
"ZEV": "Evangelista de Souza",
"ZEV": "Evangelista de Souza",
"ZRB": "Represa Billings",
"ZEJ": "Engenheiro Marsilac",
"ZMS": "Mario Souto",
"ZEM": "Embu-Guaçu",
"ZYQ": "Itaquaciara",
"ZWI": "Aldeinha",
"ZLU": "Parada de Linfa",
"ZKW": "Caucaia do Alto",
"ZWW": "Parada do Carmo",
"ZKE": "Canguera",
"ZKE": "Canguera",
"ZGA": "Guaianã",
"ZPS": "Pantojo Santista",
"ZCX": "Capricórnio",
"ZER": "Engenheiro Acrisio",
"ZDI": "Dona Catarina",
"ZDY": "Botuxim",
"ZXP": "Pirapitingui",
"ZFY": "Convenção",
"ZYU": "Itu",
"ZST": "Salto",
"ZXI": "Pimenta",
"ZIC": "Itaici",
"ZVK": "Viracopos",
"ZDS": "Descampado",
"ZQB": "Campinas",
"ZQB": "Km 254",
"ZJY": "Jundiaí",
"ZVN": "Vinhedo",
"ZCP": "Campinas",
"ZAB": "Amador Bueno",
"ZHN": "Sem informação",
"ZMY": "Sem informação",
"ZGZ": "Sem informação",
"ZMK": "Mairinque",
"ZXY": "Pantojo",
"ZAL": "Alumínio",
"ZYF": "Inhaíba",
"ZBT": "Brigadeiro Tobias",
"ZSS": "Sorocaba",
"ZGO": "George Oeterer",
"ZVB": "Bacaetava",
"ZIE": "Iperó",
"ZBX": "Boituva",
"ZWO": "Anísio de Morais",
"ZCQ": "Cerquilho",
"ZJM": "Jumirim",
"ZLJ": "Laranjal Paulista",
"ZMI": "Maristela",
"ZXR": "Pereiras",
"ZCN": "Conchas",
"ZJZ": "Juquiratiba",
"ZUT": "Pirambóia",
"ZEX": "Eng. Calixto",
"ZCO": "César Neto",
"ZAW": "Apuãs",
"ZBC": "Botucatu",
"ZRJ": "Rubião Júnior",
"ZTL": "Toledo",
"ZSN": "São Manuel",
"ZRA": "Rodrigues Alves",
"ZXN": "Paranhos",
"ZLN": "Lençóis Paulista",
"ZAO": "Agudos",
"JBU": "Bauru",
"JCR": "Curuçá",
"JVP": "Val de Palmas",
"JNG": "Nogueira",
"JAI": "Avai",
"JRI": "Araribá",
"JPY": "Pirajuí",
"JGN": "Guarantã",
"JCF": "Cafelândia",
"JLB": "Lins",
"JPM": "Promissão",
"JPN": "Penápolis",
"JGO": "Glicério",
"JBG": "Birigui",
"JAR": "Araçatuba",
"JGR": "Guararapes",
"JVA": "Valparaizo",
"JMP": "Mirandópolis",
"JGC": "Guaraçaí",
"JDR": "Andradina",
"JAS": "Alfredo Castilho",
"ZTY": "Tatuí",
"ZMF": "Morro do Alto",
"ZIP": "Itapetininga",
"ZLW": "Juriti",
"ZAT": "Angatuba",
"ZAU": "Aracaçu",
"ZBZ": "Buri",
"ZEU": "Eng. Bacelar",
"ZIX": "Itapeva",
"ZNW": "Nova Itapeva",
"ZOK": "Itaoca",
"ZXZ": "Itaboa",
"ZOA": "Serrinha",
"LLZ": "Pinhalzinho",
"ZZA": "Apiaí",
"ZUK": "Paula Souza",
"ZNV": "Miranda de Azevedo",
"ZIG": "Itatinga",
"ZWK": "Eng. Serra",
"ZJV": "Juca Novais",
"ZAV": "Avaré",
"ZBJ": "Barra Grande",
"ZCC": "Cerqueira César",
"ZZH": "São Bartolomeu",
"ZMD": "Manduri",
"ZBB": "Batista Botelho",
"ZBP": "Bernardino de Campos",
"ZLP": "Luiz Pinto",
"ZIU": "Ipauçu",
"ZXV": "Chavantes",
"ZKC": "Canitar",
"ZOU": "Ourinhos",
"ZSA": "Salto Grande",
"ZIM": "Ibirarema",
"ZPV": "Palmital",
"ZCM": "Candido Mota",
"ZAS": "Assis",
"ZPK": "Paraguaçu Paulista",
"ZQT": "Quatá",
"ZRN": "Rancharia",
"ZMT": "Martinopolis",
"ZRG": "Regente Feijó",
"ZPP": "Presidente Prudente",
"ZAE": "Álvares Machado",
"ZPR": "Presidente Bernardes",
"ZSC": "Santo Anastácio",
"ZPW": "Presidente Venceslau",
"ZPE": "Presidente Epitácio",
"ZNG": "Cnaga",
"ZVY": "Varginha",
"ZBV": "Boa Vista Velha",
"ZHO": "Hortolândia",
"ZSU": "Sumaré",
"ZAC": "Americana",
"ZTT": "Tatu",
"ZLI": "Limeira",
"ZCD": "Cordeirópolis",
"ZSQ": "Santa Gertrudes",
"ZWX": "Santana",
"ZRX": "Rio Claro Novo",
"ZRO": "Rio Claro Velho",
"ZRQ": "Batovi",
"ZQX": "Camaquã",
"ZOX": "Graúna",
"ZIQ": "Itirapina",
"ZVI": "Visconde do Rio Claro",
"ZFR": "Conde do Pinhal",
"ZSK": "São Carlos",
"ZXH": "Washington Luís",
"ZTI": "Tamoio",
"ZOI": "Ouro",
"ZAR": "Araraquara",
"ZIQ": "Itirapina",
"ZQY": "Posto 183",
"ZFH": "Campo Alegre",
"ZWF": "Aterrado",
"ZBO": "Brotas",
"ZEP": "Espraiado",
"ZFG": "Canela",
"ZTR": "Torrinha",
"ZTE": "Tabuleio",
"ZVT": "Ventania",
"ZDK": "Dois Corregos",
"ZLF": "Lacerda Franco",
"ZJU": "Jaú",
"ZWM": "Ave Maria",
"ZWY": "Ayrosa Galvão",
"ZPD": "Pederneiras",
"ZFJ": "Carajás",
"ZGY": "Guaianás",
"ZAY": "Aimorés",
"ZTP": "Triagem Paulista",
"ZBU": "Bauru",
"ZQW": "Aldeia",
"ZGR": "Garça",
"ZML": "Marília",
"ZXO": "Pompéia",
"ZTU": "Tupã",
"ZUY": "Universo",
"ZPJ": "Parapuã",
"ZIK": "Iacri",
"ZOS": "Oswaldo Cruz",
"ZYV": "Inúbia Paulista",
"ZLC": "Lucélia",
"ZAP": "Adamantina",
"ZFL": "Flórida Paulista",
"ZPU": "Pacaembu",
"ZIL": "Irapuru",
"ZJX": "Junqueiropolis",
"ZDN": "Dracena",
"ZYK": "Iandara",
"ZWZ": "Arabela",
"ZPM": "Panorama",
"ZBL": "Boa Vista Nova",
"ZOP": "Paulínia",
"ZZQ": "-",
"ZZZ": "Replan",
"ZPB": "Piracicaba",
"ZSB": "Santa Bárbara D'oeste",
"ZRC": "Recanto",
"ZTO": "Tutóia",
"ZDZ": "Bueno de Andrade",
"ZMA": "Matão",
"ZDG": "Dobrada",
"ZTN": "Tancredo França - Cruzamento",
"ZLQ": "Jurupema - Cruzamento",
"ZTQ": "Taquaritinga",
"ZCZ": "Cândido Rodrigues",
"ZZF": "Santa Sofia - Cruzamento",
"ZSD": "Santa Adélia",
"ZJP": "Jacauna - Cruzamento",
"ZJC": "Jacaúna",
"ZXB": "Areia Branca - Cruzamento",
"ZPN": "Pindorama",
"ZCV": "Catanduva",
"ZCT": "Catiguá",
"ZUC": "Uchoa",
"ZCG": "Cedral",
"ZEH": "Engenheiro Schmidt",
"ZSP": "São José Rio Preto",
"ZRU": "Rio Preto Paulista",
"ZGB": "Gonzaga de Campos - Cruzamento",
"ZMO": "Mirassol",
"ZVU": "Bálsamo",
"ZEB": "Engenheiro Balduíno",
"ZRZ": "Tanabi",
"ZEC": "Ecatu",
"ZKY": "Cosmorama",
"ZZM": "Simonsen",
"ZVP": "Votuporanga",
"ZGI": "Guimarães Rosa",
"ZMR": "Meridiano",
"ZFN": "Fernandópolis",
"ZRL": "Ligação - Cruzamento",
"ZED": "Estrela D'Oeste",
"ZJA": "Jales",
"ZUR": "Urânia",
"ZUE": "Pimenta Bueno",
"ZTF": "Três Fronteiras",
"ZSF": "Santa Fé do Sul",
"ZRW": "Rubinéia",
"TPO": "Término da Ponte",
"ZAR": "Araraquara",
"ZAX": "Américo Brasiliense",
"ZSL": "Santa Lúcia",
"ZRI": "Rincão",
"ZGT": "Guatapará",
"ZXE": "Pradópolis",
"ZBH": "Barrinha",
"ZPL": "Passagem",
"ZBD": "Bebedouro",
"ZCJ": "Colina",
"ZBR": "Barretos",
"ZCA": "Colombia",
"TMI": "Marco Inicial",
"TRP": "Rio Paraná - Cruzamento",
"TAP": "Aparecida do Taboado",
"TLG": "Lagoinha",
"TQI": "Quiteria",
"TSP": "São Pedro - Cruzamento",
"TIN": "Inocência",
"TSJ": "Fazenda São Jorge - Cruzamento",
"TMO": "Morangas",
"TCE": "Cerradão - Cruzamento",
"TID": "Indiaizinho",
"TVI": "Viaduto",
"TJA": "Agente João Amorim",
"TCS": "Chapadao do Sul",
"THE": "Humberto Eudes",
"TMR": "Mineiros - Cruzamento",
"TLA": "Lage",
"TSE": "Serrinha - Cruzamento",
"TBA": "Baus",
"JJP": "Jupiá",
"JLG": "Três Lagoas",
"JGI": "Gigante",
"JAU": "Arapua",
"JPB": "Piaba",
"JGA": "Garcias",
"JRN": "Rio Branco",
"JPK": "Pena Júnior",
"JMV": "Major Vicente",
"JAC": "Água Clara",
"JAO": "Atoladeira",
"JAZ": "Arlindo Luz",
"JFM": "Formoso",
"JLZ": "Luiz Gama",
"JRO": "Ribas do Rio Pardo",
"JBL": "Bálsamo",
"JAL": "Alegre",
"JLI": "Ligação",
"JLR": "Lagoa Rica",
"JCG": "Campo Grande",
"JIB": "Indubrasil",
"JTR": "Terrenos",
"JCH": "Cachoeirao",
"JPL": "Palmeiras",
"JKU": "Irmãos Maringoni",
"JAN": "Aquidauana",
"JVT": "Taunay",
"JMN": "Miranda",
"JGS": "Guaicurus",
"JBQ": "Bodoquena",
"JCN": "Carandazal",
"JKE": "Agente Inocêncio",
"JAB": "Albuquerque",
"JAM": "Antônio Maria Coelho",
"JUR": "Urucum",
"JCB": "Corumbá",
"JBA": "Manoel Brandão",
"JKQ": "Posto km 903",
"JLA": "Porto Ladário",
"JSD": "Sidrolândia",
"JMJ": "Maracaju",
"JIT": "Itaum",
"JRG": "General Rondon",
"JRP": "Ponta Porã",
"JPC": "Porto Esperança",
"TOM": "T. Olacyr F. Morais",
"TPC": "TPC - Cruzamento",
"TVL": "Marco Vedovelli",
"TBR": "Beira Rio - Cruzamento",
"TAG": "Alto Araguaia",
"TBE": "Fazenda Boa Esperança",
"TRM": "Romeira - Cruzamento",
"TEP": "Fazenda Espigão",
"TMJ": "Fazenda Marajoara",
"TPD": "Pátio de Dormentes",
"TCT": "João Celi Triches - Cruzamento",
"TIQ": "Itiquira",
"TSA": "Santa Bárbara - Cruzamento",
"TBS": "Bom Sucesso - cruzamento",
"TAL": "Água Limpa - cruzamento",
"TSF": "São Francisco - cruzamento",
"PGO": "Guarani D'oeste",
"POU": "Ouroeste",
"PIT": "Iturama",
"PUD": "União de Minas",
"PSS": "São Simão",
"PPR": "Paranaiguara",
"PQI": "Quirinópolis",
"POA": "Ouroana",
"PAM": "Água Mansa",
"PSO": "São Tomás",
"PSG": "Santa Helena",
"PAR": "Acreúna",
"PPG": "Palmeiras de Goiás",
"PTR": "Trindade",
"PNV": "Nova Veneza",
"POS": "Ouro Verde",
"PJA": "Jarágua",
"PJG": "Rianápolis",
"PSI": "Santa Isabel",
"PSL": "São Luiz do Norte",
"PUR": "Uruaçu",
"PCA": "Campinorte",
"PEN": "Estrela do Norte",
"PPP": "Porangatu",
"PPO": "Rio Canabrava",
"POV": "Ouro Verde de Goiás",
"PAS": "Anápolis",
"PAA": "Alvorada",
"PFI": "Figueirópolis",
"PGU": "Gurupi",
"PGI": "Eng. Wagner Correa de Oliveira",
"PNN": "Ari Neri de Oliveira",
"PCB": "Eng. Cícero Braz",
"PAC": "Alésio G. da Costa",
"PPN": "Porto Nacional",
"JAG": "Agachi",
"JBH": "Bolicho",
"JBR": "Brilhante",
"JCA": "Camisão",
"JCJ": "Coronel Juvêncio",
"JDE": "Duque Estrada",
"JFR": "Ferreiros",
"JGL": "Guia Lopes",
"JGV": "Guavira",
"JKF": "Posto km 512",
"JMA": "Mantena",
"JMD": "Eng. Mário Dutra",
"JMO": "Murtinho",
"JMS": "Ministro Pestana",
"JPA": "Porto Carreiro",
"JPI": "Pedro Celestino",
"JPQ": "Piqui",
"JPR": "Piraputanga",
"JPV": "Piúva",
"JSB": "Salobra",
"JSF": "Safira",
"JST": "Sete Voltas",
"JSV": "Santa Virgínia",
"TRC": "Costa Rica - Cruzamento",
"TGR": "Agrenco - Cruzamento",
"TRO": "Rondonópolis",
"NTQ": "Taquarichim",
"JAV": "Avanhandava",
"JCO": "Coroados",
"JFL": "Ferd Laboriau",
"JGU": "Guaiçara",
"JGY": "Aguapeí",
"JJQ": "Junqueira",
"JLV": "Lavínia",
"JPT": "Planalto",
"JRA": "Presidente Alves",
"Z03": "Atlântida",
"ZAF": "Agenor de Campos",
"ZBM": "Barragem",
"ZBQ": "Bartira",
"ZDH": "Banharão",
"ZHA": "Solemar",
"ZOW": "Manuel de Nobrega",
"ZVH": "Valinhos",
"ZWH": "Adolfo Pinto",
"ZXK": "Paulópolis",
"ZYT": "Itarare",
"ZZL": "Silvânia",
"ZCK": "Carapicuiba",
"LRD": "Rio Verde",
"LRR": "Roxo Roiz",
"LSL": "Santa Leocádia",
"LSN": "Santa Mariana",
"LSO": "Cerro Pelado",
"LTC": "Tronco",
"NCC": "Cerro Chato",
"NCR": "Curussu",
"NDI": "Dois Irmãos",
"NEM": "Eng. Marinho",
"NEZ": "Eng. Enzo Pinto",
"NFP": "Fernando Pereira",
"NGO": "Lagoão",
"NMM": "Major Marques",
"NPG": "Porongos",
"NQS": "Quarta Seção",
"NQT": "Quinta",
"NSU": "Suspiro",
"NTM": "Triângulo",
"ZCS": "Caiua",
"ZCW": "Colônia Paulista",
"ZDM": "Domingos de Moraes",
"ZFO": "Frigorífico",
"ZFQ": "Chibarro",
"ZFU": "Fernando Prestes",
"ZGK": "Guarani",
"ZGW": "Guilherme Wendel",
"ZGX": "Peixoto Gomide",
"ZHC": "Suarão",
"ZHE": "Herculândia",
"ZHL": "Santa Salete",
"ZIB": "IbitiuVa",
"ZIN": "Indiana",
"ZJF": "Jafa",
"ZLO": "Lopes de Oliveira",
"ZLV": "Louveira",
"ZNJ": "Jacupiranga",
"ZNK": "Musácea",
"ZNO": "Nova Odessa",
"ZNQ": "Marrequinhas",
"ZOR": "Oriente",
"ZPC": "Piquerobi",
"ZPH": "Pitangueiras",
"ZPO": "Posto km 183",
"ZPQ": "Presidente Altino",
"ZQO": "Quintana",
"ZSH": "Santa Ernestina",
"ZSX": "Samambaia",
"ZSY": "Sussui",
"ZTW": "Tapuia",
"ZUG": "Padre Nóbrega",
"ZVE": "Varnhagem",
"ZVS": "Vera Cruz Paulista",
"JTC": "Tibirica",
"LSL": "Santa Leocádia",
"LSN": "Santa Mariana",
"LSO": "Cerro Pelado",
"LSP": "Posto Shell",
"LTB": "Três Barras",
"LTC": "Tronco",
"LTE": "Eng. Theodor Stresser",
"LUG": "Uruguai",
"LUN": "Porto União Vitória",
"LVI": "Videira",
"LVO": "Vagues",
"N01": "Entroncamento Pq. Industrial",
"N03": "Porto de Cachoeira do Sul",
"N05": "Porto de Pelotas",
"NBE": "Bento Gonçalves",
"NBM": "Boca do Monte",
"NCB": "Carlos Barbosa",
"NCC": "Cerro Chato",
"NCL": "Cerro Largo",
"NCR": "Curussu",
"NCV": "Candida Vargas",
"NDI": "Dois Irmãos",
"NEJ": "Entr.São Borja",
"NEM": "Eng. Marinho",
"NEQ": "Esquina",
"NEZ": "Eng. Enzo Pinto",
"NFP": "Fernando Pereira",
"NGD": "G.Das Missões",
"NGI": "Garibaldi",
"NGO": "Lagoão",
"NHN": "Hulha Negra",
"NLP": "Pertile",
"NMM": "Major Marques",
"NNP": "Nhu Pora",
"NPA": "Porto de Porto Alegre",
"NPG": "Porongos",
"NQS": "Quarta Seção",
"NQT": "Quinta",
"NRH": "Gare do Porto",
"NRM": "Marcelino Ramos",
"NSI": "São Simão",
"NSJ": "São Borja",
"NSU": "Suspiro",
"NTM": "Triângulo",
"NTQ": "Taquarichim",
"NUD": "Unistalda",
"ZCK": "Carapicuiba",
"ZCS": "Caiua",
"ZCW": "Colônia Paulista",
"ZDM": "Domingos de Moraes",
"ZFO": "Frigorífico",
"ZFQ": "Chibarro",
"ZFU": "Fernando Prestes",
"ZGK": "Guarani",
"ZGW": "Guilherme Wendel",
"ZGX": "Peixoto Gomide",
"ZHC": "Suarão",
"ZHE": "Herculândia",
"ZHL": "Santa Salete",
"ZIB": "IbitiuVa",
"ZIN": "Indiana",
"ZJF": "Jafa",
"ZLO": "Lopes de Oliveira",
"ZLV": "Louveira",
"ZNJ": "Jacupiranga",
"ZNK": "Musácea",
"ZNQ": "Marrequinhas",
"ZOR": "Oriente",
"ZPC": "Piquerobi",
"ZPH": "Pitangueiras",
"ZPO": "Posto km 183",
"ZPQ": "Presidente Altino",
"ZQO": "Quintana",
"ZSH": "Santa Ernestina",
"ZSX": "Samambaia",
"ZSY": "Sussui",
"ZTW": "Tapuia",
"ZUG": "Padre Nóbrega",
"ZVE": "Varnhagem",
"ZVS": "Vera Cruz Paulista",
"LMI": "Mandaguari",
"LMH": "Minhocao",
"LMG": "Maringá",
"LMF": "Mauá do Sul",
"LME": "Monte Castelo",
"LMD": "Marcilio Dias",
"LMC": "Matos Costa",
"LMA": "Marialva",
"LLZ": "Pinhalzinho",
"LLY": "Eng. Líneo do Amaral",
"LLV": "Lavrinha",
"LLU": "Lustosas",
"LLT": "Eng. Rosaldo Leitão",
"LLS": "Lages",
"LLP": "Ângelo Lopes",
"LLO": "Paula Pereira",
"LLN": "Lança",
"LLM": "Cruz Lima",
"LLL": "Eng. Francisco Cruz",
"LLJ": "Controlador Jonas",
"LLH": "Leonardos",
"LLD": "Londrina",
"LLB": "Coronel Buarque",
"LLA": "Lapa",
"LKS": "Est km 70",
"LKP": "Posto km 103,490",
"LKM": "km 108",
"LKA": "Ramal Klabin",
"LJZ": "Jacarezinho",
"LJY": "Jataizinho",
"LJU": "Jussara",
"LJS": "Eng. João Passos",
"LJR": "Jaguariaíva",
"LJM": "Jardim América",
"LJL": "Joinville",
"LJG": "Jaraguá do Sul",
"LJD": "Jandaia do Sul",
"LIU": "Ibicare",
"LIT": "Irati",
"LIT": "Irati",
"LIS": "Itaiopolis",
"LIR": "Ibipora",
"LIP": "Itaperussu",
"LIN": "Arapoti",
"LIM": "Inacio Martins",
"LIH": "Ipiranga do Sul",
"LIG": "Andira",
"LID": "km 5",
"LIC": "Iguaçu",
"LIA": "Arigolandia",
"LHS": "Corupa",
"LHL": "Herval Doeste",
"LHA": "Harmonia",
"LGZ": "Eng. Gutierrez",
"LGZ": "Eng. Gutierrez",
"LGU": "Guarauna",
"LGU": "Guarauna",
"LGP": "Guarapuava",
"LGO": "Gal. Osório",
"LGN": "General Brito",
"LGM": "Gramado",
"LGI": "General Lucio",
"LGH": "Congonhas",
"LGE": "Germina",
"LGD": "Joaquim Tavora",
"LGA": "Gois Artigas",
"LFT": "Felipe Schmidt",
"LFP": "Fernandes Pinheiro",
"LFP": "Fernandes Pinheiro",
"LFO": "Francisco Simas",
"LFL": "Florestal",
"LFJ": "Feitor Juvencio",
"LFI": "Faxinal",
"LFC": "São Francisco do Sul",
"LFA": "Ferradura",
"LER": "Entre-Rios",
"LER": "Entre Rios",
"LEM": "Eng. Eugenio de Mello",
"LEL": "Eng. Lange",
"LEB": "Eng. Bley",
"LDV": "Desvio Ribas",
"LDR": "Parada Diretor",
"LDP": "D Pedro II",
"LDM": "Rio do Morro",
"LDC": "Dr.Camargo",
"LCZ": "Capinzal",
"LCY": "Cianorte",
"LCX": "Caxambu",
"LCV": "Aricanduva",
"LCP": "Cornelio Procopio",
"LCO": "Curitiba",
"LCN": "Canivete",
"LCM": "Cambara",
"LCH": "Cachoeira Bom Jesus",
"LCF": "California do Sul",
"LCD": "Castelar de Carvalho",
"LCC": "Cará-Cará",
"LCC": "Caracara",
"LCB": "Caranbey",
"LCA": "Castro",
"LBX": "Campinas Belas",
"LBR": "Rio Branco do Sul",
"LBQ": "Boqueirão",
"LBO": "Barreiro",
"LBN": "Balsa Nova",
"LBJ": "Bairro dos Francas",
"LBI": "Tangara",
"LBH": "Banhado",
"LBE": "Bandeirinhas",
"LBD": "Bandeirantes",
"LBA": "Guaramirim",
"LAY": "Araguari",
"LAX": "Alexandra",
"LAW": "Araucária Terminal",
"LAU": "Água Boa",
"LAT": "Antonina",
"LAR": "Araucária Carga",
"LAP": "Apucarana",
"LAO": "Afonso Camargo",
"LAN": "Rio das Antas",
"LAM": "Campo Alto do Sul",
"LAL": "Água Clara do Sul",
"LAI": "Cambira",
"LAG": "Arapongas",
"LAD": "Arroio Grande",
"LAB": "Posto km 141",
"LAA": "Km 124",
"L04": "Posto km 543",
"L03": "Fábrica Pisa",
"L02": "Monjolo",
"JVT": "Taunay",
"JVP": "Val de Palmas",
"JVA": "Valparaizo",
"JUR": "Urucum",
"JTR": "Terenos",
"JTC": "Tibirica",
"JSV": "Santa Virgínia",
"JST": "Sete Voltas",
"JSF": "Safira",
"JSD": "Sidrolandia",
"JSB": "Salobra",
"JRP": "Ponta Porã",
"JRO": "Ribas do Rio Pardo",
"JRN": "Rio Branco",
"JRI": "Arariba",
"JRG": "General Rondon",
"JRA": "Presidente Alves",
"JPY": "Pirajui",
"JPV": "Piúva",
"JPT": "Planalto",
"JPR": "Piraputanga",
"JPQ": "Piqui",
"JPN": "Penapolis",
"JPM": "Promissao",
"JPL": "Palmeiras",
"JPK": "Pena Júnior",
"JPI": "Pedro Celestino",
"JPC": "Porto Esperança",
"JPB": "Piaba",
"JPA": "Porto Carrero",
"JNG": "Nogueira",
"JMV": "Major Vicente",
"JMS": "Ministro Pestana",
"JMP": "Mirandopolis",
"JMO": "Murtinho",
"JMN": "Miranda",
"JMJ": "Maracaju",
"JMD": "Eng. Mário Dutra",
"JMA": "Mantena",
"JLZ": "Luiz Gama",
"JLV": "Lavinia",
"JLR": "Lagoa Rica",
"JLI": "Ligação",
"JLG": "Três Lagoas",
"JLB": "Lins",
"JLA": "Ladário",
"JKU": "I.Maringoni",
"JKQ": "Posto km 903",
"JKF": "Posto km 512",
"JKE": "Agente Inocêncio",
"JJQ": "Junqueira",
"JJP": "Jupia",
"JIT": "Itahum",
"JIB": "Indubrasil",
"JGY": "Aguapeí",
"JGV": "Guavira",
"JGU": "Guaicara",
"JGS": "Guaicurus",
"JGR": "Guararapes",
"JGO": "Glicério",
"JGN": "Guarantã",
"JGL": "Guia Lopes",
"JGI": "Gigante",
"JGC": "Guaracai",
"JGA": "Garcias",
"JFR": "Ferreiros",
"JFM": "Formoso",
"JFL": "Ferd Laboreau",
"JDR": "Andradina",
"JDE": "Duque Estrada",
"JCR": "Curuçá",
"JCO": "Coroados",
"JCN": "Carandazal",
"JCJ": "Cel. Juvencio",
"JCH": "Cachoeirao",
"JCG": "Campo Grande",
"JCF": "Cafelandia",
"JCB": "Corumbá",
"JCA": "Camisão",
"JBR": "Brilhante",
"JBQ": "Bodoquena",
"JBL": "Balsamo",
"JBH": "Bolicho",
"JBG": "Birigui",
"JBE": "Birigui",
"JBA": "Manoel Brandão",
"JAZ": "Arlindo Luz",
"JAV": "Avanhandava",
"JAU": "Arapua",
"JAS": "Alfredo Castilho",
"JAR": "Araçatuba",
"JAO": "Atoladeira",
"JAN": "Aquidauana",
"JAM": "Antônio Maria Coelho",
"JAL": "Alegre",
"JAI": "Avai",
"JAG": "Agachi",
"JAC": "Água Clara",
"JAB": "Albuquerque",
"ZDR": "Pátio Paratinga",
    };

    const tipificacoes = {
      "Criminal": ["Abertura", "Desengate", "Incêndio", "Furto", "Roubo", "Receptação", "Obstrução de via", "Apreensão", "Dano", "Ataque às equipes de segurança", "Ataque a funcionários e colaboradores"],
      "Mecânica": ["Desengate", "Incêndio", "Acidente", "Manutenção"],
      "Social": ["Desengate", "Acidente", "Disparo acidental", "Obstrução de via", "Apreensão", "Prevenção"],
      "Natural": ["Incêndio", "Obstrução de via", "Prevenção"]
    };
    const subtiposPorTipificacao = {
    "Abertura": ["VAGÃO", "BICA/TREMONHA", "ESCOTILHA", "CONTAINER", "VAGÃO TANQUE"],
    "Desengate": ["Durante manobra", "Durante viagem", "Composição isolada", "Entre vagões", "Na locomotiva", "VAGÃO"],
    "Incêndio": ["VAGÃO", "VIA", "COMPOSIÇÃO", "EQUIPAMENTOS", "INSTALAÇÕES"],
    "Furto": ["COMBUSTÍVEL", "CARGA/GRÃOS", "CABOS", "PEÇAS DA COMPOSIÇÃO", "MATERIAL LOGÍSTICO", "HOTBOX", "EQUIPAMENTO DE SINALIZAÇÃO", "POSTE DE MONITORAMENTO", "AMV", "DDC (DETECTOR DE DESCARRILAMENTO)", "DTQ (DETECTOR DE TRILHO QUEBRADO)", "DQB (DETECTOR DE QUEDA DE BARREIRA)", "MATERIAL DE FIXAÇÃO DE TRILHO", "DORMENTES", "TRILHO", "ENGRAXADEIRA", "EQUIPAMENTO DA EQUIPE DE SEGURANÇA"],
    "Roubo": ["COMBUSTÍVEL", "CARGA/GRÃOS", "CABOS", "PEÇAS DA COMPOSIÇÃO", "HOTBOX", "EQUIPAMENTO DE SINALIZAÇÃO", "POSTE DE MONITORAMENTO", "AMV", "DDC (DETECTOR DE DESCARRILAMENTO)", "DTQ (DETECTOR DE TRILHO QUEBRADO)", "DQB (DETECTOR DE QUEDA DE BARREIRA)", "MATERIAL DE FIXAÇÃO DE TRILHO", "DORMENTES", "ENGRAXADEIRA", "MATERIAL LOGÍSTICO", "TRILHO", "EQUIPAMENTO DA EQUIPE DE SEGURANÇA"],
    "Receptação": ["COMBUSTÍVEL", "CARGA/GRÃOS", "CABOS", "PEÇAS DA COMPOSIÇÃO", "EQUIPAMENTO DE SINALIZAÇÃO", "MATERIAL DE FIXAÇÃO DE TRILHO", "DORMENTES", "EQUIPAMENTO DA EQUIPE DE SEGURANÇA", "TRILHO", "MATERIAL LOGÍSTICO"],
    "Obstrução de via": ["MATERIAIS VARIADOS", "DESASTRE NATURAL", "Terra sobre trilho", "Vegetação", "Água", "VEÍCULOS"],
    "Apreensão": ["CARGA/GRÃOS", "COMBUSTÍVEL", "MATERIAL LOGÍSTICO", "PEÇAS DA COMPOSIÇÃO", "MATERIAL DE FIXAÇÃO DE TRILHO", "DORMENTES", "TRILHO", "ENTORPECENTES/ILÍCITOS", "MATERIAL PREPARATÓRIO PARA FURTO"],
    "Dano": ["CORTE DE MANGUEIRA", "CORTE DE CABOS", "DEPREDAÇÃO", "COMPOSIÇÃO", "INSTALAÇÕES", "TORNEIRA FECHADA", "HOT BOX", "EQUIPAMENTO DE SINALIZAÇÃO", "POSTE DE MONITORAMENTO", "AMV", "DDC (DETECTOR DE DESCARRILAMENTO)", "DTQ (DETECTOR DE TRILHO QUEBRADO)", "DQB (DETECTOR DE QUEDA DE BARREIRA)", "MATERIAL DE FIXAÇÃO DE TRILHO", "DORMENTES", "ENGRAXADEIRA", "TRILHO", "FREIO MANUAL APLICADO", "HOUSE", "MATERIAL LOGÍSTICO"],
    "Ataque às equipes de segurança": ["ROUBO DE ARMAMENTO", "LATROCÍNIO", "HOMICÍDIO", "AGRESSÃO", "AMEAÇA", "CONSTRANGIMENTO ILEGAL", "DIFAMAÇÃO/INJÚRIA"],
    "Ataque a funcionários e colaboradores": ["LATROCÍNIO", "HOMICÍDIO", "AGRESSÃO", "AMEAÇA", "CONSTRANGIMENTO ILEGAL", "DIFAMAÇÃO/INJÚRIA", "ASSÉDIO MORAL", "ASSÉDIO SEXUAL"],
    "Acidente": ["ATROPELAMENTO", "DESCARRILAMENTO", "TRÂNSITO", "ABALROAMENTO", "TRABALHO"],
    "Manutenção": ["MECÂNICA", "PERDA DE SINAL/COMUNICAÇÃO", "VIA", "INSTALAÇÕES"],
    "Disparo acidental": ["ARMA DE FOGO", "ARMAMENTO NÃO LETAL", "Sem vítimas", "Com vítima"],
    "Prevenção": ["INDIVÍDUO NA VIA", "INDIVÍDUO EMBARCADO", "CADÁVER NA VIA", "ANIMAIS NA VIA"]
  };

    function calcularTHP(id) {
      const hi = document.getElementById('hora_inicial_' + id).value;
      const hf = document.getElementById('hora_final_' + id).value;
      const thp = document.getElementById('thp_geral_' + id);
      if (hi && hf) {
        const [h1, m1] = hi.split(':').map(Number);
        const [h2, m2] = hf.split(':').map(Number);
        let t1 = h1 * 60 + m1;
        let t2 = h2 * 60 + m2;
        if (t2 < t1) t2 += 1440;
        const diff = t2 - t1;
        const hours = Math.floor(diff / 60);
        const minutes = diff % 60;
        thp.value = hours + "h " + minutes + "min";
      } else {
        thp.value = "";
      }
    }

    function atualizarLocal(siglaInput, localInput) {
      const sigla = siglaInput.value.toUpperCase();
      localInput.value = siglaParaLocal[sigla] || '';
    }

    function atualizarTipificacao(selectNatureza, tipificacaoSelect, subtipoSelect) {
      const natureza = selectNatureza.value;
      const opcoes = tipificacoes[natureza] || [];
      tipificacaoSelect.innerHTML = '<option value="">Selecione</option>';
      opcoes.forEach(opcao => {
        const opt = document.createElement("option");
        opt.text = opcao;
        tipificacaoSelect.add(opt);
      });
      if (subtipoSelect) {
        subtipoSelect.innerHTML = '<option value="">Selecione</option>';
      }
    }

    function atualizarSubtipos(tipificacaoSelect, subtipoSelect) {
      const tipificacao = tipificacaoSelect.value;
      const opcoes = subtiposPorTipificacao[tipificacao] || [];
      subtipoSelect.innerHTML = '<option value="">Selecione</option>';
      opcoes.forEach(opcao => {
        const opt = document.createElement("option");
        opt.text = opcao;
        subtipoSelect.add(opt);
      });
    }

    function limparCampos(id) {
      const ocorrencia = document.getElementById('ocorrencia_' + id);
      if (!ocorrencia) return;
      const inputs = ocorrencia.querySelectorAll('input');
      inputs.forEach(input => {
        if(input.type === 'time' || input.type === 'text') input.value = '';
        else if(input.readOnly) input.value = '';
      });
      const selects = ocorrencia.querySelectorAll('select');
      selects.forEach(sel => sel.selectedIndex = 0);
      const thp = document.getElementById('thp_geral_' + id);
      if(thp) thp.value = '';
    }
  </script>
</head>
<body>
  <h1>REGISTRO DE OCORRÊNCIAS</h1>
  <script>
    for (let i = 1; i <= 5; i++) {
      document.write(`
        <div class="ocorrencia" id="ocorrencia_${i}">
          <h2>Ocorrência ${i}</h2>
          <div class="form-row">
            <div class="form-group">
              <label>Hora Inicial</label>
              <input type="time" id="hora_inicial_${i}" onchange="calcularTHP(${i})">
            </div>
            <div class="form-group">
              <label>Composição</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>Locomotiva</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>Trecho</label>
              <select><option>0</option><option>1</option><option>2</option><option>3</option><option>FIPS</option><option>MRS</option><option>MT</option><option>MS</option><option>GO</option></select>
            </div>
            <div class="form-group">
              <label>Empresa</label>
              <select><option>RUMO</option><option>VLI</option><option>MRS</option></select>
            </div>
            <div class="form-group">
              <label>Natureza</label>
              <select id="natureza_${i}" onchange="atualizarTipificacao(this, document.getElementById('tipificacao_${i}'), document.getElementById('subtipo_${i}'))">
                <option value="">Selecione</option>
                <option>Criminal</option>
                <option>Social</option>
                <option>Natural</option>
                <option>Mecânica</option>
              </select>
            </div>
            <div class="form-group">
              <label>Tipificação</label>
              <select id="tipificacao_${i}" onchange="atualizarSubtipos(this, document.getElementById('subtipo_${i}'))">
                <option value="">Selecione</option>
              </select>
            </div>
            <div class="form-group">
              <label>Subtipo</label>
              <select id="subtipo_${i}">
                <option value="">Selecione</option>
              </select>
            </div>
            <div class="form-group">
              <label>Detalhes Tipificação</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>KM</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>Sigla</label>
              <input type="text" id="sigla_${i}" oninput="atualizarLocal(this, document.getElementById('local_${i}'))">
            </div>
            <div class="form-group">
              <label>Local</label>
              <input type="text" id="local_${i}" readonly>
            </div>
            <div class="form-group">
              <label>Hora Final</label>
              <input type="time" id="hora_final_${i}" onchange="calcularTHP(${i})">
            </div>
            <div class="form-group">
              <label>THP Geral</label>
              <input type="text" id="thp_geral_${i}" readonly>
            </div>
            <div class="form-group">
              <label>Mangueiras</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>Vagões Abertos</label>
              <input type="text">
            </div>
            <div class="form-group">
              <label>Link RFSM</label>
              <input type="text">
            </div>
          </div>

<div class="form-row">
  <div class="form-group">
    <label for="apontamento1">Apontamento</label>
    <select id="apontamento1" name="Apontamento 1">
      <option value="">Selecione</option>
      <option value="COI">COI</option>
      <option value="CCO">CCO</option>
      <option value="SEM THP / VANDALISMO">SEM THP / VANDALISMO</option>
    </select>
  </div>
</div>

          <button class="btn-limpar" onclick="limparCampos(${i})">Limpar</button>
          <button type="submit" class="btn-limpar">Submeter</button>
        </div>
      `);
    }
  </script>
</body>
</html>
