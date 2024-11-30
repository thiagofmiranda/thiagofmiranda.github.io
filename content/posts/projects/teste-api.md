---
title: "Machine Learning API Test"
date: 2024-11-28T11:06:25+06:00
description: ML API Test
menu:
  sidebar:
    name: Machine Learning API Test
    identifier: api-test
    weight: 10
tags: ["API", "Machine Learning", "AWS"]
categories: ["Machine Learning"]
---


# Introduction

I decided to write this post to demonstrate how to test my ML API deployed on AWS, you may find the API project in my repository: [Machine Learning AWS API](https://github.com/thiagofmiranda/machine-learning-aws-api). This project aims to create a Python API using FastAPI and deploy it to AWS Lambda. The API is designed to serve predictions based on models imported from an external repository: [Machine Learning Models Repository](https://github.com/thiagofmiranda/machine-learning-models). The application is containerized with Docker, providing an isolated and reproducible development environment.

Through this post, you will have the opportunity to interact with the deployed API to check its health, list available machine learning models, and detect the language of a given text (which is the unique ML model avaliable at this moment). 

Let’s dive into how to interact with the API and explore the various endpoints.

--- 

### Check API Health

Click the button below to check if the API is healthy:

<button id="check-health" class="btn btn-primary">Check API Health</button>
<div id="response-check-health" class="response"></div>

---

### List Available Machine Learning Models

Click the button below to list the available models in the API:

<button id="list-models" class="btn btn-primary">List Available Models</button>
<div id="response-list-models" class="response"></div>

---

### Test the Language Detection Model

Type some text in the field below and click the button to detect the language:

<textarea id="user-text" rows="4" placeholder="Enter your text here..." class="input-text"></textarea>
<button id="detect-language" class="btn btn-primary">Detect Language</button>
<div id="response-detect-language" class="response"></div>

---

<script>
    const apiUrl = 'https://f5fl2hbiv6.execute-api.us-east-1.amazonaws.com/dev';

    document.getElementById('check-health').addEventListener('click', () => {
        document.getElementById('response-check-health').innerHTML = '<div class="loading">Loading...</div>';
        fetch(`${apiUrl}/hc`)
            .then(response => response.json())
            .then(data => {
                document.getElementById('response-check-health').innerText = `API Health: ${data.status}`;
            })
            .catch(error => {
                document.getElementById('response-check-health').innerText = 'Error checking API health.';
            });
    });

    document.getElementById('list-models').addEventListener('click', () => {
        document.getElementById('response-list-models').innerHTML = '<div class="loading">Loading...</div>';
        fetch(`${apiUrl}/list-models`)
            .then(response => response.json())
            .then(data => {
                const models = data.available_models.map(model => `<li>${model}</li>`).join('');
                document.getElementById('response-list-models').innerHTML = `<ul>${models}</ul>`;
            })
            .catch(error => {
                document.getElementById('response-list-models').innerText = 'Error fetching models list.';
            });
    });

    document.getElementById('detect-language').addEventListener('click', () => {
        const text = document.getElementById('user-text').value;
        if (text.trim() === '') {
            document.getElementById('response-detect-language').innerText = 'Please enter some text.';
            return;
        }

        const payload = {
            input_data: {
                text: text
            }
        };

        document.getElementById('response-detect-language').innerHTML = '<div class="loading">Loading...</div>';

        fetch(`${apiUrl}/language-detection/predict`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(payload)
        })
        .then(response => response.json())
        .then(data => {
            document.getElementById('response-detect-language').innerText = `Detected Language: ${data.prediction}`;
        })
        .catch(error => {
            document.getElementById('response-detect-language').innerText = 'Error detecting language.';
        });
    });
</script>

<style>
    body {
        font-family: 'Arial', sans-serif;
        line-height: 1.6;
        margin: 0;
        padding: 20px;
        background-color: #f4f4f4;
    }

    h1 {
        color: #333;
        text-align: center;
        margin-bottom: 20px;
    }

    h2 {
        color: #007BFF;
        margin-top: 30px;
    }

    .btn {
        background-color: #007BFF;
        color: white;
        border: none;
        padding: 10px 20px;
        cursor: pointer;
        border-radius: 5px;
        font-size: 16px;
        transition: background-color 0.3s ease;
    }

    .btn:hover {
        background-color: #0056b3;
    }

    .response {
        margin-top: 20px;
        padding: 10px;
        background-color: #fff;
        border-radius: 5px;
        border: 1px solid #ddd;
    }

    .input-text {
        width: 100%;
        padding: 10px;
        margin-top: 10px;
        border-radius: 5px;
        border: 1px solid #ddd;
        font-size: 16px;
    }

    .loading {
        font-style: italic;
        color: #007BFF;
    }

    ul {
        padding-left: 20px;
    }

    ul li {
        margin-bottom: 5px;
    }
</style>
