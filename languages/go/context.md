# context



timeout example: [cancelling-long-running-goroutines-with-context-withtimeout-within-golang](http://www.inanzzz.com/index.php/post/gao6/cancelling-long-running-goroutines-with-context-withtimeout-within-golang)

```
package main
 
import (
	"context"
	"fmt"
	// "math/rand"
	"time"
)
 
func main() {
	fmt.Println(">>>>> BEGIN")
 
	ctx, cancel := context.WithTimeout(context.Background(), 3 * time.Second)
	// Cancel even if everything goes fine without an error to release resources.
	defer cancel()
 
	ch := make(chan int)
 
	go doSomething(ch)
 
	select {
	case <-ctx.Done():
		fmt.Println("TIMEOUT:", ctx.Err())
	case t := <-ch:
		fmt.Printf("JOB DONE in %d seconds\n", t)
	}
 
	fmt.Println(">>>>> END")
}
 
func doSomething(ch chan<- int) {
	// Prevent picking up the same random number all the time for sleeping.
	//rand.Seed(time.Now().UnixNano())
 
	// Pick a random number to simulate time it takes to finish the job.
	delay := 4
	fmt.Printf("RUN: %d seconds\n", delay)
	time.Sleep(time.Duration(delay) * time.Second)
 
	ch<- delay
	
	fmt.Println("END doSomething" )
}
```
