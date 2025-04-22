## approximate
```
val approximate: 
  x: Expression -> 
  Expression
```

### Purpose
Takes any kind of expression and reduces any numbers it can to real number values. I.e. 

### Parameters
- `x`: The expression to approximate 

### Returns
Returns a new expression whose type depends on whether it can be fully reduced to a numeric expression. This isn't possible if the expression contains any symbols or special values like +/- infinity. 

If the expression is fully reducable to a numeric value(e.g. 9.21**7/sqrt{3.4}) it returns an Approximation(see Approximation.md), which is a subtype of Expression defined as consisting either of a Real or Complex. In the real case, this is simply a system float. 

If it isn't, everything that is reducable to such will be, such that the resulting expression will be a composition of symbols, special values, functions and approximations. No Numbers(BigRationals)  will remain.  

### Exceptions
- `ExceptionType1`: When this exception is thrown
- `ExceptionType2`: When this exception is thrown

### Examples
```fsharp
// Basic usage
let result = functionName param1 param2
// returns: expected output

// Another example with different inputs
let result2 = functionName param3 param4
// returns: expected output
```

### Notes
Any additional information, edge cases, performance considerations, etc.

### Related Functions
- `relatedFunction1`: How it relates
- `relatedFunction2`: How it relates
