# Linear RPC

## Overview
[linear-rpc](https://github.com/linear-rpc)
includes
'[msgpack-rpc](https://github.com/msgpack-rpc/msgpack-rpc/blob/master/spec.md)
\+ α' implementations for some programming languages.  

_Although we know that there are some implementations, we need WebSocket, SSL transport etc.. And we also need 'Request from a server', 'Notify from a server' functions etc.._  
_So we implement them._

## What is '+ α'
linear-rpc is almost the same as msgpack-rpc, but there is just a little bit difference.

### Transports
Our implementation can use __TCP, SSL, WebSocket and WebSocket-Secure__ transports now.  
(But there are some limitations on each programming language. Please refer to README.md etc. in each repository)

### Request Message
All of existing implementations can send 'Request' from only a client. And in the case of receiving 'Request' at a client, they throw an exception or just ignore it.  
But linear-rpc can send 'Request' from a server and can handle 'Request' at a client.
* Msgpack-RPC  

```
[type, msgid, method, params]  
params := Array of arbitrary object
```

> params  
> The array of the function arguments. The elements of this array is arbitrary object.  
> [https://github.com/msgpack-rpc/msgpack-rpc/blob/master/spec.md#params](https://github.com/msgpack-rpc/msgpack-rpc/blob/master/spec.md#params)
* Linear-RPC
```
params := Arbitrary object
```
> params will be allowed without an array

### Response Message
linear-rpc can send and receive 'Response' on both a server and a client.
* Msgpack-RPC and Linear-RPC  
```
[type, msgid, error, result]  
```
> no difference.

### Notification Message
linaer-rpc can send and receive 'Notification' on both a server and a client.
* Msgpack-RPC  
```
[type, method, params]  
params := Array of arbitrary object
```
> params  
> The array of the function arguments. The elements of this array is arbitrary object.  
> [https://github.com/msgpack-rpc/msgpack-rpc/blob/master/spec.md#params-1](https://github.com/msgpack-rpc/msgpack-rpc/blob/master/spec.md#params-1)
* Linear-RPC
```
params := Arbitrary object
```
> params will be allowed without an array

## FAQ

### There are few tests!
Sorry. We have some more test codes and do test with some real products, but they are so dirty and complicated.  
We'll add more tests that work with Open CI platform gradually.  

### How about android (java)?
We have created linear-java internal.  
But we are using JNI like an implementation of linear-objc and android platform supports many cpu arch.  
Since we can't support all of them (Even if we receive some issues or pull requests, we can't confirm it.), we do not publish. And we don't have a plan to create Java native now.

## Contributions
__Please feel free to create issues or send pull requests__

_We'd appreciate any issues and pull requests._  
_We may not be able to replay quickly, but we surely will._

## Thanks to
Great thanks to all of the developers who contribute several open source software!
