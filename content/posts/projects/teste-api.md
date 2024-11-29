---
title: "API Test"
date: 2024-11-28
draft: false
---

## Testing the API

Below, we can test our AWS API.

<h1>Test API</h1>
  
  <!-- Campo para escolher a rota -->
  <label for="route">Choose Route:</label>
  <select id="route">
    <option value="hc">hc</option>
    <option value="list-models">list-models</option>
    <option value="language-detection/predict">language-detection</option>
    <!-- Adicione mais rotas se necessário -->
  </select>
  
  <!-- Campo para escolher o método -->
  <label for="method">Choose Method:</label>
  <select id="method">
    <option value="GET">GET</option>
    <option value="POST">POST</option>
  </select>

  <!-- Campo para inserir o corpo (body) no caso de POST -->
  <label for="body">Body (JSON for POST):</label>
  <textarea id="body" rows="5" cols="100" placeholder='{
    "input_data": {
        "text": "This is a test sentence."
    }
}'></textarea>

  <!-- Botão para disparar a requisição -->
  <button id="testApiButton">Call API</button>

  <h2>Response:</h2>
  <pre id="response"></pre> 

  <script>
    document.getElementById('testApiButton').addEventListener('click', function() {
      const baseUrl = 'https://x76cyvaxif.execute-api.us-east-1.amazonaws.com/dev/';
      
      // Pega os valores dos campos
      const route = document.getElementById('route').value;
      const method = document.getElementById('method').value;
      const body = document.getElementById('body').value;

      const targetUrl = baseUrl + route;  
      
      
      const options = {
        method: method,
        headers: {
          'Content-Type': 'application/json' 
        },
      };

      
      if (method === 'POST' && body) {
        options.body = body;  
      }

      // Realiza a requisição
      fetch(targetUrl, options)
        .then(response => {
          if (response.ok) {
            return response.json();  // Converte a resposta para JSON
          } else {
            throw new Error('Network response was not ok');
          }
        })
        .then(data => {
          // Exibe os dados JSON na tela
          document.getElementById('response').textContent = JSON.stringify(data, null, 2);
        })
        .catch(error => {
          // Exibe erro se houver
          document.getElementById('response').textContent = 'Error calling the API: ' + error.message;
        });
    });
  </script>