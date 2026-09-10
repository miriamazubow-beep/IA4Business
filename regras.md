# Regras

Regras do meu projeto de mapeamento de parcerias, ligadas a `dados/parcerias-teste.csv` (dado de teste, não histórico real — ainda não tenho o Notion conectado, ver `automacoes.md`).

## Regra 1: Proposta parada há mais de 7 dias
- **Gatilho:** tempo — todo dia às 8h
- **Fonte:** `dados/parcerias-teste.csv`, coluna `dias_sem_resposta`
- **Condição:** existe alguma proposta em aberto com `dias_sem_resposta` maior que 7
- **Ação:** escrever um alerta em `alertas/` com o nome da marca e quantos dias parada
- **Quem recebe:** eu, ao abrir o Claude Code de manhã
- **Se não disparar:** gravar em `automacoes.md` a data e quantas propostas foram olhadas

## Regra 2: Marca pede exclusividade
- **Gatilho:** tempo — todo dia às 8h
- **Fonte:** `dados/parcerias-teste.csv`, coluna `exclusividade`
- **Condição:** existe alguma proposta em aberto com `exclusividade` = sim
- **Ação:** escrever um alerta pedindo pra eu decidir se recuso (critério já registrado no `contexto/cliente.md`)
- **Quem recebe:** eu, ao abrir o Claude Code de manhã
- **Se não disparar:** gravar em `automacoes.md` a data e que nenhuma proposta pedia exclusividade
