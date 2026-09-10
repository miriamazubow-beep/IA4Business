# Biblioteca de prompts

## Responder marca que propôs parceria
Atualizado em: 10/09

### V1 — sem técnica nenhuma
Pedido: "eu preciso que a IA me entregue uma mensagem para responder uma marca que propôs parceria"

Resposta:
> Olá! Muito obrigada pelo contato e pelo interesse em fazer uma parceria comigo! 😍 Fiquei muito feliz com a proposta e adoraria saber mais detalhes! Pode me enviar mais informações sobre a campanha, valores e prazos? Estou super animada para essa parceria! Aguardo seu retorno! ✨

Problema: tom de vendedora genérica, emoji em excesso, "super animada" — não parece a Miriam, parece qualquer influencer.

### V2 — briefing completo (tarefa, formato, amostra, limite)
Pedido:
> Tarefa: escreva uma mensagem de resposta para uma marca que propôs uma parceria comigo, pedindo as informações que faltam para eu decidir se aceito (valor oferecido, prazo de pagamento, se pede exclusividade, o que a entrega envolve).
> Formato: mensagem única, direta, no máximo 6 linhas, tom profissional mas caloroso.
> Amostra: [sem exemplo real ainda — usar tom direto, sem frases de efeito, como já registrado no CLAUDE.md]
> Limite: no máximo 1 emoji, sem "super animada", sem urgência falsa, sem aceitar nada ainda.

Resposta:
> Oi! Obrigada pelo contato. Antes de decidir, preciso de mais detalhes: qual o valor oferecido, o prazo de pagamento, se a parceria exige exclusividade com outras marcas do segmento, e o que exatamente entra na entrega (posts, stories, prazo de produção). Assim que eu tiver isso, te dou uma resposta.

O que mudou da V1 para a V2: saiu o tom de vendedora entusiasmada, entrou um pedido objetivo com os quatro critérios que realmente decidem se a Miriam aceita (valor, prazo de pagamento, exclusividade, escopo) — os mesmos critérios de recusa registrados no cliente.md.

**Nota:** esta V2 usou um placeholder no lugar da amostra real (não temos uma mensagem sua de verdade colada). Quando usar essa biblioteca de verdade, cole uma resposta sua real que você goste no lugar do placeholder — isso muda o resultado mais do que qualquer outra parte do briefing.

### V3 — reescrita pela IA (meta-prompt)
Pedido:
> "Este é um pedido que eu vou usar toda semana: [colar a V2]. Critique como um revisor exigente: o que está ambíguo, o que falta, o que sobra? Depois reescreva na melhor versão possível."

Crítica recebida:
- Ambíguo: "tom profissional mas caloroso" não diz o nível de formalidade real.
- Falta: instrução para não perguntar de novo o que a marca já respondeu na proposta original.
- Sobra: "sem urgência falsa" é redundante com "sem aceitar nada ainda".

V3 (versão reescrita):
> Tarefa: escreva uma mensagem de resposta para uma marca que propôs uma parceria comigo. Antes de escrever, confira o que a proposta original já informou — só pergunte o que realmente falta entre: valor oferecido, prazo de pagamento, exclusividade, escopo da entrega.
> Formato: mensagem única, direta, no máximo 6 linhas, tom de quem já fecha parceria há um tempo — nem informal demais, nem corporativo.
> Amostra: [colar uma mensagem real seguinte que a Miriam escrever]
> Limite: no máximo 1 emoji se fizer sentido; nunca aceitar ou recusar a proposta nessa mensagem, só pedir o que falta.

Resposta:
> Oi! Obrigada pela proposta. Pelo que você mandou, ainda preciso saber o prazo de pagamento e se vocês pedem exclusividade com outras marcas do segmento — o resto ficou claro. Me passa isso que já te retorno com uma posição.

### O pedido que funciona
A V3 venceu: ela evita o desperdício de perguntar de novo o que a marca já respondeu (algo que a V2 fazia por padrão), o que deixa a mensagem mais curta e mais profissional sem perder nenhum dos quatro critérios de decisão.

### O que aprendi
A amostra (exemplo real do seu tom) é a parte que mais falta nesta biblioteca — sem ela, mesmo a V3 é uma aproximação. Na próxima vez que usar este prompt de verdade, cole uma mensagem sua real no lugar do placeholder.
