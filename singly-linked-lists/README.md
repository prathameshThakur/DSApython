[![HOME](https://img.shields.io/badge/-HOME-informational?style=plastic)](https://prathameshthakur.github.io/DSApython/)

# <a name='top'></a> Singly Linked Lists

This lesson introduces you to the ​singly linked list and implements its structure in Python.



we will go over the following different types of linked lists and implement them in Python:

- Singly Linked Lists
- Doubly Linked Lists
- Circular Linked List

Below is a simple depiction of a singly linked list:

<p align="center">
<img src='images\singly1.PNG' alt='example' style="width:500px;height:250px;"> <br>
</p>

## Structure 
Every linked list consists of nodes, as shown in the illustration above. Every node has two components:

1. Data
2. Next

The data component allows a node in the linked list to store an element of data that can be of type `string`, `character`, `number`, or any other type of object. In the illustration above, the data elements are `A`, `B`, and `C` which are of character type.

The next component in every `node` is a pointer that points from one node to another.

The start of the linked list is referred to as the `head`. head is a pointer that points to the beginning of the linked list, so if we want to traverse the linked list to obtain or access an element of the linked list, we’ll start from head and move along.

The last component of a singly linked list is a notion of `null`. This null idea terminates the linked list. In Python, we call this None. The last node in a singly linked list points to a null object, and that tells you that it’s the end of the linked list.




[![TOP](https://img.shields.io/badge/-Go%20to%20top-grey?style=plastic)](#top)