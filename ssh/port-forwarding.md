### ssh through a router without port forwarding

> <https://superuser.com/questions/595989/ssh-through-a-router-without-port-forwarding/595991#595991>

connect from `server` to something outside, for example `other_server`

1. **On `server`**, execute

```
[user@server]$ ssh -R 8022:localhost:22 <username>@<my_other_server>
```

to initiate ssh remote port forwarding to "my_other_server" and open port 8022
there which will forward back to me on port 22

2. **On `my_other_server`**, ssh back to `server` using the forwarded port

```
[user@my_other_server]$ ssh -p 8022 <username>@localhost
```

piggybacking on the `server` -> `other_server` tunnel (reverse tunnel)
