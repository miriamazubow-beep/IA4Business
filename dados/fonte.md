# Fonte canônica

## A situação real, hoje
As propostas de parceria chegam por quatro lugares (e-mail, DM do Instagram, DM do TikTok e WhatsApp) e não existe nenhum registro único: nem planilha, nem Notion, nem CRM. O controle está na minha cabeça e nas conversas. Não existe base organizada.

## 1. Qual é a fonte
`dados/amostra.csv`: uma linha por proposta de parceria. É a fonte que ganha quando qualquer outro lugar (uma DM, um e-mail, a minha memória) disser outra coisa.

**Os dados deste arquivo são inventados.** São 15 propostas fictícias, com marcas chamadas "Marca A" a "Marca O", montadas no formato que a minha operação precisa. Não são o meu histórico real nem o da Camila. É fonte de treino enquanto o registro real não existe. A fonte real vai ser o board de parcerias no Notion, quando o conector estiver ligado (ver `automacoes.md`).

O arquivo `dados/parcerias-teste.csv` é a primeira versão, usada na Aula 11 (5 linhas). Fica no repositório como histórico; não é mais consultado.

## 2. Onde ela vive
Neste repositório, em `dados/amostra.csv`.

## 3. Quem atualiza e com que frequência
Eu, à mão, uma vez por semana (segunda-feira), e sempre que chegar uma proposta nova. Cada atualização é um commit.

Como eu percebo que está desatualizada: a data do último commit do arquivo tem mais de 7 dias, ou a rotina registra a mesma quantidade de propostas em aberto por duas semanas seguidas.

## 4. Campos que importam para as regras
| Campo | O que é | Quem usa |
|---|---|---|
| `situacao` | em aberto, fechada, perdida ou recusada | Regras 1 e 2 (só olham "em aberto") |
| `dias_sem_resposta` | dias desde a última mensagem sem resposta minha, na data da atualização | Regra 1 |
| `exclusividade` | sim ou não | Regra 2 |
| `marca`, `etapa` | para o alerta dizer de quem se trata e onde parou | Regras 1 e 2 |
| `data_contato`, `data_contrato`, `valor` | para os 3 números do painel | `painel.html` |

Etapas possíveis: contato → negociação → contrato → entrega → pagamento.

## Os 3 números e a regra de cálculo de cada um
1. **Propostas em aberto (volume):** quantidade de linhas com `situacao` = "em aberto". Não conta fechada, perdida nem recusada.
2. **Valor fechado (dinheiro):** soma de `valor` das linhas com `situacao` = "fechada" (etapa contrato, entrega ou pagamento). Não entra proposta em aberto, perdida ou recusada: valor proposto não é valor fechado.
3. **Dias do primeiro contato ao contrato (qualidade):** média de (`data_contrato` − `data_contato`) das linhas com `situacao` = "fechada".

## Sanitização
Nenhum nome de marca real, pessoa, telefone, e-mail ou documento. Cada proposta tem um identificador fixo (`PAR-001`, `PAR-002`...).

## FALTA DEFINIR
- Em que data eu começo a registrar propostas reais no lugar das fictícias.
- Se o registro da Camila entra na mesma base ou em uma separada.
- Se `dias_sem_resposta` continua sendo digitado à mão ou passa a ser calculado a partir de uma coluna de data da última mensagem.
