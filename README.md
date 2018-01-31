# soap-graphql

Create a graphql schema based on a WSDL-defined soap endpoint.

Note: Not production ready (yet). Will only work for a limited number of WSDLs.

## Example
```typescript
import * as express from 'express';
import * as expressGraphql from 'express-graphql';
import { GraphQLSchema } from 'graphql';
import { soapGraphqlSchema } from 'soap-graphql';

soapGraphqlSchema("http://<<url to wsdl>>").then((schema: GraphQLSchema) => {

    const app: express.Application = express();
    app.use('/graphql', expressGraphql({
        schema: schema,
        graphiql: true,
    }));

    app.listen(4000, () => { console.log(`serving graphql on http://localhost:4000/graphql`) });

});
```
