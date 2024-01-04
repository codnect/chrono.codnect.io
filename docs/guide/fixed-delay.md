---
sidebar_position: 2
---

# Scheduling a Task with Fixed Delay

Let's schedule a task to run with a fixed delay between the finish time of the last execution of the task and the start time of the next execution of the task. 
The fixed delay counts the delay after the completion of the last execution.

```go
taskScheduler := chrono.NewDefaultTaskScheduler()

task, err := taskScheduler.ScheduleWithFixedDelay(func(ctx context.Context) {
    log.Print("Fixed Delay Task")
    time.Sleep(3 * time.Second)
}, 5 * time.Second)

if err == nil {
    log.Print("Task has been scheduled successfully.")
}
```

Since the task itself takes 3 seconds to complete and we have specified a delay of 5 seconds 
between the finish time of the last execution of the task and the start time of the next execution of the task, 
there will be a delay of 8 seconds between each execution.

**WithStartTime** and **WithLocation** options can be combined with this.