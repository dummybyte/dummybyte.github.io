---
layout: post
title: "Stack & Queues"
description: "Introduction"
date: 2016-12-22
tags: [algorithm, stack, queues, data structures]
comments: true
share: true
---
## Contents
- [Stack](#stack)
- [Queue](#queue)

## Stack

Stack is data structure which follows **LIFO** (Last in first out) property. Stack supports two operations namely:

* **```push(element)```** - put the element in Queue
* **```pop()```** - remove the element from the Queue and return the element

Lets us understand these operations (Push, Pop) through the following example:

Say a woman is making chappatis and after each of the chappatis are finished, she is keeping them in a container. So how would this look like -

First the container is empty
* When the first chappati is finished making, it is placed in the container (Push)
* When the second chappati is finished, it is placed in the container on the top of the first chappati (again a Push)

Similarly it happens for all the n chappatis she makes - it means that **nth** chappati is at the top and the 1st chappati is at bottom of the container

Now suppose you sat for having dinner, and you asked for a chappati
So she will bring you the nth  chappati first (Pop), now **(n-1)th** is at top in the container
And if you asked for another chappati, she will bring you the **(n-1)th** one (again Pop)

What happened here?

Your container behaved liked a stack. Initially your stack was empty (when there were no chappatis in the container). Once she starts putting chappatis in the container (Push operation), the stack started to fill - the last chappati put into the container represents the top of the stack. When you started having dinner, the Pop operation began. Pop only allows the top of the stack to be removed and once its removed, the new element which is on the top of the stack becomes the top element.

We will now see how to implement stack in C++ (There is also an inbuilt stack in C++, its better to use that but here we will see how to implement stack if you don't want to use inbuilt stack):

[StackCode](https://github.com/dummybyte/CodeBlog/blob/master/Stack.cpp)

#### Time Complexity

As you can see there are no loops and only insertion and deletion operation over vector which is O(1) for each **push** and **pop** operation.

Note: The stack can be implemented by arrays as well and as well by linked list.
For arrays, we will have constraint of the size of the stack which will be equal to size of the array declared. We need to just maintain the index of the top element of the stack - the variable top will point to top most element of the stack. In case of pop(), just decrement the top variable and in case of push(int x), just overwrite the next index of the array and increment top.

If you are implementing by linked list, we need to maintain two pointers one will be head and the other will be top. In case of pop(), just need to change the previous node pointer to null and free the current node. And incase of push(), create a node and point the previous top to current node and update top to current node.


## Queue
Queue is a data structure which follows **FIFO** (First in First out) property. Lets understand from this example:

Suppose you need to buy a railway ticket counter. You go to a ticket-counter and stand in line(queue). Now the person standing at first gets the ticket first (since he has come first) and the person standing at last gets the ticket at last. Basically who came first gets the ticket first - in the order in which they came, they are served in the same order.

The same happens in a Queue. The element which is inserted in queue first gets popped out first (FIFO architecture). Queue also serves two operation -
* **```push/enQueue(element)```** - put the element in Queue
* **```pop()```** - remove the element from the Queue and return the element

We will see the queue implementation in C++:

[Queue Implementation](https://github.com/dummybyte/CodeBlog/blob/master/Queue.cpp)

#### Time Complexity
The time complexity for each ```push()``` and ```pop()``` is O(1).

Note: There are many ways by which you can implement Queue e.g. using Linked Lists, Arrays etc.

Here is a Linked List Implementation of Queue:
[Queue Linked List Implementaion](https://github.com/dummybyte/CodeBlog/blob/master/QueueLinkedListImplementation.cpp)
