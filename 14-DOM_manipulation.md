# RESUME JAVASCRIPT - DOM MANIPULATION


## **innerText**
The **innerText** property **sets or returns** the text content of the specified node, and all its descendants.  

If you set the innerText property, **any child nodes are removed and replaced by a single Text node** containing the specified string.

It's similar to **textContent** but textContent also captures the text of style and script tags.

```js
    document.getElementById('main').innerText = 'Hello World';
```


---
## **innerHTML**

**Returns** the html content of the specific node, with all its tags.  

**Sets** new tags and text.

```js
document.querySelector('ul').innerHTML = '<li> item one </li> <li> item two </li> <li> item three </li> ';
```

---
## **.value/.src/.checked/.href/data-...**
Properties and attributes that can be accessed in JavaScript.

Particular note for datasets. In HTML, put a property of data-*something* and access it on JavaScript with the property dataset. Ex:

```html
<p data-test="something"> This is a paragraph with a dataset </p>
```
```js
let element = document.querySelector('p').dataset.test;
```
---
## getAttribute() and setAttribute()
getAttribute() returns the value of the attribute passed as an argument. It's very similar to dataset in its functionality. But it can also take other attributes (src, checked, any other...).
```js
element.getAttribute('data-test');
```
setAttribute() takes two parameters. The attribute itself and its value
```js
element.setAttribute('nameOfTheAttribute, value');
```
---
## Select parents, siblings, children...

The main properties are :
- parentElement
- children
- nextElementSibling
- previousElementSibling

```html
<div>
    <ul>
        <li><a>anchor</a></li>
        <p>paragraph</p>
        <li><a>anchor</a></li>
        <li><a>anchor</a></li>
    </ul>
</div>
```
```js
let anchor = document.querySelector('a');
anchor.parentElement === li
anchor.parentElement.parentElement === ul
anchor.parentElement.parentElement.parentElement === div

anchor.parentElement.children === [li, p, li li]
```
The result of children is NOT an array. It's an HTML collection. It can be selected as an array but doesn't have the methods associated to arrays. We can perform a regular for loop to iterate them.

---

## STYLE attribute

Style attribute can be accessed with .style  
We can append to it any style. Ex:
```js
p.style.color = "#eaeaea"
```
Remember there is no dash (-) in JavaScript. It's camel case. background-color => backgroundColor

---

## Get Computed Styles
The notation .style can serve to set styles but only returns html inline styles.

To get computed styles instead (coming from a stylesheet for example), use the method getComputedStyle().

```js
let styles = getComputedStyle(li);
styles.color
styles.background
styles.margin etc...
```
---
## Manipulating classes

### **classList**

It returns a list of the classes in a particular element. It has different methods that can be used to manipulate classes:

- add
- remove
- toggle
- contains
- forEach
- and others...

there is also the property className. But classList is much more powerfull.

---

## Create elements and place them in the DOM.

Some properties/methods to create and place elements in the DOM :

- **createElement**(*element*)
- *parent*.**appendChild**(*element*)
- *parent*.**append**(*element*) - (can append multiple elements)
- *parent*.**prepend**(*element*) - (can prepend multiple elements)
- *parent*.**removeChild**(*element*)
- *element*.**remove**() - (remove itself)

```js
1. let newH2 = document.createElement('h2')
2. newH2.classList.add('special');
3. newH2.innerText = 'I am a heading h2';
4. document.body.appendChild(newH2);
```

```html
1. <h2></h2>
2. <h2 class="special"></h2>
3. <h2 class="special">I am a heading h2</h2>
4. (will appear at the end of the body tag)
```
---

# EVENTS


## **addEventListener()**

```js
element.addEventListener('click, function)
```

Passes an *event* parameter that holds all informations about the event

## keyup / keydown

will take **any** press of key (including CTRL, TAB etc.)

## keypress
will only take characters that were pressed. (changing the input)

## input
takes in real-time the changes of an input

## change
listens for any change in the selected property.

---

## FORMS event

Forms have a default behavior of submitting its values. It refreshes the page. Often, we want to prevent this default behavior in order to attach our own event listener and actions.

```js
    submit.addEventListener('click', function(e){
        e.preventDefault()
    })
```