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
- [functions used in external packages](#functions-used-in-external-packages)
- [function return types](#function-return-types)
- [int examples](#int-examples)
- [float64 examples](#float64-examples)
- [example of default values of variables](#example-of-default-values-of-variables)
- [bool data type](#bool-data-type)
- [converting between data types](#converting-between-data-types)
- [if statments](#if-statments)
- [if else if statements](#if-else-if-statements)
- [for statements](#for-statements)
- [infinate loop or break on value](#infinate-loop-or-break-on-value)
- [named return values](#named-return-values)
- [constants](#constants)
- [check current user running program](#check-current-user-running-program)
- [arrays](#arrays)
- [slices](#slices)
- [maps](#maps)
- [pointers](#pointers)
- [calling a terminal command on linux](#calling-a-terminal-command-on-linux)
- [struct](#struct)

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

You can also run this code on the [go playground.](https://play.golang.org/p/NrLk9EUk4Hs)  This way you don't have to install anything and test basic golang examples.  Be careful not to put any sensitive data into this site though.  I will add `playground` links as much as possible to source code so you can also run it.  Not all examples will run in the playground.
***

### time package
This example will show you how to sleep a certain amount of time.

[playground](https://play.golang.org/p/M9H5iYfisQx)
 
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

[playground](https://play.golang.org/p/eGhmex1Pm1i)

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
variables will store data you need to use in more then one place.  For example if you needed your program to say `hello world` twice this is how you would do it. `hello` is assigned "hello world". There are 4 ways to declare variables in golang:

[playground](https://play.golang.org/p/YtE6UWyGW9H)

```
package main

import "fmt"

func main() {
	
	// creates an empty integer variabled called e
	var e int
	fmt.Println(e)
	
	// change the value to 5
	e = 5
	fmt.Println(e)
	fmt.Println()
	
	// declare a variable and assign it a value
	var a = "hello"
    	fmt.Println(a)
	fmt.Println(a)
	fmt.Println()
	
	// shorthand of the above
	hello := "hello world"
	fmt.Println(hello)
	fmt.Println(hello)
	fmt.Println()
	
	// multiple assignments in 1 line
	 var fname, lname string = "Dan", "Sheffner"
    	fmt.Println("Welcome to golang", fname, lname)
	fname = "Bob"
	fmt.Println("Welcome to golang", fname, lname)
	
}
```
output:

```
0
5

hello
hello

hello world
hello world

Welcome to golang Dan Sheffner
Welcome to golang Bob Sheffner
```

### golang basic data types
golang has a number of basic data types.  The most common ones used are int, string, bool, byte, & float64.  There are more then just these but these are the ones I use the most.  More information can be located [here.](https://tour.golang.org/basics/11)  

- string - is traditionally a sequence of characters for example  `hello world` is a string in the above examples.
- int - (integer for short) a number that is not a dceimal.  Can support negative numbers.  Examples: `5` `-10`
- bool - represents a boolean value.  It can be `false` or `true` values.
- byte - is a computer repsrentation of data.  More examples will be used in future examples.
- float64 - a decimal number.  Can support negative numbers as well example: `1.0` `5.5`

### concatenation

This gives you the ability to output multiple variables in a single statement in any order. the `%s` will be replaced with the variables you pass to it.  Printf is used for formatting strings in the order you want.  Println will print a new line and concatenate by adding spaces between all variables.

[playground](https://play.golang.org/p/VTLiVpBalQW)

```
package main

import "fmt"

func main() {
        fname := "Dan"
        lname := "Sheffner"

        fmt.Printf("%s %s welcomes you to golang!\n", fname, lname)
        fmt.Printf("Welcome to golang %s %s\n", fname, lname)
}
```
output:

```
Dan Sheffner welcomes you to golang!
Welcome to golang Dan Sheffner
```

We use `\n` to do a line break.  

### first function
a function is a collecton of code that you can re use many times.  You can call it from other parts of your code to do things.  This will help you organize your code better.  functions can take any number of parameters.  We will talk about return in the next section.

[playground](https://play.golang.org/p/MFk-3vkY_m6)

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

[playground](https://play.golang.org/p/ekLHwDeZYTc)

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
### functions used in external packages
You will notice that `fmt.Println` and `time.Second` both have upper case on the function name.  This is how golang support private/public functions.  If you declare an uppercase func name: `func Hello()` you can use this function in other scripts.  I will go into more details on how to write your own imports/packages later in the tutorial but this is why you see uppercase.

### function return types
functions can return data types as well.  A variation of the example above:

[playground](https://play.golang.org/p/kJ_Qp3_TUBP)

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

[playground](https://play.golang.org/p/mbKrBtoPFSJ)

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

[playground](https://play.golang.org/p/p4U6lUx1tcB)

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

### bool data type
bool has two values.  false or true.  here is another varient of our is this number even check.

[playground](https://play.golang.org/p/XCaWmd8pgr0)

```
package main

import "fmt"

func iseven(value int) bool {
	if value%2 == 0 {
		return true
	} else {
		return false
	}
}
func main() {

	// example of calling a func
	// without == check it is going to check if true
	if iseven(4) { // checks if boolean is True
		fmt.Println("4 is a even number")
	}

	if iseven(5) == false {
		fmt.Println("5 is not an even number")
	}
}
```
output:

```
4 is a even number
5 is not an even number
```

### example of default values of variables
if you declare a variable with no value golang will assign the default value.  Here is an example of different types we used above.

[playground](https://play.golang.org/p/xHZpM9Adde7)

```
package main

import "fmt"

func main() {
	var i int
	var f float64
	var b bool
	var s string
	fmt.Printf("The default value of int is: %v\n", i)
	fmt.Printf("The default value of float64: %v\n", f)
	fmt.Printf("The default value of bool is: %v\n", b)
	fmt.Printf("The default value of string is: %q\n", s)
}
```
output:

```
The default value of int is: 0
The default value of float64: 0
The default value of bool is: false
The default value of string is: ""
```

### converting between data types
golang supports conversion between data types. Many times you will get data in as a string and need to convert to an integer(int) or a float to do math on it.  This is very simple to do in allot of programming languages. In this example I will show you how to convert `string` to `float64`

[playground](https://play.golang.org/p/rjJE9RFHtpy)

```
package main

import (
	"fmt"
	"strconv"
	"log"
	"os"
)

func addBankValue(value1 string, value2 float64) float64 {
	f, err := strconv.ParseFloat(value1, 64)
	
	if err != nil {
		log.Fatal(err)
		os.Exit(1)
	}
	
	total := value2 + f
	return total
}
	
func main() {
	
	x := "5.50"
	
	// an example of formatting two decimal places.
	fmt.Printf("Your new total is: %.2f", addBankValue(x, 100.00))
	
}
```

output:

```
Your new total is: 105.50
```

### if statments
an example of a function that will tell you if the integer is odd or even:

[playground](https://play.golang.org/p/jtRLSZ2f3il)

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

### if else if statements
here is an example of providing more logic with an else if statement.  Here will check a temperature and tell you weather it is comfortable, cold, or hot:

[playground](https://play.golang.org/p/z5NJT7MYRv2)

```
package main

import (
	"fmt"
)

func temp(value int) {
	if value > 80 {
		fmt.Println("it is hot!")
	} else if value > 65 {
		fmt.Println("it is comfortable")
	} else {
		fmt.Println("it it cold!")
	}
}

func main() {
	temp(100)
	temp(50)
	temp(70)
	temp(80)
}

```
output:

```
it is hot!
it it cold!
it is comfortable
it is comfortable
``` 

### for statements
if we wanted to loop through 1 through 10 and add them all up.  

[playground](https://play.golang.org/p/9E2ncHlxrgK)

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

### infinate loop or break on value
Sometimes you want to loop forever.  Basically this is a program that will never end until you `ctrl-c` out of it. Many services are written like this.  Another area this is useful is to loop foverever but then `break` on some condition.  Also note the sleep time increases as x goes up.  You are also able to do `x++` to represent add `1` to `x` on each loop.

[playground](https://play.golang.org/p/A6_vD_DLcCg)

```
package main

import (
	"fmt"
	"time"
)

func main() {
	x := 1
	for {
		fmt.Println("sleeping for: ", x)
		time.Sleep(time.Duration(x) * time.Millisecond)
		x++
		if x > 30 {
			break
		}
	}
}
```

output:

```
sleeping for:  1
sleeping for:  2
sleeping for:  3
sleeping for:  4
sleeping for:  5
sleeping for:  6
sleeping for:  7
sleeping for:  8
sleeping for:  9
sleeping for:  10
sleeping for:  11
sleeping for:  12
sleeping for:  13
sleeping for:  14
sleeping for:  15
sleeping for:  16
sleeping for:  17
sleeping for:  18
sleeping for:  19
sleeping for:  20
sleeping for:  21
sleeping for:  22
sleeping for:  23
sleeping for:  24
sleeping for:  25
sleeping for:  26
sleeping for:  27
sleeping for:  28
sleeping for:  29
sleeping for:  30
```

### named return values
you can have just `return` at the end of your func which will automatically return the variables you define on the func line.  These are sometimes called a `naked` return

[playground](https://play.golang.org/p/26W5YGltTXV)

```
package main

import (
	"fmt"
)

// this function will add 10 to an x, y cordinate you pass it
// this is also called a naked return
func addToCoordinates(a, b int) (x, y int) {
	x = a + 10
	y = b + 10
	return
}

func main() {

	// we pass it 2 coordinates and we get two values back
	x, y := addToCoordinates(50, 40)
	fmt.Printf("The new X coordinate is: %v The new Y coordinate is: %v", x, y)
}
``` 

output:

```
The new X coordinate is: 60 The new Y coordinate is: 50
```

### constants
constants `const` are variables that never change. Constants can be used either inside `func()` or even outside `func()` which constrols the scope of the variable where it is accessible.  For example if we need my name in multiple func I can do this:

[playground](https://play.golang.org/p/MIGNvZiQ6st)

```
package main

import (
	"fmt"
)

const name = "Dan Sheffner"

func sayName() {
	fmt.Println("Welcome to golang", name)
}

func main() {
	sayName()
	fmt.Println("The program is completed", name)
}
```

output:

```
Welcome to golang Dan Sheffner
The program is completed Dan Sheffner
```

### check current user running program
lots of times I need a golang script to run as root.  Here is an example of how to check which user is running the script.  This also shows you how `user.Current()` returns two values.  the usr and the err.  I also check to see if there are any err before trying to use usr.  This is typical in many golang programs. More information can be located in the docs [here.](https://golang.org/pkg/os/user/#Current)

[playground](https://play.golang.org/p/Wy6_PcEaH9g)

```
package main

import (
	"fmt"
	"log"
	"os"
	"os/user"
)

func checkUser() {
	usr, err := user.Current()

	if err != nil {
		log.Fatal(err)
		os.Exit(1)
	}

	if usr.Username != "root" {
		fmt.Println("Sorry this script needs root access.")
		fmt.Println("Exiting...")
		os.Exit(2)
	} else {
		fmt.Println("You are running this script as root. congrats!")
	}

}

func main() {
	checkUser()
}
```
output: 

```
Sorry this script needs root access.
```

second output: This will also work with `sudo` 

```
You are running this script as root. congrats!

```

### arrays
arrays are a collection of data types in a single object.  You must know the length of the array that you want to create. Here is an example of an array of 3 slots.  Arrays start at location 0.  If you try to assign a value to the array and it doesn't have enough slots it will throw an error `invalid array index 3 (out of bounds for 3-element array)`

[playground](https://play.golang.org/p/b_UWknSmSqQ)

```
package main

import (
	"fmt"
)

func main() {
	var myarray [3]string
	myarray[0] = "Dan"
	myarray[1] = "Bob"
	myarray[2] = "Steve"

	for slot, value := range myarray {
		fmt.Printf("The slot is: %d The value is: %s\n", slot, value)
	}

}
```

output:

```
The slot is: 0 The value is: Dan
The slot is: 1 The value is: Bob
The slot is: 2 The value is: Steve
```

### slices
slices are like arrays but have dynamic lengths.  This way you can add any number of elements to the slice without actually knowing the actual length.

[playground](https://play.golang.org/p/PkFbiNfppMZ)


```
package main

import (
	"fmt"
)

func main() {

	// we created a slice that starts with 3 slots
	s := make([]string, 3)

	s[0] = "Dan"
	s[1] = "Bob"
	s[2] = "Steve"

	// check the length
	fmt.Println("len:", len(s))

	// check values
	fmt.Println(s)

	// now let append another value
	s = append(s, "Laura")

	// check the length
	fmt.Println("len:", len(s))

	// check values
	fmt.Println(s)

	// append mutiple values
	s = append(s, "Devin", "Carl")

	// check the length
	fmt.Println("len:", len(s))

	// check values
	fmt.Println(s)

	// slice support a subset of the slice
	// prints the 3rd and 4th slots.  Remember the slice starts at 0
	fmt.Println(s[2:4])

	//slices also support multi dementional
	twoD := make([][]int, 3)
	for i := 0; i < 3; i++ {
		innerLen := i + 1
		twoD[i] = make([]int, innerLen)
		for j := 0; j < innerLen; j++ {
			twoD[i][j] = i + j
		}
	}
	fmt.Println("2d: ", twoD)
}
```

output:

```
len: 3
[Dan Bob Steve]
len: 4
[Dan Bob Steve Laura]
len: 6
[Dan Bob Steve Laura Devin Carl]
[Steve Laura]
2d:  [[0] [1 2] [2 3 4]]
```

### maps
maps are key:value pairs similar to dictionaries in python.  These have super fast lookup performance and support any data type as the key:

[playground](https://play.golang.org/p/7_sLAXp9roP)

```
package main

import (
	"fmt"
)

func main() {

	// example of creating a map
	m := make(map[string]float64)
	
	// for example if we want to keep track of bank account values.
	 m["Dan"] = 2.0
	 m["Steve"] = 100.0
	 m["Bob"] = 75.0
	
	 for k, v := range m {
        fmt.Println("k:", k, "v:", v)
    }

	fmt.Println(len(m))
	
	m["Chris"] = 1000.0
	
	// access value directory
	fmt.Println(m["Chris"])
}
```

output:

```
k: Dan v: 2
k: Steve v: 100
k: Bob v: 75
3
1000
```

### pointers
golang supports pointers. A pointer is a refrence in memory to the address of the value. Use `&` to refrence the memory address of variables.  Use `*` as a pointer to to that memory address:
	
[playground](https://play.golang.org/p/3zHblebQfca)

```
package main

import "fmt"

func main() {

	i := 42

	// we now create a pointer to i memory address
	p := &i

	// lets check the value of i
	fmt.Println("The value of i is:", i)

	// lets check the value of p and make sure it is the same value
	fmt.Println("The value of p is:", *p)

	// lets print the memory address of p
	fmt.Println("The memory address of p is:", p)
	fmt.Println("The memory address of i is:", &i)
	fmt.Println()

	// now lets create new int
	// and reuse our pointer to point to a only
	a := 10
	p = &a

	// i and a now match
	fmt.Println("The value of p is:", *p)
	fmt.Println("The value of a is:", a)

	// check memory addresses of both values
	fmt.Println("The memory address of p is:", p)
	fmt.Println("The memory address of a is:", &a)

}
```

Of course when you run this your memory addresses will be different. Output:

```
The value of i is: 42
The value of p is: 42
The memory address of p is: 0xc000094000
The memory address of i is: 0xc000094000

The value of p is: 10
The value of a is: 10
The memory address of p is: 0xc000094018
The memory address of a is: 0xc000094018
```

### calling a terminal command on linux
This will show you how to use the os package to call a terminal command `ls`.  This is one of the examples that will not work on the playground since we are going to be calling linux commands.  Lets create a couple files so when we call our script we will see these.

```
touch abc.txt
touch hello.txt
touch world.txt
```

```
package main

import (
	"bytes"
	"fmt"
	"log"
	"os/exec"
)

func main() {
	cmd := exec.Command("ls")
	var out bytes.Buffer
	cmd.Stdout = &out
	err := cmd.Run()
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println("The value of out is:", out.String())

}
```
output:

```
The value of out is: 3
abc.txt
hello.txt
main.go
world.txt
```

### struct
in golang you can group data types together to create a struct.  Structs can also be nested with other struct.  For example if you were creating a service for veterinary.  You can create a struct that hold the pets name.  Then you can create a tested struct to hold information about cats specifically.  Golang is also smart enough to not have to use `&` of variables.    Here is a generic example:

[playground](https://play.golang.org/p/HuPP0Lz_inh)

```
package main

import (
	"fmt"
)

type Cat struct {
	Animal
	Owner          string
	Lifeexpectancy int
}
type Animal struct {
	Age  int
	Name string
}

func (a *Animal) Move() {
	fmt.Println("Animal moved")
}

func (a *Animal) SayName() {
	fmt.Printf("Animal name: %s\n", a.Name)
}

func (a *Cat) Info() {
	fmt.Printf("Animal age: %d Pet owner name: %s\n", a.Age, a.Owner)
}

func (a *Cat) Averagelife() {
	fmt.Printf("The average life of a cat is: %d.\n", a.Lifeexpectancy)
}

func main() {
	d := Cat{}
	d.Age = 3
	d.Name = "Dan"
	d.Owner = "Bob"
	d.Lifeexpectancy = 15

	d.Move()
	d.SayName()
	d.Info()
	d.Averagelife()

	fmt.Println()

	// example on how to declare data on a nested struct in 1 line
	c := Cat{Animal{10, "Comet"}, "Steve", 15}
	c.SayName()
	c.Info()
	c.Averagelife()

}
```

output:

```
Animal moved
Animal name: Dan
Animal age: 3 Pet owner name: Bob
The average life of a cat is: 15.

Animal name: Comet
Animal age: 10 Pet owner name: Steve
The average life of a cat is: 15.
```
