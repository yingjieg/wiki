# NodeJS Event Loop

> Node.js is single-threaded

Node.js has a V8 in it, and the code runs in the main thread where event-loop runs
Node.js 拥有V8引擎，代码在主线程中运行，包括event-loop

But As we know, the Node.js is not just V8. There are many APIs(C++), and all this stuff is managed by __Event Loop__, implemented via __libuv__.
但是就我们所知，Node.js不仅仅包含V8，还包括很多C++的API调用， 通过Libuv，这些都被EventLoop所管理，

C++ is working in back of javaScript code and it has access to threads. If you run the JavaScript synchronous method which has been called from Node.js, it will always run in the main thread. But if you run some asynchronous thing, it will not always run in the main thread: depending on what method you use, the event-loop can route it to one of the APIs and it __can be processed__ in another thread.

Let's see an example of CRYPTO. It has many CPU intensive methods; some of them are synchronous, some of them are asynchronous. Let's take a `pbkdf2()` method. If we run its synchronous version in 2-Core processor and make 4 calls, and if the execution time of one call is 2ms, the execution time of all 4 calls will be 4*pbkdf2() execution time(8ms).

But if we run the asynchronous version of this method in the same CPU, the execution time will be 2*pbkdf2() execution time, because the processor will take __default 4 threads__ (you will understand why and how below), host it in two processes and process the pbkdf2() in them.

![image.png](https://upload-images.jianshu.io/upload_images/77645-633e8c746937d478.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
__So Node.js runs things in parallel for you if you give it a chance.__

Node.js uses a pre-allocated set of threads called a __thread pool__, and if we do not specify how many threads to open, it will open 4 threads by default. We can increase it by setting

```bash
UV_THREADPOOL_SIZE=110 && node index.js

or

process.env.UV_THREADPOOL_SIZE=62 from code.
```

> __Epoll__(unix), __Kqueue__(BSD), __IOCP__(Win)

## Event Loop

It is infinite while loop, calling Epoll (kqueue) "wait" or "poll" when something interesting (callback, event, fs) happens for a Node.js; it routes that to Node.js, and exits when there is nothing to wait in Epoll.

![image.png](https://upload-images.jianshu.io/upload_images/77645-e8e943f6087694d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
