# Agente de Atendimento Acadêmico com Node-RED

Projeto desenvolvido para o trabalho avaliativo de Engenharia de Prompt.

O objetivo é demonstrar um agente de automação simples, funcional e explicável, utilizando o Node-RED como orquestrador. O agente recebe uma pergunta por formulário HTML, processa a entrada com regras condicionais e retorna uma resposta automática em HTML.

## O que foi construído

Este repositório contém a parte de desenvolvimento e arquitetura do agente:

- Interface de entrada em HTML.
- Fluxo completo do Node-RED exportado em JSON.
- Rota HTTP para abertura do formulário.
- Rota HTTP para recebimento da pergunta.
- Nó `function` com regras condicionais `if / else`.
- Resposta automática formatada em HTML.
- Relatório descritivo do funcionamento e das alterações realizadas.

## Arquivos do projeto

```text
.
├── index.html
├── fluxo-node-red.json
├── README.md
├── CHANGELOG.md
├── docs/
│   └── relatorio-desenvolvimento-arquitetura.md
└── prints/
    └── .gitkeep
```

## Como funciona

O fluxo segue esta lógica:

```text
Usuário acessa o formulário
        ↓
Envia uma pergunta
        ↓
Node-RED recebe via HTTP POST
        ↓
Nó function analisa a pergunta
        ↓
Regras if/else identificam a categoria
        ↓
Node-RED retorna uma resposta automática em HTML
```

## Rotas do Node-RED

### `GET /`

Exibe o formulário HTML para o usuário digitar a pergunta.

### `POST /pergunta`

Recebe o campo `pergunta`, processa a lógica do agente e retorna a resposta automática.

## Categorias identificadas pelo agente

O agente classifica perguntas nas seguintes categorias:

- Prazo e entrega.
- Documentação.
- Horários e apresentação.
- Funcionamento do agente.
- Critérios de avaliação.
- Outros.

## Exemplos de perguntas

```text
Qual é o prazo de entrega?
Quais documentos preciso entregar?
Como funciona o agente?
Quando será a apresentação?
Quais são os critérios de avaliação?
```

## Como importar o fluxo no Node-RED

1. Abra o Node-RED.
2. Clique no menu superior direito.
3. Selecione `Import`.
4. Cole o conteúdo do arquivo `fluxo-node-red.json`.
5. Clique em `Import`.
6. Clique em `Deploy`.
7. Acesse:

```text
http://localhost:1880/
```

## Como testar

1. Abra `http://localhost:1880/`.
2. Digite uma pergunta no formulário.
3. Clique em `Enviar pergunta`.
4. Confira a categoria identificada e a resposta automática.

## Observação sobre o arquivo HTML

O arquivo `index.html` também foi salvo separadamente para a entrega acadêmica. O mesmo conteúdo está embutido no fluxo do Node-RED, permitindo que o formulário seja acessado diretamente pela rota `GET /`.

## Responsabilidade de desenvolvimento e arquitetura

Esta parte cobre:

- Construção da interface de entrada.
- Configuração do orquestrador no Node-RED.
- Implementação da lógica central de decisão automática.
- Exportação do fluxo final em JSON.
- Documentação das alterações realizadas.
