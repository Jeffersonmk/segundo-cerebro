# 🧠 Conceitos Básicos de DOM com JavaScript

## 📌 O que é o DOM

- O **DOM (Document Object Model)** é uma representação em forma de **árvore** de todos os elementos HTML de uma página.
- Cada **tag HTML** (como `<div>`, `<p>`, `<img>`, etc.) é um **nó** (node) dessa árvore.
- Com JavaScript, você pode **acessar, modificar, criar e remover** esses nós.

**Exemplo de HTML:**
```html
<html>
  <body>
    <h1>Título</h1>
    <p>Parágrafo</p>
  </body>
</html>
```

**Representação em árvore:**
```
document
└── html
    └── body
        ├── h1
        └── p
```

---

## 📍 Selecionando Elementos no DOM

```javascript
// Seleciona pelo ID
const titulo = document.getElementById("meuTitulo");

// Seleciona pela classe
const itens = document.getElementsByClassName("item");

// Seleciona pela tag
const paragrafos = document.getElementsByTagName("p");

// Seleciona usando CSS (forma mais moderna)
const botao = document.querySelector("#botao");          // um elemento
const todosOsBotoes = document.querySelectorAll(".btn"); // todos os que tiverem a classe
```

---

## ✍️ Alterando Conteúdo e Estilos

```javascript
const titulo = document.getElementById("meuTitulo");

titulo.textContent = "Novo título";
titulo.style.color = "red";
titulo.style.fontSize = "32px";
```

---

## 🧩 Criando e Removendo Elementos

```javascript
// Criar elemento
const novoParagrafo = document.createElement("p");
novoParagrafo.textContent = "Olá, mundo!";

// Adicionar ao body
document.body.appendChild(novoParagrafo);

// Remover elemento
novoParagrafo.remove();
```

---

## ⚡ Respondendo a Eventos

```javascript
const botao = document.querySelector("#botao");

botao.addEventListener("click", function() {
  alert("Botão clicado!");
});
```

---

## 📝 Resumo

- `document` é o ponto de entrada para acessar o DOM.
- Você pode:
  - Selecionar elementos (`getElementById`, `querySelector`)
  - Alterar conteúdo e estilo (`.textContent`, `.style`)
  - Criar e remover elementos (`createElement`, `.remove()`)
  - Reagir a eventos (`addEventListener`)
