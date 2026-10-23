# WebForge Agent

**Versão do método: 1.2**  
Agente reutilizável para planejar, construir, preparar, auditar, testar e entregar sites e aplicações com evidências claras.

## Repositório independente

Este repositório contém o método WebForge, os prompts, os modelos e os checklists. Projetos construídos com ele devem viver em repositórios separados, para que o agente possa evoluir sem misturar o seu histórico ao de aplicações individuais.

## Comece aqui

1. Leia `01_Agente/PROMPT_MESTRE_WEBFORGE.md`.
2. Para um projeto novo, copie `02_Modelos/BRIEF_DO_PROJETO.md` para o repositório do projeto.
3. Abra o projeto no VS Code/Codex e forneça o prompt mestre.
4. Comece pelo modo `PLAN`; aprove uma fase por vez.
5. Use `PREPARE` para verificar ferramentas e preparar a inicialização local.
6. Use `AUDIT`, `TEST` e `FINALIZE` antes de considerar a entrega concluída.
7. Use `RELEASE` para preparar uma versão documentada. Push e deploy exigem autorização específica.

## Modos disponíveis

`PLAN`, `BUILD`, `AUDIT`, `FIX`, `TEST`, `FINALIZE`, `TEMPLATE`, `PREPARE`, `RELEASE`.

## Regras essenciais

- Não declarar testes aprovados sem evidência de execução.
- Não acessar serviços remotos, instalar dependências, criar commits, fazer push ou deploy sem autorização específica.
- Não incluir segredos no repositório.
- Diferenciar “pronto para iniciar”, “iniciado”, “testado localmente” e “pronto para produção”.
- Usar ambientes descartáveis para testar banco, RLS, autenticação e concorrência.
- Preservar projetos existentes; não assumir que um repositório vazio ou uma pasta sem arquivos importantes.

## Estrutura

- `01_Agente/`: prompt mestre e instruções de uso.
- `02_Modelos/`: brief e relatório de entrega.
- `03_Qualidade/`: evidências, segurança e handoff.
- `04_Licoes_ECHO2/`: lições generalizáveis do piloto.
- `CHANGELOG.md`: histórico de versões do método.

## Versão 1.2

- Reforçada a separação entre repositório do agente e repositórios de projetos.
- Adicionadas regras para versionamento, changelog e preparação de releases.
- Mantida a abordagem de baixo atrito para inicialização local sem ocultar pré-requisitos.
- Incluídas lições do ECHO 2 sobre diferença entre inspeção estática e validação real.
