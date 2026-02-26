# 🚀 Comandos Node.js no Terminal

Guia prático com os principais comandos para iniciar e gerenciar projetos em **Node.js**.

---

## 📦 Inicializando um Projeto

### npm init
Cria o arquivo `package.json`, que contém as informações e dependências do projeto.

```bash
npm init
```

Versão rápida (sem perguntas interativas):

```bash
npm init -y
```

---

## 📥 Instalando Dependências

### Instalar um pacote específico
```bash
npm install nome-do-pacote
```

Exemplo instalando o Express:

```bash
npm install express
```

Isso irá:
- Criar a pasta `node_modules`
- Atualizar o `package.json`
- Criar/atualizar o `package-lock.json`

---

## 🔄 Atualizar Pacotes

```bash
npm update
```

Mantém dependências atualizadas (segurança e performance).

---

## 🔎 Verificar Vulnerabilidades

```bash
npm audit fix
npm audit fix  --force 
```

## 🔎 Resetar o Servidor dentro do Projeto

```bash
npm run buid
```
## 🔎 Fazer Testes no Código

```bash
npm test
```
Analisa e corrige falhas de segurança automaticamente.

---

## ▶️ Scripts no package.json

Dentro do `package.json`, adicione:

```json
"scripts": {
  "dev": "nodemon index.js",
  "test": "jest",
  "build": "node index.js"
}
```

### Executar scripts:

```bash
npm run dev
npm run test
npm run build
```

### O que cada um faz:

- `npm run dev` → Roda o projeto com **nodemon** (reinicia automaticamente)
- `npm run test` → Executa testes com **Jest**
- `npm run build` → Executa o projeto para validar estabilidade

---

# 📘 Guia Para Absolutos em Node.js

Baseado no artigo:

- **Artigo Original**: AN ABSOLUTE BEGINNER'S GUIDE TO NODE.JS  
- **Tradução**: Eric Douglas  

Versão atualizada disponível no GitHub do tradutor.

---

## 🧠 O que é Node.js?

Node.js **não é um servidor web**.

Ele é um **ambiente de execução JavaScript (JavaScript Runtime)** que permite rodar JavaScript fora do navegador.

Se você quiser criar um servidor HTTP, você precisa programar isso (ou usar frameworks como Express).

---

## 💻 Executando Node

### Modo interativo (REPL)

```bash
node
```

Depois:

```js
console.log("Hello World")
```

---

### Executando arquivo

Crie `hello.js`:

```js
console.log("Hello World");
```

Execute:

```bash
node hello.js
```

---

## 📂 Trabalhando com Arquivos (fs)

Node possui módulos nativos como `fs` (filesystem):

```js
const fs = require("fs");

fs.readFile("arquivo.txt", (err, data) => {
  if (err) throw err;
  console.log(data.toString());
});
```

---

## ⚡ Callbacks Assíncronos

Node trabalha com operações assíncronas.

Isso significa que:
- Ele não trava esperando resposta
- Pode lidar com milhares de conexões simultaneamente
- Usa callbacks para executar código após terminar uma tarefa

---

## 🌐 Criando um Servidor HTTP

Usando módulo nativo `http`:

```js
const http = require("http");

http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello World");
}).listen(8080);

console.log("Servidor rodando na porta 8080");
```

Acesse:

```
http://localhost:8080
```

---

# 🚀 Express — Criando Servidores Mais Rápido

O **Express** é um framework minimalista para criar aplicações web com Node.js.

### Instalação:

```bash
npm install express
```

### Servidor estático básico:

```js
const express = require("express");
const app = express();

app.use(express.static("public"));

app.listen(8080, () => {
  console.log("Servidor rodando na porta 8080");
});
```

Agora tudo dentro da pasta `public` poderá ser acessado pelo navegador.

---

# 📦 Entendendo o package.json

Exemplo:

```json
{
  "name": "my-static-server",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

Para instalar todas as dependências:

```bash
npm install
```

---

# 🗂 Organização de Código

Separar responsabilidades melhora manutenção e testes.

Exemplo exportando módulo:

```js
// parser.js
class Parser {
  parse(text) {
    const results = {};
    const lines = text.split("\n");

    lines.forEach(line => {
      const parts = line.split(" ");
      const letter = parts[1];
      const count = parseInt(parts[2]);

      if (!results[letter]) results[letter] = 0;
      results[letter] += count;
    });

    return results;
  }
}

module.exports = Parser;
```

Importando:

```js
const Parser = require("./parser");
```

---

# 🏁 Resumo

Node.js permite:

- Executar JavaScript fora do navegador
- Criar servidores HTTP
- Manipular arquivos
- Trabalhar com milhares de conexões
- Usar milhares de pacotes via NPM

Express facilita a criação de aplicações web.
