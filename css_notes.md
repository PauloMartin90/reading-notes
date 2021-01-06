# CSS Notes

## Unviersal Selector	
> Applies to all element in the document	

 | Syntax           | Usage                              | 
 | ---------------- | ---------------------------------- |
 | * {}             | Targets all elements on the page   |

## Type Selector
> Matches element names											


 | Syntax           | Usage                              | 
 | ---------------- | ---------------------------------- |
| h1, h2, h3 {} | Targets thes <h_1>, <h_2> and <h_3> elements |

## Class Selector			
> Matches and element whose class atributes has a value tht matches the one specified after the pound (or full stop) symbol 
 
 | Syntax           | Usage                              | 
 | ---------------- | ---------------------------------- |
 | .note {} |  Targets any element whose class attribute has a value of note |
 | p.note {} | Targets only <p> elements whose class attribute has a value of note |

## ID Selector
> Matches and element whose id attribute has a value that matches the one specified after the pound or hash symbol

| Syntax | Usage |
| :--- | :---: |
| #introductions {} | Targets the element whose id attributes has a value of introduction |

## Child Selector
> Matches an element that is a direct child of another

| Syntax | Usage |
| :--- | :---: |
| li>a {}		| Targets andy <a> elements that sit inside a <p> elemet, even if there are other elements nested betweem them |


## Descendant Selector
> Matches and element that is a a descenedant of another specified element (Not Just a direct child of that element)


| Syntax | Usage |
| :--- | :---: |
| p a {} | Targets any <a> element that sits inside a <p> element, even if there are other elements nested between them
 
 
## Adjancent Sibiling Selector
> Matches an element that is the next sibling of another

| Syntax | Usage |
| :--- | :---: |
| h_1+p {} | Targets the <p> element after any <h_1> element (but not other <p> element)
 
 
 ## General Sibiling Selector
 > Matches an element that is a sibling of another, although it does not have to be the directly preceding element 
 
| Syntax | Usage |
| :--- | :---: |
 | h_1~p {} | If you had two <p> elements that are siblings of an <h_1> element, this rule would apply to both |
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
