# Hello World

```run-kotlin
package org.kotlinlang.play         // 1

fun main() {                        // 2
    println("Hello, World!")        // 3
    print("Hello, Kotlin! This is my first Kotlin program #happykotlin ") // 4
    print(":)") //5
}
```

1. Kotlin code is usually defined in packages. Package specification is optional: If you don't specify a package in a source file, its content goes to the default package.
2. An entry point to a Kotlin application is the `main` function. Since Kotlin 1.3, you can declare `main` without any parameters. The return type is not specified, which means that the function returns nothing. 
3. `println` writes a line to the standard output. It is imported implicitly. Also note that semicolons are optional.
4. `print` writes a line to the standard console but do now break the line at the end unlike `println`.
5. `:)` will print after `#happykotlin`, not on the next line.

In Kotlin versions earlier than 1.3, the `main` function must have a parameter of type `Array<String>`.
    
```run-kotlin
fun main(args: Array<String>) {
    println("Hello, World!")
}
```

