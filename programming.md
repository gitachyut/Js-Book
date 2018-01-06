- js is a signle thraded language and events are queued in the events loop, so if there is two cb method fire at same time you can't garantee to fire at the exect same time

- Dirty checking is the process by which html dom rerender 

- Netscape naviagtor was the 80% uses browser in 1990 - 1998 .. but 1995 netscape colaborated with sun microsystem to buid their next gen browser .. They decided to buid a new  scripting language for web browser which is initially known as mocha which is created by Brendan Eiche in 10 days .. for marketing 
causes they renamed the language to javascript .. At that same time microsoft was also creating their ie browser and they have also craeted new browser scripting language called jscript. Which leads to a problem for the developer to build a website which runs on every browser . they why ECMA come into the picture . Ecma international .. in 1996 Netscape give javscript language  to Ecma international to make the language spacification stanndared . 

standared 
  ecma 262
commitee 
  TC39

there exits 5 stages  0 to 4, stage 4 is the last stage for incliding a syntex to the ecmascript .. every year ecmascript relaeses a new version and stage 4 syntex are added to ecmascript the new version.



- __proto__ is the  object property to that  points to the prototype has been set 
-  prototype is set for function 



- `var` is a function scope variable and `let/const` is block scope variable `const` variables are immutables

- fat arrow function don't have `arguments` built in variable  and `this` context 

### Scope and Hoisting

```
test()

var t = function(){
  console.log('express')
}
t()
function test(){
  console.log('declaration')
}
console.log(x)

var x = 33

```


### Event Deligation

- if a event is attached to a dom element den it will fire to it's all child element

### Event Bubling

- event trigger child to parent

###  == and ===  
- == -> check for equality
- === -> check for equality and type 

```
let x = 4
let y = '4'
console.log(x==y) // true
console.log(x===y) // flase

```