Leetcode 206: Reverse Linked List

```java
ListNode reverse(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }
    ListNode last = reverse(head.next);
    head.next.next = head;
    head.next = null;
    return last;
}
```

```cpp
ListNode* reverse(ListNode* head) {
    if (head == nullptr || head->next == nullptr) {
        return head;
    }
    ListNode* last = reverse(head->next);
    head->next->next = head;
    head->next = nullptr;
    return last;
}
```

```python
def reverse(head: ListNode) -> ListNode:
    if not head or not head.next:
        return head
    last = reverse(head.next)
    head.next.next = head
    head.next = None
    return last;
```

Reverse N Nodes

```java
ListNode successor = null;

ListNode reverseN(ListNode head, int n) {
    if (n == 1) {
        successor = head.next;
        return head;
    }

    ListNode last = reverseN(head.next, n - 1);

    head.next.next = head;
    head.next = successor;
    return last;
}
```

```cpp
ListNode* successor = nullptr;

ListNode* reverseN(ListNode* head, int n) {
    if (n == 1) {
        successor = head->next;
        return head;
    }

    ListNode last = reverseN(head.next, n - 1);

    haed->next->next = head;
    head->next = succesor;
    return last;
}
```

```python
successor = None

def reverseN(head: ListNode, n: int) -> ListNode:
    if n == 1:
        successor = head.next
        return head

    last = reverseN(head.next, n - 1)
    head.next.next = head
    head.next = successor
    return last
```

Reverse part of the linked list

```java
ListNode reverseBetween(ListNode head, int m, int n) {
    if (m == 1) {
        return reverseN(head, n);
    }

    head.next = reverseBetween(head.next, m - 1, n - 1);
    return head;
}
```
```cpp
ListNode* reverseBetween(ListNode* head, int m, int n) {
    if (m = 1) {
        return reverseN(head, n);
    }
    head->next = reverseBetween(head->next, m - 1, n - 1);
    return head;
}
```

```python
def reverseBetween(head: ListNode, m: int, n: int) -> ListNode:
    if m == 1:
        return reverseN(head, n)
    head.next = reverseBetween(head.next, m - 1, n - 1)
    return head
```


}


