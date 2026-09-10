# Auditoria de automações

Tudo que foi ligado até agora (conectores, fluxos, rotinas), com a régua manter / consertar / matar.

- **Chave SSH do GitHub** (Aula 3) — MANTER. Usada em todo commit/push desde então, sem falha.
- **Skill docx** (Aula 8) — CONSERTAR. Instalada, mas os scripts originais precisam de `node`/`npm`, que não está nesta máquina; o teste real só funcionou usando `python-docx` como alternativa.
- **Skill revisa-repo** (Aula 8) — MANTER. Rodou duas vezes, achou problemas reais no repositório (inconsistência problema.md × contexto/, diario.md vazio, prompts duplicado).
- **Skill gera-briefing** (Aula 8) — MANTER. Testada com um cenário diferente do original e manteve a régua certa.
- **Skill responde-marca** (Aula 8) — MANTER. Testada com um cenário novo, não repetiu perguntas já respondidas.
- **Conector Gmail** (Aula 9) — MANTER. Usado de verdade para ler e classificar os 10 e-mails mais recentes; foi o que revelou que um colega já tinha mandado as Aulas 10 e 11.
- **Conector Notion** (Aula 9) — MATAR por enquanto. Não existe ferramenta de Notion disponível nesta sessão; o fluxo caixa de entrada → Notion não foi concluído. Retomar manualmente ou quando houver conector.
- **Rotina diária 7h30** (Aula 9) — MATAR por enquanto. Não foi criada — o exercício foi interrompido para seguir para a Aula 10. Fica como pendência, não como automação ativa.
- **fake-erp.md** (Aula 10) — MANTER. Testado numa sessão nova, só com o arquivo, e trouxe o relatório de fevereiro/2026 certo.
- **regras.md** (Aula 11) — MANTER. As duas regras rodaram à mão contra `dados/parcerias-teste.csv` e se comportaram como esperado (ver Execuções abaixo).

## Regras ligadas
Arquivo das regras: `regras.md` (2 regras: proposta parada > 7 dias, marca pede exclusividade)
Fonte: `dados/parcerias-teste.csv` (dado de teste — ainda não tenho o Notion conectado)
Como roda: à mão, no Claude Code (rotina agendada em claude.ai/code/routines não foi criada nesta sessão — plano B da própria aula)

## Execuções
| Data | Regra | Fonte | Disparou? |
|---|---|---|---|
| 10/09 | Proposta parada há mais de 7 dias | dados/parcerias-teste.csv | sim — Marca B, 10 dias |
| 10/09 | Marca pede exclusividade | dados/parcerias-teste.csv | não — nenhuma proposta com exclusividade |
