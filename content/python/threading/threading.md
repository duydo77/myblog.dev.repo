https://www.tutorialspoint.com/python/python_multithreading.htm
https://community.codenewbie.org/rwalroth/threads-locks-and-queues-1835

## 1. Starting a new thread

Multi threads mean running several different programs concurrntly. The benefits of this method are:

- Multiple threads within a process share the same data space with the main thread. This help threads comunitate with each other more easily than if they were seperate processes(run multi .py files)
- Threads sometimes called light-weight processes. They are cheap than processes because they don't require much memory overhead.

A thread has a **begining**, an **execution sequence** and a **conclusion**.  It has an instruction pointer that keeps track of where within its context it is currently running.

- It can be pre-empted (interupt)
- It can temporarily be put on hold (also known as sleeping) while other threads are running - this is called yielding.

There are two modules for threading in python: thread and threading. threading module is more powerfull. We will get more at it later. Now look over an example using thread modules:

```python
import thread
import time

# Define a function for thread
def print_time(threadName, delay):
	count = 0
	while count < 5:
		time.sleep(delay)
		count += 1
		print("%s: %s" % ( threadName, time.ctime(time.time())))

# Create two threads as follows
try:
	thread.start_new_thread(print_time, ("Thread-1", 2))
	thread.start_new_thread(print_time, ("Thread-1", 2))
except:
	print("Error: unable to start thread")

while 1:
	pass
```



## 2. The Threading Module

Threading module included with Python 2.4 and newer, exposes all the mehods of the thread module and provides some additional methods:

- threading.actionCount()
- threading.currentThread()
- threading.enumerate()

- run()
- start()
- join([time])
- isAlive()
- getName()
- setName()

### 2.1. Creating Thread Using Threading Module

1. Define a new subclass of ther Thread class.
2. Overide the \_\_init\__(self [, args]) method to add additional arguments.
3. Overide the run() method to implement what the thread should do when started

```python
#!/usr/bin/python

import threading
import time

exitFlag = 0

class myThread (threading.Thread):
   def __init__(self, threadID, name, counter):
      threading.Thread.__init__(self)
      self.threadID = threadID
      self.name = name
      self.counter = counter
   def run(self):
      print "Starting " + self.name
      print_time(self.name, 5, self.counter)
      print "Exiting " + self.name

def print_time(threadName, counter, delay):
   while counter:
      if exitFlag:
         threadName.exit()
      time.sleep(delay)
      print "%s: %s" % (threadName, time.ctime(time.time()))
      counter -= 1

# Create new threads
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# Start new Threads
thread1.start()
thread2.start()

print "Exiting Main Thread"
```

### 2.2. Synchonizing Threads



## 3. Multithreaded Priority Queue

multithreading.Lock() likes a key. Any thread call lock().acquire(), this thread will has a priority to run, other threads will wait until this thread calls lock().release(). So the data will be synchronize.