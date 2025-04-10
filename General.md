# General Notes on the library 

## Creating rational numbers
As far as I can see there isn't a concise way to create rational number. If you write an expression like `1.3*x**2 + 17/21` F# will perform integer division and thus parse it as `1.3*x**2 + 0`. Naturally the symbolics language has support for rational numbers, in fact the `Number` type everything is based is `of BigRational` which is a type in MathNet.Numerics. Thus to get an rational number as an *expression* we have to perform gymnastics like 
```fsharp
// where numerator and denominator are integers. An identical function FromBigIntFraction exists
let r = Expression.Number (MathNet.Numerics.BigRational.FromIntFraction (numerator, denominator))
```

The easiest solution seems to be make your own operator out of the above composition, like the example below. Just worth it to note that the library doesn'y natively provide this
```fsharp
// Note that this is just an example operator, but I do recommend choosing one starting with '/' to get the same precedence
let (/.) n d = Expression.Number (MathNet.Numerics.BigRational.FromBigIntFraction (n, d))
```

where we use the BigInts version of the function since F# will cast regular integers to that anyway. We can then use them as e.g. `1.3*x**2 + 17 /. 21`