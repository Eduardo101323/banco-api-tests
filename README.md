# banco-api-tests

Projeto de automação de testes de API REST desenvolvido em JavaScript para validar as funcionalidades da [banco-api](https://github.com/juliodelimas/banco-api).

## 🎯 Objetivo

O **banco-api-tests** tem como objetivo automatizar testes de integração da API REST do projeto **banco-api**, verificando o comportamento dos endpoints e as regras de negócio relacionadas a autenticação, contas e transferências.

A API REST utilizada como alvo roda, por padrão, na porta `3000`. A documentação Swagger da API pode ser acessada em `http://localhost:3000/api-docs` quando a aplicação estiver em execução.

> **Importante:** este projeto contém os testes. A aplicação `banco-api` precisa estar instalada, configurada e em execução para que os testes possam ser executados.

## 🧰 Stack utilizada

| Tecnologia | Utilização |
| --- | --- |
| **JavaScript / Node.js** | Linguagem e ambiente de execução |
| **Mocha** | Framework para estruturação e execução dos testes |
| **Supertest** | Realização de requisições HTTP e testes da API |
| **Chai** | Biblioteca de asserções |
| **dotenv** | Carregamento de variáveis de ambiente a partir do `.env` |
| **Mochawesome** | Geração de relatórios HTML dos testes |
| **npm** | Gerenciamento das dependências e scripts do projeto |

As versões declaradas atualmente no `package.json` são: Chai `^5.2.0`, dotenv `^16.5.0`, Mocha `^11.1.0`, Mochawesome `^7.1.3` e Supertest `^7.1.0`.

## 📁 Estrutura de diretórios

A estrutura atual do repositório é:

```text
banco-api-tests/
├── fixtures/                 # Dados utilizados pelos testes
├── helpers/                  # Funções auxiliares/reutilizáveis
├── test/                     # Testes automatizados
├── .env                      # Configuração local da URL da API (criado pelo usuário)
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

### Diretórios e arquivos principais

- **`test/`**: contém os arquivos de testes automatizados, organizados por funcionalidade.
- **`fixtures/`**: concentra dados de apoio utilizados durante a execução dos testes.
- **`helpers/`**: reúne funções auxiliares utilizadas para evitar duplicação e facilitar a manutenção dos testes.
- **`.env`**: arquivo de configuração local que informa a URL base da API que será testada.
- **`package.json`**: define as dependências e os scripts do projeto.
- **`package-lock.json`**: registra as versões exatas das dependências instaladas.
- **`mochawesome-report/`**: diretório gerado durante a execução dos testes com o Mochawesome. Ele não faz parte da estrutura versionada do projeto porque está incluído no `.gitignore`.

## ⚙️ Pré-requisitos

Antes de executar os testes, certifique-se de ter:

- [Node.js](https://nodejs.org/) instalado;
- npm instalado (normalmente acompanha o Node.js);
- a aplicação [banco-api](https://github.com/juliodelimas/banco-api) configurada;
- a API REST `banco-api` em execução;
- acesso à URL configurada no `BASE_URL`.

## 🚀 Instalação

Clone o repositório:

```bash
git clone https://github.com/juliodelimas/banco-api-tests.git
cd banco-api-tests
```

Instale as dependências:

```bash
npm install
```

## 🔐 Configuração do `.env`

O arquivo `.env` não é versionado no Git, pois está listado no `.gitignore`. Portanto, cada usuário precisa criá-lo manualmente na raiz do projeto.

Crie:

```text
.env
```

Com o seguinte conteúdo:

```env
BASE_URL=http://localhost:3000
```

### `BASE_URL`

A variável `BASE_URL` define o endereço base da API REST que será utilizada pelos testes.

Por exemplo:

```env
BASE_URL=http://localhost:3000
```

Caso a API esteja disponível em outro endereço ou porta, altere o valor:

```env
BASE_URL=http://192.168.1.100:3000
```

> **Atenção:** não adicione aspas ao valor, a menos que o projeto seja alterado para tratar esse formato especificamente.

## 🧪 Execução dos testes

Com a `banco-api` em execução e o `.env` configurado, execute:

```bash
npm test
```

O script definido no `package.json` é equivalente a:

```bash
mocha ./test/**/*.test.js --timeout=200000 --reporter mochawesome
```

Isso significa que o comando:

- procura os arquivos de teste dentro de `test/`;
- considera arquivos com o padrão `*.test.js`;
- define um timeout de `200000` ms;
- utiliza o **Mochawesome** como reporter.

## 📊 Relatório de testes

O projeto utiliza o **Mochawesome** para gerar um relatório dos resultados da execução.

Depois de executar:

```bash
npm test
```

o Mochawesome gera o diretório:

```text
mochawesome-report/
```

Dentro dele, normalmente estarão arquivos como:

```text
mochawesome-report/
├── assets/
├── mochawesome.html
└── mochawesome.json
```

O principal arquivo para visualização dos resultados é:

```text
mochawesome-report/mochawesome.html
```

### Abrindo o relatório no Windows

No Git Bash:

```bash
start mochawesome-report/mochawesome.html
```

No PowerShell:

```powershell
Start-Process .\mochawesome-report\mochawesome.html
```

No Linux:

```bash
xdg-open mochawesome-report/mochawesome.html
```

No macOS:

```bash
open mochawesome-report/mochawesome.html
```

> O diretório `mochawesome-report/` é gerado automaticamente e está no `.gitignore`, portanto não deve ser necessário adicioná-lo ao repositório.

## 🔄 Fluxo de execução

Para executar o projeto do zero:

```text
1. Clonar o banco-api-tests
          ↓
2. Instalar as dependências
          ↓
3. Clonar/configurar o banco-api
          ↓
4. Iniciar a API REST
          ↓
5. Criar o arquivo .env
          ↓
6. Configurar BASE_URL
          ↓
7. Executar npm test
          ↓
8. Consultar mochawesome-report/mochawesome.html
```

## 🔗 Projeto da API testada

Este projeto foi desenvolvido para testar a API REST do repositório:

**banco-api:** https://github.com/juliodelimas/banco-api

A API REST utiliza, por padrão, a seguinte URL base:

```text
http://localhost:3000
```

Entre os endpoints documentados no projeto da API estão:

```text
GET  /contas
POST /login
POST /transferencias
```

A documentação interativa Swagger fica disponível, com a API em execução, em:

```text
http://localhost:3000/api-docs
```

## 📚 Documentação das dependências

### Mocha

Framework utilizado para estruturação e execução dos testes JavaScript.

- [Documentação oficial do Mocha](https://mochajs.org/)
- [Mocha no npm](https://www.npmjs.com/package/mocha)

### Supertest

Biblioteca utilizada para realizar requisições HTTP e facilitar testes de APIs.

- [Repositório oficial do Supertest](https://github.com/ladjs/supertest)
- [Supertest no npm](https://www.npmjs.com/package/supertest)

### Chai

Biblioteca de asserções utilizada para validar os resultados esperados nos testes.

- [Documentação oficial do Chai](https://www.chaijs.com/)
- [Chai no npm](https://www.npmjs.com/package/chai)

### dotenv

Biblioteca utilizada para carregar variáveis definidas no arquivo `.env` para `process.env`.

- [Repositório oficial do dotenv](https://github.com/motdotla/dotenv)
- [dotenv no npm](https://www.npmjs.com/package/dotenv)

### Mochawesome

Reporter utilizado pelo Mocha para gerar relatórios detalhados em HTML e JSON.

- [Repositório oficial do Mochawesome](https://github.com/adamgruber/mochawesome)
- [Mochawesome no npm](https://www.npmjs.com/package/mochawesome)
- [Mochawesome Report Generator](https://www.npmjs.com/package/mochawesome-report-generator)

### Node.js

Ambiente de execução utilizado para executar o projeto JavaScript.

- [Documentação oficial do Node.js](https://nodejs.org/docs/)

## 📝 Scripts disponíveis

Atualmente, o `package.json` disponibiliza o seguinte script:

| Comando | Descrição |
| --- | --- |
| `npm test` | Executa todos os testes encontrados em `test/**/*.test.js` e gera o relatório com Mochawesome |

## 🔒 Arquivos ignorados pelo Git

O projeto possui o seguinte `.gitignore`:

```text
node_modules/
mochawesome-report/
.env
```

Esses arquivos e diretórios não devem ser versionados porque:

- `node_modules/` contém dependências instaladas localmente;
- `mochawesome-report/` contém artefatos gerados durante a execução dos testes;
- `.env` contém configurações específicas do ambiente local.

## 👨‍💻 Observações

- A API precisa estar acessível antes da execução dos testes.
- O valor de `BASE_URL` deve apontar para a instância da API que será testada.
- O arquivo `.env` deve ser criado localmente e não deve ser commitado.
- O relatório HTML é um artefato da execução dos testes e pode ser regenerado a qualquer momento executando `npm test`.

## 📄 Licença

O projeto atualmente declara a licença `ISC` no `package.json`.
