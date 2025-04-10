# MathNet.Symbolics Documentation

This repository contains community-contributed documentation for the [MathNet.Symbolics](https://symbolics.mathdotnet.com/) F# library, which provides symbolic math functionality but has limited official documentation.

## How to Contribute

1. Choose a module or function you've worked with
2. Document its behavior based on your experience
3. Submit a pull request with your documentation
4. No need to be comprehensive - document what you use

## Structure

Each module in the library gets its own markdown file. For example:
- `Algebraic.md`
- `SingleVariablePolynomial.md`
- `Calculus.md`
- etc.

---

# Function Documentation Template

When documenting a function, please use the following template:

## functionName
```
val functionName: 
  param1: Type1 -> 
  param2: Type2 -> 
  ReturnType
```

### Purpose
Brief description of what the function does and when you might use it.

### Parameters
- `param1`: What this parameter represents
- `param2`: What this parameter represents

### Returns
Description of the return value and its structure.

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


# Type Documentation Template


## TypeName

```fsharp
type TypeName = 
  | Case1 of Type1
  | Case2 of Type2 * Type3
  // or for record types
  { Field1: Type1
    Field2: Type2 }
```

### Purpose
Brief description of what this type represents and when you might use it.

### Properties/Fields
- `Field1`: What this field represents
- `Field2`: What this field represents

### Common Operations
Description of typical operations performed with this type.

### Examples
```fsharp
// Creating instances
let instance1 = Case1 value
let instance2 = { Field1 = value1; Field2 = value2 }

// Using the type
let result = someFunction instance1
```

### Notes
Any additional information, edge cases, etc.

### Related Types
- `RelatedType1`: How it relates
- `RelatedType2`: How it relates


---

# Example Documentation: SingleVariablePolynomial.coefficientsSV

## coefficientsSV

```fsharp
val coefficientsSV:
  symbol: Expression ->
  x: Expression ->
  Expression array
```

### Purpose
Extracts the coefficients of a polynomial expression in ascending order of degree.

### Parameters
- `symbol`: The polynomial expression to analyze
- `x`: The variable with respect to which to extract coefficients

### Returns
For an *n*'th degree polynomial, returns an array of *n+1*-length, with the 0th position being the constant term (0th degree coefficient) and so on until the *n*'th position.

Note that any missing terms are returned as a coefficient of 0.

### Examples
```fsharp
// Complete polynomial
let poly = 3*x**3 - 7*x**2 + 18*x + 3
coefficientsSV poly x
// returns: [3N; 18N; -7N; 3N]

// Polynomial with missing terms
let poly = 3*x**3 + 18*x
coefficientsSV poly x
// returns: [0N; 18N; 0N; 3N]
```

### Notes
- The function handles rational coefficients
- Returns BigInteger values (denoted by the N suffix)

### Related Functions
- `degreesSV`: Gets the degree of a polynomial
- `expandSV`: Expands a polynomial expression