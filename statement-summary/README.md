# brightscript

## Types
- `Boolean`
- `Integer`
- `LongInteger`
- `Float`
- `Double`
- `String`
- `Object`
- `Function`
- `Interface`
- `Invalid`

## Comments
- `' brs comment`
- `<!-- xml comment -->`

## Literals
- `true`, `false`
- `invalid`
- `"this is a string"` `""""`
- `255`, `&HFF`
- `2.01`, `1.23456E+30`, `2!`
- `1.23456789D-12`, `2.3#`
- `&hFEDC&`, `543210&`
- `LINE_NUM`
- `[]`, `[1, 2, 3]`
- `{}`, `{key1: "value", key2: 55}`, `{"key1": "value"}`

## Type declaration characters
Used to fix a variable's type.

- String: `$`
- Integer: `%`
- Float: `!`
- Double: `#`
- LongInteger: `&`

## Type Conversion (Promotion)

## Operators
- Dot: `.`
- Array: `[]`
- Optional chaining: `?.`, `?@`, `?[`, `?(`
- Exponent: `^` (right-associative)
- Unary: `-`, `+`
- Multiplication: `*`, `/`, `MOD`, Integer Div: `\`
- Additive: `-`, `+`
- Integer bitshift: `<<`, `>>`
- Comparison: `<`, `>`, `=`, `<>`, `<=`, `>=`
- Logical: `NOT`, `AND`, `OR`
- Assignment: `=`

## Component Interface Member Access

```py
i = CreateObject("roInt") ' create component
i.ifInt.SetInt(5) ' explicitly access interface
i.SetInt(5) ' searches all interfaces for matching number
```

## Associative Array Member Access

```py
aa = CreateObject("roAssociativeArray") ' create component
aa.Key = 5 ' key
aa.AddReplace("Key", 6)
aa["Key"] = 7

? aa.Key ' 5
? aa.Lookup("Key") ' 7
? aa["Key"] ' 7
```

## Multi-dimensional Array

```py
dim array[5,5,5]
dim array2[5][5][5]
item = array[1][2][3]
item = array[1,2,3]
```

## Logical Short-Circuits
