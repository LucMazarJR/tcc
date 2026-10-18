# ADR 2 - Monolito Modular

**Status** Proposto
**Data** 17/10/2026
**Autores** Luciano e Diego

## Contexto
Com microsserviços a comunicação entre eles entraria na medição de latência e misturaria com o custo da defesa.

## Decisão
Monolito modular em ASP.NET Core, com as camadas de defesa em um módulo separado.

## Consequências
**Ganhamos**
- A latência medida é da defesa e não da rede entre serviços.
- Da pra medir o tamanho e a complexidade de cada camada.

**Perdemos**
- A capacidade é medida em uma instância só, sem escala horizontal.
