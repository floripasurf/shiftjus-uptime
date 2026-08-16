# Shift Jus External Uptime

Template de monitor público e sem dados jurídicos para
`https://app.shiftjus.com`.

Quando publicado em um repositório operacional público autorizado, o workflow
roda fora da infraestrutura da Shift a cada cinco minutos e valida:

- health público e SHA esperado da release;
- disponibilidade da Mesa Shift;
- sessão anônima fechada;
- estado esperado de OAuth e MCP.

Falhas abrem ou atualizam uma única issue com o label `shiftjus-uptime`.
Recuperações fecham o alerta. O repositório não contém credenciais, OAB, CNJ,
conteúdo processual ou dados de tenants.

## Ativação

1. Confirmar no ledger a autorização do repositório operacional público
   (concedida em 2026-08-16).
2. Copiar este `README.md` e `uptime.yml` para a raiz e para
   `.github/workflows/uptime.yml` do novo repositório.
3. Atualizar `SHIFT_JUS_EXPECTED_RELEASE_SHA` para a release ativa.
4. Disparar `workflow_dispatch` com `simulate_failure=true` e confirmar a issue.
5. Disparar novamente sem simulação e confirmar o fechamento da issue.
6. Confirmar uma execução agendada bem-sucedida.
7. Atualizar `stability-soak.json`; a data da primeira execução agendada válida é
   o único `started_at` aceito.
