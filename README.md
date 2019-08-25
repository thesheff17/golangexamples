<p align="center">
  <img width="400" height="200" src="https://golang.org/lib/godoc/images/footer-gopher.jpg">
</p>

# golang examples/tutorials

## more information can be found at [golang](https://golang.org) website.

### I will add tons of examples that progressively get more complicated.  I will also store examples of features of the standard library in these examples.  If you see any issues with anything please make a pull request.

### each example will be seperated by a line seperator like below:

***

### table of contents
- [prerequisites](#prerequisites)
- [hello world](#hello-world)
- [time package](#time-package)
- [gofmt command](#gofmt-command)
- [golang documentation](#golang-documentation)
- [golang comments](#golang-comments)
- [assign values to variables and declaring variables](#assign-values-to-variables-and-declaring-variables)
- [golang basic data types](#golang-basic-data-types)
- [concatenation](#concatenation)
- [first function](#first-function)
- [function return types](#function-return-types)
- [int examples](#int-examples)
- [float64 examples](#float64-examples)
- [if statments](#if-statments)
- [for statement](#for-statements)

***

### prerequisites
The first thing you need to do is install go.  This is a little different per operating system.  First download your perspective file from [here.](https://golang.org/dl/) Follow the installation instruction [here.](https://golang.org/doc/install) 

You should be able to check which version of go you are version by running:

```
go version
go version go1.12.9 darwin/amd64
```

You will also need a decent text editor/IDE.  There are a number of free ones:

- [vscode](https://code.visualstudio.com/)
- [atom](https://atom.io/)
- [notepad++](https://notepad-plus-plus.org/) windows only

if you have the money I would recommend some paid text editors/IDE:

- [sublime text](https://www.sublimetext.com/)
- [GoLand](https://www.jetbrains.com/go/)

### hello world
[1]: abc
```
package main
import "fmt"

func main() {
    fmt.Println("hello world")
}
```

#### to run this script
Save the above code snipet as main.go in a directory you created. I usually make a directory called `golang`

to compile your script:

````
go build
````

This will produce a binary for the operating system you are on. Mac/linux will create a binary with the name of the directory you are in.  The directory I'm in was `golang`

To run on linux/mac:

```
./golang
```

To run on windows:

```
golang.exe
```

You can also run this code on the [go playground.](https://play.golang.org/p/NrLk9EUk4Hs)  This way you don't have to install anything and test basic golang examples.  Be careful not to put any sesitive data into this site though.  
***

### time package
This example will show you how to sleep a certain amount of time.
 
```
package main

import (
	"fmt"
	"time"
)

func main() {
	fmt.Println("start of script.")
	fmt.Println("sleeping 3 seconds...")
	time.Sleep(3 * time.Second)
	fmt.Println("sleep time completed.")

}
```

output:

```
start of script.
sleeping 3 seconds...
sleep time completed.
```
***
### gofmt command
go supports auto formatting of your code.  This is supper useful if you have ever used another programming language like python.  More information can be found [here.](https://golang.org/cmd/gofmt/)

to see what gofmt will do to your file do and it will display your code formatted.

```
gofmt ./main.go
```

if you want it to overwrite your file with the changes do:

```
gofmt -w ./main.go
```
Most of the text editors recommended have built in gofmt tools that will do this automatically when saving the file.

***

### golang documenation
golang documentation can be found [here.](https://golang.org/pkg/)

if you have a slow internet or no internet at all you can still view all of golang website/documentation.  This command will run a local web server with the same website you see at golang.org

```
godoc -http=:6060
```

Once you run this command you will be able to visit: [http://localhost:6060](http://localhost:6060)

****

### golang comments
comments are texted inside a script that help explain complex code.  The compiler will skip these lines and provide context to the code you are running:

```
package main

import (
	"fmt"
)

func main() {
	// comments start with two forward slashes

	// example of using fmt.Println package
	fmt.Println("Hello World")

	// you can also do inline comments
	fmt.Println("Welcome to golang!") // prints Welcome to golang!

	// you can also do big blocks of comments using the below:

	/*

		example of comments spanning multiple lines.
		this starts with a forward slash and a *.
		once you are done you can stop comments using * forward slash

	*/

	fmt.Println("script completed")

}
```
output:

```
Hello World
Welcome to golang!
script completed
```

### assign values to variables and declaring variables
variables will store data you need to use in more then one place.  For example if you needed your program to say `hello world` twice this is how you would do it. `hello` is assigned "hello world". 

```
package main

import "fmt"

func main() {
        hello := "hello world"
        fmt.Println(hello)
        fmt.Println(hello)
}
```

If you don't know the value you want but know you need a variable later on you can also declare it.  The next section will go into data types and explain what a `string` is.

```
package main

import "fmt"

func main() {
        var name string

        fmt.Println("hello world")

        name = "Dan" //asign "Dan" to the name variable
        fmt.Println("hello " + name)
        name = "Bob"
        fmt.Println("hello " + name)
}

```

output:

```
hello world
hello Dan
hello Bob
```

### golang basic data types
golang has a number of basic data types.  The most common ones used are int, string, bool, byte, & float64.  There are more then just these but these are the ones I use the most.  More information can be located [here.](https://tour.golang.org/basics/11)  

- string - is traditionally a sequence of characters for example  `hello world` is a string in the above examples.
- int - (integer for short) a number that is not a dceimal.  Can support negative numbers.  Examples: `5` `-10`
- bool - represents a boolean value.  It can be `false` or `true` values.
- byte - is a computer repsrentation of data.  More examples will be used in future examples.
- float64 - a decimal number.  Can support negative numbers as well example: `1.0` `5.5`

### concatenation

This is the ability to output multiple variables in a single statement. the `%s` will be replaced with the variables you pass to it:

```
package main

import "fmt"

func main() {
        fname := "Dan"
        lname := "Sheffner"

        fmt.Printf("Welcome to golang %s %s\n", fname, lname)
}
```
output:

```
Welcome to golang Dan Sheffner
```

We use `\n` to do a line break.  

### first function
a function is a collecton of code that you can re use many times.  You can call it from other parts of your code to do things.  This will help you organize your code better.  functions can take any number of parameters.  We will talk about return in the next section.

```
package main

import "fmt"

func hello(fname string, lname string) {
        fmt.Printf("Welcome to golang %s %s\n", fname, lname)
}

func main() {
        fname1 := "Dan"
        lname1 := "Sheffner"

        fname2 := "Bob"
        lname2 := "Sheffner"

        hello(fname1, lname1)
        hello(fname2, lname2)
}
```

output:

```
Welcome to golang Dan Sheffner
Welcome to golang Bob Sheffner
```

There is 1 thing to type less things if yo know your data types are the same.  This will assume both fname and lname are both `string` types.

```
package main

import "fmt"

func hello(fname, lname string) {
        fmt.Printf("Welcome to golang %s %s\n", fname, lname)
}

func main() {
        fname1 := "Dan"
        lname1 := "Sheffner"

        fname2 := "Bob"
        lname2 := "Sheffner"

        hello(fname1, lname1)
        hello(fname2, lname2)
}
```

### function return types
functions can return data types as well.  A variation of the example above:

```
package main

import "fmt"

func hello(fname, lname string) string {
        fullname := "Welcome to golang " + fname + " " + lname
        return fullname
}

func main() {
        fname1 := "Dan"
        lname1 := "Sheffner"

        fname2 := "Bob"
        lname2 := "Sheffner"

        output1 := hello(fname1, lname1)
        output2 := hello(fname2, lname2)

        fmt.Println(output1)
        fmt.Println(output2)
        fmt.Println(hello("Steve", "Smith"))

}
```

output:

```
Welcome to golang Dan Sheffner
Welcome to golang Bob Sheffner
Welcome to golang Steve Smith
```


### int examples
for this example we will write a function that calculates the perimeter of a triangle.  Basically `a + b + c = perimeter` use `%d` in `fmt.Printf` in order to convert from int to string. 

```
package main

import "fmt"

func perimeter(a, b, c int) {
        per := a + b + c
        fmt.Printf("The perimeter is %d\n", per)
}

func main() {
        perimeter(5, 5, 5)
        perimeter(10, 10, 10)

}
```

output:

```
The perimeter is 15
The perimeter is 30
```

### float64 examples
in this example we will calculate the area of a circle:

```
package main

import "fmt"

func areaofcircle(a float64) {
        pi := 3.14
        area := a * a * pi

        fmt.Printf("The area of the circle is %f\n", area)
}

func main() {
        areaofcircle(4.0)
        areaofcircle(5.0)

}
```
output:

```
The area of the circle is 50.240000
The area of the circle is 78.500000
```

### if statments
an example of a function that will tell you if the integer is odd or even:

```
package main

import (
	"fmt"
)

func oddevencheck(value int) {

	if value%2 == 0 {
		fmt.Printf("%d is even\n", value)
	} else {
		fmt.Printf("%d is odd\n", value)
	}
}

func main() {
	oddevencheck(2)
	oddevencheck(5)
	oddevencheck(10)
}
```
output:

```
2 is even
5 is odd
10 is even
```

### for statements
if we wanted to loop through 1 through 10 and add them all up.  

```
package main

import (
	"fmt"
)

func firstloop() {
	sum := 0
	for i := 1; i <= 10; i++ {
		sum += i
	}
	fmt.Println(sum)
}
func main() {
	firstloop()
}

```
output:

```
55
```
