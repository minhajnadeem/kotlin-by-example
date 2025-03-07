# Variables

Kotlin has powerful type inference. While you can explicitly declare the type of a variable, you'll usually let the
compiler do the work by inferring it. Kotlin does not enforce immutability, though it is recommended.
In essence use *val* over *var*.

```run-kotlin
fun main() {
//sampleStart
    var a: String = "initial"  // 1
    println(a)
    val b: Int = 1             // 2
    val c = 3                  // 3
//sampleEnd
}
```

1. Declares a mutable variable and initializes it.
2. Declares an immutable variable and initializes it.
3. Declares an immutable variable and initializes it without specifying the type. The compiler infers the type `Int`.

```run-kotlin
fun main() {
//sampleStart
    var e: Int  // 1
    println(e)  // 2
//sampleEnd
}
```
{validate="false"}

1. Declares a variable without initialization.
2. An attempt to use the variable causes a compiler error: `Variable 'e' must be initialized`.

You're free to choose when you initialize a variable, however, it must be initialized before the first read.

```run-kotlin
fun someCondition() = true 

fun main() {
//sampleStart
    val d: Int  // 1
    
    if (someCondition()) {
        d = 1   // 2
    } else {
        d = 2   // 2
    }
    
    println(d) // 3
//sampleEnd
}
```

1. Declares a variable without initialization.
2. Initializes the variable with different values depending on some condition.
3. Reading the variable is possible because it's already been initialized.

Kotlin support null-safety and late initialization. By default a variable cannot be **null** but you can make a variable null-able by using `?`. 
In kotlin if you don't want to Initialize a variable at it's declaration then you can define it as **lateinit**. Keep in note that a late initialized variable must be initialize before its usage. 

```run-kotlin
fun main() {
    //nullable variable
    var middleName : String? = null
    middleName = "Smith"
    println("Hi! I am John $middleName")
    middleName = null
    println("Hi! I am John $middleName")
    
    //late initialization
    lateinit var initMeBeforeUse : String
    println(initMeBeforeUse)	//Exception in thread "main" kotlin.UninitializedPropertyAccessException
}
```
