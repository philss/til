# Working with "with" macro

There is a macro very useful when you need to match a "chain" of cases, like:

```elixir
case patt1 do
  {:ok, result1} ->
    case do_something(result1) do
      {:ok, result2} ->
        result2
      {:error, error} -> error
    end
  {:error, error} -> error
end
```

Instead of doing that, you could do:

```elixir
with {:ok, result1} <- patt1,
     {:ok, result2} <- do_something(result1) do
  result2
else
  {:error, error} ->
    error
end
```

## Matching a case or return self

This is useful when you want to check for a pattern or return the value itself.
Example:

```elixir
with {:system, env_var} <- value, do: System.get_env(env_var)
```

The value return will be the env variable result in case the pattern matched, or the original `value`.
