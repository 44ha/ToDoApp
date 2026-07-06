# To-Do App (C++)

Console task manager using the Factory Method pattern. Supports three task types with different behaviors on display.

## Task types

**Regular** — just a description.

**Priority** — description with a priority level (1-5).

**Timed** — description with a due date set in hours or days. Shows remaining time or marks as expired when you view it.

## Design

`Task` is an abstract base class with a pure virtual `show()` method. `TaskFactory` is an abstract factory; each subclass (`RegularTaskFactory`, `PriorityTaskFactory`, `TimedTaskFactory`) knows how to prompt the user for the right inputs and construct the correct task type.

## Build

```bash
g++ -std=c++17 -o todoapp ToDo.cpp
./todoapp
```

## Usage

```
1. Add Regular Task
2. Add Timed Task
3. Add Priority Task
4. Show All Tasks
5. Exit
```

Example session:

```
Enter your choice: 1
Enter task description: Buy groceries
Regular Task: Buy groceries

Enter your choice: 3
Enter task description: Finish report
Enter priority level (1-5): 4
Priority Task: Finish report [Priority: 4]

Enter your choice: 2
Enter task description: Submit assignment
Set duration:
1. In Days
2. In Hours
Choose: 1
Enter number of days: 2
Timed Task: Submit assignment (Due: 2026-10-19 13:45:00) [Time Left: 2d 0h 0m 0s]
```

## Notes

Tasks are stored in memory only — there is no persistence between runs. The `<chrono>` library is used to store and compare due times.
