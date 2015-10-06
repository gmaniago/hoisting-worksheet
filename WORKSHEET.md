# JavaScript Hoisting Worksheet

## Instructions
1. Review each code snippet below.
2. Fill in what will be output to the console.
3. Run the code to see if you were correct.
4. Describe why the code behaved as it did.
5. Re-write the code snippet to maintain the same output, but to avoid hoisting.

```js
var myvar = 'my value'; 
  
(function() { 
	console.log(myvar);
	var myvar = 'local value'; 
})();
```

> output:
>- undefined
>-
>-
> why?
>- Because the declaration myvar is being hoisted to the top, while the value is not.
>-
>-
>-
>-
>-
> rewrite without hoisting
>- var myvar = 'my value';
>-
>-function(){
>-	var myvar;
>-	console.log (myvar;
>-	myvar = 'local value';
>-}
>-
>-
>-
>-
>-

```js
var flag = true; 
  
function test() {
	if(flag) {
		var flag = false;
		console.log('Switch flag from true to false');
	}
	else {
		flag = true;
		console.log('Switch flag from false to true');
	}
}
test();
```

> output: switch flag from false to true
>-
>-
>-
> why?
>- Flag is being declared in the if with a value of false while in the else is has the value of true
>-
>-
>-
>-
>-
> rewrite without hoisting

var flag = true; 

  function test() {
  var flag;
    if(flag) {
        flag = false;
         console.log('Switch flag from true to false');
     }
    else {
         flag = true;
         console.log('Switch flag from false to true');
    }
}
 test();

```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	var message = 'Foo bar';
}
saySomething();
```

> output: undefined
>-
>-
>-
> why?
>- foo bar is being hoisted to the top w/o its definition
>-
>-
>-
>-
>-
> rewrite without hoisting
>-
var message = 'Hello world'; 

 function saySomething() {
 	var message;
    console.log(message);
    message = 'Foo bar';
}
saySomething();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	message = 'Foo bar';
}
saySomething();
```

> output: Hello World
>-
>-
>-
> why?
>-
>-
>-
>-
>-
>-


```js
function test() {
	console.log(a);
	console.log(foo());

	var a = 1;
	function foo() {
		return 2;
	}
}
 
test();
```

> output: undefined
>-
>-
>-
> why?
>-	"a" is being called before it is defined. It is being hoisted up without being defined
>-
>-
>-
>-
>-
> rewrite without hoisting
>-
>-function test() {
	var a =1;
    console.log(a);
    console.log(foo());

    function foo() {
        return 2;
    }
}

test();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
(function() {
	console.log(bar);
	foo();

	function foo() {
		console.log('aloha');
	}

	var bar = 1;
	baz = 2;
})();
```

> output: undefined and aloha
>-
>-
>-
> why? Function foo is being run while var bar is being hoisted without being defined. 
>-
>-
>-
>-
>-
>-
> rewrite without hoisting
>-
(function() {
   var bar = 1;
    console.log(bar);
    foo();

    function foo() {
        console.log('aloha');
    }

 
    baz = 2;
})();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var run = false;

function fancy(arg1, arg2) {
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	function run() {
		console.log('Will I run?');
	}
}
fancy();
```

> output: I can run
>-
>-
>-
> why?
>- function run is being hoisted to the top, while the if statement is elavuating the run and evaluate to true inside the if.
>-
>-
>-
>-
>-
> rewrite without hoisting
>-
>-var run = false;

function fancy(arg1, arg2) {
    if(run) {
        console.log('I can run');
    }
    else {
        console.log('I can\'t run');
    }

    var run = function() {
        console.log('Will I run?');
    }
}
fancy();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var run = false;

function fancy(arg1, arg2) {
    if(run) {
        console.log('I can run');
    }
    else {
        console.log('I can\'t run');
    }

    function run() {
        console.log('Will I run?');
    }
}
fancy();
```

> output: I can't run
>-
>-
>-
> why?
>- var run is being declared but not defined which elavuate to false. the else is only being run 
>-
>-
>-
>-
>-
> rewrite without hoisting
>-
var run = false;

function fancy(arg1, arg2) {
    if(run) {
        console.log('I can run');
    }
    else {
        console.log('I can\'t run');
    }

    var run = function() {
        console.log('Will I run?');
    }
}
fancy();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-