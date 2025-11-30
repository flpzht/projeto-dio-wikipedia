# 📘 Projeto: Página Web com Layout Semântico, Header Responsivo e Sidebars com Grid

Este projeto é baseado na estrutura apresentada no repositório
**[digitalinnovationone/trilha-html-modulo-3](https://github.com/digitalinnovationone/trilha-html-modulo-3)**,
com foco em boas práticas HTML e CSS modernas.

A proposta foi **evoluir a página**, mantendo a cara da Wiki da trilha, porém aplicando:

* Tags **semânticas reais**
* Layout **responsivo** utilizando **CSS Grid**
* Um **header moderno**, com logo à esquerda e título centralizado
* Melhor organização, limpeza e padronização do CSS
* Correção de problemas comuns de responsividade

---

## 🛠️ Melhorias Implementadas

### ✅ 1. Substituição de `<div class="...">` por tags semânticas

As seções principais da página foram convertidas para:

| Antes                   | Depois                                             |
| ----------------------- | -------------------------------------------------- |
| `<div class="sidebar">` | `<aside>`                                          |
| `<div class="anchors">` | `<aside>`                                          |
| `<div class="main">`    | `<main>`                                           |
| `<div class="footer">`  | `<footer>`                                         |
| `<div class="bar">`     | Mantido, pois não existe tag semântica equivalente |

Essas mudanças melhoram:

* SEO
* Acessibilidade
* Clareza do código
* Organização semântica da página

---

### ✅ 2. Reestruturação completa do Header

O header foi remodelado para:

* **Logo alinhado à esquerda**
* **Título centralizado**
* Garantir que o título continue centralizado mesmo com o logo presente
* Comportamento responsivo em telas menores

Uso de `position: absolute` no título permite alinhamento sem comprometer o fluxo do layout.

---

### ✅ 3. Ajuste do Layout Principal usando CSS Grid

O layout da página foi mantido em **três colunas**, utilizando **CSS Grid**, garantindo:

```
[ sidebar ]  [ main ]  [ anchors ]
```

A versão responsiva reorganiza para:

```
[ sidebar ]
[ main ]
[ anchors ]
```

Assim, evita distorção de colunas e mantém leitura confortável em telas pequenas.

---

### ✅ 4. Limpeza e otimização do CSS

Foram removidas:

* Propriedades duplicadas
* Regras que não tinham efeito (ex.: grid configurado dentro de um flex)
* Estilos conflitantes

O CSS foi reorganizado em seções claras:

1. Reset / Base
2. Header
3. Layout
4. Elementos específicos
5. Responsividade

---

### ✅ 5. Responsividade completa

Foram criados breakpoints:

* **900px:** reorganiza o layout em 1 coluna
* **600px:** ajusta tamanhos de imagens e espaçamentos

Também:

* O logo some no mobile para não quebrar o layout do header
* Bordas laterais são removidas em telas estreitas
* O título deixa de usar posição absoluta e centraliza automaticamente

---

## 📄 Arquitetura Final do Projeto

```
/
├── assets/
│   ├── css/
│   │   └── style.css
│   └── imgs/
│       └── logo-wikiflp.png
│
├── index.html
└── README.md
```

---

## 🖥️ Estrutura do HTML Final (resumo)

```html
<header>
    <figure class="logo">
        <img src="assets/imgs/logo-wikiflp.png" />
    </figure>
    <h1 class="title">Título da Página</h1>
</header>

<div class="bar"></div>

<div class="content">
    <aside class="sidebar">
        ...
    </aside>

    <main>
        ...
    </main>

    <aside class="anchors">
        ...
    </aside>
</div>

<footer class="footer">
    ...
</footer>
```

---

## 🎨 CSS Final Utilizado

O CSS otimizado aplicado no projeto está reproduzido na íntegra abaixo:

<details>
<summary><strong>Clique para expandir o CSS completo</strong></summary>

```css
/* --------------------------
   RESET / BASE
--------------------------- */
html, body {
    margin: 0;
    padding: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #fff8dc;
}

ul {
    list-style: none;
    padding-left: 5px;
}

a {
    color: lightsalmon;
    text-decoration: none;
}

/* --------------------------
   HEADER
--------------------------- */
header {
    position: relative;
    display: flex;
    align-items: center;
    padding: 10px 1rem;
    border-bottom: 1px solid #f1cf85;
    background-color: #333;
    width: 100%;
}

.logo img {
    width: 100px;
    height: auto;
}

.title {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-size: 30px;
    color: #f1cf85;
    margin: 0;
}

/* Barra abaixo do header */
.bar {
    background-color: #fbbc92;
    width: 100%;
    height: 15px;
}

/* --------------------------
   LAYOUT DO CONTEÚDO
--------------------------- */
.content {
    max-width: 1000px;
    margin: auto;
    display: grid;
    gap: 3rem;
    grid-template-areas: 
        "sidebar main anchors";
    grid-template-columns: 15rem 1fr 15rem;
    padding: 1rem;
}

.sidebar {
    grid-area: sidebar;
    border-right: solid 1px #f1cf85;
    padding-right: 15px;
}

main {
    grid-area: main;
}

.anchors {
    grid-area: anchors;
    border-left: solid 1px #f1cf85;
    padding-left: 15px;
}

/* --------------------------
   FIGURA / ESCUDO
--------------------------- */
.escudo {
    text-align: center;
    margin: 2rem 0;
}

.escudo img {
    width: 150px;
    max-width: 100%;
    height: auto;
    display: block;
    margin: 1rem auto;
}

/* --------------------------
   FOOTER
--------------------------- */
.footer {
    text-align: center;
    padding: 10px 0;
    background-color: #fbbc92;
    color: #333;
    margin-top: 10px;
}

.footer p {
    margin: 10px;
}

/* --------------------------
   RESPONSIVIDADE
--------------------------- */
@media (max-width: 900px) {
    .content {
        grid-template-areas:
            "sidebar"
            "main"
            "anchors";
        grid-template-columns: 1fr;
    }

    .sidebar,
    .anchors {
        border: none;
        padding: 0;
    }

    .title {
        position: static;
        transform: none;
        text-align: center;
        width: 100%;
    }

    header {
        justify-content: center;
    }

    .logo {
        display: none;
    }
}

@media (max-width: 600px) {
    .escudo img {
        width: 120px;
    }
}
```

</details>

---

## 🚀 Como executar o projeto

1. Clone o repositório:

```
git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
```

2. Abra o arquivo:

```
index.html
```

3. (Opcional) Use a extensão "Live Server" no VS Code para visualizar dinamicamente.

---

## 📚 Conceitos aplicados

* Semântica HTML5
* CSS Grid
* Flexbox (no header)
* Imagens responsivas
* Layout fluido
* Boas práticas de acessibilidade
* Responsividade profissional

---

## 📄 Licença

Projeto baseado na trilha da Digital Innovation One, para fins educacionais.

---

Se quiser, posso:

✅ Criar também um **`index.html` final completo**
✅ Gerar uma **prévia visual** do layout
✅ Estruturar isso como um repositório Git pronto
É só pedir!
