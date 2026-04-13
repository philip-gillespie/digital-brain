# Lua Basics

## Hello world

```lua
print("hello world")
```

## Interactive mode

```bash
lua -i my_file
```

![[lib1.lua]]

```lua
dofile(lib1.lua)
n = norm(3.4, 1.0)
```

## Comments

Add comments in lua by using the dash symbol

```lua
-- This line is commented out and so will not run
```

## Separating statements

Optionally end statements with a semicolon. All these are valid lua

```lua
a = 1
b = a + 2

a = 1;
b = a + 2;

a = 1; b = a + 2
a = 1 b = a + 2 -- Ugly but valid
```

## Global Variables

Uninitialized variables simply return `nil`.

```lua
> b --> nil
> b = 10 --> 10
> b --> 10
```

Assign `nil` to delete a variable

```lua
> b = nil --> nil
> b --> nil
```

## Types and values

Lua is dynamically typed.
Each value carries its own type.

```lua
> type(nil) --> "nil"
> type(true) --> "boolean"
> type(10.4 * 3) --> "number"
> type("Hello World") --> "string"
> type(io.stdin) --> "userdata"
> type(print) --> "function"
> type(type) --> "function"
> type({}) --> "table"
> type(type(x)) --> "string"
```

The `type` function always returns a string.

The type of a variable can be changed by reassigns.

```lua
> a = 10
> type(a) --> "number"
> a = "a string"
> type(a) --> "string"
```

We can use `nil` to differentiate between a normal return and an abnormal return.

## Nil

The value `nil` of type `nil` represents a none value.

## Booleans

The boolean values in lua ar `true` and `false`.

Use `and`, `or` and `not` to perform boolean logic.

All values can be used with the boolean Operators.
Only `nil` and `false` evaluate to false; everything else evaluates to true.

### Lazy evaluation of `and`

`and` only evaluates the second operator if the first is not false.
If both values evaluate to true, then the last value is returned.
Otherwise it is the first falsey value which is returned.

```lua
> 4 and 5 --> 5
> nil and 13 --> nil
> false and 13 --> false
```

This is also called short-circuit evaluation.

### Lazy evaluation of `or`

If the first operand evaluates to `false` the second operand is returned.
If the first operand evaluates to `true` then the first operand is returned.

```lua
> false or 5 --> 5
> nil or 3 --> 3
> nil or false --> false
> false or nil --> nil
> 3 or 5 --> 3
> "cats" or false --> "cats"
> {} or nil --> {}
```

### Useful idioms

```lua
x = x or v
```

If `x` is uninitialized then assign it to a default value `v`.

```lua
(x > 5) and x or y
```

If `x` is greater than 5 return x, otherwise return `y`.

### Not operator

The `not` operator always returns a boolean

```lua
> not nil --> true
> not false --> true
> not 5 --> false
> not "bears" --> false
```
