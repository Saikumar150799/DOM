# DOM ( Document Object Model )
In this section we will discuss about [Document Object Model(DOM)](https://www.geeksforgeeks.org/dom-document-object-model/) and it's methods.

<br>

<span style="font-size:20px">

### Content of this file

<span style="font-size:167x"></a>

- <a href='#dom'>What is DOM ?</a>

- <a href='#help'>How does it help ?</a>

- <a href='#access'>How to access it ?</a>

- <a href='#methods'>What are JS DOM Helper methods ?</a>
- <a href='#References'>References</a>

<br>

<h2 id='dom'>1. What is DOM ?</h2>

**DOM** <span style="font-size:18px">Stands for Document Object Model.

The Document Object Model ( DOM ) is a programming interface for **HTML**(HyperText Markup Language) and **XML**(Extensible markup language) document. 

The **DOM** represents the data in the form of structure called a tree. Every object in the DOM is hierarchically under another object,and any object can have multiple children but only one parent.

If  you remove an object from the DOM,all of it's children will also be removed with it.

**Example :** Representation by the html

![](https://www.tutorialstonight.com/assets/js/dom-tutorial.webp)

<br>

<h2 id='help'>2. How does it help ?</h2>

DOM helps to make any relevant changes in the webpage without having to change the actual web code or the corresponding HTML page. 

DOM helps the user access the tree model. Once the access is granted, the user can make any changes related to the composition, layout, content, or style of the HTML page[(Example)](https://www.w3schools.com/js/tryit.asp?filename=tryjs_myfirst).

 

<br>

<h2 id='access'>3. How to access it ?</h2>

We can access in many ways but the most three important are as follow. 

<span style="font-size:18px">

`Here is table overview of three methods.`

| Get               | Selector Syntax | Method                          |
| ------------------| --------------- | --------------------------------|
|  ID               | #demo           |document.getElementById()        |
|  Class            | .demo           |document.getElementsByClassName()|
|  Tag              |  demo           |document.getElementsByTagName()  |



<br>

**<h3>I. Accessing Elements By Id :</h3>**

The easiest way to access the a single element in **DOM** by its unique ***ID***.

***Syntax :***
```js
    document.getElementById();
```
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <p id="demo">Accessing the elements by ID</p>
        <script>
            accessById = document.getElementById("demo");
        </script>
    </body>
</html>
```
**Note** : Id should be unique.

<br>

**<h3>II. Accessing Elements By Class Name :</h3>**


The class attribute is used to access one *or* more elements in the **DOM**.

***Syntax :***
```js
    document.getElementsByClassName();
```
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <p class="demo">Accessing the elements by class</p>
        <script>
            accessByClass = document.getElementsByClassName("demo");
        </script>
    </body>
</html>
```

<br>

**<h3>III. Accessing Elements By Tag Name :</h3>**


We can also access element by ***Tag Name***.

***Syntax :***
```js
    document.getElementsByTagName();
```
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <p>Accessing by Tag Name</p>
        <script>
            getByTag = document.getElementsByTagName("p");
        </script>
    </body>
</html>
```

<br>


<h2 id='methods'>4. What are JS DOM Helper methods ?</h2>

***DOM  HELPERS :***

A few **DOM** helpers to assist with the transition from jQuery to vanilla JavaScript.


- <a href='#indexInParent'>indexInParent</a>
- <a href='#indexOfParent'>indexOfParent</a>
- <a href='#matches'>matches</a>
- <a href='#closest'>closest</a>
- <a href='#offset'>offset top</a>
- <a href='#next'>next</a>
- <a href='#prev'>prev</a>
- <a href='#siblings'>siblings</a>

<br>

**<h3 id='indexInParent'>1. indexInParent</h3>**
```js
    export function indexInParent(el) {
    let children = el.parentNode.childNodes;
    let num = 0;

    for (let i = 0; i < children.length; i++) {
        if (children[i] == el) return num;
        if (children[i].nodeType == 1) num++;
    }
    return -1;
}
```

**<h3 id='indexOfParent'>2. indexOfParent</h3>**
```js
    export function indexOfParent(el) {
    return [].indexOf.call(el.parentElement.children, el);
}
```
**<h3 id='matches'>3. matches</h3>**
```js
export function matches(elem, selector) {
    const isMsMatch = 'msMatchesSelector' in elem && elem.msMatchesSelector(selector);
    const isMatchSelector = 'matchesSelector' in elem && elem.matchesSelector(selector)
    const isMatch = 'matches' in elem && elem.matches(selector);
     
    return isMsMatch || isMatchSelector || isMatch;
}
```

**<h3 id='closest'>4. closest</h3>**

For each element in the set, get the first element that matches the selector by testing the element itself and traversing up through its ancestors in the DOM tree.
```js
export function getClosest(elem, selector) {
    for (; elem && elem !== document; elem = elem.parentNode) {
        if (matches(elem, selector)) {.
            return elem
        }
    }
    return null;
}
export const closest = getClosest;
```

**<h3 id='offset'>5. offset top</h3>**
```js
export function getOffsetTop(el) {
    let offsetTop = 0;
    do {
        if (!isNaN(el.offsetTop)) {
            offsetTop += el.offsetTop;
        }
    } while (el = el.offsetParent);
    return offsetTop;
}
```

**<h3 id='next'>6. next</h3>**

Get the immediately following sibling of each element in the set of matched elements.
```js
export function next(el, selector) {
    if (el.nextElementSibling) {
        if (matches(el.nextElementSibling, selector)) {
            return el.nextElementSibling;
        } else {
            return prev(el.nextElementSibling, selector);
        }
    }

    return false;
}
```
**<h3 id='prev'>7. prev</h3>**

Get the immediately preceding sibling of each element in the set of matched elements.

```js
export function prev(el, selector) {
    if (el.previousElementSibling) {
        if (matches(el.previousElementSibling, selector)) {
            return el.previousElementSibling;
        } else {
            return prev(el.previousElementSibling, selector);
        }
    }
    return false;
}
```

**<h3 id='siblings'>8. siblings**</h3>

Get the siblings of each element in the set of matched elements.

```js
export function siblings(el, selector) {
    return Array.prototype.filter.call(el.parentNode.children, function (child) {
        return matches(child, selector);
    }) || [];
}
```

<br>

 ***<h3 id='References'>For more information:</h3>***
 <br>

 **DOM**      
 
 >https://www.geeksforgeeks.org/dom-document-object-model/

**Accessing DOM**
>https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom

**JS DOM helper methods**
>https://dev.to/jimfrenette/javascript-document-object-dom-helpers-2911

