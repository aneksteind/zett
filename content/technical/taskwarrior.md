---
tags: [taskwarrior, todo]
---


# TaskWarrior cheat sheet


## add a task

```
task <filter> add <description>
task +tag add <description>
```

## list tasks

```
task <filter> list
task +tag list
```

## link dependencies

```
task <filter> add <desc> depends:<taskid>
task <filter> modify depends:<taskid>
```