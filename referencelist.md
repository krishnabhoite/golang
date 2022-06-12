+ <B>Go lang passing argument by reference </B>
    1. slices(not array) are passed by references by default
    2. maps are also passed by reference 
    
+ <B> Go lang passing argument by value </B>
    1. all basic data types (int,float,bool,string,array) are passed by value
    2. 
    
+ <B> Structs </B>
    1. Passing structs to functions 
       use pointers to pass the structs
    2. Comparing structs
       using simple equalt to operator but the struct type should be same
+ <B> Methods </B>
    1. declration
      func (<receiver>) <method_name>(<parameter>) <return_params> {
        //code 
        }
        <receiver> if it is declared as a pointer then the method can be used to change the value of structs of instance
        <receiver> if it is defined as a normal then method would not change the value of the structs
        in short reciver is a instance hence if it is defined as a poitner then the value would be change
        
+ <B> Interfaces </B>
      
            type <interface_name> interface {
         //method signatures
          //no var declaritons
          
         }
         
       implementing an interfaces
         go lang inteface implemented implicity and there is no sytax or keyword to implement interfaces
         
         func which needs to be implemented should have same method siganture along with the recievers
         it means it has implemnted the interfaces.
         
         
+ <B> Log Levels </B>
            Info 
            Warn
            Error
            Fatal
            Debug
            
      Trace loggin can be used to trace the functions here is an simple example
            the files created can be read by using <I>go tool trace trace.log</I>
         

			package main
			import (
				"fmt"
				"log"
				"math/rand"
				"os"
				"runtime/trace"
				"time"
			)

			func main() {
				f, err := os.Create("trace.out")
				if err != nil {
					log.Fatalf("failed to create trace output file: %v", err)
				}
				defer func() {
					if err := f.Close(); err != nil {
						log.Fatalf("failed to close trace file: %v", err)
					}
				}()

				if err := trace.Start(f); err != nil {
					log.Fatalf("failed to start trace: %v", err)
				}
				defer trace.Stop()

				AddRandomNumbers()
			}

			func AddRandomNumbers() {

				firstNumber := rand.Intn(100)
				secondNumber := rand.Intn(100)

				time.Sleep(2 * time.Second)

				var result = firstNumber * secondNumber

				fmt.Printf("Result of 2 numbers is %d\n", result)
			}

            
            
            
