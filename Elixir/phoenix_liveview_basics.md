# Basics

## Sockets
- Every running live view keeps data describing state
in a socket. You’ll establish and update that state by interacting with the map
within the socket’s :assigns key.

```elixir
Phoenix.LiveView.Socket.__struct__
#Phoenix.LiveView.Socket<
id: nil,
endpoint: nil,
view: nil,
parent_pid: nil,
root_pid: nil,
router: nil,
assigns: %{__changed__: %{}}, #contains data describing state
transport_pid: nil,
...
>
```

## LiveView Lifecycle Callbacks

- mount/3 when our process starts and sets up the Socket
- render/1 function when it’s time to render
- handle_event/3 function when someone clicks links

## LiveView Loop
- receive events, change the state, and render the page again.
