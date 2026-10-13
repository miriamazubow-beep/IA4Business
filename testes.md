# Testes de falha

Testado em 01/10/2026, às 09:45, no Claude Code. A rotina testada é a "Vigia de parcerias" (ver `automacoes.md`), rodada à mão sobre `dados/amostra.csv`. Depois de cada teste a fonte voltou ao estado original (15 linhas).

## Cenário 1 · A fonte saiu do ar
**O que eu testei:** renomeei `dados/amostra.csv` para `dados/amostra_OLD.csv` e rodei a rotina.

**O que aconteceu:** a leitura deu erro de arquivo não encontrado, então a falha apareceu. Mas o `regras.md` não dizia o que fazer nesse caso: nada mandava parar nem registrar. E na mesma pasta ficou o `dados/parcerias-teste.csv`, a fonte antiga, com as mesmas colunas que as regras usam. Sem instrução, a rotina podia aplicar as regras nele e devolver um resultado com cara de normal, em cima de dado velho.

**O que eu consertei:** acrescentei ao `regras.md` a seção "Quando a fonte falha": escrever "FONTE INDISPONÍVEL", parar e não usar outro arquivo da pasta. Repeti o teste. Antes: erro de leitura sem regra do que fazer. Depois: "FONTE INDISPONÍVEL: não encontrei dados/amostra.csv. Parei. 0 linhas lidas."

## Cenário 2 · Chegou dado inesperado
**O que eu testei:** estraguei 3 linhas da fonte e rodei a rotina e o cálculo do painel:
- PAR-007: `dias_sem_resposta` vazio (era 9, a proposta que dispara a Regra 1)
- PAR-012: `dias_sem_resposta` = -5
- PAR-014: `data_contrato` escrita como 29/09/2026 em vez de 2026-09-29

**O que aconteceu:**
- A Regra 1 não disparou e não avisou nada: 15 linhas lidas, 8 em aberto, nenhum alerta. O alerta da Marca G, que tinha saído minutos antes, sumiu em silêncio, porque campo vazio não é "maior que 7".
- O valor negativo passou sem aviso.
- A Regra 1 não usa data, então não percebeu a data errada. O cálculo do painel percebeu do pior jeito: "Dias do contato ao contrato" virou NaN, sem dizer qual linha causou.
- Nenhum número foi inventado, mas nenhuma linha foi apontada como ignorada.

**O que eu consertei:** a mesma seção do `regras.md` agora manda dizer quantas linhas leu e quantas ignorou, e trata campo vazio, negativo ou data fora do formato como linha ignorada, com identificador e motivo no alerta do dia. O que não consertei: o `painel.html` continua mostrando NaN se a data vier em outro formato. Plano B: conferir a data das linhas novas à mão toda segunda, antes de gerar o painel de novo.

## Cenário 3 · A condição nunca dispara
**O que eu testei:** olhei o histórico da Regra 2 (marca pede exclusividade) no `automacoes.md`. Ela rodou em 10/09 e em 01/10 e não disparou nenhuma vez. Para saber se era operação saudável ou regra quebrada, troquei `exclusividade` para "sim" na PAR-010 (Marca J) e rodei a regra.

**O que aconteceu:** disparou: PAR-010, Marca J. Desfiz a troca, rodei de novo e voltou a não disparar, com 15 linhas na fonte. A regra funciona; o silêncio é porque nenhuma das propostas da fonte pede exclusividade. Como a fonte é dado fictício que eu mesma montei sem nenhum caso de exclusividade, esse silêncio ainda não diz nada sobre as minhas propostas reais.

**O que eu consertei:** nada na regra. Plano B registrado no `regras.md`: se a Regra 2 passar 30 dias sem disparar, forçar uma vez o dado que dispara, ver o alerta sair e desfazer.
