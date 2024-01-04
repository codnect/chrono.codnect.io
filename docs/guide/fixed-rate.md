---
sidebar_position: 3
---

# Schedule Task at a Fixed Rate

Let's schedule a task to run at a fixed rate of seconds.

```go
taskScheduler := chrono.NewDefaultTaskScheduler()

task, err := taskScheduler.ScheduleAtFixedRate(func(ctx context.Context) {
    log.Print("Fixed Rate of 5 seconds")
}, 5 * time.Second)

if err == nil {
    log.Print("Task has been scheduled successfully.")
}
```

The next task will run always after 5 seconds no matter the status of the previous task, which may be still running. So even if the previous task isn't done, the next task will run. 
We can also use the **WithStartTime** option to specify the desired first execution time of the task.

```go
now := time.Now()

task, err := taskScheduler.ScheduleAtFixedRate(func(ctx context.Context) {
    log.Print("Fixed Rate of 5 seconds")
}, 5 * time.Second, chrono.WithStartTime(now.Year(), now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second() + 2))
```

When we use this option, the task will run at the specified execution time and subsequently with the given period. In the above example, the task will first be executed 2 seconds after the current time.

We can also combine this option with **WithLocation** based on our requirements.

```go
now := time.Now()

task, err := taskScheduler.ScheduleAtFixedRate(func(ctx context.Context) {
	log.Print("Fixed Rate of 5 seconds")
}, 5 * time.Second, chrono.WithStartTime(now.Year(), now.Month(), now.Day(), 18, 45, 0),
    chrono.WithLocation("America/New_York"))
```

In the above example, the task will first be executed at 18:45 of the current date in America/New York time. 
If the start time is in the past, the task will be executed immediately.