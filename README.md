
# Task Time Report

> Calculate spent time for taskwarrior projectstasktime

Reads tasks by project from [taskwarrior](http://www.taskwarrior.org) and calculates time spent with this project for each task.

## Usage

```
tasktime [options] <project>
```

### Parameters

    -h, --help              Show this help
    -a, --all               Print all project tasks (include task with no time tracking)
    -c, --format-csv        Print output in CSV format
    -m, --format-md         Print output in Markdown Table format
    -t, --task [cmd]        Change task command


### Setup

Add `journal.time=on` to your taskwarrior configuration (`.taskrc`)

Taskwarrior will save start and stop annotations from now on.

Only these annotations are evaluated by tasktime.


### Note time with taskwarrior

taskwarrior has the operations *start* and *stop*.

This information is used to calculate the spent time.

Use `start` and `stop` on tasks you work on.

Example:

    task 2 start

    # Work on task 2...

    task 2 stop

## Examples

### Default 

    Project: myproject

    Do something cool
        Duration: 00:13:05
    Do something really cool
        Duration: 02:18:35

    Sum: 02:31:40


### All project tasks

    Project: myproject

    Do something cool
        Duration: 00:13:05
    Do something boring
    Do something really cool
        Duration: 02:18:35

    Sum: 02:31:40



### Markdown output

To allow for easier text parsing the default csv delimeters and string escape characters or `|` and \`

The task uuid is included to assist in editing tasks that may continue running after you stop working on them

__Project:__ myproject  

|TASKID|DURATION|DESCRIPTION|
| --- | --- |--- |  
|d402b020-d049-4523-b5fa-e2dbbca54f6a|01:00:00|taskwarrior reports|
|d402b020-d049-4523-b5fa-e2dbbca5123a|92:06:12|taskwarrior extra reports|

---  

__Total:__ 93:06:12


```md
__Project:__ myproject  

|TASKID|DURATION|DESCRIPTION|
| --- | --- |--- |  
|d402b020-d049-4523-b5fa-e2dbbca54f6a|01:00:00|taskwarrior reports|
|d402b020-d049-4523-b5fa-e2dbbca5123a|92:06:12|taskwarrior extra reports|

---

__Total:__ 93:06:12
```


### CSV output

    `PROJECT`|`TASKID`|`DURATION`|`DESCRIPTION`
    `dev`|`d402b020-d049-4523-b5fa-e2dbbca54f6a`|`01:00:00`|`taskwarrior reports`
    `dev`|`d402b020-d049-4523-b5fa-e2dbbca5123a`|`92:06:12`|`taskwarrior extra reports`
    =================================================
    `Sum`|`93:06:12`


### Contact and copyright

tasktime is distributed under the MIT license. See [http://www.opensource.org/licenses/MIT](http://www.opensource.org/licenses/MIT) for more information.
