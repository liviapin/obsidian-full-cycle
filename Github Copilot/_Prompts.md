---
tags: [github-copilot, mba, prompts]
materia: "Github Copilot"
tema: "Prompts consolidados"
status: revisado
---

# Prompts consolidados: Github Copilot

## Recursos no Editor

**Gerar função via comentário** ([[Inline Suggestions e Ghost Text]])
```text
// gere uma função que retorna a sequência de Fibonacci
```

**Refinar via comentário** ([[Inline Suggestions e Ghost Text]])
```text
// função recursiva de sequência Fibonacci
```

## Chat e Prompts

**Quick Chat: pergunta sobre o arquivo** ([[Tipos de Chat do Copilot]])
```text
Qual é o método que lista os dados?
```

**Inline Chat: alteração pontual** ([[Tipos de Chat do Copilot]])
```text
Adicionar um segundo parâmetro para lançar uma exceção caso o dado não exista.
```

**Terminal Inline Chat: gerar comando** ([[Tipos de Chat do Copilot]])
```text
Eu quero um comando para buscar o termo payment no arquivo payment service.
```

**Terminal Inline Chat: explicar seleção** ([[Tipos de Chat do Copilot]])
```text
#terminalSelection quero saber o que este comando faz
```

**Dúvida de configuração do VS Code** ([[Participantes do Chat]])
```text
@vscode como mudar a cor de borda do VS Code?
```

**Listar capacidades do participante** ([[Participantes do Chat]])
```text
@vscode quais as suas skills?
```

**Pesquisa de biblioteca no GitHub** ([[Participantes do Chat]])
```text
@github como instalar a lib axios/axios
```

**Explicar o projeto com contexto** ([[Participantes do Chat]])
```text
@workspace me explique como este projeto funciona
```

**Abrir PR sem Coding Agent (reconstituído da narração da aula)** ([[Participantes do Chat]])
```text
@github.pr abra uma pull request do branch dev para o branch main no repositório <dono/repo>, com o título <título> e a descrição <descrição>. Não use o Coding Agent.
```

**Explicar o projeto** ([[Slash Commands do Copilot]])
```text
/explain me explique como funciona o projeto
```

**Explicar comandos do terminal** ([[Slash Commands do Copilot]])
```text
@terminal /explain me explique os comandos que estão no terminal
```

**Gerar projeto novo** ([[Slash Commands do Copilot]])
```text
/new eu quero criar um projeto Spring Boot
```

**Explicação com contexto de arquivo** ([[Context Mentions e Tools]])
```text
@workspace /explain como funciona o #<arquivo>
```

**Implementação com documentação externa (reconstituído da narração da aula)** ([[Context Mentions e Tools]])
```text
Quero persistir os pagamentos deste serviço usando o TypeORM. Se baseie na doc dele: #fetch <url da documentação>
```

**Implementação seguindo padrões do projeto (reconstituído da narração da aula)** ([[Context Mentions e Tools]])
```text
Quero mudar a persistência dos pagamentos de memória para banco de dados Postgres. #codebase se baseie nos padrões do projeto.
```
