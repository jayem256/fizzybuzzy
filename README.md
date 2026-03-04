# fizzybuzzy
Novel approach to classic problem

The following compact Golang code solves the *Fizz Buzz* problem without loops or conditions.

```
package main

import (
	"fmt"
)

func main() {
	fizzybuzzy(1, 100)
}

// fizzybuzzy a recursive loopless/branchless solution to common problem
func fizzybuzzy(i, r int) {
	// Will panic on division by zero at i = r+1 and breaks the recursion
	defer func(int) { recover() }(1 / (i % (r + 1)))

	nmb := func(fb int) { fmt.Println(fb) }         // Prints the given number
	fzz := func(fb int) { fmt.Println("Fizz") }     // Prints Fizz
	bzz := func(fb int) { fmt.Println("Buzz") }     // Prints Buzz
	fzb := func(fb int) { fmt.Println("FizzBuzz") } // Prints FizzBuzz

	[]func(int){nmb, nmb, fzz, nmb, bzz, fzz, nmb, nmb, fzz, bzz, nmb, fzz, nmb, nmb, fzb}[(i-1)%15](i)

	fizzybuzzy(i+1, r)
}
```