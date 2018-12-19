# GraphQL CRUD methods

## ```npm run json:server```
## ```npm run dev:server```

### This starts a qrapghl server that allows you to create remove update and delete mock json data on `localhost:3000/graphql`

# CREATE:
```
addCustomer: {
      type: CustomerType,
      args: {
        name: { type: new GraphQLNonNull(GraphQLString) },
        email: { type: new GraphQLNonNull(GraphQLString) },
        age: { type: new GraphQLNonNull(GraphQLInt) }
      },
      resolve(parentValue, args) {
        return axios
          .post("http://localhost:3000/customers", {
            name: args.name,
            email: args.email,
            age: args.age
          })
          .then(res => res.data);
      }
    },
```
# READ
# UPDATE: 
```
editCustomer:{
      type:CustomerType,
      args:{
          id:{type: new GraphQLNonNull(GraphQLString)},
          name: {type: GraphQLString},
          email: {type: GraphQLString},
          age: {type: GraphQLInt}
      },
      resolve(parentValue, args){
          return axios.patch('http://localhost:3000/customers/'+args.id, args)
          .then(res => res.data);
      }
  },
```
# DELETE:
```
deleteCustomer: {
      type: CustomerType,
      args: {
        id: { type: new GraphQLNonNull(GraphQLString) }
      },
      resolve(parentValue, args) {
        return axios
          .delete(`http://localhost:3000/customers/${args.id}`)
          .then(res => res.data);
      }
    },
```


### https://graphql.org/
