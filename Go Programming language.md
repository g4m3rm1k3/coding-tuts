## Notes

[![GO](https://www.vhv.rs/dpng/d/53-533217_go-lenguaje-de-programacion-hd-png-download.png)](#https://go.dev/)

## Table of contents:

1. [Array](#arrays)
2. [Structs](#structs)
3. [Pointers](#pointers)
4. [Slices](#slices)
5. 

> The secret to doing anything is believing that you can do it. Anything that you believe you can do strong enough, you can do. Anything. As long as you believe.
> > --_Bob Ross_

  

## Arrays

arrays can hold one type

```go

var MyStrings [3]string
myStrings[0] = "cat"
myStrings[1] = "dog"
myStrings[2] = "fish"

```

---
## Structs

### You can create a struct in two ways

1. define the struct and then assign objects like this.
```go
    type Car struct {
	    NumberOfTires int
	    Luxury        bool
	    BucketSeats   bool
	    Make          string
	    Model         string
	    Year          int
  }

  func main() {
    var myCar Car
    myCar.NumberOfTires = 4
    myCar.Luxury = false
    myCar.Make = "Subaru"
    myCar.Year = 2017
    fmt.Printf("My car is a %d %s %s", myCar.Year, myCar.Make, myCar.Model)
  }
```

2. or you can assign inline like this
```go
    myCar := Car{
      NumberOfTires:3
      Luxury: false
      Make: "Subaru"
      Year: 2017
  }
```
---

## Pointers

To create a pointer in go
```go
func main() {

  x := 10
  myFirstPointer := &x
  fmt.Println("x is", x)
  fmt.Println("myFirstPointer is", myFirstPointer)
}
```

the output is as follows
```go
x is 10
myFirstPointer is 0xc000018098
```

changing the value to the pointer changes the value of x because it points to the memory address where x is stored

```go
func main() {

  x := 10
  myFirstPointer := &x
  fmt.Println("x is", x)
  fmt.Println("myFirstPointer is", myFirstPointer)
  *myFirstPointer = 15
  fmt.Println("x is now", x)
}
```
the output is now
```go
x is 10
myFirstPointer is 0xc000018098
x is now 15
```
to pass a pointer to a function call you would do this
```go
func main() {
  x := 10
  myFirstPointer := &x
  fmt.Println("x is", x)
  fmt.Println("myFirstPointer is", myFirstPointer)
  *myFirstPointer = 15
  fmt.Println("x is now", x)
  
  // passed the pointer as a reference to a function call
  changeValueOfPointer(&x)
  fmt.Println("After function call x is now", x)
}
func changeValueOfPointer(num *int) {
  *num = 25
}
```
when you want a reference to a pointer you prepend an ampersand ` &x `
when you want to get the value to a pointer and change it you prepend an asterisk ` *myPointer `

---
## Slices

to declare a slice you initialize a var and give the type prepended by the brackets

```go
func main() {
  var animals []string
}
```

to append data to the slice you use the syntax ` append(variable, "item") `
```go
func main() {

  var animals []string
  // appending to animals
  animals = append(animals, "dog")
  animals = append(animals, "fish")
  animals = append(animals, "cat")
  animals = append(animals, "horse")
  fmt.Println(animals)

}
```
The output looks like this
```go
[dog fish cat horse]    
```
To iterate over the slice use this syntax
```go
func main() {

  var animals []string
  animals = append(animals, "dog")
  animals = append(animals, "fish")
  animals = append(animals, "cat")
  animals = append(animals, "horse")
  fmt.Println(animals)
  
// i is the index and x is the iterable
  for i, x := range animals {
    fmt.Println(i, x)
  }
}
```

to print a subset of a string you use pass a start and stop value in the brackets
```go
animals[0:2]
```

use can use the len() function to get the length of a slice 
```go 
len(animals)
```

to check if a slice is sorted you can use the `sort.StringsAreSorted()` function
```go
fmt.Println("Is it sorted?", sort.StringsAreSorted(animals))
```

To sort a slice you can use the `sort.Strings()` method
```go
sort.Strings(animals)
```


[TOP](#notes)
















