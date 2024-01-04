---
sidebar_position: 4
---

# Scheduling a Task using Cron Expression

Sometimes **Fixed Rate** and **Fixed Delay** can not fulfill your needs, and we need the flexibility of cron expressions to schedule the execution of your tasks. 
With the help of the provided **ScheduleWithCron** method, we can schedule a task based on a cron expression.

```go
taskScheduler := chrono.NewDefaultTaskScheduler()

task, err := taskScheduler.ScheduleWithCron(func(ctx context.Context) {
    log.Print("Scheduled Task With Cron")
}, "0 45 18 10 * *")

if err == nil {
    log.Print("Task has been scheduled")
}
```

In this case, we're scheduling a task to be executed at 18:45 on the 10th day of every month

By default, the local time is used for the cron expression. However, we can use the **WithLocation** option to change this.

:::warning

**WithStartTime** option cannot be used with **ScheduleWithCron**.

:::

```go
task, err := taskScheduler.ScheduleWithCron(func(ctx context.Context) {
    log.Print("Scheduled Task With Cron")
}, "0 45 18 10 * *", chrono.WithLocation("America/New_York"))
```

In the above example, Task will be scheduled to be executed at 18:45 on the 10th day of every month in America/New York time.
