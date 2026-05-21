# Registro do que foi feito e alterado

## Implementação inicial do agente acadêmico

Foram adicionados os arquivos base do projeto para entrega e apresentação do trabalho.

### Arquivos criados

#### `index.html`

Criado formulário HTML simples para entrada de perguntas do usuário.

O formulário contém:

- Campo de texto para pergunta.
- Botão de envio.
- Exemplos de perguntas.
- Layout simples e responsivo.
- Envio via método `POST` para a rota `/pergunta`.

#### `fluxo-node-red.json`

Criado fluxo completo do Node-RED com os seguintes nós:

- `http in` com método `GET` na rota `/`.
- `template` para renderizar o formulário HTML.
- `http response` para devolver a página do formulário.
- `http in` com método `POST` na rota `/pergunta`.
- `function` para processar a pergunta com regras condicionais.
- `http response` para devolver a resposta automática ao usuário.

#### `docs/relatorio-desenvolvimento-arquitetura.md`

Criado relatório explicando:

- Objetivo do agente.
- Arquitetura desenvolvida.
- Funcionamento do fluxo.
- Regras implementadas.
- Critérios de teste.
- Sugestões de prints para a entrega.

#### `README.md`

Criada documentação principal do repositório contendo:

- Descrição do projeto.
- Estrutura de arquivos.
- Explicação do fluxo.
- Instruções de importação no Node-RED.
- Instruções de teste.

#### `prints/.gitkeep`

Criada pasta reservada para armazenar prints do funcionamento.

### Lógica implementada

A lógica central foi criada no nó `function` do Node-RED.

O código recebe a pergunta enviada pelo formulário, converte o texto para minúsculas e verifica palavras-chave com estruturas condicionais `if / else`.

As categorias tratadas são:

- Prazo e entrega.
- Documentação.
- Horários e apresentação.
- Funcionamento do agente.
- Critérios de avaliação.
- Outros.

### Resultado final

O projeto agora possui uma aplicação funcional de ponta a ponta:

```text
Formulário HTML → HTTP POST → Node-RED → Function if/else → HTTP Response
```

O agente recebe uma pergunta, identifica automaticamente a categoria e retorna uma resposta em HTML.
