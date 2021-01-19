Domain Modeling

From the Duckett HTML book:

Chapter 6: “Tables” (pp.126-145)
From the Duckett JS Book:

Chapter 3: “Functions, Methods, and Objects” (pp.106-144)

## Domain Modeling
Domain modeling is the process of creating a conceptual model in code for a specific problem. A model describes the various entities, their attributes and behaviors, as well as the constraints that govern the problem domain. An entity that stores data in properties and encapsulates behaviors in methods is commonly referred to as an object-oriented model.

A domain model that's articulated well can verify and validate the understanding of a specific problem among various stakeholders. As a communication tool, it defines a vocabulary that can be used within and between both technical and business teams.


## Summary
Domain modeling is the process of creating a conceptual model for a specific problem. And a domain model that's articulated well can verify and validate your understanding of that problem.

Here's some tips to follow when building your own domain models.

1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.
2. Model its attributes with a constructor function that defines and initializes properties.
3. Model its behaviors with small methods that focus on doing one job well.
4. Create instances using the `new` keyword followed by a call to a constructor function.
5. Store the newly created object in a variable so you can access its properties and methods from outside.
6. Use the `this` variable within methods so you can access the object's properties and methods from inside.


# Tables

## What's a table?
A table represents information in a grid format. Examples of tables include financial reports, TV schedules and sports results.

- Grids allows us to inderstand complex data by referencing information on tow axes.
- Each block in the grid is referred to as a **table cell**. In HTML a table is written out row by row.


## Basic Table Structure 
```html
<table>
    <tr>
        <td> Grid </td>
        <td> Grid </td>
        <td> Grid </td>
    </tr>
    <tr>
        <td> Grid </td>
        <td> Grid </td>
        <td> Grid </td>
    </tr>
    <tr>
        <td> Grid </td>
        <td> Grid </td>
        <td> Grid </td>
    </tr>
</table>
```


Syntax | Definition
:---: | :---:
`<table>` | The `<table>` element is used to create a table. The contents of the table are written out row by row
`<tr>` | You indicate the start of each row using the opening `<tr>` tag.
`<td>` | Each cell of a table is represented using a `<td>` element
`<th>` | The `<th>` element is used just like the `<td>` element but its purpose is to represent the heading for either a column or a row.
`span` | Stretching the colum across more than one column. The colspan attribute can be used on a `<th>` or `<td>` element and indicatea how many columns that cell should run across
`<thead>` | The headings of the table should sit inside the `<thead>` element
`<tbody>` | the body should sit inside the `<tbody>` element
`<tfoot>` | The foorer belongs inside the `<tfoot>` element.

There are three gropus of built-in objects:

- Browser Object Model - creates a model of the browser tab or window.
- Document Object Model - The DOM creates a model of the current web page.
- Global JavaScript Objects - The global objects do not form a single model. They are a group of individual objects that relate to different parts of the JS language.