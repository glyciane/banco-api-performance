# Banco API Performance

## Introdução

Este repositório contém testes de performance em JavaScript utilizando o k6 para validar o comportamento de uma API em cenários de carga e desempenho. O objetivo é simular requisições reais e verificar se a API atende aos critérios definidos para disponibilidade, estabilidade e tempo de resposta.

Os testes foram organizados para facilitar a execução, manutenção e reutilização de componentes comuns, como autenticação e configuração de ambiente.

## Tecnologias utilizadas

- JavaScript
- k6
- JSON para configuração e fixtures
- HTTP para requisições de teste

## Estrutura do repositório

```text
banco-api-performance/
├── config/
│   └── config.local.json
├── fixtures/
│   └── postLogin.json
├── helpers/
│   └── autenticacao.js
├── tests/
│   ├── login.test.js
│   └── transferencias.test.js
├── utils/
│   └── variaveis.js
└── README.md
```

## Objetivo de cada grupo de arquivos

- `config/`: armazena as configurações locais do projeto, como a URL base da API.
- `fixtures/`: contém os corpos de requisição reutilizáveis nos testes.
- `helpers/`: reúne funções auxiliares, como a autenticação e a obtenção de tokens.
- `tests/`: concentra os scripts de teste de performance, como login e transferências.
- `utils/`: contém utilidades compartilhadas, como a função responsável por retornar a URL base do ambiente.
- `README.md`: documenta o projeto, sua estrutura e os passos para instalação e execução.

## Modo de instalação

1. Certifique-se de que o Node.js esteja instalado em sua máquina.
2. Instale o k6 seguindo as instruções oficiais para o seu sistema operacional.
3. Clone este repositório e acesse a pasta do projeto:

```bash
git clone <url-do-repositorio>
cd banco-api-performance
```

4. Configure a variável de ambiente `BASE_URL` para apontar para a API que será testada. Exemplo:

```cmd
set "BASE_URL=http://localhost:3000"
```

> Em ambientes Linux/macOS, a sintaxe pode ser:
>
> ```bash
> export BASE_URL=http://localhost:3000
> ```

## Modo de execução do projeto

Os testes podem ser executados diretamente com o k6. Exemplo:

```cmd
k6 run tests\login.test.js
```

Para executar o teste de transferências:

```cmd
k6 run tests\transferencias.test.js
```

### Execução com acompanhamento do relatório em tempo real

Para acompanhar o relatório em tempo real no dashboard do k6, use as variáveis de ambiente abaixo:

```cmd
set "K6_WEB_DASHBOARD=true" && set "K6_WEB_DASHBOARD_EXPORT=html-report.html" && k6 run tests\login.test.js
```

Essa execução:
- habilita o dashboard web do k6;
- exporta o relatório em formato HTML para o arquivo `html-report.html`.

Você também pode substituir o arquivo de teste conforme necessário, como por exemplo:

```cmd
set "K6_WEB_DASHBOARD=true" && set "K6_WEB_DASHBOARD_EXPORT=html-report.html" && k6 run tests\transferencias.test.js
```
