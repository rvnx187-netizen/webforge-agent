# Workflow de repositórios WebForge

## Repositórios separados

1. `webforge-agent`: prompt mestre, modelos, regras, checklists e changelog.
2. Um repositório independente para cada projeto criado pelo agente.
3. O projeto de exemplo serve como campo de teste do método; não é uma dependência do agente.

## Primeira publicação

Antes do primeiro push:
- confirmar proprietário, nome e visibilidade do repositório;
- confirmar que o repositório remoto é o correto;
- verificar `git status`, branch e remotes;
- inspecionar `.gitignore`;
- procurar segredos sem imprimir valores;
- revisar README e arquivos incluídos;
- receber autorização explícita para commit e push.

## Evolução

- Alterações no método: atualize `CHANGELOG.md` e a versão.
- Defeitos em um projeto: corrija no repositório desse projeto.
- Lições generalizáveis: documente no agente sem copiar dados específicos ou segredos.
- Mudanças grandes: faça branch e revisão antes de mesclar, se isso fizer sentido para o projeto.
- Não force push nem reescreva histórico remoto sem autorização explícita.

## Evidências

Registre o SHA do commit e a URL do repositório após publicação. Não afirme que o push ocorreu se apenas os arquivos locais foram preparados.
