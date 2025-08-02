![unit-tests](https://github.com/lazeroffmichael/ticktick-py/workflows/unit-tests/badge.svg)
[![documentation](https://img.shields.io/badge/docs-mkdocs%20material-blue.svg?style=flat)](https://lazeroffmichael.github.io/ticktick-py/)

# ticktick-py
## Unofficial TickTick API Client for Python 3

## [Full Documentation](https://lazeroffmichael.github.io/ticktick-py/)

## Description
`ticktick-py` is an unofficial API library for interacting with [TickTick.com](<https://www.ticktick.com/>). 
It allows
users a way to interact with their [TickTick](<https://www.ticktick.com/>) account 
using [Python](https://www.python.org/). 

## Features

The library automatically fetches all the tasks, tags, lists, and more linked to your profile and stores them in a 
dictionary named [`state`](docs/usage/api.md).

 - [Tasks](docs/usage/tasks.md)
    - Create, Update, and Delete Tasks
    - Acquire all your uncompleted tasks
    - Move tasks easily between projects
    - Acquire all completed tasks in a certain date range
 - [Tags](docs/usage/tags.md)
    - Batch create, update, and delete tags
    - Create tags with parameters that are not usually allowed: `\\ / " # : * ? < > | Space`
 - [Projects](docs/usage/projects.md)
    - Batch create, update, and delete 'lists' (projects)
    - Batch archive projects

### Example: Creating A Task

Lets create a task in our ```inbox``` titled "Get Groceries"

``` python
name = 'Get Groceries'                      # Task Name
local_task = client.task.builder(name)      # Create a dictionary for the task
groceries = client.task.create(local_task)  # Actually create the task
```

### Result

A simplified dictionary for the newly created task is returned.

```python
print(groceries)

{'id': '60c6a40b8f083f896c9444a0', 'projectId': 'inbox115781412', 'title': 'Get Groceries', 'timeZone': '', 
 'reminders': [], 'priority': 0, 'status': 0, 'sortOrder': -3298534883328, 'items': []}
```
You can retrieve the full dictionary with every parameter by using the `get_by_id` method. 

```python
full_task = client.get_by_id(groceries['id'])
print(full_task)

{'id': '60c6a40b8f083f896c9444a0', 'projectId': 'inbox115781412', 'sortOrder': -3298534883328, 
 'title': 'Get Groceries', 'timeZone': '', 'isFloating': False, 'reminder': '', 'reminders': [], 
 'priority': 0, 'status': 0, 'items': [], 'modifiedTime': '2021-06-14T00:34:19.907+0000', 'etag': 't8xnwewi', 
 'deleted': 0, 'createdTime': '2021-06-14T00:34:19.907+0000', 'creator': 113581412, 'tags': [], 'kind': 'TEXT'}
```

**Created Task In `TickTick`**

![image](https://user-images.githubusercontent.com/56806733/121826787-7c5ef980-cc6e-11eb-8483-745df39e973b.png)

Most methods will return the object that was changed. Consult the [usage](docs/usage/api.md) documentation for more information on specific methods.

    
## Installation

Note: `ticktick-py` requires [Python 3.6](https://www.python.org/downloads/) or above.

```md
pip install ticktick-py
```
