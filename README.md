# ValidatorKMP
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/io.github.alexandrakomkova/validator-kmp/badge.svg)](https://central.sonatype.com/artifact/io.github.alexandrakomkova/validator-kmp)

**Validator KMP** is a Kotlin Multiplatform library for straightforward data validation. It provides a `Validator` interface and several ready-to-use implementations for common scenarios such as email and password validation.

## Features

* **Kotlin Multiplatform:** Developed using Kotlin Multiplatform, ensuring compatibility with Android and iOS.
* **Ready-to-use Validators:** Includes validators for email and password with various configuration options.
* **Informative Results:** Returns a `ValidationResult` object with an `isValid` flag and an optional `errorMessage`.

## Installation

To use ValidatorKMP in your Kotlin Multiplatform project, add the dependency to your `build.gradle.kts` file:

```kotlin
dependencies {
    implementation("io.github.alexandrakomkova:validator-kmp:1.0.1")
}
```
Sync your Gradle project.

## Usage
### Built-in Validators
The library provides the following built-in validators.

**EmailValidator** is a validator for checking email addresses.
```kotlin
import com.alexandrakomkova.validator.EmailValidator
import com.alexandrakomkova.validator.ValidationResult

val validator = EmailValidator()
val result1 = validator.validate("test@example.com")
println(result1) // ValidationResult(isValid=true, errorMessage=null)

val result2 = validator.validate("testexample.com")
println(result2) // ValidationResult(isValid=false, errorMessage=Email must contain one '@' symbol.)
```
**PasswordValidator** is a validator for checking passwords.
```kotlin
import com.alexandrakomkova.validator.PasswordValidator
import com.alexandrakomkova.validator.ValidationResult

val validator1 = PasswordValidator()
val result1 = validator1.validate("StrongPass123!")
println(result1) // ValidationResult(isValid=true, errorMessage=null)

val result2 = validator1.validate("")
println(result2) // ValidationResult(isValid=false, errorMessage=Password must be at least 8 characters long.)
```
### Custom Validators
You can change the validator parameters. 
```kotlin
import com.alexandrakomkova.validator.PasswordValidator
import com.alexandrakomkova.validator.ValidationResult

val validator = PasswordValidator(
        minLength = 3,
        maxLength = 10,
        shouldContainDigits = false,
        shouldContainUpperCase = false,
        shouldContainSpecialSymbols = false
    )
val result1 = validator.validate("abc")
println(result1) // ValidationResult(isValid=true, errorMessage=null)

```

## Properties
### EmailValidator
| Property  | Type | Description | Default value |
| ------------- | ------------- | ------------- | ------------- |
| maxLength  | Int  | The maximum length of the email address.  | 254 |

### PasswordValidator
| Property  | Type | Description | Default value |
| ------------- | ------------- | ------------- | ------------- |
| minLength  | Int  | The minimum length of the password.  | 8 |
| maxLength  | Int  | The maximum length of the password.  | 16 |
| shouldContainUpperCase  | Boolean  | Whether at least one uppercase letter is required.  | true |
| shouldContainDigits  | Boolean  | Whether at least one digit is required.  | true |
| shouldContainSpecialSymbols  | Boolean  | Whether at least one special symbol (from the set !@#$%^&*(),.?":{}\|<>) is required.  | true |

## Demo
<img src='https://github.com/alexandrakomkova/ValidatorKMP/blob/main/Screenshot_20250416_112702.png' width='250'> <img src='https://github.com/alexandrakomkova/ValidatorKMP/blob/main/Screenshot_20250416_112730.png' width='250'> <img src='https://github.com/alexandrakomkova/ValidatorKMP/blob/main/Screenshot_20250416_121624.png' width='250'>

## Platforms Supported
ValidatorKMP currently supports the following platforms:
* Android
* iOS

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
