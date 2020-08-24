# swift Questions

1 - **Type Annotations**
- This example provides a type annotation for a variable called welcomeMessage, to indicate that the variable can store String values:
```swift
var welcomeMessage: String
```
2- **What is the difference between Int and UInt?**
- Swift provides signed and unsigned integers in 8, 16, 32, and 64 bit forms. These integers follow a naming convention similar to C, in that an 8-bit unsigned integer is of type UInt8, and a 32-bit signed integer is of type Int32. Like all types in Swift, these integer types have capitalized names.
- Signed Integer -> Int  
- Unsigned Integer -> UInt

> NOTE
>
> Use UInt only when you specifically need an unsigned integer type with the same size as the platform’s native word size. If this isn’t the case, Int is preferred, even when the values to be stored are known to be nonnegative. A consistent use of Int for integer values aids code interoperability, avoids the need to convert between different number types, and matches integer type inference, as described in Type Safety and Type Inference.


