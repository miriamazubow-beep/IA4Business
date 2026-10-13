# Mapa de parcerias

Repositório da disciplina AI for Business, 2026-2.
O problema: influencer que negocia sozinha perde parceria e dinheiro porque as propostas ficam espalhadas em e-mail, DM e WhatsApp, sem registro de etapa nem de prazo.
O projeto organiza cada proposta por etapa (contato → negociação → contrato → entrega → pagamento) e avisa quando uma fica parada. Quem decide preço e responde a marca sou eu.

## Arquivos

| Arquivo | O que é |
|---|---|
| `problema.md` | O problema, quem sofre, o primeiro experimento e a métrica que eu acompanho |
| `CLAUDE.md` | Como o Claude deve trabalhar comigo neste projeto |
| `contexto/` | Quem eu sou (`sobre-mim.md`), o que é o projeto (`negocio.md`) e quem são as marcas parceiras (`cliente.md`) |
| `dados/fonte.md` | De onde vem o dado, quem atualiza e a regra de cálculo dos 3 números |
| `dados/amostra.csv` | A fonte canônica: 15 propostas fictícias de treino, uma por linha |
| `dados/parcerias-teste.csv` | Primeira amostra, usada na Aula 11. Histórico, não é mais consultada |
| `regras.md` | As regras que a minha operação segue e o que fazer quando a fonte falha |
| `automacoes.md` | O que está ligado, o que roda, quando rodou e o que devolveu |
| `alertas/` | Os alertas escritos pelas regras, um arquivo por dia |
| `pendencias.md` | A lista de pendências que a rotina diária lê |
| `painel.html` | O painel com os 3 números, gerado a partir da fonte |
| `testes.md` | O que acontece quando a operação quebra: 3 cenários testados |
| `escala.md` | O portão de 5 perguntas: a operação está pronta para escalar? |
| `radar/` | Os 42 comentários coletados de um post de marca (`comentarios.md`) e o radar de tendências feito sobre eles (`radar-tendencias.md`) |
| `prompts.md` | Os pedidos que funcionam neste projeto e o que eu aprendi comparando as versões |
| `prompts/` | As versões V1, V2 e V3 do pedido de resposta a marca, em arquivos separados |
| `fake-erp.md` | O contexto da API de treino usada na Aula 10 |
| `diario.md` | Diário de uso da IA (ainda sem entradas) |
| `.claude/skills/` | As skills que eu instalei e criei: `responde-marca`, `gera-briefing`, `revisa-repo`, `docx` |
