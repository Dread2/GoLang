* GoLang: This repo is filled with my progress of the Go Tour. It may also contain some other resources/documentation that proves helpful. 
* Credits:
  * Go Tour, Can be found at the URL: https://go.dev/tour/welcome/1
  * awesome-cheatsheets, Can be found at the URL: https://github.com/Dread2/awesome-cheatsheets
# Go Cheatsheet 

## Summary

-   Introduction
    -   [Hello World](#hello-world)
    -   [Go CLI Commands](#go-cli-commands)
    -   [Go Modules](#go-modules)
-   Basic
    -   [Basic Types](#basic-types)
    -   [Variables](#variables)
    -   [Operators](#operators)
    -   [Conditional Statements](#conditional-statements)
    -   [Loops](#loops)
    -   [Arrays](#arrays)
    -   [Functions](#functions)
-   Advanced
    -   [Structs](#structs)
    -   [Maps](#maps)
    -   [Pointers](#pointers)
    -   [Methods and Interfaces](#methods-and-interfaces)
    -   [Errors](#errors)
    -   [Testing](#testing)
    -   [Concurrency](#concurrency)
-   Standard Libs
    -   [Package fmt](#package-fmt)
-   Printing Within Certain Standard Libs
    -   [fmt](#fmt-printing)
## Hello World

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello Gophers!")
}
```

[Return to Summary](#summary)

<hr/>

## Go CLI Commands

```bash
# Compile & Run code
$ go run [file.go]

# Compile
$ go build [file.go]
# Running compiled file
$ ./hello

# Test packages
$ go test [folder]

# Install packages/modules
$ go install [package]

# List installed packages/modules
$ go list

# Update packages/modules
$ go fix

# Format package sources
$ go fmt

# See package documentation
$ go doc [package]

# Add dependencies and install
$ go get [module]

# See Go environment variables
$ go env

# See version
$ go version
```

[Return to Summary](#summary)

<hr/>

## Go Modules

-   Go projects are called **modules**
-   Each module has multiple **packages**
-   Each package should has a scoped functionality. Packages talk to each other to compose the code
-   A module needs at least one package, the **main**
-   The package main needs a entry function called **main**

```bash
# Create Module
$ go mod init [name]
```

Tip: By convention, modules names has the follow structure:

domain.com/user/module/package

Example: github.com/spf13/cobra

<hr/>

[Return to Summary](#summary)

## Basic Types

|    Type    |               Set of Values                |                    Values                     |
| :--------: | :----------------------------------------: | :-------------------------------------------: |
|    bool    |                  boolean                   |                  true/false                   |
|   string   |            array of characters             |             needs to be inside ""             |
|    int     |                  integers                  |             32 or 64 bit integer              |
|    int8    |               8-bit integers               |                 [ -128, 128 ]                 |
|   int16    |              16-bit integers               |               [ -32768, 32767]                |
|   int32    |              32-bit integers               |          [ -2147483648, 2147483647]           |
|   int64    |              64-bit integers               | [ -9223372036854775808, 9223372036854775807 ] |
|   uint8    |          8-bit unsigned integers           |                  [ 0, 255 ]                   |
|   uint16   |          16-bit unsigned integers          |                 [ 0, 65535 ]                  |
|   uint32   |          32-bit unsigned integers          |               [ 0, 4294967295 ]               |
|   uint64   |          64-bit unsigned integers          |          [ 0, 18446744073709551615 ]          |
|  float32   |                32-bit float                |                                               |
|  float64   |                64-bit float                |                                               |
| complex64  | 32-bit float with real and imaginary parts |                                               |
| complex128 | 64-bit float with real and imaginary parts |                                               |
|    byte    |                sets of bits                |                alias for uint8                |
|    rune    |             Unicode characters             |                alias for int32                |

[Return to Summary](#summary)

<hr/>

## Variables

```go
// Declaration
var value int

// Initialization
value = 10

// Declaration + Initialization + Type inference
var isActive = true

// Short declaration (only inside functions)
text := "Hello"

// Multi declaration
var i, j, k = 1, 2, 3

// Variable not initialized = Zero values
// Numeric: 0
// Boolean: false
// String: ""
// Special value: nil (same as null)

var number int // 0
var text string // ""
var boolean bool // false

// Type conversions
// T(v) converts v to type T

i := 1.234 // float
int(i) // 1

// Constants
const pi = 3.1415
```

<hr/>

## Operators

[Return to Summary](#summary)

Arithmetic Operators
| Symbol | Operation | Valid Types |
|:---------:|:-------------:|:-------------:|
| `+` | Sum | integers, floats, complex values, strings |
| `-` | Difference | integers, floats, complex values |
| `*` | Product | integers, floats, complex values |
| `/` | Quotient | integers, floats, complex values |
| `%` | Remainder | integers |
| `&` | Bitwise AND | integers |
| `|` | Bitwise OR | integers |
| `^` | Bitwise XOR | integers |
| `&^` | Bit clear (AND NOT) | integers |
| `<<` | Left shift | integer << unsigned integer |
| `>>` | Right shift | integer >> unsigned integer |

Comparison Operators
| Symbol | Operation |
|:---------:|:-------------:|
| `==` | Equal |
| `!=` | Not equal |
| `<` | Less |
| `<=` | Less or equal |
| `>` | Greater |
| `>=` | Greater or equal |

Logical Operators
| Symbol | Operation |
|:---------:|:-------------:|
| `&&` | Conditional AND |
| `||` | Conditional OR |
| `!` | NOT |

[Return to Summary](#summary)

<hr/>

## Conditional Statements

```go
// If / Else
i := 1

if i > 0 {
    // Condition is True! i is greater than zero
} else {
    // Condition is False! i is lower or equal to zero
}

// Else if
i := 1

if i > 0 {
    // Condition is True! i is greater than zero
} else if i > 0 && i < 2 {
    // Condition is True! i greater than zero and lower than two
} else if i > 1 && i < 4 {
    // Condition is True! i greater than one and lower than four
} else {
    // None of the above conditions is True, so it falls here
}

// If with short statements
i := 2.567

if j := int(i); j == 2 {
    // Condition is True! j, the integer value of i, is equal to two
} else {
    // Condition is False! j, the integer value of i, is not equal to two
}

// Switch
text := 'hey'

switch text {
    case 'hey':
        // 'Hello!'
    case 'bye':
        // 'Byee'
    default:
        // 'Ok'
}

// Switch without condition
value := 5

switch {
    case value < 2:
        // 'Hello!'
    case value >= 2 && value < 6:
        // 'Byee'
    default:
        // 'Ok'
}
```

[Return to Summary](#summary)

<hr/>

## Loops

```go
// Golang only has the for loop
for i := 0; i < 10; i++ {
    // i
}

// The first and third parameters are ommitable
// For as a while
i := 0;

for i < 10 {
    i++
}

// Forever loop
for {

}
```

[Return to Summary](#summary)

<hr/>

## Arrays

```go
// Declaration with specified size
var array [3]string
array[0] = "Hello"
array[1] = "Golang"
array[2] = "World"

// Declaration and Initialization
values := [5]int{1, 2, 3, 4, 5}

// Slices: A subarray that acts as a reference of an array
// Determining min and max
values[1:3] // {2, 3, 4}

// Determining only max will use min = 0
values[:2] // {1, 2, 3}

// Determining only min will use max = last element
values[3:] // {3, 4}

// Length: number of elements that a slice contains
len(values) // 5

// Capacity: number of elements that a slice can contain
values = values[:1]
len(values) // 2
cap(values) // 5

// Slice literal
slice := []bool{true, true, false}

// make function: create a slice with length and capacity
slice := make([]int, 5, 6) // make(type, len, cap)

// Append new element to slice
slice := []int{ 1, 2 }
slice = append(slice, 3)
slice // { 1, 2, 3 }
slice = append(slice, 3, 2, 1)
slice // { 1, 2, 3, 3, 2, 1 }

// For range: iterate over a slice
slice := string["W", "o", "w"]

for i, value := range slice {
    i // 0, then 1, then 2
    value // "W", then "o", then "w"
}

// Skip index or value

for i := range slice {
    i // 0, then 1, then 2
}

for _, value := range slice {
   value // "W", then "o", then "w"
}
```

[Return to Summary](#summary)

<hr/>

## Functions

```go
// Functions acts as a scoped block of code
func sayHello() {
    // Hello World!
}
sayHello() // Hello World!

// Functions can take zero or more parameters, as so return zero or more parameters
func sum(x int, y int) int {
    return x + y
}
sum(3, 7) // 10

// Returned values can be named and be used inside the function
func doubleAndTriple(x int) (double, triple int) {
    double = x * 2
    triple = x * 3
    return
}
d, t := doubleAndTriple(5)
// d = 10
// t = 15

// Skipping one of the returned values
_, t := doubleAndTriple(3)
// t = 9

// Functions can defer commands. Defered commands are
// runned in a stack order after the execution and
// returning of a function
var aux = 0

func switchValuesAndDouble(x, y int) {
    aux = x
    defer aux = 0 // cleaning variable to post use
    x = y * 2
    y = aux * 2
}

a, b = 2, 5
switchValuesAndDouble(2, 5)

// a = 10
// b = 4
// aux = 0

// Functions can be handled as values and be anonymous functions
func calc(fn func(int, int) int) int {
    return fn(2, 6)
}

func sum(x, y int) int {
    return x + y
}

func mult(x, y int) int {
    return x * y
}

calc(sum) // 8
calc(mult) // 12
calc(
    func(x, y int) int {
		return x / y
    }
) // 3

// Function closures: a function that returns a function
// that remembers the original context
func calc() func(int) int {
    value := 0
    return func(x int) int {
        value += x
        return value
    }
}

calculator := calc()
calculator(3) // 3
calculator(45) // 48
calculator(12) // 60
```

[Return to Summary](#summary)

<hr/>

## Structs

Structs are a way to arrange data in specific formats.

```go
// Declaring a struct
type Person struct {
    Name string
    Age int
}

// Initializing
person := Person{"John", 34}
person.Name // "John"
person.Age // 34

person2 := Person{Age: 20}
person2.Name // ""
person2.Age // 20

person3 := Person{}
person3.Name // ""
person3.Age // 0
```

[Return to Summary](#summary)

<hr/>

## Maps

Maps are data structures that holds values assigneds to a key.

```go
// Declaring a map
var cities map[string]string

// Initializing
cities = make(map[string]string)
cities // nil

// Insert
cities["NY"] = "EUA"

// Retrieve
newYork = cities["NY"]
newYork // "EUA"

// Delete
delete(cities, "NY")

// Check if a key is setted
value, ok := cities["NY"]
ok // false
value // ""
```

[Return to Summary](#summary)

<hr/>

## Pointers

Pointers are a direct reference to a memory address that some variable or value is being stored.

```go
// Pointers has *T type
var value int
var pointer *int

// Point to a variable memory address with &
value = 3
pointer = &value

pointer // 3
pointer = 20
pointer // 20
pointer += 5
pointer // 25

// Pointers to structs can access the attributes
type Struct struct {
    X int
}

s := Struct{3}
pointer := &s

s.X // 3
```

Obs: Unlike C, Go doesn't have pointer arithmetics.

[Return to Summary](#summary)

<hr/>

## Methods and Interfaces

Go doesn't have classes. But you can implement methods, interfaces and almost everything contained in OOP, but in what gophers call "Go Way"

```go
type Dog struct {
    Name string
}

func (dog *Dog) bark() string {
    return dog.Name + " is barking!"
}

dog := Dog{"Rex"}
dog.bark() // Rex is barking!
```

Interfaces are implicitly implemented. You don't need to inform that your struct are correctly implementing a interface if it already has all methods with the same name of the interface.
All structs implement the `interface{}` interface. This empty interface means the same as `any`.

```go
// Car implements Vehicle interface
type Vehicle interface {
    Accelerate()
}

type Car struct {

}

func (car *Car) Accelerate() {
    return "Car is moving on ground"
}
```

[Return to Summary](#summary)

<hr/>

## Errors

Go doesn't support `throw`, `try`, `catch` and other common error handling structures. Here, we use `error` package to build possible errors as a returning parameter in functions

```go
import "errors"

// Function that contain a logic that can cause a possible exception flow 
func firstLetter(text string) (string, error) {
    if len(text) < 1 {
        return nil, errors.New("Parameter text is empty")
    }
    return string(text[0]), nil
}

a, errorA := firstLetter("Wow")
a // "W"
errorA // nil

b, errorB := firstLetter("")
b // nil
errorB // Error("Parameter text is empty")
```

[Return to Summary](#summary)

<hr/>

## Testing

Go has a built-in library to unit testing. In a separate file you insert tests for functionalities of a file and run `go test package` to run all tests of the actual package or `go test path` to run a specific test file.

```go
// main.go
func Sum(x, y int) int {
    return x + y
}

// main_test.go
import ( 
    "testing"
    "reflect"
)

func TestSum(t *testing.T) {
    x, y := 2, 4
    expected := 2 + 4

    if !reflect.DeepEqual(Sum(x, y), expected) {
        t.Fatalf("Function Sum not working as expected")
    }
}
```

[Return to Summary](#summary)

<hr/>

## Concurrency

One of the main parts that make Go attractive is its form to handle with concurrency. Different than parallelism, where tasks can be separated in many cores that the machine processor have, in concurrency we have routines that are more lightweight than threads and can run asynchronously, with memory sharing and in a single core.

```go
// Consider a common function, but that function can delay itself because some processing
func show(from string) {
	for i := 0; i < 3; i++ {
		fmt.Printf("%s : %d\n", from, i)
	}
}

// In a blocking way...
func main() {
	show("blocking1")
	show("blocking2")

	fmt.Println("done")
}
/*  blocking1: 0
    blocking1: 1
    blocking1: 2
    blocking2: 0
    blocking2: 1
    blocking2: 2
    done 
*/

// Go routines are a function (either declared previously or anonymous) called with the keyword go
func main() {
	go show("routine1")
	go show("routine2")

	go func() {
		fmt.Println("going")
	}()

	time.Sleep(time.Second)

	fmt.Println("done")
}

/*  Obs: The result will depends of what processes first
    routine2: 0
    routine2: 1
    routine2: 2
    going
    routine1: 0
    routine1: 1
    routine1: 2
    done
*/

// Routines can share data with channels
// Channels are queues that store data between multiple routines
msgs := make(chan string)

go func(channel chan string) {
    channel <- "ping"
}(msgs)

go func(channel chan string) {
    channel <- "pong"
}(msgs)

fmt.Println(<-msgs) // pong
fmt.Println(<-msgs) // ping

// Channels can be bufferized. Buffered channels will accept a limited number of values and when someone try to put belong their limit, it will throw and error
numbers := make(chan int, 2)

msgs<-0
msgs<-1
msgs<-2

// fatal error: all goroutines are asleep - deadlock!

// Channels can be passed as parameter where the routine can only send or receive
numbers := make(chan int)

go func(sender chan<- int) {
    sender <- 10
}(numbers)

go func(receiver <-chan int) {
    fmt.Println(<-receiver) // 10
}(numbers)

time.Sleep(time.Second)

// When working with multiple channels, the select can provide a control to execute code accordingly of what channel has bring a message
c1 := make(chan string)
c2 := make(chan string)

select {
case msg1 := <-c1:
    fmt.Println("received", msg1)
case msg2 := <-c2:
    fmt.Println("received", msg2)
default:
    fmt.Println("no messages")
}

go func() {
    time.Sleep(1 * time.Second)
    c1 <- "channel1 : one"
}()
go func() {
    time.Sleep(2 * time.Second)
    c2 <- "channel2 : one"
}()

for i := 0; i < 2; i++ {
    select {
    case msg1 := <-c1:
        fmt.Println("received", msg1)
    case msg2 := <-c2:
        fmt.Println("received", msg2)
    }
}

/*
    no messages
    received channel1: one
    received channel2: one
*/

// Channels can be closed and iterated
channel := make(chan int, 5)

for i := 0; i < 5; i++ {
    channel <- i
}

close(channel)

for value := range channel {
    fmt.Println(value)
}

/*
    0
    1
    2
    3
    4
*/
```

[Return to Summary](#summary)

<hr/>

## Package `fmt`

```go
import "fmt"

fmt.Print("Hello World") // Print in console
fmt.Println("Hello World") // Print and add a new line in end
fmt.Printf("%s is %d years old", "John", 32) // Print with formatting
fmt.Errorf("User %d not found", 123) // Print a formatted error
```

[Return to Summary](#summary)

<hr/>

## Fmt Printing

Standard Verbs	
```%v	the value in a default format
	when printing structs, the plus flag (%+v) adds field names
%#v	a Go-syntax representation of the value
%T	a Go-syntax representation of the type of the value
```%%	a literal percent sign; consumes no valu
-Boolean:
	%t	the word true or false
-Integer:
	-%b	base 2
	-%c	the character represented by the corresponding Unicode code point
	-%d	base 10
	-%o	base 8
	-%O	base 8 with 0o prefix
	-%q	a single-quoted character literal safely escaped with Go syntax.
	-%x	base 16, with lower-case letters for a-f
	-%X	base 16, with upper-case letters for A-F
	-%U	Unicode format: U+1234; same as "U+%04X"
Floating-point and complex constituents:
	%b	decimalless scientific notation with exponent a power of two,
		in the manner of strconv.FormatFloat with the 'b' format,
		e.g. -123456p-78
	%e	scientific notation, e.g. -1.234456e+78
	%E	scientific notation, e.g. -1.234456E+78
	%f	decimal point but no exponent, e.g. 123.456
	%F	synonym for %f
	%g	%e for large exponents, %f otherwise. Precision is discussed below.
	%G	%E for large exponents, %F otherwise
	%x	hexadecimal notation (with decimal power of two exponent), e.g. -0x1.23abcp+20
	%X	upper-case hexadecimal notation, e.g. -0X1.23ABCP+20
String and slice of bytes (treated equivalently with these verbs):
	%s	the uninterpreted bytes of the string or slice
	%q	a double-quoted string safely escaped with Go syntax
	%x	base 16, lower-case, two characters per byte
	%X	base 16, upper-case, two characters per byte
Slice:
	%p	address of 0th element in base 16 notation, with leading 0x
Pointer:
	%p	base 16 notation, with leading 0x
	The %b, %d, %o, %x and %X verbs also work with pointers,
	formatting the value exactly as if it were an integer.
The default format for %v is:
	bool:                    %t
	int, int8 etc.:          %d
	uint, uint8 etc.:        %d, %#x if printed with %#v
	float32, complex64, etc: %g
	string:                  %s
	chan:                    %p
	pointer:                 %p
For compound objects, the elements are printed using these rules, recursively,
laid out like this:
	struct:             {field0 field1 ...}
	array, slice:       [elem0 elem1 ...]
	maps:               map[key1:value1 key2:value2 ...]
	pointer to above:   &{}, &[], &map[]
Width is specified by an optional decimal number immediately preceding the verb.
If absent, the width is whatever is necessary to represent the value.
Precision is specified after the (optional) width by a period followed by a
decimal number. If no period is present, a default precision is used.
A period with no following number specifies a precision of zero.
Examples:
	%f     default width, default precision
	%9f    width 9, default precision
	%.2f   default width, precision 2
	%9.2f  width 9, precision 2
	%9.f   width 9, precision 0
Width and precision are measured in units of Unicode code points,
that is, runes. (This differs from C's printf where the
units are always measured in bytes.) Either or both of the flags
may be replaced with the character '*', causing their values to be
obtained from the next operand (preceding the one to format),
which must be of type int.
For most values, width is the minimum number of runes to output,
padding the formatted form with spaces if necessary.
For strings, byte slices and byte arrays, however, precision
limits the length of the input to be formatted (not the size of
the output), truncating if necessary. Normally it is measured in
runes, but for these types when formatted with the %x or %X format
it is measured in bytes.
For floating-point values, width sets the minimum width of the field and
precision sets the number of places after the decimal, if appropriate,
except that for %g/%G precision sets the maximum number of significant
digits (trailing zeros are removed). For example, given 12.345 the format
%6.3f prints 12.345 while %.3g prints 12.3. The default precision for %e, %f
and %#g is 6; for %g it is the smallest number of digits necessary to identify
the value uniquely.
For complex numbers, the width and precision apply to the two
components independently and the result is parenthesized, so %f applied
to 1.2+3.4i produces (1.200000+3.400000i).
When formatting a single integer code point or a rune string (type []rune)
with %q, invalid Unicode code points are changed to the Unicode replacement
character, U+FFFD, as in strconv.QuoteRune.
Other flags:
	'+'	always print a sign for numeric values;
		guarantee ASCII-only output for %q (%+q)
	'-'	pad with spaces on the right rather than the left (left-justify the field)
	'#'	alternate format: add leading 0b for binary (%#b), 0 for octal (%#o),
		0x or 0X for hex (%#x or %#X); suppress 0x for %p (%#p);
		for %q, print a raw (backquoted) string if strconv.CanBackquote
		returns true;
		always print a decimal point for %e, %E, %f, %F, %g and %G;
		do not remove trailing zeros for %g and %G;
		write e.g. U+0078 'x' if the character is printable for %U (%#U).
	' '	(space) leave a space for elided sign in numbers (% d);
		put spaces between bytes printing strings or slices in hex (% x, % X)
	'0'	pad with leading zeros rather than spaces;
		for numbers, this moves the padding after the sign;
		ignored for strings, byte slices and byte arrays
Flags are ignored by verbs that do not expect them.
For example there is no alternate decimal format, so %#d and %d
behave identically.
For each Printf-like function, there is also a Print function
that takes no format and is equivalent to saying %v for every
operand.  Another variant Println inserts blanks between
operands and appends a newline.
Regardless of the verb, if an operand is an interface value,
the internal concrete value is used, not the interface itself.
Thus:
	var i interface{} = 23
	fmt.Printf("%v\n", i)
will print 23.
Except when printed using the verbs %T and %p, special
formatting considerations apply for operands that implement
certain interfaces. In order of application:
1. If the operand is a reflect.Value, the operand is replaced by the
concrete value that it holds, and printing continues with the next rule.
2. If an operand implements the Formatter interface, it will
be invoked. In this case the interpretation of verbs and flags is
controlled by that implementation.
3. If the %v verb is used with the # flag (%#v) and the operand
implements the GoStringer interface, that will be invoked.
If the format (which is implicitly %v for Println etc.) is valid
for a string (%s %q %v %x %X), the following two rules apply:
4. If an operand implements the error interface, the Error method
will be invoked to convert the object to a string, which will then
be formatted as required by the verb (if any).
5. If an operand implements method String() string, that method
will be invoked to convert the object to a string, which will then
be formatted as required by the verb (if any).
For compound operands such as slices and structs, the format
applies to the elements of each operand, recursively, not to the
operand as a whole. Thus %q will quote each element of a slice
of strings, and %6.2f will control formatting for each element
of a floating-point array.
However, when printing a byte slice with a string-like verb
(%s %q %x %X), it is treated identically to a string, as a single item.
To avoid recursion in cases such as
	type X string
	func (x X) String() string { return Sprintf("<%s>", x) }
convert the value before recurring:
	func (x X) String() string { return Sprintf("<%s>", string(x)) }
Infinite recursion can also be triggered by self-referential data
structures, such as a slice that contains itself as an element, if
that type has a String method. Such pathologies are rare, however,
and the package does not protect against them.
When printing a struct, fmt cannot and therefore does not invoke
formatting methods such as Error or String on unexported fields.
# Explicit argument indexes
In Printf, Sprintf, and Fprintf, the default behavior is for each
formatting verb to format successive arguments passed in the call.
However, the notation [n] immediately before the verb indicates that the
nth one-indexed argument is to be formatted instead. The same notation
before a '*' for a width or precision selects the argument index holding
the value. After processing a bracketed expression [n], subsequent verbs
will use arguments n+1, n+2, etc. unless otherwise directed.
For example,
	fmt.Sprintf("%[2]d %[1]d\n", 11, 22)
will yield "22 11", while
	fmt.Sprintf("%[3]*.[2]*[1]f", 12.0, 2, 6)
equivalent to
	fmt.Sprintf("%6.2f", 12.0)
will yield " 12.00". Because an explicit index affects subsequent verbs,
this notation can be used to print the same values multiple times
by resetting the index for the first argument to be repeated:
	fmt.Sprintf("%d %d %#[1]x %#x", 16, 17)
will yield "16 17 0x10 0x11".
# Format errors
If an invalid argument is given for a verb, such as providing
a string to %d, the generated string will contain a
description of the problem, as in these examples:
	Wrong type or unknown verb: %!verb(type=value)
		Printf("%d", "hi"):        %!d(string=hi)
	Too many arguments: %!(EXTRA type=value)
		Printf("hi", "guys"):      hi%!(EXTRA string=guys)
	Too few arguments: %!verb(MISSING)
		Printf("hi%d"):            hi%!d(MISSING)
	Non-int for width or precision: %!(BADWIDTH) or %!(BADPREC)
		Printf("%*s", 4.5, "hi"):  %!(BADWIDTH)hi
		Printf("%.*s", 4.5, "hi"): %!(BADPREC)hi
	Invalid or invalid use of argument index: %!(BADINDEX)
		Printf("%*[2]d", 7):       %!d(BADINDEX)
		Printf("%.[2]d", 7):       %!d(BADINDEX)
All errors begin with the string "%!" followed sometimes
by a single character (the verb) and end with a parenthesized
description.
If an Error or String method triggers a panic when called by a
print routine, the fmt package reformats the error message
from the panic, decorating it with an indication that it came
through the fmt package.  For example, if a String method
calls panic("bad"), the resulting formatted message will look
like
	%!s(PANIC=bad)
The %!s just shows the print verb in use when the failure
occurred. If the panic is caused by a nil receiver to an Error
or String method, however, the output is the undecorated
string, "<nil>".
# Scanning
An analogous set of functions scans formatted text to yield
values.  Scan, Scanf and Scanln read from os.Stdin; Fscan,
Fscanf and Fscanln read from a specified io.Reader; Sscan,
Sscanf and Sscanln read from an argument string.
Scan, Fscan, Sscan treat newlines in the input as spaces.
Scanln, Fscanln and Sscanln stop scanning at a newline and
require that the items be followed by a newline or EOF.
Scanf, Fscanf, and Sscanf parse the arguments according to a
format string, analogous to that of Printf. In the text that
follows, 'space' means any Unicode whitespace character
except newline.
In the format string, a verb introduced by the % character
consumes and parses input; these verbs are described in more
detail below. A character other than %, space, or newline in
the format consumes exactly that input character, which must
be present. A newline with zero or more spaces before it in
the format string consumes zero or more spaces in the input
followed by a single newline or the end of the input. A space
following a newline in the format string consumes zero or more
spaces in the input. Otherwise, any run of one or more spaces
in the format string consumes as many spaces as possible in
the input. Unless the run of spaces in the format string
appears adjacent to a newline, the run must consume at least
one space from the input or find the end of the input.
The handling of spaces and newlines differs from that of C's
scanf family: in C, newlines are treated as any other space,
and it is never an error when a run of spaces in the format
string finds no spaces to consume in the input.
The verbs behave analogously to those of Printf.
For example, %x will scan an integer as a hexadecimal number,
and %v will scan the default representation format for the value.
The Printf verbs %p and %T and the flags # and + are not implemented.
For floating-point and complex values, all valid formatting verbs
(%b %e %E %f %F %g %G %x %X and %v) are equivalent and accept
both decimal and hexadecimal notation (for example: "2.3e+7", "0x4.5p-8")
and digit-separating underscores (for example: "3.14159_26535_89793").
Input processed by verbs is implicitly space-delimited: the
implementation of every verb except %c starts by discarding
leading spaces from the remaining input, and the %s verb
(and %v reading into a string) stops consuming input at the first
space or newline character.
The familiar base-setting prefixes 0b (binary), 0o and 0 (octal),
and 0x (hexadecimal) are accepted when scanning integers
without a format or with the %v verb, as are digit-separating
underscores.
Width is interpreted in the input text but there is no
syntax for scanning with a precision (no %5.2f, just %5f).
If width is provided, it applies after leading spaces are
trimmed and specifies the maximum number of runes to read
to satisfy the verb. For example,
	Sscanf(" 1234567 ", "%5s%d", &s, &i)
will set s to "12345" and i to 67 while
	Sscanf(" 12 34 567 ", "%5s%d", &s, &i)
will set s to "12" and i to 34.
In all the scanning functions, a carriage return followed
immediately by a newline is treated as a plain newline
(\r\n means the same as \n).
In all the scanning functions, if an operand implements method
Scan (that is, it implements the Scanner interface) that
method will be used to scan the text for that operand.  Also,
if the number of arguments scanned is less than the number of
arguments provided, an error is returned.
All arguments to be scanned must be either pointers to basic
types or implementations of the Scanner interface.
Like Scanf and Fscanf, Sscanf need not consume its entire input.
There is no way to recover how much of the input string Sscanf used.
Note: Fscan etc. can read one character (rune) past the input
they return, which means that a loop calling a scan routine
may skip some of the input.  This is usually a problem only
when there is no space between input values.  If the reader
provided to Fscan implements ReadRune, that method will be used
to read characters.  If the reader also implements UnreadRune,
that method will be used to save the character and successive
calls will not lose data.  To attach ReadRune and UnreadRune
methods to a reader without that capability, use
bufio.NewReader.
*/
package fmt

