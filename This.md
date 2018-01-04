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

```

```

