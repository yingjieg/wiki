# Event Loop

An event loop has one or more task queues. A task queue is a set of tasks.
event loop 拥有一个或多个task queue。A task queue是多个任务的集合。

> Task queue并不是传统的队列，而是集合，因为在Event Loop处理模型中，它会从所选队列中获取第一个**可执行的task**，而不是简单的将第一个**task**出列。
