---
sidebar_position: 5
---

# Canceling a Scheduled Task

**Schedule** methods return an instance of type **ScheduledTask**, which allows us to cancel a task or to check if the task is canceled. 


:::warning

The **Cancel** method cancels the scheduled task but running tasks won't be interrupted.

:::

```go
taskScheduler := chrono.NewDefaultTaskScheduler()

task, err := taskScheduler.ScheduleAtFixedRate(func(ctx context.Context) {
    log.Print("Fixed Rate of 5 seconds")
}, 5 * time.Second)

/* ... */

task.Cancel()
```
