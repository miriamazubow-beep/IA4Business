---
name: revisa-repo
description: revisa o repositório do projeto antes de qualquer entrega
---

Leia todos os arquivos `.md` do repositório (raiz, `contexto/`, `prompts/`) como um leitor cético que não conhece o negócio da Miriam.

Aponte, nessa ordem de gravidade:
1. Inconsistências entre arquivos — por exemplo, o `problema.md` e o `contexto/` contando histórias diferentes sobre quem é o "quem sofre" ou qual é o escopo do projeto.
2. Arquivos de tarefa vazios ou não preenchidos (ex: `diario.md` sem entradas reais).
3. Conteúdo duplicado entre arquivos que deveriam ser a mesma fonte de verdade (ex: `prompts.md` na raiz vs pasta `prompts/`).
4. Trechos vagos, genéricos ou sem número onde deveria haver um critério mensurável.
5. Nomes de arquivo fora do padrão minúsculas-com-hífen.

Liste os achados do mais grave ao menor, e para cada um proponha a correção específica (não só aponte o problema).
