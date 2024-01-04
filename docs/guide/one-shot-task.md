---
sidebar_position: 1
---

# Scheduling a One-Shot Task

The Schedule method helps us schedule the task to run once at the specified time. 
In the following example, the task will first be executed 1 second after the current time. 
**WithTime** option is used to specify the execution time.

```go
taskScheduler := chrono.NewDefaultTaskScheduler()
now := time.Now()
startTime := now.Add(time.Second * 1)

task, err := taskScheduler.Schedule(func(ctx context.Context) {
    log.Print("One-Shot Task")
}, chrono.WithTime(startTime))

if err == nil {
    log.Print("Task has been scheduled successfully.")
}
```

:::warning

**WithStartTime** option can be used to specify the execution time. But It's **deprecated**.
:::


```go
taskScheduler := chrono.NewDefaultTaskScheduler()

task, err := taskScheduler.Schedule(func(ctx context.Context) {
    log.Print("One-Shot Task")
}, chrono.WithStartTime(now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second()+1))

if err == nil {
    log.Print("Task has been scheduled successfully.")
}
```

Since the task itself takes 3 seconds to complete and we have specified a delay of 5 seconds 
between the finish time of the last execution of the task and the start time of the next execution of the task, 
there will be a delay of 8 seconds between each execution.

**WithStartTime** and **WithLocation** options can be combined with this.