# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)


Kotlin incorporates null safety by distinguishing between nullable and non-null types:

-Non-Null Types: By default, types in Kotlin are non-null, meaning variables cannot hold null values. Attempting to assign null to such a variable will result in a compile-time error.
```kotlin 
var nonNullableString: String = "Hello" // Cannot be null
```

-Nullable Types: To allow a variable to hold null, its type is marked with a question mark (?). This explicit declaration enables the variable to be null.
```kotlin 
var nullableString: String? = null // Can be null
```

Kotlin provides tools for safe operations on nullable types:

-Safe Call (?.): Safely access properties or methods of a nullable object, returning null if the object is null.
```kotlin 
val length = nullableString?.length // null if nullableString is null
```

-Elvis Operator (?:): Provides a default value for a nullable expression if it is null.
```kotlin 
val lengthOrDefault = nullableString?.length ?: 0 // Default to 0 if null
```

-Non-Null Assertion (!!): Forces a value to be non-null, throwing an exception if it is null.
```kotlin 
val length = nullableString!!.length // Throws an exception if null
```

Kotlin's approach to null safety aims to minimize null pointer exceptions by making nullability explicit and providing safe ways to work with nullable types.

### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)

Lambda expressions are concise blocks of code that can take parameters and return values. In Kotlin, they are defined within curly braces {}. For example:
```kotlin 
val sum = { a: Int, b: Int -> a + b }
```

Higher-order functions are functions that can take functions as parameters or return them. They allow for more abstract and flexible code by enabling functions to be passed around as arguments or results. For instance:

```kotlin 
fun <T> List<T>.customFilter(predicate: (T) -> Boolean): List<T> {
    
}
```

Storing a function in a variable is useful for:

-Reusability: Define a function once and use it multiple times.

-Flexibility: Pass functions as arguments to or from higher-order functions.

-Deferred Execution: Execute the function later, potentially with different arguments.

This approach supports programming patterns like deferred execution, strategy pattern, and handling events or callbacks dynamically, enhancing the flexibility and expressiveness of your Kotlin code.






### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

