# Leetcode-Python3
## Linked List Theory, 203. Remove Linked List Elements, 707. Design Linked List，206. Reverse Linked List.
May 11, 2023  4h

The third day for Linked List. Today we will learn about the linked list and its difference with arrays.\
The challenges today are about how to remove items from the linked list, create a new linked list, and the reversed linked list. Have fun!😀

## Linked List Theory
[Reading link](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/%E9%93%BE%E8%A1%A8%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%80.md)\
A linked list is a linear structure connected by pointers. Each node is composed of two parts, one is the data field and the other is the pointer field (stores the pointer to the next node). The pointer field of the last node points to null (meaning null pointer).\
Arrays are continuously distributed in memory, but linked lists are not contiguously distributed in memory. Each node in the linked list is connected by  the pointers.\
Create a linked list:

```python
# Here is a code block to create a linked list
class ListNode:
  def __init__(self, val, next=None):
    self.val = val
    self.next = next
```

## 203. Remove Linked List Elements
[Leetcode link](https://leetcode.com/problems/remove-linked-list-elements/)\
There are two conditions when remove an element from a linked list:
1. remove a middle node
2. remove the head node: head = head.next 

By creating a virtual head node **dummy head**, both of the two kind of nodes can be removed in the same way.\
To remove an element, find its last element, and change the last element's pointer,pointing to the removed one's next element.\
Here define a <ins>current pointer</ins>, and **point to the dummy head**.


<img src="https://github.com/gyjbb/Leetcode-Python3/blob/main/Screen%20Shot%202023-05-11%20at%208.39.06%20PM.png" width="700" height="300">


## 707. Design Linked List
[Leetcode link](https://leetcode.com/problems/design-linked-list/)\
Can also use a **dummy head** to solve this comprehensive question.\
We need to finish defining the following functions:
1. get the element in linked list at a given index 
2. add a new value before the head of a linked list
3. add a new value after the tail of a linked list
4. add a new node before the given index
5. delete the node at the given index. 

For question 1, firstly, define a <ins>current pointer</ins> for traverse. And **point to the real head** this time. The head of the linked list will be returned in the end. If there is no cur defined and use head for the traverse, the head will change and can't be used to return at the end of the operation.\
For question 2 add a new node, the order is very important. Create the right new pointer first, then create the left one. Like follows: 
> newnode.next = dummynode.next \
> dummynode.next = newnode

<img src="https://github.com/gyjbb/Leetcode-Python3/blob/main/Screen%20Shot%202023-05-11%20at%209.19.17%20PM.png" width="300" height="180">

For question 3, current needs to traverse from the **dummy head** to the last actual node. When current.next is null, it means the current has now points to the tail. Then let the current node point to the newnode.\
For question 4, to add a new node before the index n, must know the (n-1) node. So the <ins>current pointer</ins>/node needs to traverse from the **dummy head** to the (n-1) node. Then follow the same order as question 2:
> newnode.next = cur.next \
> cur.next = newnode

For question 5, the same as For question 4, the current pointer needs to traversa from **dummy head** to the (n-1) node, and point to (n-1) node. So the node with index n will be current.next. Let current.next = current.next.next, then node n will be deleted.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
        
class MyLinkedList:
    def __init__(self):
        self.dummy_head = ListNode()
        self.size = 0

    def get(self, index: int) -> int:
        if index < 0 or index >= self.size:
            return -1
        
        current = self.dummy_head.next
        for i in range(index):
            current = current.next
            
        return current.val

    def addAtHead(self, val: int) -> None:
        self.dummy_head.next = ListNode(val, self.dummy_head.next)
        self.size += 1

    def addAtTail(self, val: int) -> None:
        current = self.dummy_head
        while current.next:
            current = current.next
        current.next = ListNode(val)
        self.size += 1

    def addAtIndex(self, index: int, val: int) -> None:
        if index < 0 or index > self.size:
            return
        
        current = self.dummy_head
        for i in range(index):
            current = current.next
        current.next = ListNode(val, current.next)
        self.size += 1

    def deleteAtIndex(self, index: int) -> None:
        if index < 0 or index >= self.size:
            return
        
        current = self.dummy_head
        for i in range(index):
            current = current.next
        current.next = current.next.next
        self.size -= 1
        
# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```

## 206. Reverse Linked List
[Leetcode link](https://leetcode.com/problems/reverse-linked-list/) \
[reading link](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0206.%E7%BF%BB%E8%BD%AC%E9%93%BE%E8%A1%A8.md) \
Can use **Two Pointers** to solve this question: current pointer and a previous pointer.\
**The current pointer** starts from the **real head**, and traverses to the tail(before null).\
Here the order is also very important. We can define a temporary pointer to store the current node's next node. Then let the current point to the previous node and change the direction of the linked list. The temporary pointer is to save the original current node's next node. 
> temp = cur.next \
> cur.next = pre

<img src="https://github.com/gyjbb/Leetcode-Python3/blob/main/Screen%20Shot%202023-05-11%20at%2011.25.18%20PM.png" width="300" height="150">

Then move both pre and cur to the next position:
> pre = cur \
> cur = temp
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        cur = head   
        pre = None
        while cur:
            temp = cur.next # 保存一下 cur的下一个节点，因为接下来要改变cur->next
            cur.next = pre #反转
            #更新pre、cur指针
            pre = cur
            cur = temp
        return pre
```

[Reading for single linked list](https://cloud.tencent.com/developer/article/1794143)




