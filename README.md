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

2- **Type Safety and Type Inference?**
- Swift uses `type inference` to work out the appropriate type. `Type inference` enables a compiler to deduce the type of a particular expression automatically when it compiles your code, simply by examining the values you provide.

3- **Optional Binding**
- You use optional binding to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable. Optional binding can be used with if and while statements to check for a value inside an optional, and to extract that value into a constant or variable, as part of a single action.
```swift
if let constantName = someOptional {
    statements
}
```
4- **Implicitly Unwrapped Optionals**
- Sometimes it’s clear from a program’s structure that an optional will always have a value, after that value is first set. In these cases, it’s useful to remove the need to check and unwrap the optional’s value every time it’s accessed, because it can be safely assumed to have a value all of the time.

- These kinds of optionals are defined as `implicitly unwrapped optionals`. You write an implicitly unwrapped optional by placing an exclamation point (String!) rather than a question mark (String?) after the type that you want to make optional. Rather than placing an exclamation point after the optional’s name when you use it, you place an exclamation point after the optional’s type when you declare it.

5- **Assertions and Preconditions**
- Assertions and preconditions are checks that happen at runtime
- Assertions help you find mistakes and incorrect assumptions during development
- preconditions help you detect issues in production.


   
6- **Range Operators**
- **Closed Range Operator**
```swift
   for index in 1...5 {
       print("\(index) times 5 is \(index * 5)")
   }
```
- **Half-Open Range Operator** 
```swift
   let names = ["Anna", "Alex", "Brian", "Jack"]
   let count = names.count
   for i in 0..<count {
       print("Person \(i + 1) is called \(names[i])")
   }
```
- **One-Sided Ranges**
```swift
   for name in names[2...] {
       print(name)
   }

   for name in names[...2] {
       print(name)
   }
   
   for name in names[..<2] {
       print(name)
   }
   let range = ...5
```
7- **Strings Are Value Types**
- Swift’s String type is a value type. If you create a new String value, that String value is copied when it’s passed to a function or method, or when it’s assigned to a constant or variable. In each case, a new copy of the existing String value is created, and the new copy is passed or assigned, not the original version.

8- **String Interpolation**
- String interpolation is a way to construct a new String value from a mix of constants, variables, literals, and expressions by including their values inside a string literal. You can use string interpolation in both single-line and multiline string literals. Each item that you insert into the string literal is wrapped in a pair of parentheses, prefixed by a backslash (\):
```swift
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
```

9- **Counting Characters**
- Note that Swift’s use of extended grapheme clusters for Character values means that string concatenation and modification may not always affect a string’s character count.
For example, if you initialize a new string with the four-character word cafe, and then append a COMBINING ACUTE ACCENT (U+0301) to the end of the string, the resulting string will still have a character count of 4, with a fourth character of é, not e:
```swift
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in cafe is 4"

word += "\u{301}"    // COMBINING ACUTE ACCENT, U+0301

print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in café is 4"
```
10- **String Indices**
- Each String value has an associated index type, String.Index, which corresponds to the position of each Character in the string.

As mentioned above, different characters can require different amounts of memory to store, so in order to determine which Character is at a particular position, you must iterate over each Unicode scalar from the start or end of that String. For this reason, Swift strings can’t be indexed by integer values.

Use the startIndex property to access the position of the first Character of a String. The endIndex property is the position after the last character in a String. As a result, the endIndex property isn’t a valid argument to a string’s subscript. If a String is empty, startIndex and endIndex are equal.

You access the indices before and after a given index using the index(before:) and index(after:) methods of String. To access an index farther away from the given index, you can use the index(_:offsetBy:) method instead of calling one of these methods multiple times.

You can use subscript syntax to access the Character at a particular String index.
```swift
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
```
- Attempting to access an index outside of a string’s range or a Character at an index outside of a string’s range will trigger a runtime error.
```swift
greeting[greeting.endIndex] // Error
greeting.index(after: greeting.endIndex) // Error
```
- Use the indices property to access all of the indices of individual characters in a string.
```swift
for index in greeting.indices {
    print("\(greeting[index]) ", terminator: "")
}
// Prints "G u t e n   T a g ! "
```
> NOTE
>
> You can use the startIndex and endIndex properties and the index(before:), index(after:), and index(_:offsetBy:) methods on any type that conforms to the Collection protocol. This includes String, as shown here, as well as collection types such as Array, Dictionary, and Set.

11- **Collection Types**
- Swift provides three primary collection types, known as arrays, sets, and dictionaries, for storing collections of values. Arrays are ordered collections of values. Sets are unordered collections of unique values. Dictionaries are unordered collections of key-value associations.

12- **Mutability of Collections**
- If you create an array, a set, or a dictionary, and assign it to a variable, the collection that is created will be mutable. This means that you can change (or mutate) the collection after it’s created by adding, removing, or changing items in the collection. If you assign an array, a set, or a dictionary to a constant, that collection is immutable, and its size and contents cannot be changed.

13- **Arrays**
>NOTE
>
>Swift’s Array type is bridged to Foundation’s NSArray class.
For more information about using Array with Foundation and Cocoa, see [Bridging Between Array and NSArray](https://developer.apple.com/documentation/swift/array#2846730)

14- **Sets**
- A set stores distinct values of the same type in a collection with no defined ordering. You can use a set instead of an array when the order of items is not important, or when you need to ensure that an item only appears once.
>NOTE
>
>Swift’s Set type is bridged to Foundation’s NSSet class.
For more information about using Set with Foundation and Cocoa, see [Bridging Between Set and NSSet](https://developer.apple.com/documentation/swift/set#2845530).

15- **Fundamental Set Operations**

[comment]: <> (<img align="center" src="assets/setVennDiagram_2x.png" width="80%" />  )

<img src="assets/setVennDiagram_2x.png" width="50%" />

- Use the intersection(_:) method to create a new set with only the values common to both sets.
- Use the symmetricDifference(_:) method to create a new set with values in either set, but not both.
- Use the union(_:) method to create a new set with all of the values in both sets.
- Use the subtracting(_:) method to create a new set with values not in the specified set.

16- **Set Membership and Equality**

<img src="assets/setEulerDiagram_2x.png" width="50%" />

- Use the “is equal” operator (==) to determine whether two sets contain all of the same values.
- Use the isSubset(of:) method to determine whether all of the values of a set are contained in the specified set.
- Use the isSuperset(of:) method to determine whether a set contains all of the values in a specified set.
- Use the isStrictSubset(of:) or isStrictSuperset(of:) methods to determine whether a set is a subset or superset, but not equal to, a specified set.
- Use the isDisjoint(with:) method to determine whether two sets have no values in common.

17- **Dictionaries**
> NOTE
>
> Swift’s Dictionary type is bridged to Foundation’s NSDictionary class.
For more information about using Dictionary with Foundation and Cocoa, see [Bridging Between Dictionary and NSDictionary](https://developer.apple.com/documentation/swift/dictionary#2846239).

>NOTE
>
>A dictionary Key type must conform to the Hashable protocol, like a set’s value type.

