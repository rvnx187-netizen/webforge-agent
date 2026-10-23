# Checklist de handoff local — WebForge 1.2

Objetivo: entregar um projeto que seja fácil de iniciar pelo usuário, usando Supabase ou outro backend escolhido, sem esconder pré-requisitos ou riscos.

## Escolha e arquitetura
- [ ] Backend preferido foi confirmado; não foi trocado silenciosamente.
- [ ] Motivos da escolha e dependências relevantes estão documentados.
- [ ] O caminho local não exige credenciais de produção.
- [ ] Existe uma alternativa documentada caso o backend escolhido não possa ser executado localmente.

## Ferramentas
- [ ] Ferramentas necessárias foram verificadas no computador/ambiente disponível.
- [ ] Versões foram registradas.
- [ ] Ferramentas ausentes estão listadas com pré-requisitos e comandos de verificação.
- [ ] Nenhuma instalação foi executada sem autorização.

## Inicialização
- [ ] README contém um início rápido testável.
- [ ] Há script de inicialização seguro quando ele realmente reduz complexidade.
- [ ] O script verifica pré-requisitos e explica falhas sem expor segredos.
- [ ] O comando de parada está documentado.
- [ ] O endereço local esperado está documentado, sem presumir que o serviço iniciou com sucesso.
- [ ] Configuração local é ignorada pelo Git e existe exemplo sem segredos.
- [ ] Não há instalação silenciosa, deploy ou acesso remoto escondido no script.

## Banco e backend
- [ ] Ambiente alvo foi identificado explicitamente como local/descartável.
- [ ] Migrations não serão aplicadas até confirmar o alvo e o impacto.
- [ ] Há passos para verificar migrations, funções, Auth, RLS e integrações.
- [ ] Reset ou exclusão de dados exige confirmação explícita e aviso do impacto.
- [ ] Não há fallback inseguro para simular backend funcional.

## Estado da entrega
Marque separadamente um estado para cada item:
- [ ] **Pronto para iniciar** — instruções e arquivos preparados.
- [ ] **Iniciado** — processo confirmado em execução.
- [ ] **Testado localmente** — testes executados com comandos e resultados registrados.
- [ ] **Pronto para produção** — todos os requisitos de produção foram verificados e riscos residuais avaliados.

Esses estados não são equivalentes. Nunca marque um estado superior sem evidência correspondente.

## Handoff ao usuário
- [ ] O usuário recebe os próximos passos exatos, não uma lista vaga de ferramentas.
- [ ] Está claro o que ele precisa fazer manualmente e por quê.
- [ ] Nenhum segredo foi solicitado para ser enviado pelo chat.
- [ ] Ações remotas, instalações, custos e ações destrutivas estão separadas e aguardam autorização.
