# Elixir Notebook

[`n0b0dy-su`](https://github.com/n0b0dy-su)

## Caps

### Sorting order

`number < atom < reference < function < port < pid < tuple < map < list < bitstring`

### List and Tuples

- **performance of list concatenation depends on the length of the left-hand list**

```elixir
list = [1, 2, 3]
# fast
[0] ++ list
# slow
list ++ [4]
```

- **update or add elemts to a tupple requires create a new tuple**

### Operators

`++`

```elixir
#add right hand side list to the left hand side list

[1, 2, 3] ++ [4, 5, 6]
# return: [1, 2, 3, 4, 5, 6]
```

`--`

```elixir
#substract the right hand side list to the left hand side list
[1, 2, 3] -- [2]
#return: [1, 3]
```

### Booleans

`and`, `or`, `not`

- Just expect to evalute booleans
- Only execute right side if left side is not enough to determine the result

`&&`, `||`, `!`

- Use just if the arguments are non-booleans

### Matching

`^`

- Use to match against a variable’s existing value rather than rebinding the variable.

```elixir
 #Example:
 x = 1
 {^x, y} = {1, 3} 
```

`_`

- Use it to ignore a particular value in a match pattern

 ```elixir
 #Example:
 [head | _] = [1, 2, 3]
 #head returns: 1
 ```

### Case, Cond and If

#### Case

- Allows us to compare a value against many patterns until we find a matching one

 ```elixir
 case {1, 2, 3} do
  {1, x, 3} when x > 0 ->
   "Will match"
  _ ->
   "Would match, if guard condition were not satisfied"
 end
 # return: "Will match"
 ```

- **Use `_` clause would match any value**, if not match any value and `_` is unused then raise an error.

#### Cond

- Use like a else if clause, two or more conditions

#### If and Unless

- Only for check one condition
- `if` check for a truthy value
- `unless` check for a false value
- Support `else` clause
- Both are **macros**

#### do/end

- Can be used in a keyword list with an if and a else too

```elixir
# Example
if true, do: "its true", else: "its false"
# returns: "its true"
```
- In **blocks** do not require comma

```elixir
if true do
 a = 1 + 2
 a + 10
end

# returns: 13
```

- In functions use explicit parentheses to work

```elixir
# Example
is_number(if true do
 1 + 2
 end)

 # returns true
```

### Binaries, strings, and charlists

[`unicode standard`](https://unicode.org/standard/standard.html)
[`code points`](https://en.wikipedia.org/wiki/Code_point)

- Some characters like **é** are the combination of two characters like **e** and **´**

```elixir
# to see the iiner binary representation concatenate the null bye <<0>>
# Exmaple
"hello" <> <<0>>
# returns: <<104, 101, 108, 108, 111, 0>>

# Or with IO.inspect/2

IO.inspect("hello", binaries: :as_binaries)
# returns: <<104, 101, 108, 108, 111, 0>>
```

`::`

- Use to specify the numbers of bits to an bitstring item
- The values that exceeds the number of bits to store it are truncate

```elixir
# Example

<<1>> === <<257>>
# returns: true
```

Its beacuse **257** need 9 bits to be stored `100000001` and just have 8 bits for default, with the truncate turn on `00000001` and its the bit representation of **1**

#### Binary

Its a bitstring whene their number of bits is divisble by. Its mean al binary are bitstring but not all bitsstring all binary.

In a pattern match the `binary` modifier, match a binary with a unkonown size with the element thau use the modifier and all the next items.

```elixir
# Example

<<0, 1, x :: binary>> = <<0, 1, 2, 3>>

# the value of x is: <<2, 3>>
```

The `binary-size(n)` modifier specify the number **n** of bytes to match in a binary

```elixir
# Example

<<head::binary-size(2), rest::binary>> = <<0, 1, 2, 3>>

# head has  <<0, 1>> as value
# rest has <<2, 3>> as value
```

- Multiple  byte characters in a pattern match just match the first byte, to solve this use `::utf8` modifier.

```example
<<x::utf8, rest::binary>> = "über"

#x is equal to ""ü"
# and the rest is "ber"
```

### TODO
> - [ ] continue in charlist
> - [ ] Check [Operators page](https://hexdocs.pm/elixir/operators.html)
> - [ ] Check [Guards page](https://hexdocs.pm/elixir/patterns-and-guards.html#guards)
