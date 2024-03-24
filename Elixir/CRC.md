# CRC “Construct, Reduce, Convert”

## Layers
- Constructors create a term of the core type
from convenient inputs. 
-Reducers transform a term of the core type to
another term of that type. 
-Converters convert the core type to some other type

## Example

```elixir
iex(1)> defmodule Number do
...(1)> def new(string), do: Integer.parse(string) |> elem(0)
...(1)> def add(number, addend), do: number + addend
...(1)> def to_string(number), do: Integer.to_string(number)
...(1)> end
```

## Where Phoenix comes into Play

- Phoenix processes requests with the CRC pattern (Conn)
- Phoenix itself serves as the constructor. It builds a
common piece of data that has both request data and response information.
Initially, the request data is populated with information about the request,
but the response data is empty. Then, Phoenix builds a response, piece by
piece, with small reducers. Finally, Phoenix converts the connection to a
response with the render/1 converter.

## Phoenix uses Plugs

- Plugs are reducer functions
- They take a Plug.Conn struct as the first argument
- They return a Plug.Conn struct.
