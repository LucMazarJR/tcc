# ADR 4 - Protocolo de Comunicação

**Status** Proposto
**Data** 17/10/2026
**Autores** Luciano e Diego

## Contexto
O bot atacante usa o mesmo protocolo do cliente normal, se o protocolo mudar entre os níveis os ataques não são mais os mesmos.

## Decisão
Um contrato só em JSON via SignalR, igual em todos os níveis. O cliente manda a intenção da jogada com um nonce e um campo de resultado opcional, e o que muda por nível é como o servidor trata isso.

- N0 aceita o resultado do cliente.
- N1 ignora o resultado e resolve no servidor.
- N2 rejeita nonce repetido.
- N3 para de mandar as cartas do oponente.
- N4 e N5 não mudam o contrato.

Mensagem rejeitada sempre volta com o motivo.

## Consequências
**Ganhamos**
- Os mesmos ataques rodam em todos os níveis.
- Com o motivo da rejeição o bot consegue contar quantas tentativas passaram.

**Perdemos**
- Campos que alguns níveis não usam continuam no contrato.
