876 Middle of the Linked List
===========================
回傳 Linked List 的 Middle Node，當總數為偶數時，回傳 Second Node
![](141.png)

解法如下：
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head
        while fast != None and fast.next != None:
            fast = fast.next.next
            slow = slow.next

        return slow
```
心得：
- 藉由快慢指標來確認當快指針走到終點時，慢指針就在中間
