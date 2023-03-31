# Sealed Classes

[Sealed classes](https://kotlinlang.org/docs/reference/sealed-classes.html) let you restrict the use of inheritance. Once you declare a class sealed, it can only be subclassed from inside the same package where the sealed class is declared. It cannot be subclassed outside of the package where the sealed class is declared. 

```run-kotlin
sealed class HttpResponse   // 1                                                   

data class Success(val code:Int, val message:String): HttpResponse()    // 2
data class Fail(val code:Int, val message:String): HttpResponse()                                       

fun main() {
    val response : HttpResponse = getCustomers()
    when(response){     // 3
        is Success -> println(response.message)     // 4
        is Fail -> println(response.message)        // 5  
        //else -> {}       // 6
    }
}
```

1. Defines a sealed class. 
2. Defines subclasses. Note that all subclasses must be in the same package.
3. Uses an instance of the sealed class as an argument in a `when` expression. 
4. A smartcast is performed, casting `HttpResponse` to `Success`.
5. A smartcast is performed, casting `HttpResponse` to `Fail`.
6. The `else`-case is not necessary here since all possible subclasses of the sealed class are covered. With a non-sealed superclass `else` would be required.


