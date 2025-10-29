# MEU-PROJETO-CSS
## 🎨 **1. Sistema de Design**


```css
:root {
  /* 🎨 Paleta de cores (mínimo 8) */
  --color-primary: #0077ff;
  --color-primary-light: #66aaff;
  --color-secondary: #ff6600;
  --color-accent: #00cc99;
  --color-success: #2ecc71;
  --color-warning: #f1c40f;
  --color-danger: #e74c3c;
  --color-neutral-100: #f9f9f9;
  --color-neutral-300: #cccccc;
  --color-neutral-600: #666666;
  --color-neutral-900: #222222;

  /* 🔠 Tipografia hierárquica (mínimo 5 tamanhos) */
  --font-xs: 0.75rem;
  --font-sm: 0.875rem;
  --font-md: 1rem;
  --font-lg: 1.25rem;
  --font-xl: 1.5rem;
  --font-family: "Roboto", sans-serif;

  /* 📏 Sistema de espaçamento (8px, 16px, 24px, 32px, 48px, 64px) */
  --space-1: 8px;
  --space-2: 16px;
  --space-3: 24px;
  --space-4: 32px;
  --space-5: 48px;
  --space-6: 64px;
}
```

Depois, aplique essas variáveis no restante dos arquivos CSS (`layout.css`, `components.css`, etc).

---

## 🧱 **2. Layouts Responsivos com Grid e Flexbox**

### 🧩 Estrutura geral (CSS Grid)

Use grid no layout principal (ex: cabeçalho, conteúdo, rodapé):

```css
body {
  display: grid;
  grid-template-areas:
    "header"
    "main"
    "footer";
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
}

header { grid-area: header; }
main { grid-area: main; }
footer { grid-area: footer; }
```

### 🧮 Sistema de Grid Customizado (12 colunas)

Crie um sistema genérico para posicionar elementos em colunas.

```css
.container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--space-2);
  max-width: 1200px;
  margin: 0 auto;
  padding: var(--space-2);
}

.col-6 { grid-column: span 6; }
.col-4 { grid-column: span 4; }
.col-12 { grid-column: span 12; }
```

### 🧰 Flexbox em componentes internos

Use Flexbox para alinhar itens dentro de seções ou componentes:

```css
.flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

### 📱 Breakpoints (mínimo 5)

Crie um arquivo `responsive.css` com seus breakpoints:

```css
@media (max-width: 1200px) { /* desktops grandes */ }
@media (max-width: 992px)  { /* notebooks */ }
@media (max-width: 768px)  { /* tablets */ }
@media (max-width: 576px)  { /* celulares médios */ }
@media (max-width: 400px)  { /* celulares pequenos */ }
```

---

## 🧭 **3. Navegação Sofisticada e Interativa**

### 🖥️ Menu principal com dropdown

```html
<nav class="navbar">
  <div class="logo">MinhaMarca</div>
  <ul class="menu">
    <li><a href="#">Home</a></li>
    <li class="dropdown">
      <a href="#">Serviços ▾</a>
      <ul class="submenu">
        <li><a href="#">Design</a></li>
        <li><a href="#">Marketing</a></li>
      </ul>
    </li>
    <li><a href="#">Contato</a></li>
  </ul>
  <button class="menu-toggle">☰</button>
</nav>
```

**CSS:**

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--space-2);
  background: var(--color-dark);
  color: white;
}

.menu {
  display: flex;
  gap: var(--space-2);
  list-style: none;
}

.submenu {
  display: none;
  position: absolute;
  background: white;
  color: var(--color-dark);
  padding: var(--space-2);
  border-radius: 4px;
}

.dropdown:hover .submenu {
  display: block;
}
```

### 📱 Navegação Mobile (menu hambúrguer)

**JS simples:**

```js
document.querySelector('.menu-toggle').addEventListener('click', () => {
  document.querySelector('.menu').classList.toggle('active');
});
```

**CSS Mobile:**

```css
@media (max-width: 768px) {
  .menu { 
    display: none; 
    flex-direction: column; 
  }
  .menu.active { display: flex; }
}
```

---

## 🧩 **4. Componentes de Interface**

### 🃏 **Cards responsivos**

```css
.card {
  background: var(--color-light);
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  padding: var(--space-3);
  transition: transform 0.3s;
}
.card:hover { transform: translateY(-5px); }
```

### 🔘 **Botões com estados**

```css
.btn {
  background: var(--color-primary);
  color: #fff;
  padding: var(--space-2) var(--space-3);
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background 0.3s;
}
.btn:hover { background: var(--color-primary-light); }
.btn:active { transform: scale(0.98); }
.btn:disabled { background: var(--color-neutral-300); cursor: not-allowed; }
```

### 🧾 **Formulários estilizados**

```css
input, textarea {
  border: 1px solid var(--color-neutral-300);
  padding: var(--space-2);
  border-radius: 4px;
  width: 100%;
}

input:focus {
  border-color: var(--color-primary);
  outline: none;
  box-shadow: 0 0 5px var(--color-primary-light);
}

input.error {
  border-color: var(--color-danger);
}
```

### ⚠️ **Feedback (alerts, toasts, modals)**

```css
.alert {
  padding: var(--space-2);
  border-radius: 4px;
  margin: var(--space-2) 0;
}

.alert-success { background: var(--color-success); color: white; }
.alert-danger  { background: var(--color-danger);  color: white; }
.alert-warning { background: var(--color-warning); color: #222; }
```

### 🏷️ **Badges e Tags**

```css
.badge {
  display: inline-block;
  background: var(--color-secondary);
  color: white;
  padding: 4px 8px;
  border-radius: 12px;
  font-size: var(--font-xs);
}
```

---

## 🗂️ **Estrutura de Pastas Recomendada**

meu-projeto/
│
├── index.html
├── css/
│   ├── variables.css
│   ├── layout.css
│   ├── components.css
│   ├── responsive.css
│   └── main.css        /* importa os outros */
├── img/
│   └── (imagens)
└── README.md

Quer que eu gere essa **estrutura completa com todos os arquivos base (HTML + CSS modularizado + menu responsivo)** para você baixar e personalizar?
Posso montar um **modelo funcional pronto para GitHub Pages**.
