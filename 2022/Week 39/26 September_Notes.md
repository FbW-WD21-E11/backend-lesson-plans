# Lesson Notes

## asynchronous vs synchronous

with the await keyword, we are converting an asynchronous operation into a synchronous operation

## Read operations

### findOne()

Only going to return 1 result from the database

##### Example

```js
// cats collection

[{
    name: 'Zildjian',
    age: 5
},
{
    name: 'Zildjian',
    age: 1
}]
```

We run

```js
const cat = await Cat.findOne({
    name: 'Zildjian'
});
```

##### Example

```js
// users collection

[
{
    username: "terry",
},
{
    username: "terry"
}
]
```

## Special fields


### _id


ObjectId()


## Type coercion

If Mongodb finds your data does not match the type of data in the schema, it will try and convert the data to match the type in the schema

### Type coercion in JS

== vs ===

## Querying with Mongoose

When Mongoose / Mongodb can't find a value for a single document that you've searched for, it always returns with `null`

When Mongoose / Mongodb can't find a value for many documents that you've searched for, it will return with an empty array `[]`

### Enums

You will find enums;

- C++
- Python (3)
- TypeScript
- Java

Enum = Enumerator

##### Enums and Interfaces in TS

```ts
enum Category {
    Black = "black",
    Green = "green",
    Herbal = "herbal",
    Fruit = "fruit"
}

interface TeaSchema {
    dateCreated: number;
    name: string;
    description: string;
    category: Category
    ingredients: string[]
}
```

