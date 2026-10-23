# Checklist de segurança antes de publicar

## Escopo e dados
- [ ] O produto coleta somente os dados necessários.
- [ ] Dados sensíveis foram identificados e protegidos.
- [ ] Política de retenção e exclusão está definida quando aplicável.
- [ ] Segredos não aparecem no frontend, repositório, logs ou relatórios.

## Autenticação e autorização
- [ ] Cada ação protegida é autorizada no servidor.
- [ ] O backend não confia em `user_id` enviado pelo cliente.
- [ ] Testes cobrem usuário permitido, usuário não autorizado e token inválido.
- [ ] Permissões seguem o princípio do menor privilégio.

## Banco e SQL
- [ ] Migrations foram aplicadas em ambiente descartável.
- [ ] RLS e grants foram verificados com as roles relevantes.
- [ ] Funções privilegiadas têm owner, grants e `search_path` revisados.
- [ ] Extensões e schemas foram confirmados.
- [ ] Operações concorrentes e transações foram testadas.

## Entradas e interface
- [ ] Entradas são validadas no servidor.
- [ ] Conteúdo do usuário é renderizado de forma segura.
- [ ] Respostas do servidor são validadas antes de confirmar sucesso.
- [ ] Falhas preservam dados digitados quando apropriado.
- [ ] Erros não expõem stack traces, tokens ou detalhes internos.
- [ ] Teclado, foco, contraste e telas pequenas foram verificados.

## Abuso e disponibilidade
- [ ] Rate limits existem onde são necessários.
- [ ] Limites foram testados, incluindo concorrência.
- [ ] Idempotência foi testada quando há retries ou transações repetíveis.
- [ ] Uploads, denúncias e conteúdo público têm proteção proporcional contra abuso.
- [ ] Existe procedimento para incidentes ou indisponibilidade.

## Operação
- [ ] Instruções de configuração e recuperação existem.
- [ ] Backup e restauração foram testados quando há dados persistentes.
- [ ] Dependências e licenças foram revisadas.
- [ ] Existe plano de reversão para publicação.
- [ ] Publicação e acesso remoto foram autorizados explicitamente.

## Decisão
- [ ] Nenhum risco crítico conhecido permanece sem aceitação explícita.
- [ ] Relatório final corresponde aos testes realmente executados.
- [ ] As pendências estão visíveis para quem receber o produto.
