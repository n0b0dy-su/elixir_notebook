# Elixir Notebook

[`n0b0dy-su`](https://github.com/n0b0dy-su)

### Sorting order

`number < atom < reference < function < port < pid < tuple < map < list < bitstring`

### List and Tuples

**performance of list concatenation depends on the length of the left-hand list**

```elixir
list = [1, 2, 3]
# fast
[0] ++ list
# slow
list ++ [4]
```

**update or add elemts to a tupple requires create a new tuple**

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
> - **Just expect to evalute booleans **
> - **Only execute right side if left side is not enough to determine the result**

`&&`, `||`, `!`
> - **Use just if the arguments are non-booleans**

### Matching

`^`
> - **use to match against a variable’s existing value rather than rebinding the variable.**
> ```elixir
> #Example:
> x = 1
> {^x, y} = {1, 3} 
> ```

`_`
> - **Use it to ignore a particular value in a match pattern**
> ```elixir
> #Example:
> [head | _] = [1, 2, 3]
> #head returns: 1
> ```

### Case, Cond and If

**Case**
> - **allows us to compare a value against many patterns until we find a matching one**
> ```elixir
> case {1, 2, 3} do
> 	{1, x, 3} when x > 0 ->
> 		"Will match"
>	_ ->
>		"Would match, if guard condition were not satisfied"
> end
> # return: "Will match"
> ```
> - **Use `_` clause would match any value**, if not match any value and `_` is unused then raise an error.


### TODO

> - [ ] **CONTINUE ON IF AND UNLESS**
> - [ ] Check [Operators page](https://hexdocs.pm/elixir/operators.html)
> - [ ] Check [Guards page](https://hexdocs.pm/elixir/patterns-and-guards.html#guards)
