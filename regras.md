# Regras

Regras do meu projeto de mapeamento de parcerias, ligadas a `dados/amostra.csv`, a fonte canônica declarada em `dados/fonte.md` (dado fictício de treino, não histórico real — ainda não tenho o Notion conectado, ver `automacoes.md`).

## Regra 1: Proposta parada há mais de 7 dias
- **Gatilho:** tempo — todo dia às 8h
- **Fonte:** `dados/amostra.csv`, coluna `dias_sem_resposta`
- **Condição:** existe alguma proposta com `situacao` = "em aberto" e `dias_sem_resposta` maior que 7
- **Ação:** escrever um alerta em `alertas/` com o nome da marca e quantos dias parada
- **Quem recebe:** eu, ao abrir o Claude Code de manhã
- **Se não disparar:** gravar em `automacoes.md` a data e quantas propostas foram olhadas

## Regra 2: Marca pede exclusividade
- **Gatilho:** tempo — todo dia às 8h
- **Fonte:** `dados/amostra.csv`, coluna `exclusividade`
- **Condição:** existe alguma proposta com `situacao` = "em aberto" e `exclusividade` = sim
- **Ação:** escrever um alerta pedindo pra eu decidir se recuso (critério já registrado no `contexto/cliente.md`)
- **Quem recebe:** eu, ao abrir o Claude Code de manhã
- **Se não disparar:** gravar em `automacoes.md` a data e que nenhuma proposta pedia exclusividade

## Quando a fonte falha (vale para todas as regras)
- Se a fonte não existir ou vier vazia, escreva "FONTE INDISPONÍVEL" e pare. Não use outro arquivo da pasta `dados/` no lugar (o `dados/parcerias-teste.csv` é antigo).
- Nunca invente número. Sempre me diga quantas linhas leu e quantas ignorou, e por quê.
- Linha com `dias_sem_resposta` vazio, negativo ou que não seja número, ou com data fora do formato AAAA-MM-DD, é linha ignorada: liste o identificador e o motivo no alerta do dia.
- Se a Regra 2 passar 30 dias sem disparar, force uma vez `exclusividade` = sim em uma linha, confira que o alerta sai e desfaça.
