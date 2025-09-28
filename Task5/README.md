## Сопоставление AS IS -> TO BE
- GET /clients/{id} → `client(id: ID!): Client`
- GET /clients/{id}/documents → `clientDocuments(id: ID!): [Document!]!`
- GET /clients/{id}/relatives → `clientRelatives(id: ID!): [Relative!]!`

## Примеры
Запрос клиента с базовыми полями:

```graphql
query GetClient($id: ID!) {
  client(id: $id) {
    id
    name
    age
  }
}
```

Клиент с документами и родственниками одним запросом:
```graphql
query GetClientFull($id: ID!) {
  client(id: $id) {
    id
    name
    documents { id type number expiryDate }
    relatives { id relationType name }
  }
}
```

Только документы:
```graphql
query GetClientDocuments($id: ID!) {
  clientDocuments(id: $id) { id type number }
}
```