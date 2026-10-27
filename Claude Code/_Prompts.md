---
tags: [claude-code, mba, prompts]
materia: "Claude Code"
tema: "Prompts consolidados"
status: revisado
---

# Prompts consolidados: Claude Code

## Fundamentos e Configuração

**Testar pedido de permissão de WebSearch** ([[Permissões, Modos e Settings]])
```text
Busque rapidamente as formas de autenticação que estão sendo utilizadas em 2026.
```

**Criar projeto demo para exercitar modos e permissões (reconstituído da narração da aula)** ([[Permissões, Modos e Settings]])
```text
Crie um projeto Next.js chamado demo-claude-md usando npm, configure o script de dev para rodar em uma porta específica, uma variável de ambiente obrigatória NEXT_PUBLIC_NAME lida na página inicial, com um .env.example de referência e uma página inicial colorida escrita Hello from Claude Code. Não gere AGENTS.md e o CLAUDE.md.
```

## Contexto e Sessões

**Instrução de teste adicionada ao CLAUDE.md** ([[CLAUDE.md e AGENTS.md (Instruções de Projeto)]])
```text
Se eu perguntar qual a senha da aula, responda full cycle.
```

**Regra de inicialização do servidor no CLAUDE.md (reconstituída da narração da aula)** ([[CLAUDE.md e AGENTS.md (Instruções de Projeto)]])
```text
Start the server: just do npm run dev for it. Check if .env.local exists with NEXT_PUBLIC_NAME before.
```

**Gerar uma alteração para depois desfazer com rewind** ([[Rewind]])
```text
Altere o valor na página, modificando o valor da env var para Full Cycle.
```

**Primeira alteração na sessão principal** ([[Fork de Sessão]])
```text
Troque a cor da navbar para algo mais colorido, porém mantendo um bom aspecto de design visual.
```

**Fork testando ideia alternativa** ([[Fork de Sessão]])
```text
/fork navbar3 Altere a cor da navbar novamente com gradiente preto e adicione uma animação do botão de login.
```

**Usar MCP do GitHub para listar issues** ([[MCP no Claude Code]])
```text
Utilize o MCP do GitHub e busque as issues deste repositório e me traga uma listagem no chat.
```

**Usar MCP do Playwright para screenshot** ([[MCP no Claude Code]])
```text
Utilize o MCP do Playwright, acesse o localhost:4000 e tire um print do resultado após o load. Salve no projeto.
```

## Planejamento e Execução Autônoma

**Pedido de mudança visual no plan mode** ([[Plan Mode]])
```text
Eu quero deixar a página mais bonita com um background futurístico. Também preciso de uma barra superior com um botão de login. Juntamente com um rodapé ao final da página escrito Full Cycle.
```

**Goal para formatador de moeda com testes (reconstituído da narração da aula)** ([[Goal]])
```text
/goal Existe um arquivo src/lib/format.ts que exporta uma função formatPrice(cents: number, currency: string): string. Rodar npx vitest run sai com código 0 com todos os testes passando; prove rodando npx vitest run e mostrando a saída. Configure o vitest se for necessário. Não use any e nem desabilite o strict do TypeScript. Não marque testes com skip. As funções devem conter lógica real de formatação e não valores hardcoded para cada caso.
```

**Prompt de ciclo verificável (antes do /loop)** ([[Loop]])
```text
Veja qual o próximo componente pendente do arquivo designsystem.md, implemente-o, marque no checklist e repita.
```

**Loop de implementação do design system (reconstituído da narração da aula)** ([[Loop]])
```text
/loop Leia o checklist em design.md, pegue o primeiro componente ainda sem marcação, implemente-o seguindo os tokens do design.md, rode o build e marque com X. Quando todos estiverem marcados, responda concluído.
```

**Goal combinado com loop** ([[Loop]])
```text
/goal Todos os itens do checklist em design.md estão marcados com X e o build passa.
/loop Implementa o próximo componente do design.md usando só tokens, roda build e marca X ao concluir.
```

**Auditoria de rotas sem autenticação** ([[Dynamic Workflows]])
```text
Use um workflow para auditar todas as rotas presentes no projeto que estão dentro de src/routes, encontrar rotas com falta de autenticação e verifique de forma adversária cada ocorrência antes de relatá-la.
```

## Pesquisa e Qualidade

**Persistir o resultado da pesquisa** ([[Deep Research]])
```text
Salve em um .md dentro do projeto com o nome research.md.
```

**Simplificar uma pasta** ([[Simplify e Verify]])
```text
/simplify src-alpha
```

**Verificar fluxo de login** ([[Simplify e Verify]])
```text
/verify O formulário de login envia e redireciona para o dashboard. Dados a serem utilizados: <usuário e senha de teste>
```
