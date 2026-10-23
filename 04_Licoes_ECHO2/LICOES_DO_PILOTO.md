# Lições aprendidas — piloto ECHO 2

## Contexto

O ECHO 2 foi usado como piloto para avaliar o método WebForge. A auditoria e o plano foram feitos por inspeção estática. Não houve comprovação de execução de migration, testes de PostgreSQL, Edge Function, autenticação, RLS, concorrência ou deploy.

O ECHO original e o Supabase remoto devem continuar protegidos. Não usar dados reais para testes.

## Decisões positivas observadas
- Projeto separado do original.
- Configuração de exemplo sem credenciais reais conhecidas nos arquivos examinados.
- Interface desabilita publicação quando a configuração está ausente.
- Renderização de mensagens com `textContent`.
- Identidade derivada da sessão autenticada, não de `user_id` enviado pelo cliente.
- Sem fallback conhecido de INSERT direto no fluxo da Edge Function.
- RLS e tabelas internas foram incluídos na proposta de arquitetura.
- Documentação registra que ainda existem testes pendentes.

## Defeitos identificados por inspeção
- Corrida de idempotência: reler/revalidar a chave depois do lock é necessário; confirmar semântica no PostgreSQL real.
- Chaves expiradas podem continuar ocupando a chave primária.
- Frontend pode mostrar sucesso e limpar o campo após resposta malformada.
- Preflight CORS constrói resposta `204` com corpo.
- Origem CORS não é comparada explicitamente com a origem recebida.
- Owner e privilégios da função `SECURITY DEFINER` não são explicitamente controlados.
- `search_path` e resolução de `digest()`/`pgcrypto` precisam ser revisados.
- Retries não preservam a chave da mesma tentativa.
- Configuração ausente na Edge Function pode falhar sem resposta padronizada.
- Tabela de denúncias sem interface/fluxo completo.
- Ausência de testes automatizados.
- Relatório de teste anterior mistura aprovação por inspeção com teste não executado.

## Regras que passam a ser permanentes no WebForge
1. Não declarar sucesso de UI sem validar o contrato da resposta.
2. Reutilizar chave de idempotência durante retries da mesma operação.
3. Testar concorrência em idempotência, rate limit e transações.
4. Testar reuso após expiração.
5. Revisar owner, grants, `SECURITY DEFINER`, `search_path`, schemas e extensões.
6. Verificar CORS com origem permitida e não permitida, incluindo preflight sem corpo em `204`.
7. Todo recurso no banco precisa de fluxo de produto ou ser documentado como não implementado.
8. Separar inspeção estática, teste manual e teste automatizado executado.
9. Não declarar RLS, Auth ou migration funcional antes de validar em ambiente descartável.
10. Falta de ferramenta deve virar bloqueio documentado, não um teste inventado.

## Requisitos do MVP ECHO 2 que precisam de decisão e validação
- 15 segundos de intervalo mínimo entre publicações.
- 5 publicações em 10 minutos.
- 20 publicações em 24 horas.
- Definir se janelas são móveis ou fixas; a recomendação do plano é janelas móveis.
- Mesma chave + mesmo conteúdo: replay sem nova mensagem nem incremento de contadores.
- Mesma chave + conteúdo diferente: conflito.
- Chaves diferentes + conteúdo igual: publicações distintas permitidas, se essa continuar sendo a regra do produto.
- Definir retenção de chaves de idempotência e política de denúncias.
- Definir quem pode revisar denúncias e como proteger esse acesso.

## Estado honesto
O relatório de auditoria e o plano de correção são documentos de inspeção. Eles não comprovam que o ECHO 2 está funcional ou pronto para produção. Corrigir o código não é suficiente: executar testes relevantes continua obrigatório.


## Nova lição: a entrega deve reduzir a configuração manual

O piloto mostrou que um projeto pode ter documentação e código preparados, mas ficar bloqueado porque as ferramentas locais não estão instaladas. O WebForge deve antecipar esse ponto e planejar o handoff desde o início.

Regras permanentes adicionadas na versão 1.1:
- Identificar cedo o backend preferido e as ferramentas necessárias.
- Construir um caminho de inicialização local claro, curto e reproduzível.
- Sempre que possível, preparar scripts de verificação e inicialização para que o usuário não precise montar o ambiente manualmente.
- O usuário deve conseguir escolher Supabase ou outra solução compatível; a metodologia não pode depender de um único fornecedor.
- Não instalar ferramentas, criar contas, usar credenciais, alterar serviços remotos ou executar ações destrutivas sem autorização específica.
- Se faltar uma ferramenta, produzir instruções exatas e um estado explícito de bloqueio, em vez de deixar a pessoa descobrir sozinha ou afirmar que o projeto está pronto.
- Um botão/script de “iniciar” não substitui os testes: migration, autenticação, permissões, concorrência e integração só podem ser marcadas como testadas depois de execução com evidências.
- A documentação deve diferenciar “pronto para iniciar localmente”, “iniciado”, “testado localmente” e “pronto para produção”.
