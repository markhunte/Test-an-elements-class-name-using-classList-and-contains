There will be times when instead of using an elements ID, you will wish or need to use an elements class.

This could be  due to the inherent limitations of IDs,  in particular when using them with layouts or symbols.<br>

It may be because you need a way to groups a set of elements and:<br>
* influence them with css 
* access to iterate on that group of elements using code 
* testing if an element is of a particular class before you proceed.

An element can have more than one class name assigned to it. Where in contrast that same element can only have one ID.<br><br>
An Element can have the same class name as any other element.<br><br>
Class names do not have to be unique and limited to a single element, in contrast an ID must be unique and limited to a single element.




## Hype Element class

In Hype we can assign class names to an element via the identity inspector

 <img src="Test an elements class name using classList and contains.assets/foo1.jpg" alt="foo1" style="zoom:50%;" />



Hype elements already have a class name given to them by the app.<br>
This is not shown in hypes UI.

But you can see this element has been assigned the class name HYPE_element if you inspect the element.<br>

 <img src="Test an elements class name using classList and contains.assets/foo2.jpg" alt="foo2" style="zoom:67%;" />

You can also see the class name _foo_ we gave the element in the class name field in the _**identity inspector**_. <br>


### The <span style='color:darkblue'>classList</span> command

An Elements Class names are held in a list.  In code you access the class list with the ***classList*** command

```javascript
element.classList
```


The [classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)  will return a  [DOMTokenList](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList) collection of the class attributes with the class names as well as other things.

<img src="Test an elements class name using classList and contains.assets/foo3.jpg" alt="foo3" style="zoom:50%;" />



For our use in accessing the class names in the collection we treat this as we would an array.<br>

## Class Index

The class names get an index number in the collection.<br>
The index is the position number in the collection.<br>

When you add a class name to an hype element that elements class name will gain an index number. <br>
The index number will go up.<br>

The position of the class name will always remain in the same order.<br>
So the index should always be the same, unless a change is made to the class list like a class name is removed or a new class name is inserted between two existing class names.<br>

### Using the <span style='color:darkblue'>index</span> 

You can use the the index number ( position in the class list )<br>

If you give the element a class name in the identity inspector then its index number will be 1.<br>

So you can get the class name at position 1 with code like this<br>

```javascript
var theClass = element.classList[1] 
```

If you give the element more than one class via the  identity inspector, the index number for each will match the order in the ui.

<img src="Test an elements class name using classList and contains.assets/foo4.jpg" alt="foo4" style="zoom:50%;" />



  _foo_  will be index **1**, _foo2_ will be index  **2**  <br>

Using the code 

```javascript
var theClass = element.classList[2]
```

 --> _foo2_


_Note the index actually starts at 0 but the 0 position is always taken by the hype assigned class mentioned above_


### Using the <span style='color:darkblue'>contains</span>  command

You can directly test if the class list contains a class name.

```javascript
 if (element.classList.contains('foo')){ 
	 // - -  do stuff 
	 }
```


The **contain** command will only find whole words from the expression. It will not find **foo** in the class name _foo2_.