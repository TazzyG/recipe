# Learning React

## Getting Started

1. a) Added Bootstrap library and created a project https://gist.github.com/Thomas-Smyth/006fd507a7295f17a8473451938f9935

1. b) Added FontAwesome library, add to index import 'font-awesome/css/font-awesome.css';

1. React snippets were installed on Explorer Editor, it has shortcuts for components. Add a components folder, if one is not added already

## Components

3. Create a file in our case file_name.jsx in camel notation (first lowercase, if 2+ words uppercase)
   imrc (import react component), then cc (create class) Add name to your component to the class, it should copy to export default.
   You may or may not use state depending on how simple the component is.. for hello world, no state is used.

   We have an exported result that we can use.

4. in src/index.js import fileName from './components/file_name'; You will see it in the browser!

5. Per babel rules, jsx methods must have one parent element, so 2 elements side by side (e.g. h1 and button) so wrap it in a div.
   Also Remember to put () around the block after return.
   For a div that does nothing, we can use React.Fragment in place of div.

## Classes, Events, State

### Dynamic values.. Embedding Exressions (using state)

state = { object: value, object: value }
In div .. {this.state.object} or {can use any JavaScript in here e.g. 2 + 2 }

add methods such as
formatCount() {
const {count} = this.state;
return count === 0 ? <h1> Zero </h1> : count;
}

### Set attributes

In state add a property such as this cool one. imageUrl: 'https://picsum.photos/200'
which would be <img src={this.state.imageUrl} alt = ""/>

className = "badge badge-primary" can use bootstrap classes
Not best practice but can add style
Separate from State, add
styles = {
fontSize: 10;
color: black;
}
<span style = {this.styles} ....> </span>
or <span style = {{ fontSize: 30} ...> </span >

### Rendering Classes Dynamically

Use case, change colors as warnings, etc.
Example
render () {
let classes = "badge m-2 badge-";
classes += (this.state.count === 0) ? "warning" : "badge-primary";
return (

<div>.classe
<span className = {classes}> </span>
</div>
);
}

Refactor! move this method by using a shortcut command r
It should appear as this

getBachClasses() {
let classes = "badge m-2 badge-";
classes += (this.state.count === 0) ? "warning" : "badge-primary";
return classes;  
}
and className={this.getBadgeClasses()}....
Voila = Our first method!

### Render Lists, using Map method

<ul>
    {this.state.objects.map(tag => <li key= {object}>{object}</li>)
</ul>

Add a condition to be clever using if and else condition
e.g.
renderTags() {
if (this.state.tags.length === 0) return <p>There are no tags! </p>;
return <ul>{this.state.tags.map(tag => <li key={tag}> {tag} </li>)</ul> };
}

Add another condition using &&
e.g.
{this.state.tags.length === 0 && "Please create a new tag!"}... truthy keeps going, picks last operant
{this.renderTags()}
Both lines will render

### Events

onClick onKey etc.

1. Define a method.
   e.g.
   handleIncrement() {
   console.log('Increment Clicked')
   }

<button onClick={this.handleIncrement}>....

#### Access to State Property (this)

if called with an object, no problem
but if strict mode is enabled and a function outside the object is called, result is undefined.

Solve with constructor

#### Bind Method

constructor() {
super();
console.log("Constuctor", this);
or specifically..
this.handleIncrement = this.handleIncrement.find(this);

REFACTOR using arrow function, may not work in later versions of react, warning
handleIncrement = () => {
.....
}

### Updating State, Hold on, not so simple

Need to let react sync the DOM
We do not update the State Directly!

Use setState method

this.setSate({ count: this.sate.count + 1})

Under the hood: This is what happens

1. setState({...}) tells React state change
2. schedule call to render method (asynchnronous)
3. returns a new react element .. divs etc
4. new and old Doms are compared side by side, and only changes the updates, only elements that change... Clever!!!

### Passing Event Arguments as Parameter

.e.g pass the id of a product to a shopping list

1.  add product as input to handle increment
    handleIncrement = product => {...}

2.  Pass this in the onClick like so...
    onClick= { () => this.handleIncrement( {product})}  
    }

    ## Creating the Files

1) Head over to getBootstrap.com and grab a template
