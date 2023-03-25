# Functions

### How to define a fun?

```run-kotlin
fun functionName() :  returnType  {
    //your code goes here...
    return returnType
}
```
return type `unit` can be omited. In kotlin, funtion can have named and default value arguments. One of the thing I love about kotlin consiceness is that kotlin functions can be converted into expression if they have single line to execute.

### Default Parameter Values and Named Arguments


```run-kotlin
fun printMessage(message: String): Unit {                               // 1
    println(message)
}

fun printBill(total: String, currency: String = "$") {  // 2
    println("Total bill is $currency$total")
}

fun sum(x: Int, y: Int): Int {                                          // 3
    return x + y
}

fun multiply(x: Int, y: Int) = x * y                                    // 4

fun main() {
    printMessage("Hello")                                               // 5                    
    printBill("150", "Rs")                              // 6
    printBill("220")                                     // 7
    printBill(currency = "Kd", total = "20")           // 8
    println(sum(1, 2))                                                  // 9
    println(multiply(2, 4))                                             // 10
}
```

1. A simple function that takes a parameter of type `String` and returns `Unit` (i.e., no return value).
2. A function that takes a second [optional parameter with default value](https://kotlinlang.org/docs/reference/functions.html#default-arguments) `Info`. The return type is omitted, meaning that it's actually `Unit`.
3. A function that returns an integer.
4. A single-expression function that returns an integer (inferred).
5. Calls the first function with the argument `Hello`.
6. Calls the function with two parameters, passing values for both of them.
7. Calls the same function omitting the second one. The default value `$` is used. 
8. Calls the same function using [named arguments](https://kotlinlang.org/docs/reference/functions.html#named-arguments) and changing the order of the arguments.
9. Prints the result of the `sum` function call.
10. Prints the result of the `multiply` function call.

### Infix Functions

Member functions and extensions with a single parameter can be turned into [infix functions](https://kotlinlang.org/docs/reference/functions.html#infix-notation). Infix functions are used to increase the readability of code. 

```run-kotlin
fun main() {

  infix fun Int.times(str: String) = str.repeat(this)        // 1
  println(2 times "Bye ")                                    // 2

  val pair = "Ferrari" to "Katrina"                          // 3
  println(pair)

  infix fun String.onto(other: String) = Pair(this, other)   // 4
  val myPair = "McLaren" onto "Lucas"
  println(myPair)

  val sophia = Person("Sophia")
  val claudia = Person("Claudia")
  sophia likes claudia                                       // 5
}

class Person(val name: String) {
  val likedPeople = mutableListOf<Person>()
  infix fun likes(other: Person) { likedPeople.add(other) }  // 6
}
```

1. Defines an infix extension function on `Int`.
2. Calls the infix function.
3. Creates a `Pair` by calling the infix function `to` from the standard library.
4. Here's your own implementation of `to` creatively called `onto`.
5. Infix notation also works on members functions (methods).
6. The containing class becomes the first parameter.

Note that the example uses [local functions](https://kotlinlang.org/docs/reference/functions.html#local-functions) (functions nested within another function).

### Local Function
Kotlin supports local functions, i.e. it allows you to put a function inside a function.

```run-kotlin
fun main() {

    fun count(list : List<Any>) : Int{
        return list.size
    }
    
    val weeks = listOf("Monday","Tuesday","Wednesday")
    println("total days is the list = ${count(weeks)}")
    
    val fruits = listOf("Apple", "Orange", "Banana", "Strawberry")
    println("total fruits is the basket = ${count(fruits)}")
}
```
