# Protocolo de evidências e qualidade

## Estados permitidos

- **PLANEJADO** — ainda não implementado.
- **IMPLEMENTADO, NÃO TESTADO** — o código existe, mas não foi validado por execução.
- **INSPECIONADO ESTATICAMENTE** — houve leitura/revisão de código, sem comprovação de runtime.
- **TESTADO COM SUCESSO** — o teste foi executado e passou; guardar comando/método e resultado.
- **FALHOU** — teste executado ou defeito confirmado.
- **BLOQUEADO / NÃO EXECUTADO** — faltou ferramenta, ambiente, permissão ou pré-requisito.
- **NÃO APLICÁVEL** — requisito fora do escopo, com justificativa.

## Regras

1. Um arquivo criado não significa que a funcionalidade funciona.
2. Uma página aberta não prova autenticação, persistência, API ou banco.
3. Uma revisão SQL não prova que a migration aplica.
4. Uma política RLS escrita não prova que os privilégios efetivos estão corretos.
5. Um teste manual não substitui todos os testes automatizados.
6. Não afirmar “100% seguro”, “sem bugs” ou “pronto para produção” sem uma base de validação adequada — e mesmo assim declarar limites.
7. Não omitir testes que falharam.
8. Relatórios de fases diferentes não devem se contradizer.
9. Para cada requisito crítico, registrar um teste de aceitação.
10. Para idempotência, limites, transações e filas, testar chamadas simultâneas e fronteiras.
11. Para autenticação e autorização, testar acesso permitido e negado.
12. Para UI, testar estados vazios, carregando, sucesso, erro e falha de rede.
13. Para formulários, testar valores vazios, limites, Unicode, dados inválidos e respostas malformadas.
14. Guardar os resultados em `docs/TEST-REPORT.md`.

## Matriz mínima

| Área | Evidência mínima antes de afirmar que funciona |
|---|---|
| Frontend estático | build/servidor local quando aplicável, navegação, console, telas e acessibilidade básica |
| API | testes de contrato, entradas inválidas, autenticação, erros e status HTTP |
| Banco/migration | aplicação em banco descartável, consultas e verificações de privilégios |
| RLS | testes com cada role relevante, incluindo tentativas negadas |
| Idempotência | repetição, conflito, expiração e concorrência |
| Rate limit | limites, fronteiras temporais e concorrência |
| Uploads | tipos, tamanho, autorização, armazenamento e abuso |
| Pagamentos | ambiente sandbox, eventos repetidos, falhas e reconciliação |
| Deploy | confirmação explícita, configuração revisada, smoke tests e plano de reversão |
