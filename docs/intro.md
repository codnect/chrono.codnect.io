---
slug: /
sidebar_position: 1
---

# Introduction

Let's discover **Chrono in less than 5 minutes**.

## What is Chrono?

**Chrono** is a scheduler library that lets you run your tasks and code periodically. 
It provides different scheduling functionalities to make it easier to create a scheduling task.

## What you'll need

- [Golang](https://go.dev/dl/) version 1.13 or above.

Run the following Go command to install the Chrono package:

```bash
go get -u codnect.io/chrono
```

## Scheduling Functionalities
 Chrono provides the following scheduling functionalities.
 * **One-Shot**: Run tasks once at the specified time.
 * **Fixed Delay**: Run tasks with a fixed delay between the finish time of the last execution of the task and the start time of the next execution of the task
 * **Fixed Rate**: Run tasks at a fixed rate of seconds.
 * **Cron Expression**: Run tasks based on a cron expression.
