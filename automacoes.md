# Auditoria de automações

Tudo que foi ligado até agora (conectores, fluxos, rotinas), com a régua manter / consertar / matar.

- **Chave SSH do GitHub** (Aula 3) — MANTER. Usada em todo commit/push desde então, sem falha.
- **Skill docx** (Aula 8) — CONSERTAR. Instalada, mas os scripts originais precisam de `node`/`npm`, que não está nesta máquina; o teste real só funcionou usando `python-docx` como alternativa.
- **Skill revisa-repo** (Aula 8) — MANTER. Rodou duas vezes, achou problemas reais no repositório (inconsistência problema.md × contexto/, diario.md vazio, prompts duplicado).
- **Skill gera-briefing** (Aula 8) — MANTER. Testada com um cenário diferente do original e manteve a régua certa.
- **Skill responde-marca** (Aula 8) — MANTER. Testada com um cenário novo, não repetiu perguntas já respondidas.
- **Conector Gmail** (Aula 9) — MANTER. Usado de verdade para ler e classificar os 10 e-mails mais recentes; foi o que revelou que um colega já tinha mandado as Aulas 10 e 11.
- **Conector Notion** (Aula 9) — MATAR por enquanto. Não existe ferramenta de Notion disponível nesta sessão; o fluxo caixa de entrada → Notion não foi concluído. Retomar manualmente ou quando houver conector.
- **Rotina diária 7h30** (Aula 9) — CONSERTAR. Não está agendada; desde 01/10 roda à mão sobre o `pendencias.md` (ver "Primeira automação" abaixo). Falta agendar e trocar o arquivo pelo Notion.
- **fake-erp.md** (Aula 10) — MANTER. Testado numa sessão nova, só com o arquivo, e trouxe o relatório de fevereiro/2026 certo.
- **regras.md** (Aula 11) — MANTER. As duas regras rodam à mão contra a fonte e se comportam como esperado (ver Execuções abaixo).
- **painel.html** (Aula 12) — MANTER. Gerado a partir de `dados/fonte.md` e `dados/amostra.csv`; atualização à mão (ver Painel abaixo).

## Primeira automação (Aula 9)

### Conectores
- Gmail: ligado na Aula 9 e usado uma vez (classificação dos 10 e-mails mais recentes).
- Notion: não ligado. Sem ele, o destino do fluxo e da rotina é um arquivo do repositório.

### Fluxo caixa de entrada → Notion
Prompt:
> Leia os meus 10 e-mails mais recentes e classifique cada um em: responder hoje, responder esta semana, só ler, ignorar. Proposta de marca nunca é ignorar. Depois crie no Notion uma página chamada "Caixa de entrada — [data]" com a lista classificada, cada e-mail com remetente, assunto e a ação recomendada em uma linha.

Status: a leitura e a classificação rodaram na Aula 9; a página no Notion não foi criada (conector não ligado).

### Rotina diária de pendências
- Nome: Pendências do dia
- Horário: todo dia às 7h30
- Fonte: `pendencias.md` (no lugar da página "Pendências" do Notion)
- Prompt:
> Leia o arquivo pendencias.md. Para cada item: se o prazo venceu, marque como atrasado; se está concluído no texto, mova para a seção Feito. No fim, escreva no topo um resumo de 3 linhas: o que vence hoje, o que atrasou, o que anda bem.

Status: rodada à mão (a função de agendar não está disponível na minha conta)

| Data | Hora | Resultado |
|---|---|---|
| 01/10 | 09:42 | 6 itens lidos. 1 marcado como atrasado (entrega da NP2, prazo 21/09). Nada vence hoje. Nenhum item movido para Feito. Resumo gravado no topo do `pendencias.md`. |

## Regras ligadas
Arquivo das regras: `regras.md` (2 regras: proposta parada há mais de 7 dias, marca pede exclusividade)
Fonte: `dados/amostra.csv`, declarada em `dados/fonte.md` (dado fictício de treino — ainda não tenho o Notion conectado). Até 10/09 a fonte era `dados/parcerias-teste.csv`.

### Rotina que aplica as regras
- Nome: Vigia de parcerias
- Horário: todo dia às 8h
- Condição que ela checa: as duas do `regras.md` — proposta em aberto com `dias_sem_resposta` maior que 7; proposta em aberto com `exclusividade` = sim
- Prompt:
> Leia o regras.md e o dados/fonte.md. Abra a fonte indicada nas regras e aplique cada regra. Para cada regra me diga: disparou ou não, e qual foi o número que decidiu. Se disparou, escreva o alerta em alertas/AAAA-MM-DD.md, em até 3 linhas, com o identificador e o nome da marca. Se não disparou, registre no automacoes.md a data, a hora e quantas propostas foram olhadas. Não deduza nada: mostre quantas linhas leu antes de aplicar a regra.

Status: rodada à mão (a função de agendar não está disponível na minha conta)

## Execuções
| Data | Hora | Regra | Fonte | Disparou? |
|---|---|---|---|---|
| 10/09 | não anotada | Proposta parada há mais de 7 dias | dados/parcerias-teste.csv | sim — Marca B, 10 dias. Alerta em `alertas/2026-09-10.md` |
| 10/09 | não anotada | Marca pede exclusividade | dados/parcerias-teste.csv | não — 5 propostas olhadas, nenhuma com exclusividade |
| 01/10 | 09:43 | Proposta parada há mais de 7 dias | dados/amostra.csv | sim — PAR-007 (Marca G), 9 dias. 15 linhas lidas, 8 em aberto. Alerta em `alertas/2026-10-01.md` |
| 01/10 | 09:43 | Marca pede exclusividade | dados/amostra.csv | não — 8 propostas em aberto olhadas, nenhuma com exclusividade |

## Painel
- Arquivo: `painel.html`, na raiz. Abre com dois cliques, sem internet.
- O que mostra: propostas em aberto, valor fechado e dias do primeiro contato ao contrato, com as regras de cálculo do `dados/fonte.md`.
- Como é atualizado: à mão. Depois de atualizar o `dados/amostra.csv` (toda segunda), peço no Claude Code para gerar o painel de novo a partir do `dados/fonte.md` e do `dados/amostra.csv`. Os dados ficam copiados dentro do próprio `painel.html`, então painel e CSV só batem depois de gerar de novo.
- Última geração: 01/10/2026 — 8 propostas em aberto, R$ 4.200 de valor fechado, 14,4 dias do contato ao contrato.
