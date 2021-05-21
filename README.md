# Serverless Data API


[![MIT License](https://badgen.now.sh/badge/License/MIT/blue)](https://github.com/thomasmilner/serverlessdataapi/blob/main/LICENSE)

Cloudformation/SAM yaml file to create a GraphQL API with AWS AppSync backed by a DynamoDB table.

## Schema

```graphql
        schema {
          query: Query
          mutation: Mutation
        }
        type Data {
          data: [AWSJSON]
          pk1: String
          sk1: String
        }
        type DataCollection {
          items: [Data]
          nextToken: String
        }
        input WriteDataInput {
          pk1: String!
          sk1: String!
          data: [AWSJSON]!
        }
        input UpdateDataInput {
          pk1: String!
          sk1: String!
          data: [AWSJSON]!
        }
        type Mutation {
          writeData(input: WriteDataInput!): Data
          updateData(input: UpdateDataInput!): Data
          deleteData(pk1: String!, sk1: String!): Data
        }
        type Query {
          readData(pk1: String!, sk1: String!): Data
          readAllPKData(pk1: String!): DataCollection
        }
```
