# **This**   

- Callback function alaways run in context of window/global object  
- Fat arrow function don't have it's own `This` Context, so if `"use strict"` mode is off laxical 
scoping try to find the nearest `this`  
- `This` means the context, which function is runing.  
- How is the function is invoked that will give you `This`


# Code   

```
const obj= {
  name : 'Achyut',
  sayName : function(){
    console.log(this.name)
  }
}
const fn = obj.sayName // This will give you a function 
fn() // undefine, cause fn() === window.fn() || fn() === global.fn() , window or global don't have any name property 

```  

### Every function has its own `this` context  
```
const obj = {
  id : 2,
  renderId : function(){
    setTimeout(function(){
      console.log(this.id)
    },1000)
  }
}
- output undefine
------------

const obj = {
  id : 2,
  renderId : function(){
    setTimeout(function(){
      console.log(this.id)
    }.bind(this),1000)
  }
}
- output 2
--------


const obj = {
  id : 2,
  renderId : function(){
    setTimeout(() => {
      console.log(this.id)
    },1000)
  }
}


```

### Clouser and variable Scoping

```
var ps = function(){
    var msg = 'sdd'
    for(let i =0; i<= 10 ; i++){
        setTimeout(function(){ console.log(i) },1000)
    }
}
ps() // output ->  1,2,3,4,5,....,10

var ps = function(){
    var msg = 'sdd'
    for(var i =0; i<= 10 ; i++){
        setTimeout(function(){ console.log(i) },1000)
    }
}
ps() // output -> 11


```
