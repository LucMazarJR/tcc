# ADR 1 - Resolução Parametrizavel

**Status** Proposto
**Data** 17/10/2026
**Autores** Luciano e Diego

## Contexto
Precisamos comparar os níveis de defesa N0 a N5, e se cada um tiver um código diferente não da pra saber se a diferença veio da defesa ou da implementação.

## Decisão
Um servidor só, configurado pela variável DEFENSE_LEVEL, cada nível ativa as camadas anteriores mais a sua. No N0 o cliente resolve a disputa, a partir do N1 quem resolve é o servidor.

## Consequências
**Ganhamos**
- Só a defesa muda entre as medições.

**Perdemos**
- Não da pra medir uma camada isolada, só somada com as anteriores.
- O código das camadas desligadas continua no servidor e pode deixar algum custo nos níveis mais baixos.
