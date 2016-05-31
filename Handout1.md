#Classic Question #1: Coin Puzzle
You have 8 coins which are all the same weight, except for 1 which is slighlt heavier than the others (you don't know
which is heavier). You also have an old-style balance, which allows you to weight two piles of coins to see which one is
heavier (or if they are of equal weight). What is the fewest number of weighings that you can make which tell you which
coin is the heavier one?

Good answer: Weigh 3 coins against 3 coins. If one of the groups is heavier, weigh one of its coins against another one of
its coins; this allows you to identify the heavy coin. If the two groups balance, weigh the two leftover coins.

Not-so-good answer: Weigh 4 coins against 4 coins. Discard the lighter coins, and weigh 2 coins against 2 coins. Discard
the lighter coins and weigh the remaining two coins.

#Question: Searching Through an Array
Given a sorted array of integers, how can you find the position of a particular integer x?

Good answer: Use binary search. Compare the number in the middle of the array with x. If it is equal, we are done. 
If the number is greater, we know to look in the second half of the array. If it is smaller, we know to look in the first
half. We can repeat the search on the appropriate half of the array by comparing the middle element of that array with x, 
once again by narrowing our search by a factor of 2. We repeat this process until we find x. This algorithm takes O(logn)
time.

Not-so-good answer: Go through each number in order to compare it to x. This algorithm takes O(n) time.

#Parallelism

#Threads and Processes:
A computer will often appear to be doing many things simultaneously, such as checking for new email messages, saving a 
Word document, and loading a website. Each program is a separate "process". If a process has several threads, they appear
to run simultaneously. For example, an email client may have had one thread that checks for new email messages and one
thread for GUI so that it can show a button being pressed.In fact, only one thread is run at any given time. The processor
switches between threads so quickly that they appear to be running simultaneously. 

Multiple threads in a single process have access to the same memory. By contrast, multiple processes have separate regions
of memory and can only communicate by special mechanisms. The processor loads and saves a separate set of registers for each
thread. 

Remember, each process has one or more threads, and the processor switches between threads. 

#Mutexes and Semaphores:
A mutex is like a lock. Mutexes and used in parallel programming to ensure that only one thread can access a shared resource
at a time. For example, say one thread is modifying an array. When it has gotten halfway through the array, the processor switches to another thread. If we were not using mutexes, the thread might not try to modify the arrays as well, which is
probably not what we want.

To prevent this, we could use a mutex. Conceptually, a mutex is an integer that starts at 1. Whenever a thread needs to alter an array, it locks the mutex. This causes the thread to wait until the number is positive and then decreases it by one.
When the thread is done modifying the array, it "unlocks" the mutex, causing the number to increase by one. If we are sure to lock the mutex before modifying the array and to unlock it when we are done, then we know that no two threads will modify the array at the same time. 

Semaphores are more general than mutexes. They differ only in that a semaphore's integer may start at a number greater than 1. The number at which a semaphore starts is the number of threads that may access the resource at once. Semaphores support
wait and signal operations, which are equivalent to the lock and unlock in mutexes.

#Synchronized Methods
Each object in Java has its own mutex. Whenever a synchronized method is called, the mutex is locked. When the method is
finshed, the mutex is unlocked. This ensures that only one synchronized method is called at a time on a given object. 

#Deadlock
Deadlock is a problem that sometimes arises in parallel programming. It is typified by the following, which is supposedly 
a law that came through the Kansas legislature: 

"When two trains approach each other at a crossing, both shall come to a full stop and niether shall start up again until 
the other is gone"

Strange as this sounds, a similar situation can occur using mutexes. Say we have two threads running the following code:

                             Thread 1:
                             acquire(lock1);
                             acquire(lock2);
                             [do stuff]
                             release(lock1);
                             release(lock2);
                             
                             Thread 2:
                             acquire(lock2);
                             acquire(lock1);
                             [do stuff]
                             release(lock2);
                             release(lock1);
                             
Suppose that thread 1 is executed to just after the first statement. Then the processor switches one to two and executes
both statements. Then, the processor switches back to thread 1 and executes the second statement. In this situation, thread
1 will be waiting for thread 2 to release lock1 and thread 2 will be waiting for thread1 to release lock2. Both threads
will be locked indefinitely. This is called deadlock. 

#Classic Question #2: Preventing Deadlock
How can we ensure that deadlock does not occur?
Answer: There are many possible answers to this problem, but the answer the interviewer will be looking for is this: we
can prevent deadlock if we assign an order to our locks and require the locks always be acquired in order. For example,
if a thread needs to acquire locks 1, 5, and 2, it must acquire lock1, followed by lock 2, followed by lock 5. That way
we prevent one thread trying to acquire lock 1 then lock 2 an another thread trying to acquire lock2then lock1, which could
cause deadlock.

