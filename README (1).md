# 🌾 Gestão Agronegócios

> Sistema de gestão rural para pecuaristas de corte — do terminal Python a uma Progressive Web App.

![Status](https://img.shields.io/badge/status-ativo-brightgreen)
![Versão](https://img.shields.io/badge/versão-2.0-blue)
![Python](https://img.shields.io/badge/Python-3.x-yellow)
![HTML](https://img.shields.io/badge/HTML5%20%2F%20CSS3%20%2F%20JS-Vanilla-orange)
![Licença](https://img.shields.io/badge/licença-MIT-green)

---

## 📌 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Versões](#-versões)
  - [v1.0 — MVP Python (Terminal)](#v10--mvp-python-terminal)
  - [v2.0 — Progressive Web App](#v20--progressive-web-app)
- [Regras de Negócio](#-regras-de-negócio)
- [Estrutura do Repositório](#-estrutura-do-repositório)
- [Como Executar](#-como-executar)
- [Tecnologias](#-tecnologias)
- [Autor](#-autor)

---

## 📖 Sobre o Projeto

O **Gestão Agronegócios** nasceu como projeto acadêmico de 1º semestre e evoluiu para uma aplicação web instalável. O sistema resolve um problema real do pequeno pecuarista: tomar decisões rápidas no campo sem precisar de planilhas ou conexão com internet.

**Dois módulos principais:**

| Módulo | O que resolve |
|---|---|
| 💰 Gestão Financeira | Calcula lucro/prejuízo da operação e exibe o status de saúde financeira |
| ⚖️ Pesagem e Nutrição | Verifica se o animal atingiu o peso ideal e, se não, aciona automaticamente o plano de nutrição com custo estimado |

---

## 🔄 Versões

### v1.0 — MVP Python (Terminal)

Primeira versão entregue como trabalho acadêmico de 1º semestre. Desenvolvida com recursos básicos de Python, sem uso de bibliotecas, funções, classes ou dicionários.

**Arquivo:** `main.py`

**Funcionalidades:**
- Menu interativo no terminal com `while True`
- Módulo de Gestão Financeira com `if/else`
- Módulo de Pesagem e Nutrição com lógica condicional encadeada
- Opção de sair com `break`

**Restrições técnicas aplicadas (nível 1º semestre):**
- Apenas: `while`, `if/elif/else`, `input()`, `print()`, `float()`
- Zero bibliotecas externas
- Zero funções (`def`), classes, listas ou dicionários

**Como executar:**
```bash
python main.py
```

**Exemplo de saída:**
```
==================================================
        🌾  AGRO GESTÃO  🌾
   Sistema de Gestão para Produtor Rural
==================================================
  [1]  💰  Gestão Financeira
  [2]  🐂  Pesagem e Nutrição Inteligente
  [3]  🚪  Sair do Sistema
==================================================
  👉  Escolha uma opção: 2

  🎯  Peso Ideal / Meta (KG): 450
  ⚖️   Peso Atual na Balança (KG): 380

  ──────────────────────────────────
  Peso Ideal:  450.00 kg
  Peso Atual:  380.00 kg
  ──────────────────────────────────
  ⚠️   Animal abaixo do peso em 70.00 kg.

  🌽  MÓDULO DE NUTRIÇÃO ACIONADO
  ──────────────────────────────────
  💲  Preço do KG de ração (R$): 3.50

  ──────────────────────────────────
  KG de ração necessário:     70.00 kg
  Custo estimado de nutrição: R$ 245.00
  ──────────────────────────────────
  📋  Recomendação: acompanhar a dieta
      e pesar novamente em 30 dias.
==================================================
```

---

### v2.0 — Progressive Web App

Refatoração completa para uma Single Page Application instalável no celular, com suporte offline via Service Worker.

**Arquivo principal:** `index.html`  
**Arquivos de suporte:** `manifest.json`, `service-worker.js`

**O que foi adicionado nesta versão:**

| Recurso | Descrição |
|---|---|
| Tab Bar inferior | Navegação nativa estilo app mobile |
| Validação inline | Erros exibidos abaixo de cada campo, sem `alert()` |
| `localStorage` | Últimos valores preenchidos são restaurados automaticamente |
| Service Worker | Cache offline — funciona sem internet no campo |
| `manifest.json` | Instalável como app no Android e iOS (PWA) |
| `inputmode="decimal"` | Teclado numérico nativo no celular |
| `safe-area-inset` | Suporte a notch e barra de gestos do iPhone |
| Banner de instalação | Aparece automaticamente no Chrome/Android |

**Deploy no GitHub Pages:**
1. Faça upload de `index.html`, `manifest.json` e `service-worker.js` na raiz do repositório
2. Vá em **Settings → Pages → Branch: main → Save**
3. Acesse `https://seu-usuario.github.io/nome-do-repositorio`

---

## 🧮 Regras de Negócio

### Módulo 1 — Gestão Financeira

```
Lucro = Ganhos Totais − Custos Totais
```

| Condição | Status exibido |
|---|---|
| `Lucro > 0` | ✅ OPERAÇÃO SAUDÁVEL |
| `Lucro ≤ 0` | ❌ PREJUÍZO |

### Módulo 2 — Pesagem e Nutrição

```
Défice = Peso Ideal − Peso Atual
KG de Ração = Défice × Conversão Alimentar (CA = 7,0)
Custo Total  = KG de Ração × Preço do KG de Ração
```

| Condição | Status exibido |
|---|---|
| `Peso Atual >= Peso Ideal` | ✅ Animal no peso ideal |
| `Peso Atual < Peso Ideal` | ⚠️ Módulo de Nutrição acionado |

> **CA = 7,0** é a constante de Conversão Alimentar utilizada no projeto — valor fictício adotado para fins acadêmicos.

---

## 📁 Estrutura do Repositório

```
gestao-agronegocios/
│
├── main.py              # v1.0 — Script Python para terminal
│
├── index.html           # v2.0 — SPA completa (HTML + CSS + JS)
├── manifest.json        # v2.0 — Configuração PWA
├── service-worker.js    # v2.0 — Cache offline
│
├── icons/               # Ícones do app (72px até 512px)
│   ├── icon-192.png
│   └── icon-512.png
│
└── README.md
```

---

## 🚀 Como Executar

### Versão Python (v1.0)

**Pré-requisito:** Python 3 instalado.

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/gestao-agronegocios.git

# Entre na pasta
cd gestao-agronegocios

# Execute
python main.py
```

### Versão Web (v2.0)

**Opção 1 — Direto no navegador:**
Abra o arquivo `index.html` diretamente no Chrome ou Edge.

**Opção 2 — GitHub Pages (recomendado):**
```
https://seu-usuario.github.io/gestao-agronegocios
```

**Opção 3 — Servidor local:**
```bash
# Com Python
python -m http.server 8000

# Com Node.js
npx serve .
```

> Para o Service Worker funcionar corretamente, é necessário rodar via servidor HTTP (opções 2 ou 3), não pelo protocolo `file://`.

---

## 🛠️ Tecnologias

### v1.0 — Python
| Recurso | Uso |
|---|---|
| `while True` | Mantém o menu ativo |
| `if / elif / else` | Lógica de negócio e condicionais |
| `input()` + `float()` | Captura e conversão de dados |
| `print()` + f-strings | Saída formatada no terminal |

### v2.0 — Web
| Tecnologia | Uso |
|---|---|
| HTML5 | Estrutura da SPA |
| CSS3 (Variáveis + Flexbox) | Layout mobile-first e temas |
| JavaScript Vanilla | Lógica, navegação e DOM |
| Web App Manifest | Instalação como PWA |
| Service Worker | Funcionamento offline |
| localStorage | Persistência leve de dados |

---

## 👤 Autor

Desenvolvido como projeto acadêmico de 1º semestre.

---

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.
