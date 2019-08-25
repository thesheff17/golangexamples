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
./golang.exe
```
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
