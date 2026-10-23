# Como iniciar um projeto com o WebForge

## Antes de abrir o Codex

1. Crie uma pasta própria para o projeto.
2. Salve uma cópia deste kit em local permanente.
3. Copie `02_Modelos/BRIEF_DO_PROJETO.md` para a pasta do projeto e preencha o que souber.
4. Não coloque senhas, tokens ou dados reais de clientes no brief.

## Primeiro comando no Codex

Abra a pasta do projeto no VS Code/Codex e forneça o conteúdo de `01_Agente/PROMPT_MESTRE_WEBFORGE.md`. Em seguida, peça:

> Use o WebForge em modo PLAN. Leia o brief do projeto e inspecione a pasta atual sem modificar arquivos. Identifique o que existe, os requisitos, os riscos, as ferramentas disponíveis e o plano por fases. Para cada requisito, defina critério de aceitação e teste. Não acesse serviços remotos, não instale ferramentas, não faça commits, push ou deploy. Entregue o plano e aguarde minha autorização.

## Novo objetivo: deixar o projeto pronto para iniciar

Inclua no plano a etapa **PREPARE**. O WebForge deve descobrir as ferramentas disponíveis, confirmar o backend preferido e preparar um caminho local simples. A meta é que, quando os pré-requisitos já estiverem disponíveis, a pessoa consiga iniciar o backend com o mínimo de passos possível.

Não autorize instalação automática, acesso remoto, migrations em produção, deploy ou operações destrutivas por padrão. Se uma ferramenta estiver ausente, peça ao agente um bloco com pré-requisitos, instruções de instalação oficial a consultar e comandos para verificar a instalação. Não cole segredos no chat.

Para projetos com backend, exija no README: comando de início, URL local esperada, comando de parada, configuração local necessária e problemas comuns. “Pronto para iniciar” não significa “testado” nem “pronto para produção”.

## Depois do plano

- Leia o plano e corrija qualquer requisito entendido errado.
- Autorize apenas uma fase por vez.
- Após cada fase, examine os arquivos alterados e o relatório de testes.
- Peça uma auditoria independente quando houver autenticação, banco, dados de usuários, pagamentos ou exposição pública.
- Antes de publicar, use o checklist de segurança e o modelo de relatório final.

## Convenção recomendada de pastas

```text
NomeDoProjeto/
  README.md
  docs/
    BRIEF.md
    PLAN.md
    SECURITY.md
    TEST-REPORT.md
    CHANGELOG.md
  src/
  tests/
  .env.example
  .gitignore
```

Adapte a estrutura à tecnologia; não crie pastas vazias sem necessidade.

## Encerramento de sessão

Peça ao agente um resumo com:
- fase atual;
- arquivos alterados;
- decisões tomadas;
- comandos e testes executados;
- falhas e bloqueios;
- próxima tarefa exata;
- ações que NÃO foram feitas.

Guarde esse resumo em `docs/SESSION-HANDOFF.md` ou no histórico do projeto. Na próxima sessão, peça para o agente ler esse arquivo antes de continuar.
