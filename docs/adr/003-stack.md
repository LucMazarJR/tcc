# ADR 3 - Stack Tecnológica

**Status** Proposto
**Data** 17/10/2026
**Autores** Luciano e Diego

## Contexto
Precisamos de estado no servidor, tempo real por turnos, controle de compra concorrente, métricas e o mesmo ambiente em todas as execuções.

## Decisão
| Camada | Tecnologia | Motivo |
|---|---|---|
| Backend | ASP.NET Core | Tipagem forte |
| Tempo real | SignalR | Comunicação bidirecional nos turnos |
| Sessão | Redis | Estado em memória com operação atômica |
| Banco | PostgreSQL | Transação para compra concorrente |
| Métricas | OpenTelemetry e Grafana | Latência e recurso por nível |
| Carga | k6 | Teste de capacidade |
| Front-end | React | Cliente para demonstração |
| Infra | Docker Compose | Mesmo ambiente sempre |

## Consequências
**Ganhamos**
- Cada necessidade do experimento tem uma ferramenta.

**Perdemos**
- Tem que definir se a compra concorrente fica no Redis ou no PostgreSQL.
- O k6 não suporta SignalR direto, então vamos precisar testar isso antes.
