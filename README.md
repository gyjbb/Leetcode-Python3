# Leetcode-Python3
## 977.Squares of a Sorted Array, 209.Minimum Size Subarray Sum, 59.Spiral Matrix II, Summary of Array.
May 11, 2023 

The third day for Linked List. Today we will learn about the linked list and its difference with arrays.\
The challenges today are about how to remove items from the linked list, create a new linked list, and the reversed linked list. Have fun!😀

## Linked List Theory
[Reading link](https://programmercarl.com/%E9%93%BE%E8%A1%A8%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%80.html#%E5%8D%95%E9%93%BE%E8%A1%A8)\
A linked list is a linear structure connected by pointers. Each node is composed of two parts, one is the data field and the other is the pointer field (stores the pointer to the next node). The pointer field of the last node points to null (meaning null pointer).\
Arrays are contiguously distributed in memory, but linked lists are not contiguously distributed in memory. Each node in the linked list is connected by  the pointers.\
Create a linked list:

```python
# Here is a code block to create a linked list
class ListNode:
  def __init__(self, val, next=None):
    self.val = val
    self.next = next
```

<img src="https://github.com/gyjbb/Leetcode-Python2/blob/main/Screen%20Shot%202023-05-10%20at%203.35.08%20PM.png" width="600" height="400">

## 203. Remove Linked List Elements
[Leetcode link](https://leetcode.com/problems/remove-linked-list-elements/)\
There are two conditions when remove an element from a linked list:
1. remove a middle node
2. remove the head node: head = head.next \
By creating a virtual head node *dummy head*, both of the two kind of nodes can be removed in the same way.\
To remove an element, find its last element, and change the last element's pointer points to the removed one's next element.\


## 707.

## 206.



