## Libraries and Frameworks

Libraries are a set of tools, that do not impose a structure on your code

Frameworks are there to solve a much more complex problem, and imposes a structure on your code

Libraries and frameworks are technologies

Every technology is a solution to a problem

## Licensing

Open-source = source code is visible, anybody can contribute

Proprietary = source code hidden

## Glossary

### Document

An individual record in a collection; like an individual item in an array

```js
const document = {
    id: 5892345829548,
    name: "Mars",
    elevation: 384,
    azmiuth: 344,
    size: 323,
    colour: "red"
};
```

### Collection

- A group of documents; like an array of documents
- A database can contain 1 or more collections

```js
const collection = [
{
    id: 5892345829548,
    name: "Mars",
    elevation: 384,
    azmiuth: 344,
    size: 323,
    colour: "red"
},
{
    id: 5892345829549,
    name: "Jupiter",
    elevation: 111,
    azmiuth: 112,
    size: 345566,
    colour: "orange"
}];
```

### Schema

- A "pattern" which the data must follow
- For example, we can specify what fields a document in a collection might contain, and the type of data for that field
- We use a schema to build a Model

### Model

- We use a model to interface to our collection

## Identifiers / IDs

0-9 - 10
a-z - 24

## Setting up interaction with Db

1. What data will I store?
2. Create the schema
3. Create the model
4. Use the model
