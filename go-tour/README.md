# Go Tour Notes

## Packages

Every Go program is made up of packages.

Programs start running in package main.

```go
package main
```

Packages are used in programs with `import`

```go
import (
"fmt"
"math/rand"
)
```

## Functions

A function can take zero or more arguments.

In this example, add takes two parameters of type int.

Notice that the type comes after the variable name.

```go
func add(x int, y int) int {
    return x+y
}
```

## Variables

```go
// variable declaration
// with variable type
var i, i int
// without variable type but with values Either one should be provided
var a, c, python, java = 1, true, false, "no!"
// short variable declaration
i := 1
```

### Default variables

```go
var i int // 0
var f float64 // 0
var b bool // false
var s string // ""
```

### Variable types

``` go
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

### Type Conversions/Interference

```go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)
```

## Constants

Constants are declared like variables, but with the const keyword.

Constants can be character, string, boolean, or numeric values.

Constants cannot be declared using the := syntax.

```go
const Truth = true
const Pi = 3.14
```

### Numberic Constants

Numeric constants are high-precision values.

An untyped constant takes the type needed by its context.

```go
const (
// Create a huge number by shifting a 1 bit left 100 places.
// In other words, the binary number that is 1 followed by 100 zeroes.
Big = 1 << 100
// Shift it right again 99 places, so we end up with 1<<1, or 2.
Small = Big >> 99
)
```

## Loops(for)

Go has only one looping construct, the for loop.

The basic for loop has three components separated by semicolons:

the init statement: executed before the first iteration
the condition expression: evaluated before every iteration
the post statement: executed at the end of every iteration

```go
sum := 0
for i := 0; i <= 10; i++ {
sum += i
}
// init and post are optional
for ; sum < 1000 ; {
    sum+= sum
}
// For is Go's while
for sum < 1000 {
    sum += sum
}
// infinite loop
for {

}
```

## Conditionl Statements

### If-Else

Go's if statements are like its for loops; the expression need not be surrounded by parentheses ( ) but the braces { } are required.

```go
if x > 0 {
    fmt.Println("x values is greater than 0")
}
// can have init and condition
if x:= math.Pow(x,y); x < 10 {
    fmt.Println("testing init in if block")
}
if x >= 10 {
fmt.Println("x values is greater than 10")
}
else {
fmt.Println("x values is smaller than 10")
}
```

### Switch

A switch statement is a shorter way to write a sequence of if - else statements. It runs the first case whose value is equal to the condition expression.

Break is provided by default. Executes for only one condition, then exits 

```go
switch false {
case t.Hour() < 12:
fmt.Println("Good morning!")
case t.Hour() < 17:
fmt.Println("Good afternoon.")
default:
fmt.Println("Good evening.")
```

## Pointers

Go has pointers. A pointer holds the memory address of a value.

```go
var p *int
i := 42
p = &i
fmt.Println(*p) // read i through the pointer p
*p = 21         // set i through the pointer p
fmt.Println(*p) // prints 21 as its updated via pointer.
```

## Structs

Struct is a collection of fields.
Struct fields are accessed via DOT.
Values must be provided for all components, if values for field is missing .
Pointers are used to access the struct elements.

```go
type name_of_struct struct {
    A string
    B string
    X int
    Y int
}

fmt.Println(name_of_struct{"hello","world", 3,33})
s := name_of_struct{"hello", "world", 3, 33}
fmt.Println(s.B)
p = &s
p.B = "hello" // struct elements are accessed by pointers as well.

```

## Arrays

The type [n]T is an array of n values of type T.

### Slices

An array has a fixed size. A slice, on the other hand, is a dynamically-sized, flexible view into the elements of an array. In practice, slices are much more common than arrays.
A slice does not store any data, it just describes a section of an underlying array.

Changing the elements of a slice modifies the corresponding elements of its underlying array.

Other slices that share the same underlying array will see those changes.

```go
var a [10] int // int array of size 10

primes := [6]int{2, 3, 5, 7, 11, 13}

var s []int = primes[1:4]
fmt.Println(s)
```

## Keywords

func - declares the funcion
package - declares the package
import - Import a package
for - for loop
switch - switch case
var - declare variable
return - Function return statement
defer - A defer statement defers the execution of a function until the surrounding function returns
struct - collection of fields
