# orders-checkout-api

AsyncAPI-first service repository for the Arcadia Editions checkout contracts.

## Contents

- [SUMMARY.md](./SUMMARY.md): bounded context description, scope, and main domain elements
- `domain-model.zdl`: source of truth for the order aggregate, lifecycle, and events
- `asyncapi.yml`: AsyncAPI contract generated from the ZDL model
- `openapi.yml`: HTTP API contract generated from the ZDL model
- `avro/`: Avro event schemas referenced by the AsyncAPI document
