![Módulo 02 | Introdução ao NodeJS](https://repository-images.githubusercontent.com/474757409/ffa632d4-d203-4a28-8fb1-1a7f2b55f8ad)

# Módulo 02 | Introdução ao NodeJS

Resolução prática PG do módulo 02 - Introdução a Node e JavaScript.

___

## Objetivo

Pôr em prática os conceitos aprendidos ao longo do módulo "Introdução ao Node e JavaScript" através das práticas propostas no PG.

___

## Pré Requisitos

O que é necessário para acompanhar a prática?

* Ter as ferramentas instaladas em ambiente local (*node.js*, *npm*, *VSCode*, *gitBash*)

* Ter uma conta no gitHub (ou similar) para versionar o projeto

* Consumir o conteúdo do PlayGround

* Assistir as aulas síncronas

___

## Enunciados e Respostas

Replicação dos enunciados para facilitar a compreensão dos exercícios.

### Módulo 02 | Aula 01 - Introdução a NodeJS

Práticas referentes a Aula 01

#### Parte 01

* No terminal verificar se o *node* foi instalado

```sh
node -v
```

* Criar pasta para projeto, chamada CineHouse

```sh
mkdir CineHouse
```

* Criar arquivo chamado *cinema.js*, nele criar uma variável chamada cinema e esta deverá receber um valor como nome da loja

```sh
cd CineHouse && touch cinema.js
```

```js
const cinema = "CineMarco"
```

#### Parte 02

* Executar `npm init` e verificar as mudanças que ocorreram na pasta e arquivos novos adicionados ao projeto

```sh
npm init

# Preencher as perguntas conforme preferências
```

* No arquivo *cinema.js* passar a variável anteriormente criada como parâmetro do `console.log`, a fim de que ao executar o arquivo

```js
console.log(cinema)
```

* Executar o arquivo

```sh
node cinema.js
```

* Instalar o pacote *nodemon*

```sh
npm i --save -D nodemon
```

* Analisar a pasta *node_modules*

### Módulo 02 | Aula 02 - Revisão de funções, condicionais e Arrays

Práticas referentes a Aula 02

#### Parte 01

* No arquivo criado na última aula (*cinema.js*), deve ser criada uma variável do tipo *array* chamada catalogo. Esta será um *array* de objetos, onde cada objeto representará um filme.

```js
const catalogo = []
```

* O filme deve conter os seguintes atributos:

  a. `codigo` (numérico - identificador do filme)

  b. `titulo` (*string*)

  c. `duracao` (numérico - em horas)

  d. `atores` (*array* de *strings* - nomes)

  e. `anoDeLancamento` (numérico)

  f. `emCartaz` (*booleano*)

* Deverão ser criados dois registros de filmes (de acordo com sua preferência). É importante apenas que um deles receba o valor de `true` na propriedade `emCartaz` e o outro o valor `false`.

```js
const catalogo = [{
        codigo: 1,
        titulo: "O Poderoso Chefão",
        duracao: 2.91,
        atores: ["Al Pacino", "Marlon Brando", "Diane Keaton", "Robert De Niro"],
        anoDeLancamento: 1972,
        emCartaz: true
    },
    {
        codigo: 2,
        titulo: "O Mágico de Oz",
        duracao: 1.86,
        atores: ["Judy Garland", "Jack Haley", "Bert Lahr", "Frank Morgan"],
        anoDeLancamento: 1939,
        emCartaz: false
    }
]
```

#### Parte 02

* `adicionarFilme` | A função deve receber os parâmetros com as informações necessárias para criar um objeto do tipo Filme.

```js
const adicionarFilme = filme => catalogo.push(filme)
const testarAdicionarFilme = () => {
    console.log(`Antes da adição do novo filme ao catálogo, o catálogo possui ${catalogo.length} filmes.`)
    adicionarFilme({
        codigo: 3,
        titulo: "Cidadão Kane",
        duracao: 1.98,
        atores: ["Orson Welles", "Joseph Cotten", "Dorothy Comingore", "William Alland"],
        anoDeLancamento: 1941,
        emCartaz: false
    })
    console.log(`Após adição do novo filme ao catálogo, o catálogo possui ${catalogo.length} filmes.`)
}
testarAdicionarFilme()
```

* `buscarFilme` | A função deve receber como parâmetro o número identificador do filme e fazer busca no *array* de catálogo e ao fim retornar o objeto encontrado. Preferencialmente, retorne de forma mais amigável ao usuário final (pode utilizar `console` para não retornar apenas o objeto).

```js
const buscarFilme = codigo => {
    for (let filme of catalogo) {
        if (filme.codigo === codigo) {
            console.log(`O filme de código ${codigo} se chama ${filme.titulo}`)
        }
    }
}
const testarBuscarFilme = () => {
    buscarFilme(1)
    buscarFilme(2)
}
testarBuscarFilme()
```

* `alterarStatusEmCartaz` | A função deve receber como parâmetro o número identificador do filme escolhido, buscar o filme com base no parâmetro recebido e alterar o status existente da propriedade `emCartaz` (se estava como `true`, alterar para `false`, e vice e versa).

```js
const alterarStatusEmCartaz = codigo => {
    for (let filme of catalogo) {
        if (filme.codigo === codigo) {
            console.log(`Status do filme ${filme.titulo} (código ${codigo}) antes: ${filme.emCartaz}`)
            filme.emCartaz = !filme.emCartaz
            console.log(`Status do filme ${filme.titulo} (código ${codigo}) depois: ${filme.emCartaz}`)
        }
    }
}
const testarAlterarStatusEmCartaz = () => {
    alterarStatusEmCartaz(1)
    alterarStatusEmCartaz(2)
}
testarAlterarStatusEmCartaz()
```

#### Parte 03

* Criar uma pasta nova - *Calculadora* - (separa dos projetos anteriores para perdermos onde essa prática será feita).

```sh
cd .. && mkdir Calculadora
```

* Criar um arquivo *somar.js* que contenha uma função chamada `somar`, a qual deve ser exportada ao final do arquivo. Esta função deve receber 2 parâmetros e retornar a soma dos mesmos.

```sh
touch somar.js && code ./somar.js
```

```js
const somar = (num1, num2) => num1 + num2
console.log(`Função somar recebendo 1 e 2 retorna: ${somar(1,2)}`)

module.exports = somar
```

* Criar um arquivo *subtrair.js* que contenha uma função chamada `subtrair`, a qual deve ser exportada ao final do arquivo. Esta função deve receber 2 parâmetros e retornar a diferença entre eles.

```sh
touch subtrair.js && code ./subtrair.js
```

```js
const subtrair = (num1, num2) => num1 - num2
console.log(`Função subtrair recebendo 10 e 2 retorna: ${subtrair(10,2)}`)

module.exports = subtrair
```

* Criar um arquivo *multiplicar.js* que contenha uma função chamada `multiplicar`, a qual deve ser exportada ao final do arquivo. Esta função deve receber 2 parâmetros e retornar a multiplicação dos mesmos.

```sh
touch multiplicar.js && code ./multiplicar.js
```

```js
const multiplicar = (num1, num2) => num1 * num2
console.log(`Função multiplicar recebendo 10 e 2 retorna: ${multiplicar(10,2)}`)
console.log(`Função multiplicar recebendo 10 e 0 retorna: ${multiplicar(10,0)}`)
console.log(`Função multiplicar recebendo 0 e 10 retorna: ${multiplicar(0,10)}`)
console.log(`Função multiplicar recebendo 0 e 0 retorna: ${multiplicar(0,0)}`)

module.exports = multiplicar
```

* Criar um arquivo *dividir.js* que contenha uma função chamada `dividir`, a qual deve ser exportada ao final do arquivo. Esta função deve receber 2 parâmetros e retornar a divisão dos mesmos. Importante: contemplar o cenário em que se algum dos dois parâmetros é zero, a função
retornará "Não se pode dividir por zero".

> **ERRATA**: na realidade, apenas o segundo parâmetro não pode ser 0. Isso por que não se pode dividir um número por 0, mas **é possível dividir 0 por qualquer número (que não seja 0)**.

```sh
touch dividir.js && code ./dividir.js
```

```js
const dividir = (num1, num2) => num2 === 0 ? "Não se pode dividir por zero" : num1 * num2
/**
 * NOTA DE ESCLARECIMENTO 
 * O exercício pede para retornarmos "Não se pode dividir por zero" caso qualquer um dos dois números seja 0.
 * No entanto, não se pode dividir um número por 0, mas é possível dividir 0 por qualquer número (que não seja 0).
 */
console.log(`Função dividir recebendo 10 e 2 retorna: ${dividir(10,2)}`)
console.log(`Função dividir recebendo 10 e 0 retorna: ${dividir(10,0)}`)
console.log(`Função dividir recebendo 0 e 10 retorna: ${dividir(0,10)}`)
console.log(`Função dividir recebendo 0 e 0 retorna: ${dividir(0,0)}`)

module.exports = dividir
```

#### Parte 04

* Criar um arquivo *calculadora.js*, em que devemos importar os quatro arquivos feitos anteriormente.

```sh
touch calculadora.js && code ./calculadora.js
```

```js
const somar = require('./somar')
const subtrair = require('./subtrair')
const multiplicar = require('./multiplicar')
const dividir = require('./dividir')
```

* Executar a função que permite somar e a função que permite subtrair, passando como argumentos dois números quaisquer. Mostrar no *console* os resultados.

```js
console.log(`Função somar recebendo 1 e 2 retorna: ${somar(1,2)}`)
console.log(`Função subtrair recebendo 10 e 2 retorna: ${subtrair(10,2)}`)
```

* Executar a função que permite multiplicar, passando como argumentos dois números quaisquer. Mostrar no *console* o resultado.

```js
console.log(`Função multiplicar recebendo 10 e 2 retorna: ${multiplicar(10,2)}`)
```

* Executar a função que permite multiplicar, passando agora como um dos dois argumentos, o número zero. Mostrar no *console* o resultado.

```js
console.log(`Função multiplicar recebendo 10 e 0 retorna: ${multiplicar(10,0)}`)
console.log(`Função multiplicar recebendo 0 e 10 retorna: ${multiplicar(0,10)}`)
console.log(`Função multiplicar recebendo 0 e 0 retorna: ${multiplicar(0,0)}`)
```

* Executar a função que permite dividir, passando como argumentos dois números quaisquer. Mostrar no *console* o resultado.

```js
console.log(`Função dividir recebendo 10 e 2 retorna: ${dividir(10,2)}`)
console.log(`Função dividir recebendo 0 e 10 retorna: ${dividir(0,10)}`)
```

* Executar a função que permite dividir, passando agora como um dos dois argumentos, o número zero. Mostrar no *console* o resultado.

```js
console.log(`Função dividir recebendo 10 e 0 retorna: ${dividir(10,0)}`)
console.log(`Função dividir recebendo 0 e 0 retorna: ${dividir(0,0)}`)
```

### Módulo 02 | Aula 03 - JSON, mais condicionais e ciclos

Práticas referentes a Aula 03

#### Parte 01

* Chegou o momento de deixarmos de utilizar o objeto literal integrado ao arquivo principal. Vamos modularizar essa nossa base de informações de filmes. Para isso crie, na pasta raíz do projeto, uma nova pasta chamada *database* (aqui será alocado qualquer arquivo que nos sirva como base de informações a serem consultadas).

```sh
mkdir database
```

* Crie, dentro da pasta, um arquivo chamado *catalogo.json*.

```sh
cd database && touch catalogo.json && code ./catalogo.json
```

* Passe para esse arquivo todos os registros criados por você no arquivo *cinema.js*. E exclua o objeto `catalogo` do arquivo citado.

> Lembre-se de que a forma de escrita de objeto para JSON, apesar de serem bem parecidas, não são iguais.

```json
{
  "name": "cinehouse",
  "version": "1.0.0",
  "description": "Prática CineHouse do módulo 02 - Introdução ao Node e JavaScript'",
  "main": "cinema.js",
  "scripts": {
    "start": "node cinema.js",
    "dev": "nodemon cinema.js"
  },
  "keywords": [
    "node",
    "javascript"
  ],
  "author": "Marcelo Diament",
  "license": "MIT",
  "devDependencies": {
    "nodemon": "^2.0.15"
  }
}
[
  {
    "codigo": 1,
    "titulo": "O Poderoso Chefão",
    "duracao": 2.91,
    "atores": [
      "Al Pacino",
      "Marlon Brando",
      "Diane Keaton",
      "Robert De Niro"
    ],
    "anoDeLancamento": 1972,
    "emCartaz": true
  },
  {
    "codigo": 2,
    "titulo": "O Mágico de Oz",
    "duracao": 1.86,
    "atores": [
      "Judy Garland",
      "Jack Haley",
      "Bert Lahr",
      "Frank Morgan"
    ],
    "anoDeLancamento": 1939,
    "emCartaz": false
  }
]
```

* Perceba que ainda precisaremos das informações dos filmes para que as funções criadas no arquivo *cinema.js* funcione. Para isso você deve importar o arquivo JSON e armazená-los em uma variável.

```js
const catalogo = require('./database/catalogo.json')
```

* Teste as funções novamente certificando-se de que a migração de arquivo e formato não prejudicou seu funcionamento.

```sh
node cinema.js
```

#### Parte 02

* `listarTodosOsFilmes` | A função deve percorrer toda a lista de filmes armazenada no catálogo utilizando o *loop* `for` e retornar as informações de maneira amigável ao usuário.

```js
const listarTodosOsFilmes = () => {
    for (let filme of catalogo) {
        console.log(`
      Título: ${filme.titulo}
      Código: ${filme.codigo}
      Ano: ${filme.anoDeLancamento}
      Duração (hs): ${filme.duracao}
      Atores: ${filme.atores.join(', ')}
      Status: ${filme.emCartaz ? "Em cartaz" : "Não está em cartaz"}
    `)
    }
}
const testarListarTodosOsFilmes = () => listarTodosOsFilmes()
testarListarTodosOsFilmes()
```

* `listarFilmesEmCartaz` | A função deve percorrer toda a lista de filmes armazenada no catálogo utilizando o *loop* `for` e retornar os filmes disponíveis em cartaz - as informações de maneira amigável ao usuário.

```js
const listarFilmesEmCartaz = () => {
    for (let filme of catalogo) {
        if (filme.emCartaz) {
            console.log(`
        Título: ${filme.titulo}
        Código: ${filme.codigo}
        Ano: ${filme.anoDeLancamento}
        Duração (hs): ${filme.duracao}
        Atores: ${filme.atores.join(', ')}
        Status: ${filme.emCartaz ? "Em cartaz" : "Não está em cartaz"}
      `)
        }
    }
}
const testarListarFilmesEmCartaz = () => listarFilmesEmCartaz()
testarListarFilmesEmCartaz()
```

* `alterarStatusEmCartaz` | A função deve receber como parâmetro o número identificador do filme escolhido, buscar o filme com base no parâmetro recebido e alterar o status existente da propriedade `emCartaz` (se estava como `true`, alterar para `false`, e vice e versa). O escopo é igual ao da aula passada, porém o desafio é ao invés de usarmos a estrutura condicional `if` que estamos habituados, mudar para `if` ternário.

```js
const alterarStatusEmCartaz = codigo => {
    for (let filme of catalogo) {
        if (filme.codigo === codigo) {
            console.log(`Status do filme ${filme.titulo} (código ${codigo}) antes: ${filme.emCartaz}`)
            filme.emCartaz = filme.emCartaz ? false : true
            console.log(`Status do filme ${filme.titulo} (código ${codigo}) depois: ${filme.emCartaz}`)
        }
    }
}
const testarAlterarStatusEmCartaz = () => {
    alterarStatusEmCartaz(1)
    alterarStatusEmCartaz(2)
}
testarAlterarStatusEmCartaz()
```

### Refatoração

Algumas melhorias aplicadas, de acordo com o conteúdo apresentado no módulo.

**CineHouse/cinema.js**

```js
const catalogo = require('./database/catalogo.json')

// const cinema = "CineMarco"
// console.log(cinema)

const adicionarFilme = filme => catalogo.push(filme)
const testarAdicionarFilme = () => {
    console.log(`Antes da adição do novo filme ao catálogo, o catálogo possui ${catalogo.length} filmes.`)
    adicionarFilme({
        codigo: 3,
        titulo: "Cidadão Kane",
        duracao: 1.98,
        atores: ["Orson Welles", "Joseph Cotten", "Dorothy Comingore", "William Alland"],
        anoDeLancamento: 1941,
        emCartaz: false
    })
    console.log(`Após adição do novo filme ao catálogo, o catálogo possui ${catalogo.length} filmes.`)
}
// testarAdicionarFilme()

const buscarFilme = codigo => {
    let resultado = catalogo.filter(filme => filme.codigo == codigo)[0]
    console.log(resultado ? `O filme de código ${codigo} se chama ${resultado.titulo}` : `Não existe filme cujo código seja ${codigo}`)
    return resultado
}
const testarBuscarFilme = () => {
    buscarFilme(1)
    buscarFilme(2)
    buscarFilme(3)
}
// testarBuscarFilme()

const alterarStatusEmCartaz = codigo => {
    let resultado = buscarFilme(codigo)
    if (resultado && resultado.titulo) {
        let {
            titulo,
            emCartaz
        } = resultado
        console.log(`Status do filme ${titulo} (código ${codigo}) antes: ${emCartaz}`)
        emCartaz = !emCartaz
        console.log(`Status do filme ${titulo} (código ${codigo}) depois: ${emCartaz}`)
    }
    return resultado
}
const testarAlterarStatusEmCartaz = () => {
    alterarStatusEmCartaz(1)
    alterarStatusEmCartaz(2)
    alterarStatusEmCartaz(3)
}
// testarAlterarStatusEmCartaz()

// Função de Apoio
const mostrarDetalhesFilme = filme => {
    const {
        titulo,
        codigo,
        anoDeLancamento,
        duracao,
        atores,
        emCartaz
    } = filme
    return `
    Título: ${titulo}
    Código: ${codigo}
    Ano: ${anoDeLancamento}
    Duração (hs): ${duracao}
    Atores: ${atores.join(', ')}
    Status: ${emCartaz ? "Em cartaz" : "Não está em cartaz"}
  `
}

const listarTodosOsFilmes = () => {
    catalogo.forEach(filme => console.log(mostrarDetalhesFilme(filme)))
}
const testarListarTodosOsFilmes = () => listarTodosOsFilmes()
// testarListarTodosOsFilmes()

const listarFilmesEmCartaz = () => {
    const filmesEmCartaz = catalogo.filter(filme => filme.emCartaz)
    for (let filme of filmesEmCartaz) {
        console.log(mostrarDetalhesFilme(filme))
    }
}
const testarListarFilmesEmCartaz = () => listarFilmesEmCartaz()
// testarListarFilmesEmCartaz()
```

**CineHouse/package.json**

```json
{
  "name": "cinehouse",
  "version": "1.0.0",
  "description": "Prática CineHouse do módulo 02 - Introdução ao Node e JavaScript'",
  "main": "cinema.js",
  "scripts": {
    "start": "node cinema.js",
    "dev": "nodemon cinema.js"
  },
  "keywords": [
    "node",
    "javascript"
  ],
  "author": "Marcelo Diament",
  "license": "MIT",
  "devDependencies": {
    "nodemon": "^2.0.15"
  }
}
```

___

## Changelog

Registro de alterações (em ordem cronológica decrescente).

### Documentação | Resoluções

* **doc: [#M2] Atualizando changelog**
_Atualizando o changelog._

* **doc: [#M2] Adicionando resoluções a cada enunciado - 2**
_Atualizando o README.md com esoluções de cada etapa (Aula 03 e refatoração)._

* **doc: [#M2] Adicionando resoluções a cada enunciado**
_Atualizando o README.md com esoluções de cada etapa (Aulas 01 e 02)._

### Refactor | Melhorando nosso código - CineHouse

* **doc: [#M2] Atualizando changelog com melhorias**
_Atualizando o changelog._

* **chore: [#M2] Adicionando scripts start e dev**
_Atualizando o package.json com scripts start (node) e dev (nodemon)._

* **fix: [#M2] Ajustando indentação e comentando const não utilizada**
_Atualizando o cinema.js comendando a variável `cinema` e ajustando indentação._

* **refactor: [#M2] Refatorando `listarFilmesEmCartaz` usando `filter`,  `for/of` e a função de apoio `mostrarDetalhesFilme`**
_Refatorando `listarFilmesEmCartaz` usando `filter` , `for/of` e a função de apoio `mostrarDetalhesFilme` ._

* **refactor: [#M2] Refatorando `listarTodosOsFilmes` usando `forEach`,  `arrowFunction` e interpolação**
_Refatorando `listarTodosOsFilmes` usando `forEach` , `arrowFunction` e interpolação._

* **refactor: [#M2] Refatorando `alterarStatusEmCartaz` usando `buscarFilme` e desestruturação**
_Refatorando `alterarStatusEmCartaz` usando `buscarFilme` e desestruturação._

* **refactor: [#M2] Refatorando `buscarFilme` com `filter` e `if` ternário**
_Refatorando `buscarFilme` com `filter` e `if` ternário._

### Hotfix | Ajustando a função `adicionarFilme`

* **doc: [#M2] Atualizando changelog com o HotFix**
_Atualizando o changelog._

* **hotfix: [#M2] Ajustando a função `adicionarFilme`**
_Ajustando a função `adicionarFilme` - estava adicionando o catálogo ao invés do filme recebido como argumento._

### Módulo 02 - Aula 03 - CineHouse | Parte 02

* **doc: [#M2A03-pt02] Atualizando changelog da Parte 02 da Aula 03 do Módulo 02**
_Atualizando o changelog._

* **fix: [#M2A03-pt02] Comentando `testarAlterarStatusEmCartaz`**
_Comentando o teste `testarAlterarStatusEmCartaz` ._

* **feat: [#M2A03-pt02] Usando `if` ternário na função `alterarStatusEmCartaz`**
_Atualizando a função `alterarStatusEmCartaz` para usar o `if` ternário (ainda que a solução anterior fosse mais enxuta) e testando._

* **feat: [#M2A03-pt02] Adicionando função `listarFilmesEmCartaz`**
_Adicionando a função `listarFilmesEmCartaz` e testando._

* **feat: [#M2A03-pt02] Adicionando função `listarTodosOsFilmes`**
_Adicionando a função `listarTodosOsFilmes` e testando._

### Módulo 02 - Aula 03 - CineHouse | Parte 01

* **doc: [#M2A03-pt01] Atualizando changelog da Parte 01 da Aula 03 do Módulo 02**
_Atualizando o changelog._

* **feat: [#M2A03-pt01] Importando o catalogo em JSON para *cinema.js***
_Importando o JSON `catalogo` e testando as funções de cinema.js novamente._

* **feat: [#M2A03-pt01] Movendo o array `catalogo` para um arquivo JSON em *database/catalogo.json***
_Movendo o `catalogo` para um arquivo à parte (catalogo.json) e realizando os ajustes necessários._

### Módulo 02 - Aula 03 - CineHouse | Extra

* **doc: [#M2A03] Adicionando enunciados da Aula 03 do Módulo 02**
_Adicionando os enunciados da Aula 03 do Módulo 02 (projeto CineHouse) e atualizando o changelog._

### Módulo 02 - Aula 02 - CineHouse e Calculadora | Extra

* **doc: [#M2A02] Adicionando enunciados da Aula 02 do Módulo 02**
_Adicionando os enunciados da Aula 02 do Módulo 02 (projetos CineHouse e Calculadora) e atualizando o changelog._

### Módulo 02 - Aula 01 - CineHouse | Extra

* **doc: [#M2A01] Adicionando enunciados da Aula 01 do Módulo 02**
_Adicionando os enunciados da Aula 01 do Módulo 02 e atualizando o changelog._

### Módulo 02 - Aula 02 - Calculadora | Extra

* **doc: [#M2A02-pt04] Adicionando documentação**
_Adicionando detalhes sobre as etapas realizadas na parte 04, Calculadora (changelog)._

### Módulo 02 - Aula 02 - Calculadora | Parte 04

* **feat: [#M2A02-pt04] Executando `dividir` - com num2 recebendo 0 - em *calculadora.js***
_Movendo o teste de dividir.js (usando num2 como 0) para calculadora.js._

* **feat: [#M2A02-pt04] Executando `dividir` em *calculadora.js***
_Importando o arquivo dividir.js e movendo o teste de dividir.js para calculadora.js._

* **feat: [#M2A02-pt04] Executando `multiplicar` em *calculadora.js***
_Importando o arquivo multiplicar.js e movendo o teste de multiplicar.js para calculadora.js._

* **feat: [#M2A02-pt04] Executando `subtrair` em *calculadora.js***
_Importando o arquivo subtrair.js e movendo o teste de subtrair.js para calculadora.js._

* **feat: [#M2A02-pt04] Executando `somar` em *calculadora.js***
_Importando o arquivo somar.js e movendo o teste de somar.js para calculadora.js._

* **feat: [#M2A02-pt04] Adicionando arquivo *calculadora.js***
_Criando o arquivo `calculadora.js` ._

### Módulo 02 - Aula 02 - Calculadora | Extra

* **fix: [#M2A02-pt03] Ajustando título da etapa de documentaçao da Calculadora no *changelog***
_Atualizando o título "Módulo 02 - Aula 02 - Calculadora | Extra" e atualizando o changelog._

* **doc: [#M2A02-pt03] Adicionando documentação**
_Adicionando detalhes sobre as etapas realizadas na parte 03, Calculadora (changelog)._

### Módulo 02 - Aula 02 - Calculadora | Parte 03

* **feat: [#M2A02-pt03] Adicionando função `dividir` com condicional e testando**
_Criando a função `dividir` - que recebe 2 números e retorna a divisão (a menos que o segundo número seja 0) - e testando._

* **feat: [#M2A02-pt03] Adicionando função `multiplicar` e testando**
_Criando a função `multiplicar` - que recebe 2 números e retorna a multiplicação - e testando._

* **feat: [#M2A02-pt03] Adicionando função `subtrair` e testando**
_Criando a função `subtrair` - que recebe 2 números e retorna a subtração - e testando._

* **feat: [#M2A02-pt03] Criando projeto Calculadora, adicionando função `somar` e testando**
_Criando a pasta `Calculadora` e a função `somar` - que recebe 2 números e retorna a soma - e testando._

### Módulo 02 - Aula 02 - CineHouse | Extra

* **doc: [#M2A02] Adicionando documentação**
_Adicionando detalhes sobre as etapas realizadas (changelog)._

### Módulo 02 - Aula 02 - CineHouse | Parte 02

* **feat: [#M2A02-pt02] Adicionando função `alterarStatusEmCartaz` e testando**
_Criando a função `alterarStatusEmCartaz` - que recebe um código e modifica o valor da propriedade `emCartaz` - e testando._

* **feat: [#M2A02-pt02] Adicionando função `buscarFilme` e testando**
_Criando a função `buscarFilme` - que recebe um código e retorna o filme identificado - e testando._

* **feat: [#M2A02-pt02] Adicionando função `adicionarFilme` e testando**
_Criando a função `adicionarFilme` - que recebe um objeto com um novo filme e adiciona ao `catalogo` - e testando._

### Módulo 02 - Aula 02 - CineHouse | Parte 01

* **feat: [#M2A02-pt01] Adicionando *Array* catalogo com 2 filmes**
_Atribuindo um array com 2 objetos (que representam filmes) à variável `catalogo` ._

### Módulo 02 - Aula 01 - CineHouse | Extra

* **doc: [#M2A01] Adicionando documentação**
_Adicionando detalhes sobre a prática e as etapas realizadas (changelog)._

### Módulo 02 - Aula 01 - CineHouse | Parte 02

* **feat: [#M2A01-pt02] Adicionando *nodemon* como dependência de desenvolvimento**
_Instalando nodemon como devDependency com `npm i --save -D nodemon` ._

* **feat: [#M2A01-pt02] Exibindo valor da variável cinema com `console.log()`**
_Exibindo o valor de `cinema` com `console.log()` ._

* **feat: [#M2A01-pt02] Adicionando `package.json`**
_Criação do `package.json` ._

### Módulo 02 - Aula 01 - CineHouse | Parte 01

* **feat: [#M2A01-pt01] Adicionaendo nome do cinema**
_Criação da pasta CineHouse e do arquivo `cinema.js` ._
_Criação da variável `cinema` , quer recebe o nome do cinema._
