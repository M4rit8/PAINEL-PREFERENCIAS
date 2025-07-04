# 🎨 Painel de Preferências

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow) ![Vue.js](https://img.shields.io/badge/Vue.js-2.x%2F3.x-42b883?logo=vue.js) ![License](https://img.shields.io/badge/license-MIT-green)

<p align="center">
  <img src="https://vuejs.org/images/logo.png" alt="Vue.js Logo" width="120"/>
</p>

> **Projeto didático para aprender a estrutura básica do Vue.js, com foco em formulários, validação, integração com API de CEP e feedback visual.**

---

## 🔎 Palavras-chave

`vuejs` `formulário` `validação` `cep` `aprendizado` `projeto didático` `frontend` `javascript` `vue` `api` `mask` `reactividade`

---

## ✨ Sobre o Projeto

O <b>Painel de Preferências</b> é um projeto didático criado para <b>aprender a estrutura básica do Vue.js</b>.<br>
Aqui você encontra um formulário moderno e interativo, com validação de campos, integração com API de CEP e feedback visual dinâmico.

---

## 🚀 Tecnologias Utilizadas

- <img src="https://img.shields.io/badge/Vue.js-2.x%2F3.x-42b883?logo=vue.js" height="20"/> [Vue.js](https://vuejs.org/)
- <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=fff" height="20"/> HTML5
- <img src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=fff" height="20"/> CSS3
- <img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=000" height="20"/> JavaScript
- <img src="https://img.shields.io/badge/API-ViaCEP-blue" height="20"/> [ViaCEP](https://viacep.com.br/)

---

## 📋 Funcionalidades

- Cadastro de nome, idade, e-mail, CEP, cor favorita, hobbies e história
- Máscara e validação para o campo de CEP
- Validação de e-mail (formato e espaços)
- Consulta automática de endereço pelo CEP
- Feedback visual para campos obrigatórios e inválidos
- Ativação do perfil apenas quando todos os campos estão corretos

---

## 🎯 Objetivo

> <b>Este projeto foi criado para aprender a estrutura básica do Vue.js, praticar conceitos de reatividade, diretivas, validação de formulários e integração com APIs.</b>

Se você está começando com Vue.js, este repositório é um ótimo ponto de partida para entender como construir componentes, manipular dados e criar interfaces dinâmicas!

---

## 🖥️ Como rodar o projeto

```bash
# Clone o repositório
$ git clone https://github.com/seu-usuario/painel-preferencias.git
$ cd painel-preferencias

# Instale as dependências
$ npm install

# Inicie o servidor de desenvolvimento
$ npm run serve

# Acesse no navegador
http://localhost:8080
```

---

## 📷 Demonstração

<p align="center">
  <img src="https://user-images.githubusercontent.com/placeholder/demo.gif" alt="Demonstração do Painel de Preferências" width="600"/>
</p>

---

## 📚 Referências

- [Documentação Oficial do Vue.js](https://vuejs.org/v2/guide/)
- [ViaCEP - API de CEP](https://viacep.com.br/)
- [Vue CLI](https://cli.vuejs.org/)

---

## 🤝 Contribuição

Sinta-se à vontade para abrir issues, sugerir melhorias ou enviar pull requests!

---

## 🧠 Aprendizados Vue.js: Reatividade na Prática

Durante o desenvolvimento deste projeto, foram explorados conceitos fundamentais do Vue.js, com foco em **reatividade** e **experimentos práticos**:

- Utilização do `v-model` para ligação bidirecional dos campos do formulário.
- Máscara dinâmica para o campo de CEP, utilizando métodos e eventos.
- Validação reativa de e-mail e CEP com regex e feedback visual imediato.
- Integração com a API ViaCEP para busca automática de endereço.
- Implementação de **dark mode** com alternância de tema e CSS dinâmico.
- Feedback visual para campos obrigatórios e inválidos, melhorando a experiência do usuário.
- Controle do estado do formulário e dos botões de forma reativa, respeitando o fluxo de ativação do perfil.

> **Experimento prático:**
> - O formulário foi projetado para só permitir ativação do perfil quando todos os campos obrigatórios estão corretos.
> - O darkmode permanece ativo mesmo após o envio do formulário, respeitando a escolha do usuário.
> - O feedback visual só aparece após interação do usuário, evitando "campos vermelhos" ao carregar.

Essas práticas reforçam o entendimento de como o Vue.js gerencia o DOM de forma eficiente e reativa, tornando o desenvolvimento frontend mais intuitivo e produtivo.

---

## 🔄 SDLC (Ciclo de Vida do Desenvolvimento de Software) aplicado

O projeto seguiu um fluxo de desenvolvimento inspirado em boas práticas de SDLC, promovendo organização, rastreabilidade e colaboração:

1. **Criação de branch para cada melhoria/feature:**
   - Exemplo: `git checkout -b feature/darkmode`
2. **Desenvolvimento incremental:**
   - Implementação de cada funcionalidade de forma isolada, com testes manuais e validação visual.
3. **Commits descritivos:**
   - Mensagens claras, seguindo padrão: `feat: adiciona darkmode com alternância de tema`
4. **Push para o repositório remoto:**
   - `git push origin feature/darkmode`
5. **Pull Request (PR):**
   - Revisão do código, descrição do que foi feito, evidências (prints/gifs) e checklist de boas práticas.
6. **Merge após aprovação:**
   - Integração da feature na branch principal (`main` ou `master`).
7. **Atualização do changelog/histórico:**
   - Registro das melhorias no README.md, facilitando o acompanhamento da evolução do projeto.

> **Exemplo de fluxo SDLC aplicado:**
> 1. Criação de branch para darkmode
> 2. Desenvolvimento e testes locais
> 3. Commit e push
> 4. Pull request com descrição e evidências
> 5. Merge após revisão
> 6. Atualização do README.md

Essas etapas garantem um desenvolvimento controlado, seguro e documentado, facilitando o aprendizado e a colaboração.

---

<p align="center">
  <b>Desenvolvido com 💚 para fins de aprendizado.</b>
</p>
