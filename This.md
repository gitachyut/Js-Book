# **This**   

- Callback function alaways run in context of window/global object  
- Fat arrow function don't have it's own `This` Context, so if `"use strict"` mode is off laxical 
scoping try to find the nearest `this`  
- `This` means the context, which function is runing.  
- How is the function is invoked that will give you `This`


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


var ps = function(){
    var msg = 'sdd'
    for(var i =0; i<= 10 ; i++){ ((i) => {
        setTimeout(function(){ console.log(i) },1000) })(i)
    }
} // // output ->  1,2,3,4,5,....,10






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
