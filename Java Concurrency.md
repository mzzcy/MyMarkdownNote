####Concurrency

#####Method 1
**Use Runnable interface:**
`implements Runnable`
`run(){}`
`new Thread(nwe Runnable()).start();`



>`Thread.yield()`:is a suggestiont to the thread scheduler.

**Priority**
`getPriority()`:read the priority.
`setPriority()`:change priority.
>`Thread.currentThread().setPriority();`:call current thread.

#####Method 2
**Use Subclass of Thread:**
`xxx extends Thread`
`new xxx().start();`