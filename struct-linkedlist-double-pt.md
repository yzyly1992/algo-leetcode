1. Merge Two Linked Lists
```java
ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(-1), p = dummy;
    ListNode p1 = l1, p2 = l2;
    
    while (p1 != null && p2 != null) {
        if (p1.val > p2.val) {
            p.next = p2;
            p2 = p2.next;
        } else {
            p.next = p1;
            p1 = p1.next;
        }
        p = p.next;
    }
    
    if (p1 != null) {
        p.next = p1;
    }

    if (p2 != null) {
        p.next = p1;
    }
    if (p2 != null) {
        p.next = p2;
    }
    return dummy.next;
}
```

```cpp
ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode* dummy = new ListNode(-1), *p = dummy;
    ListNode* p1 = l1, *p2 = l2;

    while (p1 != NULL && p2 != NULL {
        if (p1->val > p2->val) {
            p->next = p2;
            p2 = p2->next;
        } else {
            p->next = p1;
            p1 = p1->next;
        }
        p = p->next;
    }

    if (p1 != NULL) {
        p->next = p1;
    }

    if (p2 != NULL) {
        p->next = p2;
    }
    
    return dummy->next;
}
```

```python
def mergeTwoLists(l1: ListNode, l2: ListNode) -> ListNode:
    dummy = ListNode(-1)
    p = dummy;
    p1 = l1
    p2 = l2

    while p1 && p2:
        if p1.val > p2.val:
            p.next = p2
            p2 = p2.next
        else:
            p.next = p1
            p1 = p1.next
        p = p.next
    
    if p1:
        p.next = p1
    if p2:
        p.next = p2

    return dummy.next
```

Leetcode 86: Seperate LinkedList

```java
ListNode partition(ListNode head, int x) {
    ListNode dummy1 = new ListNode(-1);
    ListNode dummy2 = new ListNode(-1);
    ListNode p1 = dummy1, p2 = dummy2;
    ListNode p = head;

    while (p != null) {
        if (p.val >= x) {
            p2.next = p;
            p2 = p2.next;
        } else {
            p1.next = p;
            p1 = p1.next;
        }
        
        // break the node
        ListNode temp = p.next;
        p.next = null;
        p = temp;
    }
    
    // link two linkedlist
    p1.next = dummy2.next;

    return dummy1.next;
}
```

```cpp
ListNode* partition(ListNode* head, int x) {
    ListNode* dummy1 = new ListNode(-1);
    ListNode* dummy2 = new ListNode(-1);
    ListNode* p1 = dummy1, *p2 = dummy2;
    ListNode* p = head;

    while (p != nullprt) {
        if (p->val >= x) {
            p2->next = p;
            p2 = p2->next;
        } else {
            p1->next = p;
            p1 = p1->next;
        }
        
        //break the node
        ListNode* temp = p->next;
        p->next = nullptr;
        p = temp;
    }

    // link two linkedlist
    p1->next = dummy2->next;
    
    return dummy1->next;
}
``` 

```python
def partition(head: ListNode, x: int) -> ListNode:
    dummy1 = ListNode(-1)
    dummy2 = ListNode(-2)
    p1 = dummy1
    p2 = dummy2
    p = head

    while p:
        if p.val >= x:
            p2.next = p
            p2 = p2.next
        else:
            p1.next = p
            p1 = p1.next
        
        temp = p.next
        p.next = None
        p = temp
    pl.next = dummy2.next
    return dummy1.next
```

LeetCode 23: Combine K Ascend List

```java
ListNode mergeKLists(ListNode[] lists) {
    if (lists.length == 0) return null;

    ListNode dummy = new ListNode(-1);
    ListNode p = dummy;

    PriorityQueue<ListNode> pq = new PriorityQueue<>(
        lists.length, (a, b)->(a.val - b.val));

    for (ListNode head : lists) {
        if (head != null) {
            pq.add(head);
        }
    }

    while (!pq.isEmpty()) {
        ListNode node = pq.poll();
        p.next = node;
        if (node.next != null) {
            pq.add(node.next);
        }
        p = p.next;
    }
    return dummy.next;
}
```

```cpp
ListNode* mergeKLists(vector<ListNode*>& lists) {
    if (lists.empty()) return nullptr;

    ListNode* dummy = new ListNode(-1);
    ListNode* p = dummy;
    
    priority_queue<ListNode*, vector<ListNode*>, function<bool(ListNode*, [] (ListNode* a, ListNode* b) { return a->val > b->val; });

    for (auto head : lists) {
        if (head != nullptr) {
            pq.push(head);
        }
    }

    while (!pq.empty()) {
        ListNode* node = pq.top();
        pq.pop();
        p->next = node;
        if (node->next != nullptr) {
            pq.push(node->next);
        }
        p = p->next;
    }
    return dummy->next;
}
```

```python
from typing import List
import heapq

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def mergeKLists(lists: List[ListNode]) -> ListNode:
    if not lists:
        return None

    dummy = ListNode(-1)
    p = dummy

    pq = []
    for head in lists:
        if head:
            heapq.heappush(pq, (head.val, head))

    while pq:
        node = heapq.heappop(pq)[1]
        p.next = node
        if node.next:
            heapq.heappush(pq, (node.next.val, node.next))
        p = p.next
    return dummy.next
```

Single List Last-K Node

```java
ListNode findFromEnd(ListNode head, int k) {
    ListNode p1 = head;
    for (int i = 0; i < k; i++) {
        p1 = p1.next;
    }
    ListNode p2 = head;
    while (p1 != null) {
        p2 = p2.next;
        p1 = p1.next;
    }

    return p2;
}
```

```cpp
ListNode* findFromEnd(ListNode* head, int k) {
    ListNode* p1 = head;
    for (int i = 0; i < k; i++) {
        p1 = p1->next;
    }
    ListNode* p2 = head;
    while (p1 != nullptr) {
        p2 = p2->next;
        p1 = p1->next;
    }
    return p2;
}
```

```python
def findFromEnd(head: ListNode, k: int) -> ListNode:
    p1 = head
    for i in range(k):
        p1 = p1.next
    p2 = head
    while p1:
        p2 = p2.next
        p1 = p1.next
    return p2
```

Leetcode 19: Delete the last-N node

```java
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(-1);
    dummy.next = head;
    ListNode x = findFromEnd(dummy, n + 1);
    x.next = x.next.next;
    return dummy.next;
}

private ListNode findFromEnd(ListNode head, int k) {
    // see above code
}
```

```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode* dummy = new ListNode(-1);
    dummy->next = head;
    ListNode* x = findFromEnd(dummy, n + 1);
    x->next = x->next->next;
    return dummy->next;
}
```

```python
def removeNthFromEnd(head: ListNode, n: int) -> ListNode:
    dummy = ListNode(-1)
    dummy.next = head
    x = findFromEnd(dummy, n + 1)
    x.next = x.next.next
    return dummy.next
```

Leetcode 876: Middle point of a single list

```java
ListNode middleNode(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```

```cpp
ListNode* middleNode(ListNode* head) {
    ListNode* slow = head, * fast = head;
    while (fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
    }
    return slow;
}
```

```python
def middleNode(head: ListNode) -> ListNode:
    slow = head
    fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

Detect cirlce

```java
boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) {
            return true;
        }
    }
    return false;
}
```

```cpp
bool hasCycle(ListNode* head) {
    ListNode* slow = head;
    ListNode* fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (fast == slow) {
            return true;
        }
    }
    return false;
}
```

```python
def hasCycle(head: ListNode) -> Boolean:
    slow = head
    fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if fast == slow:
            return True
    return False
```

Find the start node of the circle

```java
class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head, slow = head;
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
            if (fast == slow) break;
        }

        if (fast == null || fast.next == null) {
            return null;
        }

        slow = head;
        while (slow != fast) {
            fast = fast.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

Leetcode 160: Get intersection Node

```java
ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    ListNode p1 = headA, p2 = headB;
    while (p1 != p2) {
        if (p1 == null) p1 = headB;
        else p1 = p1.next;
        if (p2 == null) p2 = headA;
        else p2 = p2.next;
    }
    return p1;
}
```

```cpp
ListNode* getIntersectionNode(ListNode* headA, ListNode* headB) {
    ListNode* p1 = headA, *p2 = headB;
    while (p1 != p2) {
        if (p1 == nullptr) {
            p1 = headB;
        } else {
            p1 = p1->next;
        }

        if (p2 == nullptr) {
            p2 = headA;
        } else {
            p2 = p2->next;
        }
    }
    return p1;
}
```

```python
def getIntersectionNode(headA: ListNode, headB: ListNode) -> ListNode:
    p1 = headA
    p2 = headB
    while p1 != p2:
        if not p1:
            p1 = headB
        else:
            p1 = p1.next
        if not p2:
            p2 = headA
        else:
            p2 = p2.next
    return p1
```




