# Lesson notes

## MongoDB collection reference

Here we create our model

```js
const Tea = model("Tea", teaSchema);
```

"Tea" is a string reference to the model
1. Internally as a reference to that model
2. Informs MongoDB how to name that collection

However collection is named "teas" in Db

"Tea" !== "teas" Why?

MongoDB has it's own naming conventions

1. Makes everything lowercase
2. It tries to turn the noun into the plural form


## Validation

required = that field must be present
default = to give a default value

min = minimum number allowed
max = maxmimum number allowed
