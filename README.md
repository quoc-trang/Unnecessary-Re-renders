---
difficulty: 1
training: true
chapter: "Chapter 5: Best Practices"
tags: vue
---

# Fix the Unnecessary Re-renders

In this challenge, we're listing a bunch of people within a table. You can select a person by clicking on a table row. BUT whenever 1 person is selected, all the other rows are re-rendered needlessly.

Fix it, so that we only re-render the necessary rows (the newly selected and deselected).

> 💡 HINT: There is a console log on each component row whenever it re-renders.

## Requirements

1. Fix the bug causing all the rows to re-render whenever a single row is selected

![Screenshot of the solution](https://images.certificates.dev/csvd-training-code-challenge-16.gif)
