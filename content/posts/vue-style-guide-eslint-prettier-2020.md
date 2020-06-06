---
title: Vue Style Guide Eslint + Prettier (2020)
date: 2020-06-06
published: true
tags: ['style-guide', 'eslint', 'prettier']
series: false
cover_image: ./images/vue-style-guide.svg
canonical_url: false
description: "Ter um código padronizado e apresentável é algo essencial para todos nos como desenvolvedores. Para isso, podemos recorrer a algumas ferramentas que facilitam na hora que estamos codando, até mesmo consertando automaticamente alguns errinhos que podemos cometer, afinal não somos robôs. Esse é o papel do Style Guide."
---

#### Por que usar um Style Guide ?

Ter um código padronizado e apresentável é algo essencial para todos nós como desenvolvedores. Para isso, podemos recorrer a algumas ferramentas que facilitam na hora em que estamos codando, até mesmo consertando automaticamente alguns errinhos que podemos cometer, afinal não somos **robôs**. Esse é o papel do **Style Guide**.

Vamos padronizar nosso código Vue. Usaremos 2 carinhas, **eslint e prettier**.

#### Ferramentas Necessárias
- [Editor de Código - Vscode](https://code.visualstudio.com/)

#### Extensões Necessárias
- [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
- [Eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)


#### Configurando EsLint
Após instalarmos todas as extensões, iremos começar a configuração do eslint. A função do eslint é encontrar e corrigir problemas em nosso código. Vamos até o arquivo de configuração do vscode em: **File>Preferences>Settings**. No canto superior direito terá uma opção **Open configuration**.

Iremos inserir as seguintes instruções no settings.json:

```json
"eslint.validate": [
  "vue",
  "html",
  "javascript"
]
```
A partir desse momento, o eslint sabe que deve validar esses três tipos de arquivos: Vue, Html, JavaScript.

Usaremos agora a seguinte linha de código:

```json
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
}
```

Ao cetar essa configuração, estamos dizendo ao eslint para rodar por debaixo dos panos, um comando chamado **ESLint: Fix all problems**, que será executado sempre que salvarmos nosso arquivo (**Famoso Ctrl + S**).

Para finalizar, vamos escrever só mais algumas linhas:

```json
"vetur.validation.template": false,
"vetur.format.defaultFormatter.js": "vscode-typescript",
"vetur.format.defaultFormatter.html": "prettier"
```
A primeira linha irá desabilitar o formatador padrão que vem integrado com a  extensão do Vetur. As duas últimas informam qual será o formatador padrão dos arquivos com extensões **html** e **js**

Após todas essas modificações, teremos no nosso settings.json algo parecido com isso:

```json
"eslint.validate": [
  "vue",
  "html",
  "javascript",
],
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
},
"vetur.validation.template": false,
"vetur.format.defaultFormatter.js": "vscode-typescript",
"vetur.format.defaultFormatter.html": "prettier"
```

#### Configurando Prettier
O Prettier já está configurado no seu VsCode. Agora vamos adicioná-lo ao seu projeto.
Abra seu terminal e digite os seguintes comandos:

```shell
Npm ou Yarn
npm install eslint-plugin-prettier eslint-config-prettier --save-dev
yarn add eslint-plugin-prettier eslint-config-prettier -D
```

Aguarde a término da instalação.

Procure na raiz do seu projeto o arquivo **.eslintrc.js**. Se o arquivo não estiver
na raiz, procure dentro do seu package.json. Encontre um array chamado **extends** e adicione
o seguinte argumento:

```js
extends: [
  "plugin:prettier/recommended"
]
```
Isso fará o eslint trabalhar em conjunto com prettier. O eslint tratará os erros
enquanto o prettier formata seu código.

Crie um arquivo na raiz chamado **.prettierrc.json**. Passe
o seguinte objeto de configuração:
```json
  {
    "singleQuote": true,
    "semi": false
  }
```

Perfeito! As 2 ferramentas já estão configuradas. Agora só aproveitar seu código
lindão e livre de problemas.

*obs - As vezes o prettier entra em conflito com o eslint gerando alguns incômodos.
Para solucioná-los, basta rodar o seguinte comando:
```shell
Npm ou Yarn
npm run eslint --fix src --ext .vue
yarn eslint --fix src --ext .vue
```
