# FakeERP — API sem conector

Sistema de demonstração da Aula 10, sem conector MCP. Documentação: `fake-erp.isilab.com.br/v3/api-docs` (OpenAPI 3.1).

## Como autenticar
`POST https://fake-erp.isilab.com.br/auth/login`
Body: `{"login": "user", "password": "user"}`
Resposta: `{"token": "...", "type": "Bearer", "expiresInMs": 3600000}` — o token expira em 1 hora.

## Endpoints
- `GET /report/{year}/{month}` — relatório de pedidos do mês. Precisa do header `Authorization: Bearer <token>`.
  Resposta: `count`, `totalValue`, `totalDiscount`, `totalAmount`, e a lista `orders` (cada um com `orderId`, `orderDateTime`, `value`, `discount`, `total`, `status`).

## Exemplo que funciona
```
curl -X POST https://fake-erp.isilab.com.br/auth/login -H "Content-Type: application/json" -d '{"login":"user","password":"user"}'
curl https://fake-erp.isilab.com.br/report/2026/1 -H "Authorization: Bearer <token>"
```

## Pegadinha
O `totalAmount`/soma bruta do relatório inclui pedidos `CANCELLED` e `PENDING`. "Quanto vendemos de verdade" = somar só os pedidos com `status: PAID`, não o total do relatório.

## Erros comuns
- 401/403: token expirado (dura 1h) ou campo errado no login — o campo é `login`, não `username`.
- Resposta vazia sem erro: o mês não tem pedidos (a base de teste só tem dados em 01, 02, 03 e 07/2026).

## Meses testados
Janeiro/2026: 4 pedidos, 2 pagos (R$ 1.430,00 vendido de verdade), 1 cancelado, 1 pendente.
