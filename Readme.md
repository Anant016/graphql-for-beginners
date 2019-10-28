# Migration from REST to GraphQl
## GraphiQl
### http://localhost:8080/graphql

* ADD
mutation{
  createContact(input:{
    firstName:"Anant",
    lastName:"Rungta",
    email:"anantrungta199.com",
    company:"Google"
  }){
    id
    firstName
  }
}

* QUERY1
query{
  getContacts{
    firstName
    lastName
    company
  }
}

* QUERY2
query{
 getOneContact(id:"5db7345ae90bec1ccc4fddb5"){
    firstName
    lastName
    company
    email
  }
}

* ALIASES
query{
  one:getOneContact(id:"5db7345ae90bec1ccc4fddb5"){
    firstName
    lastName
    company
    email
  }
  two:getOneContact(id:"5db73487e90bec1ccc4fddb6"){
    firstName
    lastName
  }
}

* FRAGMETS 
query{
  one:getOneContact(id:"5db7345ae90bec1ccc4fddb5"){
  ...contactFragment
  }
  two:getOneContact(id:"5db73487e90bec1ccc4fddb6"){
 ...contactFragment
  }
}

fragment contactFragment on Contact {
    firstName
    lastName
    company
}

* UPDATE
mutation{
  updateContact(input:{
    id:"5db7345ae90bec1ccc4fddb5",
    firstName:"BoaAli"
  }){
    firstName
  }
}

* DELETE
mutation{
  deleteContact(id:"5db7345ae90bec1ccc4fddb5")
}