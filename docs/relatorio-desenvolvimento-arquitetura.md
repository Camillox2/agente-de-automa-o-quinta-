# Relatório de Desenvolvimento e Arquitetura

## Projeto

Agente de Atendimento Acadêmico com Node-RED.

## Objetivo do agente

O objetivo do agente é receber perguntas simples relacionadas ao trabalho acadêmico, analisar automaticamente o conteúdo da pergunta e retornar uma resposta adequada para o usuário.

O foco do projeto está no comportamento automático do agente, ou seja:

- Existe um gatilho.
- Existe uma decisão automática.
- Existe uma resposta.
- O fluxo funciona do início ao fim.

## Responsabilidade de desenvolvimento e arquitetura

A parte de desenvolvimento e arquitetura foi organizada em quatro entregas principais:

1. Construção da interface de entrada.
2. Configuração do orquestrador no Node-RED.
3. Implementação da lógica central de decisão.
4. Exportação do fluxo em JSON.

## 1. Construção da interface de entrada

Foi criado um formulário HTML simples para captura da pergunta do usuário.

O formulário possui:

- Título do agente.
- Campo de texto para digitação da pergunta.
- Botão de envio.
- Exemplos de perguntas.
- Envio da pergunta para a rota `/pergunta` usando o método `POST`.

A interface não foi desenvolvida com foco em estética avançada, pois o objetivo principal da atividade é demonstrar o funcionamento do agente automático.

## 2. Configuração do orquestrador Node-RED

O Node-RED foi utilizado como orquestrador da aplicação.

Foram configuradas duas rotas HTTP:

### Rota `GET /`

Responsável por exibir o formulário HTML para o usuário.

Fluxo:

```text
http in → template → http response
```

### Rota `POST /pergunta`

Responsável por receber a pergunta enviada pelo formulário, processar a lógica e retornar a resposta automática.

Fluxo:

```text
http in → function → http response
```

## 3. Implementação da lógica central

A lógica central foi implementada em um nó `function`.

Esse nó recebe o campo `pergunta`, normaliza o texto e aplica regras condicionais com `if / else`.

O agente identifica palavras-chave e classifica a pergunta em categorias.

## Regras implementadas

### Regra 1: Prazo e entrega

Palavras-chave:

```text
prazo, entrega, data, quando, blackboard
```

Resposta esperada:

```text
O prazo de entrega do trabalho é 28/05/2026 pelo Blackboard.
```

### Regra 2: Documentação

Palavras-chave:

```text
documento, documentos, relatório, relatorio, arquivo, json, html, print, prints
```

Resposta esperada:

```text
Os entregáveis são: fluxo do Node-RED exportado em JSON, arquivo HTML do formulário e relatório curto com objetivo, funcionamento, regras implementadas e prints.
```

### Regra 3: Horários e apresentação

Palavras-chave:

```text
horário, horario, aula, apresentação, apresentacao
```

Resposta esperada:

```text
A apresentação será feita na data definida pela disciplina, junto com a entrega do projeto.
```

### Regra 4: Funcionamento do agente

Palavras-chave:

```text
funciona, funcionamento, agente, node-red, node red, fluxo, orquestrador
```

Resposta esperada:

```text
O agente recebe uma pergunta pelo formulário, envia os dados para o Node-RED, analisa palavras-chave em um nó function e retorna uma resposta automática em HTML.
```

### Regra 5: Critérios de avaliação

Palavras-chave:

```text
nota, avaliação, avaliacao, critério, criterio, pontuação, pontuacao
```

Resposta esperada:

```text
A avaliação considera funcionamento correto do agente, clareza da lógica, uso correto do Node-RED, organização do fluxo, documentação e trabalho em equipe.
```

### Regra 6: Outros

Caso nenhuma palavra-chave seja identificada, o agente retorna uma resposta padrão solicitando que o usuário pergunte sobre prazo, documentos, horários, entrega, nota ou funcionamento.

## 4. Exportação do projeto

O fluxo foi exportado no arquivo:

```text
fluxo-node-red.json
```

Esse arquivo pode ser importado diretamente no Node-RED.

## Estrutura do fluxo

```text
GET / 
  → Template do formulário
  → HTTP Response

POST /pergunta
  → Function com if/else
  → HTTP Response
```

## Testes sugeridos

Para validar o funcionamento, devem ser feitos testes com perguntas de diferentes categorias.

### Teste 1

Pergunta:

```text
Qual é o prazo de entrega?
```

Resultado esperado:

```text
Categoria: Prazo e entrega.
```

### Teste 2

Pergunta:

```text
Quais documentos preciso entregar?
```

Resultado esperado:

```text
Categoria: Documentação.
```

### Teste 3

Pergunta:

```text
Como funciona o agente?
```

Resultado esperado:

```text
Categoria: Funcionamento do agente.
```

### Teste 4

Pergunta:

```text
Quais são os critérios de avaliação?
```

Resultado esperado:

```text
Categoria: Critérios de avaliação.
```

### Teste 5

Pergunta:

```text
Quero falar com a secretaria.
```

Resultado esperado:

```text
Categoria: Outros.
```

## Prints recomendados para entrega

Os prints devem ser salvos na pasta `prints`.

Sugestões:

```text
prints/formulario.png
prints/fluxo-node-red.png
prints/resposta-prazo.png
prints/resposta-documentacao.png
```

## Explicação para apresentação

Minha parte foi desenvolver a interface de entrada, configurar o fluxo HTTP no Node-RED, implementar a lógica de decisão automática e exportar o fluxo final em JSON.

O usuário acessa o formulário, digita uma pergunta e envia os dados. O Node-RED recebe essa entrada por HTTP, executa uma função com regras condicionais e devolve uma resposta automática. Dessa forma, o sistema possui entrada, processamento, decisão e saída, caracterizando o comportamento de um agente automático.

## Conclusão

O agente implementado atende aos requisitos principais do trabalho, pois possui um gatilho HTTP, uma lógica de decisão automática e uma resposta final ao usuário. A aplicação é simples, funcional e explicável, mantendo o foco no comportamento do agente.
