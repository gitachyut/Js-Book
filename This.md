# **This**   

- Callback function alaways run in context of window/global object  
- Fat arrow function don't have it's own `This` Context, so if `"use strict"` mode is off laxical 
scoping try to find the nearest `this`  
- `This` means the context, which function is runing.  
- How is the function is invoked that will give you `This`


### There is two default arguments to every function call - This and arguments

### Context   

```
const obj= {
  name : 'Achyut',
  sayName : function(){
    console.log(this.name)
  }
}
const fn = obj.sayName // This will give you a function 
fn() 
// undefine, cause fn() === window.fn() || fn() === global.fn() , 
// window or global don't have any name property 


var x = {
  a:function(){return 1},
  b:function(){ console.log(this) 
          return this.a()
  },
  c:function(){
    setTimeout(function(){
      console.log(this.a()) 
      return this.a()
    }.bind(this),200)
  }
}



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

----------






var x = 1;
var foo = {
  x:2,
  bar: function() {
    x = 3;
    return this.x;
  }
}
var run = foo.bar;

run() // 3

```

### Clouser and variable Scoping

```



var ps = function(){
    var msg = 'sdd'
    for(var i =0; i<= 10 ; i++){
        setTimeout(function(){ console.log(i) },1000)
    }
}
ps() // output -> 11


var ps = function(){
    var msg = 'sdd'
    for(let i =0; i<= 10 ; i++){
        setTimeout(function(){ console.log(i) },1000)
    }
}
ps() // output ->  1,2,3,4,5,....,10



var ps = function(){
    var msg = 'sdd'
    for(let i =0; i<= 10 ; i++){
       
        setTimeout(function(){ "use strict"
         console.log(i) },1000)
    }
}

'let' is block scoped, in that you are creating a scope for 'i' in the for loop, like  'for(..) {..}', the { } is the block that is the scope for 'i'. this is only half the solution.
The other half is that let works in a special way for 'for loops'. Along with block scoping, 'let' also rebinds 'i' to the body { } of the for loop at each iteration, updating it from the value of the previous iteration. In other words, you can think of it as a  new block scope being created along with updated 'i' for every iteration! And of course, you can exercise closure on those scopes.


var ps = function(){
    var msg = 'sdd'
    for(var i =0; i<= 10 ; i++){ ((i) => {
        setTimeout(function(){ console.log(i) },1000) })(i)
    }
} // // output ->  1,2,3,4,5,....,10

```


## Obj Creation Patterns

### Fectory Pattern  
```
function fectory(name,age){
  let newObj = {}
  newObj.name = name
  newObj.age = age 
  return newObj
}
var obj = fectory('achyut',22)

```
### Constructor Pattern

```
function constructorPattern(name,age){
  this.name = name
  this.age = age 
  this.sayname = function(){
    return this.name
  }
  return this
}
var obj = new constructorPattern('achyut',22)

```

### Prototype Pattern

```
function Ppf(name,age){
    this.name = name
    this.age = age 
}

Ppf.prototype.sayname = function(){
    return this.name
}

```




### Prototype Chain and inheritence  

```
function Parent(a,b){
  this.a = a
  this.b = b
}
Parent.prototype.callAB = function(){
  return `${this.a} uu, ${this.b}` 
}

Parent.prototype.diff = function(){
  return Math.abs(this.a - this.b)
}

function Child(a,b){
	Parent.call(this,a,b)
}

Child.prototype = Object.create(Parent.prototype,{
  otherThing : {
    value : function(){
      console.log('do some thing else')
    }
  }
})
Child.prototype.constructor = Child;

Child.prototype.noha = function(){
  return 'noha'
}


```



```
const module1 = (()=>{
  function mod(){
    
  }
  mod.prototype.name = function(){
    return 'module 1'
  }
  mod.prototype.hello = function(){
    return 'hello'
  }
  return {
    mod:mod
  }
})()

const module2 = (()=>{
  
  function mod(){
    module1.mod.call(this)
  }

  mod.prototype = Object.create(module1.mod.prototype)
  mod.prototype.constructor = mod
  
  mod.prototype.name = function(){
   	return 'module 2'
  }
  mod.prototype.other = function(){
   	return 'module 2 other'
  }
  return {
    mod:mod
  }
})()

```

```

const module1 = (()=>{
  function mod(){
    
  }
  var test = function(){
    return 33
  }
  
  mod.prototype.name = function(){
    return test()
  }
  mod.prototype.hello = function(){
    return 'hello'
  }
  return mod
})()
var m1 = new module1()

```


### Clouser 

- Clouser is the way by which js access it's parent scope, even after the parent function has closed

