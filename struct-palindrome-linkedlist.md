Leetcode 234: Palidrome Linkedlist

```java
ListNode left;

boolean isPalindrome(ListNode head) {
    left = head;
    return traverse(head);
}

boolean traverse(ListNode right) {
    if (right == null) return true;
    boolean res = traverse(right.next);
    res = res && (right.val == left.val);
    left = left.next;
    return res;
}
```

```cpp
ListNode* left;

bool isPalindrome(ListNode* head) {
    left = head;
    return traverse(head);
}

bool traverse(ListNode* right) {
    if (right == nullptr) return true;
    bool res = traverse(right->next);
    res = res && (right->val == left->val);
    left = left->next;
    return res;
}
```

```python
left = None

def isPalindrome(head: ListNode) -> bool:
    left = head
    return traverse(head)

def traverse(right: ListNode) -> bool:
    if not right:
        return True
    res = traverse(right.next)
    res = res and (right.val == left.val)
    left = left.next
    return res
```

Space optimization

```java
boolean isPalindrome(ListNode head) {
    ListNode slow, fast;
    slow = fast =head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    if (fast != null) {
        slow = slow.next;
    }

    ListNode left = head;
    ListNode right = reverse(slow);
    while (right != null) {
        if (left.val != right.val)
            return false;
        left =left.next;
        right = right.next;
    }
    return true;
}

ListNode reverse(ListNode head) {
    ListNode pre = null, cur = head;
    while (cur != null) {
        ListNode next = cur.next;
        cur.next = pre;
        pre = cur;
        cur = next;
    }
    return pre;
}
```
```cpp
bool isPalindrome(ListNode* head) {
    ListNode* slow = head, * fast = head;
    while (fast != nullptr && fast->next != nullptr) {
        slow = slow->next;
        fast = fast->next->next;
    }

    if (fast != nullptr) {
        slow = slow->next;
    }

    ListNode* left = head;
    ListNode* right = reverse(slow);
    while (right != nullptr) {
        if (left->val != right->val) {
            return false;
        }
        left = left.next;
        right = right.next;
    }
    return true;
}

ListNode* reverse(ListNode* head) {
    ListNode* pre = nullptr, * cur = head;
    while (cur != nullptr) {
        ListNode* next = cur->next;
        cur->next = pre;
        pre = cur;
        cur = next;
    }
    return pre;
}
```

```python
def isPanlindrome(head: ListNode) -> bool:
    slow = head
    fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

    if fast:
        slow = slow.next

    left = head
    right = reverese(slow)
    while right:
        if left.val != right.val:
            return False
        left = left.next
        right = right.next
    return True

def reverse(head: ListNode) -> ListNode:
    pre = None
    cur = head
    while cur:
        next = cur.next
        cur.next = pre
        pre = cur
        cur = next
    return pre
```

### Summary
- Finding palindrome starts from center and spread to two ends.
- Determining a palindrome starts from two ends and shrink back to center
- For linked list that can't not traverse in reverse order, we could create a new reversed linked list.
- Use post-order traverse
- Use stack to process linked list in reverse order
- reverse partial list instead of whole list

