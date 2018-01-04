# **This**   
- Callback function alaways run in context of window/global object  
- Fat arrow function don't have it's own `This` Context, so if `"use strict"` mode is off laxical 
scoping try to find the nearest `this`  
- `This` means the context, which function is runing.  
- How is the function is invoked that will give you `This`