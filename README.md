# Risico Indicator
> Vue.js code based project
***
<br>

## Introduction
***
For this project we have to improve the Jeugdhulp Risico indicator(jri) app. This web app was built for the social workers to calculate the chance of the youth of being placed into a foster care. The actual app right work but isnt easy to navigate through. Click in the [link](http://174.138.1.153/kindveiligthuis) for the web app. We have to change this app by the framework of our choice to make it easier for the social worker to fill in the data.
<br>

### The proces
The proces for this project has been very frustrating i dont go in to much detail here. For the whole story of how it went click on this [link](https://locnguyen.gitbook.io/vue-project/)
NOTE: the proces in the link is written in dutch!
<br>

### How did i learned Vue
***
My usual best practice for a project is by first learning everything then applying what i have learned on the project. So i have watched over 3 courses of Vue from diffrent sources. The sources are from Youtube.com and lynda.com. The actual courses i have used  can be found below with the links attached so you can check them out by yourself.

**Source links:**
<br>
Youtube NetNinja:
<br>
*Link courses: [Vue Beginners course by NetNinja](https://www.youtube.com/watch?v=5LYrN_cAJoA&list=PL4cUxeGkcC9gQcYgjhBoeQH7wiAyZNrYa)*

Youtube Acedemind:
<br>
*Link courses: [Vue Getting Started courses by Acedemind](https://www.youtube.com/watch?v=nyJSd6V2DRI&list=PL55RiY5tL51p-YU-Uw90qQH419BM4Iz07)*

Lynda Vue:
<br>
*Link courses: [Learning Vue.js(2017)](https://www.lynda.com/JavaScript-tutorials/Welcome/562924/594465-4.html?srchtrk=index%3a2%0alinktypeid%3a2%0aq%3avue.js%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2)*

I have watched all the courses to expand my basic knowledge about Vue and seeing diffrent people explaining the basics. Because everyone codes in their own way and i wanted to see how these people explain the Vue basics diffrently.
<br>

### What should i have done diffrently?
***
I have completed and watched a lot of courses first before applying it to my project. That was a huge mistake, because before i finished the course i forgot what the instructor explained in the first few chapters so i have to rewatch those chapters. That took up a whole lot of time. The second problem with this approach of first learning all than applying is that i also have to rewatch some parts because i forgot how it acutally works and how it benifits my project. So what i will definitly do diffrent next time is applying the knowledge right away when i learn something in the world of coding. **You will learn more by practicing than learning!**
<br>

### What have i learned about Vue?
***
I have learned a lot of how the Vue framework works and the syntaxes that Vue uses. In this chapter im gonna describe all the synthaxes i have learned about Vue and how Vue works.

**How Vue works**<br>
Vue works with diffrent components that will load in the page that you declare it to load. That gives us the ability to separate the diffrent components in diffrent files. Each component has template tag with only **one root element** more elements gives an error. Each components also have their own styling and script tag. In the script tag we can export our vue instance(see below for the explaination of vue instance) to the template to make use of the data in the components. In the templates (which represents the html element) we can use the vue syntaxes to use some javascript in the html document to take control over the lay out. Because we can use javascript in the template we can load in the elements dynamicly.

**_Diffrence between vue in js file and vue cli packages_**<br>
At first i thought the vue syntaxes are everywhere the same. But there are actually some diffrenence between the synthax depending in the way you wanna use the vue framework. The first big diffrence is that you declare your components diffrently _(see the section Vue components for more detail)_. The other diffrence is in the instances of the Vue the way you write them is a little bit diffrent _(see the section Vue instances for more detail)_

<br>

**_Vue components_**<br>
The components are the diffrent parts of the website which we can declare everywhere we want. The components in this project are all declared in the main.js file. We import in our main.js file the diffrent vue files and than make components of them. If you use vue in a js file instead of vue file you have to declare the components diffrently. _See below what the syntaxes are for importing vue files and making components of them_

Through vue cli .vue files
``` js
// _____Js_____
// import the title.vue as Title
import Title from './titel.vue';

// making vue component with the name off app-title from Title
Vue.component('app-title', Title);

```


Through .js files:<br>
Instead of using the whole document as template and properties you have to write the whole template in the component as one object
``` js
// _____Js_____
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

```


``` html
<!-- _____Html_____ -->
 <!-- now we can use the component in every other vue file by declaring as a basic html tag -->
<app-title> </app-title>
```
<br>


**_Vue instances_**
<br>
A Vue instance is an object with the properties data, methods, and even compontents(if you use them). In this object we can save data and hold functions. We can reference to this data and function in our html file or our template. _See below for more information of how Vue instances work_


Through basic js file you have to use the vue instance like below
``` js
// _____Js_____
// We create first a Vue instance(object) and put it in a variable. NOTE: Its slightly diffrenct synthax if we use this in vue cli packages
var app = new Vue({
  el: '#app', // Target the element so that the element can make use of the vue object properties
  data: { // we put our data in between this curly braces
    message: 'Hello Vue.js!' // In the variable message there is a string stored we can use this variable in the #app-5 element now
  },
  methods: { // Here are the functions stored
    reverseMessage: function () { // We can use the reverseMessage function in our #app-5 element now
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```

If you use a vue package or you make use of vue files you have to write your instances like below:
``` js
// _____Vue_____
export default { // as you can see its exactly the same but you dont declare in which element you want to put it in
  data() {
    return{
      message: "test"
    }
  },
  methods:{
    testFunction: function(){
      return "just a test"
    }
  }
}
```
<br>


**_{{Mustache}}_**
<br>
You can use the data in the vue instances and print out the value in the data by using the mustache declaration by putting the property name in between the mustache symbol. _See below for more information of how Vue instances work_


Through basic js file you have to use the vue instance like below
``` html
<!-- _____Html_____ -->
<div>
  {{propertyData}}
</div>
```
<br>


**_v-html_**
<br>
Just like the mustache synthax the v-html prints out the value of a property from the vue instance. The big diffrence between those two is that the v-html doesnt print the value as a string but as an actual html synthax. This allows use legit html codes that are stored in the data property. _See below for more information of how Vue instances work_


Through basic js file you have to use the vue instance like below
``` html
<!-- _____Html_____ -->
<div id="app">
  <p v-html="Testing"></p>
</div>
```
``` js
<!-- _____js_____ -->
var app = new Vue({
  el: '#app',
  data: {
    testing: <span>a legit html</span> // because in the html we call it as a v-html it doesnt show the span tag
  }
})
```
<br>


**_v-if_**
<br>
A v-if is declared in the template self or in the html document (it depends on if you make use of the vue cli or templates to make your vue file). The v-if syntax allows us to use if statements in the html document itself so that _See below for more information of the v-if synthax_

``` html
<!-- _____Html_____ -->
<div id="app">
   <span v-if="seen">Now you see me</span><!-- Span berichtje word weergeven als seen op true staat anders niet -->
</div>
```
``` js
// _____Js_____
var app3 = new Vue({
  el: '#app',
  data: {
    seen: true // staat op true dus de element in het html document word weergeven
  }
})
```
<br>


**_v-for_**
<br>
You can use for loops in the html document by declaring just like the v-if a v-for in the html element. The v-for uses just like v-if also data from the vue intance, but instead of using one string or number it is normally used with a array data _See below for more information of the v-for synthax_

``` html
<!-- _____Html_____ -->
<div id="app">
  <ol>
    <li v-for="todo in todos"> <!--The v-for syntax creates a new variable to loop through the todos array  -->
      {{ todo.text }} <!-- The newly made variable is used to loop through and print out the value in the text property for each iteration -->
   </li>
 </ol>
</div>
```
``` js
// _____Js_____
var app = new Vue({
  el: '#app',
  data: {
    todos: [ // Array
      { text: 'Learn JavaScript' }, // property name text with a value stored in it
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
```

**_{{Mustache}}_**
<br>
You can use the data in the vue instances and print out the value in the data by using the mustache declaration by putting the property name in between the mustache symbol. _See below for more information of how Vue instances work_


Through basic js file you have to use the vue instance like below
``` html
<!-- _____Html_____ -->
<div>
  {{propertyData}}
</div>
```
<br>









***
<br>

### Build Setup
``` bash
# Open your command prompt
# navigate in your command promt to this folder
# CD ~this file

# type npm install to install the neccersary packages
npm install

# Type npm run dev to open this file the default browser
# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```
