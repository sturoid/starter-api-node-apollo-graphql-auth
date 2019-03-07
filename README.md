## starter-api-node-apollo-graphql-auth

Starter API project with Node, Apollo Server, GraphQL, (WIP) authentication, (WIP) password requesting and resetting, email configuration, current user on context, file structure, and code formatting. Mongo DB and Mongoose are initially set up, but can easily be swapped for whatever DB you use.

### Updating to latest packages releases

To quickly and simply force update all packages to their latest release:

```
> npm run update:packages
```

### Running project

```
> npm install
> npm run dev
```

### Running authenticated queries in Graphql playground

First run the sign in method to get an auth token:

```
mutation {
  signIn(email:"user@gmail.com", password:"password") {
    token
    userId
  }
}
```

Then under headers set the token like so:

```
{
  "Authorization": "Bearer <my-token>"
}
```

### Code formatting

#### File Naming

All files are lower case and dash (-) separated. Much thought and turmoil went into this decision but was influenced by multiple articles:

- https://blog.codinghorror.com/of-spaces-underscores-and-dashes/
- https://x-equals.com/dashes-versus-underscores/

#### Folder structure

- config/ - Application config including db, jest/testing, etc.
- seed/ - Database seeding related files. Initial seeds for users are present to show structure.
- src/ - Application logic.
  - src/app - Global/shared app logic.
  - src/<entity-folder> - All logic is separated by entity or resource. Files in each folder are named as "entity-"file-purpose".js". Examples are: (user-utils.js, user-model.js, etc...).
  - src/"entity-folder"/"entity-files" - Initial structure is:
    - entity-model.js - DB model.
    - entity-types.js - GraphQL types.
    - entity-resolvers.js - GraphQL resolvers.
    - entity-utils.js - Non-database related functions.
    - entity-services.js - Detabase related functions.
