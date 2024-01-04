---
sidebar_position: 6
---

# Shutting Down a Scheduler

The **Shutdown()** method doesn't cause immediate shut down of the Scheduler and returns a channel. 

:::warning

It will make the **Scheduler** stop accepting new tasks and shut down after all running tasks finish their current work.

:::

```go
taskScheduler := chrono.NewDefaultTaskScheduler()

/* ... */

shutdownChannel := taskScheduler.Shutdown()
<- shutdownChannel

/* after all running task finished their works */
```
