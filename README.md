"# go_guide_for_beginner" 
---
[![build status](https://img.shields.io/travis/erikras/react-redux-universal-hot-example/master.svg?style=flat-square)](https://travis-ci.org/erikras/react-redux-universal-hot-example)
[![react-redux-example channel on slack](https://img.shields.io/badge/slack-react--redux--example%40reactiflux-blue.svg)](http://www.reactiflux.com)
[![Demo on Heroku](https://img.shields.io/badge/demo-heroku-lightgrey.png)](https://react-redux.herokuapp.com)
[![Dependency Status](https://david-dm.org/erikras/react-redux-universal-hot-example.svg)](https://david-dm.org/erikras/react-redux-universal-hot-example)
[![devDependency Status](https://david-dm.org/erikras/react-redux-universal-hot-example/dev-status.svg)](https://david-dm.org/erikras/react-redux-universal-hot-example#info=devDependencies)
[![PayPal donate button](http://img.shields.io/paypal/donate.png?color=yellowgreen)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=E2LK57ZQ9YRMN)


### What is Go program?
A Go program file is a simple UTF-8 text file with .go file extension. Hence you can edit a Go program in simple text editors like notepad, sublime text and IDEs like VSCode or WebStorm. You can also use terminal text editors like vim or nano etc.
If you are using VSCode, then install vscode-go extension. This will help you write better code and make formatting/debugging easier.
## Go program structure
Every Go program must be included in a package. A standalone executable Go program must have a main function and must be included in main package. main function is the entry point for execution.
A standalone executable program is a Go program that can be built using go build command or ran using go run command.
package main
import "fmt"
func main() {
    fmt.Println("Hello World!")
}

From above code, we defined package main because this is our standalone executable program and we also added main function which will execute when we will run this program. We have used fmt package from Go's standard library (it comes with Go installation). To import a package, we used import keyword.
fmt package is used here to print messages to the standard output. This package provides different functions to print anything to the standard output in different formats. In above example, we have used Printf function which prints any data passed as argument to the standard output / terminal.
## Running a Go program
To run any Go program (assuming you have installed Go on your system), you need to instruct Go Compiler to compile and run a program file with given file path. If we put our earlier Go program code in hello.go file, then command to run this program in the directory of this file would be
$ go run hello.go
This will yield following result to the console
Hello World!
If you want to run multiple Go files at once, you can give a glob pattern or mention files in one command
$ go run dir/*.go
$ go run dir/**/*.go
$ go run file-a.go file-b.go file-c.go

To create a binary executable file, you can use build command.
$ go build hello.go
Above command will create a binary executable file hello in current directory which you can execute from terminal / command prompt.
$ ./hello

To deploy binary files to bin directory, you can use below command.
$ go install hello.go
This will install hello binary file in bin directory of your current Go workspace. Since, bin directory is in PATH, we can execute it from anywhere.
$ hello
Hello World!

Comments
If you are used to JavaScript or c++ comments, Go uses same comment format. For single line comment, you can use //comment and for block comments, you can use /*comment*/.
// I am a single line comment
// I am another single line comment
/*
    I am a block comment.
    And GoLang is awesome.
    Say it with me, GoLang is awesome.
*/

Semicolons
Until now you might have noticed that we haven’t used semicolons in our programs which are heavily use by other programming languages like c, c++ or JavaScript.
Like C, Go’s formal grammar uses semicolons to terminate statements, but unlike in C, those semicolons do not appear in the source code. Instead Go’s Lexer program uses a simple rule to insert semicolons automatically as it scans your Go program, so the source code is mostly free of them.
The rule is this. If the last token before a newline is an identifier (which includes words like int and float64), a basic literal such as a number or string constant, or one of the below tokens
break continue fallthrough return ++ -- ) }
then Lexer always inserts a semicolon after the token. This could be summarized as, “if the newline comes after a token that could end a statement, insert a semicolon”.
Hence, Go code is free of semicolons. If you accidentally write semicolons in source code, VSCode plugin will strip them off on save. You can also use gofmt command to format your code according to go specifications. The only place you will find semicolons is in for loops where statements have to be terminated deliberately using ; (semicolon) and switch statement.
You are free to use semicolons whenever you want, but that won’t be idiomatic Go code. For example, you could write following code and program will still execute.
package main
import("fmt"; "math";);
func main() {
    fmt.Println(math.Sqrt(16));
};

But following code is idiomatic way to write go code
package main
import(
    "fmt"                           // ;
    "math"                          // ;
)                                   // ;
func main() {
    fmt.Println(math.Sqrt(16))      // ;
}                                   // ;
Best practices
Go is a very clean and systematic language. Hence your code must follow community guidelines and Go specifications. gofmt is a tool that automatically formats Go source code, which can be helpful to write Go idiomatically.
Effective Go
Follow Effective Go documentation to understand these standard practices. https://golang.org/doc/effective_go.html
Go Playground
Go community has created an online IDE to play with simple Go programs. This is like JSFiddle or CodePen but strictly for Go Programing language. I recommend not using this IDE every single time because it is hosted on powerful servers. In my experience, I got different experience and results on local system and on this IDE while testing concurrency related programs. But for other simple programs, GO ahead.