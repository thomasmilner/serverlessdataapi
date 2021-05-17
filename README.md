# Serverless Data API

Cloudformation/SAM yaml file to create a GraphQL API with AWS AppSync backed by a DynamoDB table.

## Schema

```graphql
  schema {
    query: Query
    mutation: Mutation
  }
  type Item {
    payload: [AWSJSON]
    pk1: String
    sk1: Int
  }
  type ItemConnection {
    items: [Item]
    nextToken: String
  }
  input CreateItemInput {
    pk1: String!
    sk1: Int!
    payload: [AWSJSON]!
  }
  input UpdateItemInput {
    pk1: String!
    sk1: Int!
    payload: [AWSJSON]!
  }
  type Mutation {
    createItem(input: CreateItemInput!): Item
    updateItem(input: UpdateItemInput!): Item
    deleteItem(pk1: String!, sk1: Int!): Item
  }
  type Query {
    getItem(pk1: String!, sk1: Int!): Item
    getAllPKItems(pk1: String!): ItemConnection
  }
```
