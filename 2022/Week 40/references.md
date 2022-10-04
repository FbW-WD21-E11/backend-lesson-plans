---
title: Presenting - References
theme: 'league'
---

<!-- .slide: data-background="./assets/wallpaper.jpg" -->

# References

---

## We will cover:

- What are references?
- Creating references
- Populating references
- Differences between subdocuments & references

---

## What are references?

---

Unlike subdocuments, references are links to data in other collections

The schema is not embedded - it is linked via the **_id**

> This is similar to an SQL `JOIN`

---

## Creating references

---

```javascript
const questionSchema = new mongoose.Schema({
    question: { type: String, required: true },
    answers: { type: [String], required: true }
});

const quizSchema = new mongoose.Schema({
    name: String,
    questions: [{
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Question'
    }]
});

const QuizModel = mongoose.model('Quiz', quizSchema);
const QuestionModel = mongoose.model('Question', questionSchema);
```

---

## Populating references

---

In the previous example, if we were to query the data from the `QuizModel`, for the field `questions`, we would get an array of `_id`s

```javascript
[ '89f0dsiuf9s08u9324', '89f0dsiuf9s08u9325' ]
```

---

So how do we get the data?

We use the `populate()` method with our query

This will replace the `_id`s with the actual data

```javascript
[
    {
        question: 'How many students in FBW6?',
        answers: [ '20', '19', '10' ]
    },
    {
        question: 'What does the mongoose populate method do?',
        answers: [ 'It does nothing', 'It creates a person', 'None of the above' ]
    }
]
```

---

Example:

```javascript
const populated = await QuizModel.findById('4sad0983j4qe').populate('questions');
```

---

## Differences between subdocuments & references

---

1. Subdocuments might have a separate schema, but they do not have a model

2. Subdocuments do not have a separate collection

3. Subdocuments are embedded inside our document

4. Subdocuments are simpler to work with

5. References are linked to other collections

6. With references, we have a separate collection, which means we can use it in multiple places
