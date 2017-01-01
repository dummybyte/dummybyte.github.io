---
layout: post
title: "Linked Lists"
description: "Introduction"
date: 2016-12-22
tags: [algorithm, linked list, data structures]
comments: true
share: true
---

## Contents
- [Linked Lists](#linked-lists)
- [Doubly Linked List](#doubly-linked-list)
- [Circular Linked List](#circular-linked-list)

## Linked Lists

What is the difference between Linked Lists and Arrays? Arrays are linear data structures where similar data is stored at contiguous locations. Linked list are also linear data structures but here data is not stored at contiguous memory locations but here each memory location is linked by pointers.

Linked list can be traversed like arrays to access each element stored at memory locations. So for traversing linked lists ,we need the starting pointer of the linked list also known as head of the linked list. **head** is the starting point of a linked list. So for traversing head must be known.

Notation to denote a Linked List

```
struct node {
    int data;
    struct node *next;
}
```

Now what does the above notation means? Here, it means that a memory location is represented by a node type (struct) and each memory location stores a value which is of type ```int``` and also has pointer which points to a node type.

Consider the following example of linked list:
![image](/blog/images/linkedlist_1.jpg)

Here we can see that each node points to the next node (basically each node knows the memory address of the next node). The last node is pointed to ```null``` since the list ends there.

Now how to traverse the linked list. As discussed above, we need head of the linked list and since each node, from head onwards, knows the address of the next node we can just jump to next address till we reach the end of the linked list. Here is the code snippet on how to traverse the linked list:

```
    traverse(struct node *head) {
        while(head != NULL) {
            cout<<head->data<<"\n";
            head = head->next;
        }
    }
```

We are not doing anything special. We are just going over each node and printing the data stored at each node. The main thing here is going over each node - thats where ```next``` ptr comes handy. Using this ```next``` ptr, we jump from one node over another.

**Simplified Thinking:** Suppose we want to create a linked list with 5 elements. Think of each node of linked list as a memory location (for the time being forget about the size of each memory locations). So we need 5 memory locations, right!! Now, suppose we have got this 5 memory locations.

They are just random 5 locations. They need to be connected so that it can become list. Now, how to connect them? Here, the next pointer comes into picture. Basically we tell each node that "this is the location of next node in the list". Thats it. This is done by next pointer.

Linked lists support operations such as insertion, deletion, search operations also. We will see by code how to implement Linked list in C++:

[Linked List Code](https://github.com/dummybyte/CodeBlog/blob/master/LinkedList.cpp)


Now there are various types of linked list. Though we will not discuss them in detail, but we will give a brief idea of what is there structure.

## Doubly Linked List

Doubly linked list is nothing but a linked list which also points to the previous node. Here is how doubly linked list structure looks like:

```
    struct node {
        int data;
        struct node *previous;
        struct node *next;
    }
```

Here how the doubly linked list would look like:

![image](/blog/images/linkedlist_2.jpg)

## Circular Linked List

Circular linked list is a linked list where the last pointer doesn't point to the ```NULL``` rather it points to the head of the linked list.

Here is how the Circular linked list would look like:

![image](/blog/images/linkedlist_3.jpg)
