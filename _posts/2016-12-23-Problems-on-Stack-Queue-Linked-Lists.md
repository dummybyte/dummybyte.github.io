---
layout: post
title: "Problems on Stack, Queues and Linked Lists"
description: "Problems"
date: 2016-12-23
tags: [algorithm, stack, queues, linked list, data structures, problems]
comments: true
share: true
---
## Contents

- [Braces Validation](#braces-validation)
- [Reverse Linked List](#reverse-linked-list)
- [Clone Linked List](#clone-linked-list)
- [Detect loop in Linked List](#detect-loop-in-linked-list)
- [Stack implementation using Queues](#stack-implementation-using-queues)
- [Queue implementation using Stacks](#queue-implementation-using-stacks)
- [Adhoc Problem 1](#adhoc-problem-1)


### Braces Validation

Given a sequence of opening and closing braces, find whether the given sequence is a valid sequence or not. e.g. ((())) - valid,  (()()) - valid, ()()(  - invalid

**Solution:** This problem can be solved by using stack. Following is the algorithm:

* Traverse over the string, on encounter with '(' push it to the stack
* On encounter with ')' pop from the stack
* After having finished with the traversal, check if the stack is empty or not - if its empty - the given sequence is valid, if not empty - its invalid
For complete working code go to :

[BracketValidationCode](https://github.com/dummybyte/CodeBlog/blob/master/BracketValidation.cpp)


### Reverse Linked List

Given a linked list, reverse it.

* **Input:** head of the linked list to be reversed
* **Output:** head of the reverse linked list

**Solution:** Following is the algorithm: (3 pointers method)

* if there is single node or no node then return that node
* if there is two nodes then reverse those nodes and return the newHead
* if there are more nodes then:
* we will maintain 3 pointers namely- previous, current and newHead such that ```current = previous->next;``` and ```newHead = current->next;``` initially
* Now for each iteration of the loop, we will be reversing only current and previous nodes and this will result into breaking of linked list into two linked lists whose one head is current and other head is newHead after each iteration of the while loop.
* We just need to connect current and newHead each time

For the detail working code please see:

[Reverse Linked List](https://github.com/dummybyte/CodeBlog/blob/master/ReverseLinkedList.cpp)


### Clone Linked List
Clone a linked list with next and a random pointer

* **Input** head of linked list to be cloned
* **Output** head of the clone linked list

**Solution:** The solution would here be trivial if the given linked list didn't have the random pointer.
To solve this problem, lets see at following steps:

* First of all, we will insert nodes between all the two nodes of the given linked list such that

```
    newNode->next = oldNode->next;
    oldNode->next = newNode;
```
* One node we need to insert either at the beginning or at the end (we will insert at the end)
* Now we need to define the next and the random pointers for the newly inserted nodes

```
    newNode->next = oldNode->next->next;
    newNode->randomPtr = oldNode->randomPtr->next;
```

* Insert a node at the last node and configure it accordingly
For the full working code, see the following link:

[Clone Linked List with random ptr](https://github.com/dummybyte/CodeBlog/blob/master/CloneLinkedListRndPtr.cpp)


### Detect loop in Linked List
Detect whether a loop is present in linked list or not

* **Input** head of the linked list
* **Output** yes/no if a loop is present in the linked list

**Solution** The underlying idea which we will use here is that - Consider a circular track in where two atheletes are running. Now, consider both the athletes are running at different speeds i.e. one is faster than the other. Notice one thing- faster runner will cross the slower one at some point.
This idea we will use here to detect a loop in the linked list. Consider two pointers moving in the linked list and one is moving at twice the speed of the other. So once they get into loop(if the loop exist) they will certainly meet at some point and if they don't meet it means that there is no loop in the linked list.

[Detect Loop in Linked List](https://github.com/dummybyte/CodeBlog/blob/master/LoopInLinkedList.cpp)

**BrainStorm** Will the above logic work if the other pointer speed is 3x,4x... times the first one?

### Stack implementation using Queues

Implement Stack using Queues

**Solution:** We know that Stack follows LIFO property. Now our target is to implement ```push()``` and ```pop()``` using Queues. We will be doing this by using two Queues. Lets call the queues as Q1 and Q2. Now say an ```push()``` request comes, then we will push that element to Q1 i.e. keep on pushing the elements to Q1 as long as ```push()``` requests are coming. Now lets say a ```pop()``` query comes, then follow the following steps:

- keep on popping from the Q1 and pushing the popped element to Q2
- while popping check if Q1 is empty, if its empty, the last popped element is our output
- keep on doing that till Q1 is empty
- Now again keeping on popping from Q2 and pushing it to Q1
- Keep on doing that as long as Q2 is not empty

The above five steps are needed to be done, for each pop operation. Notice one thing here: we are using Q2 as supporting Queue (just to store popped elements from Q1). The last two steps are just to transfer elements from Q2 to Q1.

Following is the C++ code for the above(here I will be using STL Queues):

[Stack implementation using Queues](https://github.com/dummybyte/CodeBlog/blob/master/StackImplementationUsingQueues.cpp)

### Queue implementation using Stacks

Implement Queue using Stack/s

**Solution:** Queue follows FIFO property. So we will try to achieve FIFO by the use of two stacks. Lets call the stacks as S1 and S2. Now when a ```push()``` happens we will insert the element into S1 and whenever a ```pop()``` operation happens, then we will follow the following steps:

- keep on popping from S1 and push the corresponding element to S2
- keep on doing above till S1 is empty
- Now our target element is the top element of S2, so ```pop()``` it
- keep on popping from S2 and push the corresponding element to S1
- keep on doing the 4th step till S2 is empty

So what we are doing above?

We are just using the S2 as a supportive stack to preserve the order of elements present in S1. Click on the link below to see the full working code:

[Queue implementation using Stacks](https://github.com/dummybyte/CodeBlog/blob/master/QueueImplementationUsingStack.cpp)

### Adhoc Problem 1

There is a stream of numbers. At any instant you need to output last n numbers which appeared in the stream.

Think about it before looking at the solution.

**Solution:** Maintain a queue of size n, and as the numbers keep on coming, keeping on pushing them to queue until queue is full. Now as the queue is full, the queue will have n elements.

Now as the numbers keep on coming, keep popping elements from the front end and pushing the new element from the rear end. Its like a pipe which has capacity of n elements.

This way you will maintain last n elements in the queue.
