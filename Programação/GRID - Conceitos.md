# 📘 Conceitos Fundamentais de CSS Grid

> Um resumo didático dos principais conceitos de **CSS Grid**, para consultas rápidas e aprendizado progressivo.

---

## 🧱 1. O que é CSS Grid

**CSS Grid** é um sistema de layout bidimensional — ele organiza elementos em **linhas e colunas**.  
Permite criar estruturas de página complexas com pouco código e de forma responsiva.

```css
.container {
  display: grid; /* ativa o Grid */
}
```

---

## 🧩 2. Termos Importantes

- **Contêiner de Grid**: o elemento com `display: grid`.
- **Itens de Grid**: os filhos diretos do contêiner.
- **Trilhas (tracks)**: as linhas e colunas.
- **Células de Grid**: a interseção entre uma linha e uma coluna.
- **Linhas de Grid**: os limites que separam as trilhas; são numeradas (1, 2, 3... e também -1 a partir do fim).

---

## 🪟 3. Definindo Linhas e Colunas

### 3.1. Tamanhos Fixos
Define valores absolutos:
```css
grid-template-columns: 200px 400px;
grid-template-rows: 100px 200px;
```

### 3.2. Unidade Fracionária (`fr`)
Divide o espaço disponível proporcionalmente:
```css
grid-template-columns: 1fr 2fr; /* 2ª coluna = 2x a 1ª */
```

### 3.3. Automático (`auto`)
- Em **colunas**: expande para ocupar todo o espaço horizontal.
- Em **linhas**: ajusta à altura do conteúdo.

```css
grid-template-columns: 200px auto;
```

### 3.4. Função `minmax()`
Define limites mínimo e máximo:
```css
grid-template-columns: minmax(200px, 600px) 1fr;
```

### 3.5. Função `repeat()`
Evita repetição de valores:
```css
grid-template-columns: repeat(8, 1fr);
```

---

## 🧭 4. Espaçamento

O espaçamento entre linhas e colunas é feito com `gap`:
```css
gap: 10px;         /* linhas e colunas */
row-gap: 20px;     /* apenas linhas */
column-gap: 8px;   /* apenas colunas */
```

---

## ⚙️ 5. Grade Explícita e Implícita

- **Explícita**: definida manualmente (`grid-template-*`).
- **Implícita**: criada automaticamente quando há mais itens do que células.

Controle as novas trilhas criadas:
```css
grid-auto-rows: 150px;
grid-auto-columns: 200px;
grid-auto-flow: row | column | dense;
```

---

## 🎯 6. Posicionando Itens

### 6.1. `grid-column` e `grid-row`
```css
.item {
  grid-column: 1 / 3; /* da linha 1 até antes da 3 */
  grid-row: 2 / span 2; /* ocupa 2 linhas a partir da linha 2 */
}
```

### 6.2. `grid-area`
Forma abreviada para definir início e fim:
```css
.item {
  grid-area: 1 / 2 / 3 / 4; /* row-start / column-start / row-end / column-end */
}
```

### 6.3. `span`
Define quantas trilhas o item deve abranger:
```css
.item {
  grid-column: span 2;
}
```

> 🔸 Use `-1` para se referir à última linha ou coluna da grade.

---

## 🔀 7. Grid x Flexbox

| Ferramenta | Tipo | Melhor uso |
|-------------|------|-------------|
| **Flexbox** | Unidimensional | Alinhar conteúdo em uma linha ou coluna |
| **Grid**    | Bidimensional  | Criar layouts com linhas e colunas |

> 💡 Use **Grid** para estruturar o layout geral e **Flexbox** dentro dos blocos para alinhar conteúdo.

---

## 🧮 8. Áreas Nomeadas

Permite dar nomes às partes do layout — ideal para páginas completas.

```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "nav    main"
    "footer footer";
}

header { grid-area: header; }
nav    { grid-area: nav; }
main   { grid-area: main; }
footer { grid-area: footer; }
```

---

## 🪞 9. Alinhamento

Três níveis de alinhamento:

### 9.1. Grade inteira
```css
justify-content: center; /* horizontal */
align-content: center;   /* vertical */
```

### 9.2. Itens dentro das células
```css
justify-items: center;
align-items: center;
```

### 9.3. Um item específico
```css
.item {
  justify-self: end;
  align-self: start;
}
```

---

## 🧊 10. Sobreposição (Overlap)

Itens podem ocupar o mesmo espaço:
```css
.item1 {
  grid-area: 1 / 1 / 3 / 3;
}
.item2 {
  grid-area: 1 / 2 / 3 / 4;
  z-index: 2; /* aparece sobre o item1 */
}
```

---

## 🔄 11. Reordenação

A propriedade `order` muda a **ordem visual** dos itens, sem alterar o HTML:
```css
.item {
  order: 1;
}
```

> ⚠️ Atenção: `order` não muda a ordem de leitura para leitores de tela.

---

## 🧰 12. Depuração

Use as **Ferramentas do Desenvolvedor** (DevTools):
- Clique com o botão direito → *Inspecionar*.
- Ative o chip **Grid**.
- Visualize linhas numeradas, colunas e áreas com cores diferentes.

---

## ⚡ 13. Diferenças-Chave entre Grid e Flexbox

| Aspecto | Grid | Flexbox |
|----------|-------|---------|
| Dimensão | 2D (linhas + colunas) | 1D (linha **ou** coluna) |
| Controle | Layout completo | Alinhamento interno |
| Aplicação típica | Estrutura de página | Componentes e conteúdo |
| Eixo principal | X e Y | Um eixo (horizontal ou vertical) |

---

## 🧠 14. Resumo Mental

- **Grid** = estrutura geral do layout.  
- **Flexbox** = alinhamento interno de blocos.  
- Use `fr`, `auto`, `minmax()`, `repeat()` para dimensionamento dinâmico.  
- Use `grid-area` para layout semântico e responsivo.  
- Combine com `@media` para diferentes tamanhos de tela.

---

> [!note] Dica final  
> Quando pensar **“tabela”**, use **Grid**.  
> Quando pensar **“fila ou coluna de itens”**, use **Flexbox**.
