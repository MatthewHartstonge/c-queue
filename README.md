# c-queue
@author: Matt Hartstonge (2015)

A C based concurrent, FIFO queue.

A concurrent FIFO Queue written in C. Takes in any type of data as
underlying implementation is a linked list containing pointers to
the actual data. Needs to be cast to (void *).

Uses POSIX semaphores and mutexes. Tested under linux, unsure of
operation on Windows.

## Usage ##
  ```C
  Queue *queue_alloc(int size);
  void enqueue(Queue *queue, void *item);
  void *dequeue(Queue *queue);
  ```

## Code Examples ##
  Below is a struct for the purposes of providing an example.
  ``` C
  typedef struct {
      int value;
  } Task;
  ```
  
  Initalisation of a queue
  ``` C
  Queue *queue = queue_alloc(QUEUE_SIZE);
  ```
  
  Enqueuing (a Task) an item into a given Queue.
  ``` C
  Task *task = (Task*)malloc(sizeof(Task));
  task->value = i;
  enqueue(queue, task);
  ```
  
  Dequeuing (a Task) an item from a given Queue.
  ``` C
  Task *task = (Task*)dequeue(queue);
  ```

