```
$ brew install erlang
$ brew install elixir
```



guessing_game.ex

```elixir
# Elixir convintion: name file.ex snake_case and name defmodule CamelCase
defmodule GuessingGame do
  #  will only match when a > b
  def guess(a, b) when a > b, do: guess(b, a)

  def guess(low, high) do
    #  IO.gets to get string from the user
    #  #{} -> for string interpulation
    answer = IO.gets("Hmm... maybe you're thinking of #{mid(low, high)}?\n")

    # String.trim to remove \n from the end of user string (system add it to make new line)
    case String.trim(answer) do
      "bigger" ->
        bigger(low, high)

      "smaller" ->
        smaller(low, high)

      "yes" ->
        "I knew I could guess your number!"

      _ ->
        # ~s{} to evaluate the entire text as string and accept "" inside the string
        IO.puts(~s{Type "bigger", "smaller" or "yes"})
        guess(low, high)
    end
  end

  def mid(low, high) do
    # div function return Integer from divid  two numbers with out remide  # div(5, 2) -> 2
    div(low + high, 2)
  end

  def bigger(low, high) do
    # min -builtin function- here to chose high if result og mid more than high like bigger(25, 25) -> 26
    new_low = min(high, mid(low, high) + 1)
    guess(new_low, high)
  end

  def smaller(low, high) do
    new_high = max(low, mid(low, high) - 1)
    guess(low, new_high)
  end
end


```



```
$ iex  # elixir shell

iex> c "guessing_game.ex"  # to compile the file
iex> GuessingGame.mid(2,9) -> 5

iex> i :hany  # to get information about thing
iex> [:foo, :bar] ++ [1, 2, 3]  # to connect two lists
# a list in Elixir ia a linked array which accepts any mixed type

iex> "asdf" <> "ghjk"  # to connect two bainary strings

iex> i 'asdf' # Data type -> List  # a list of caracters
iex> i "asdf" # Data type -> BitString  # a bainary string


```



vsc note:

```
Ctrl+Shift+Enter  -> New Line Up

Command + x  -> delete the current line

Command + b  -> open and close file explorer

```

