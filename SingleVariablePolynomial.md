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