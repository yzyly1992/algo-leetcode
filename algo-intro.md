Iterate / traverse linearly

```java
void traverse(int[] arr) {
    for (int = 0; i < arr.length; i++) {
        // do something with arr[i]
    }
}
```

```cpp
void traverse(vector<int>& arr) {
    for (int i = 0; i < arr.size(); i++) {
        // visit arr[i]
    }
}

```

```python
def traverse(arr: List[int]):
    for i in range(len(arr)):
        # visit arr[i]
```

Traverse a linked list

```java
class ListNode {
    int val
    ListNode next;
}

void traverse(ListNode head) {
    for (ListNode p = head; p != null; p = p.next) {
        // visit p.val
    }
}

// traverse recursively
void traverse(ListNode head) {
    traverse(head.next);
}
```

```cpp
class ListNode {
    public:
        int val;
        ListNode* next;
};

void traverse(ListNode* head) {
    for (ListNode* p = head; p != nullptr; p = p->next)
        // visit p->val
    }
}

// traverse recursively
void traverse(ListNode* head) {
    traverse(head->next);
}
```

```python
class ListNode:
    def __init__(self, val):
    self.val = val
    self.next = None

def traverse(head: ListNode) -> None:
    p = head
    while p is not None:
        # visit p.val
        p = p.next

# traverse recursively
def traverse(head: ListNode) -> None:
    traverse(head.next)
```

Traverse binary tree
```java
class TreeNode {
    int val;
    TreeNode left, right;
}

void traverse(TreeNode root) {
    traverse(root.left);
    traverse(root.right);
}
```

```cpp
struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
};

void traverse(TreeNode* root) {
    traverse(root->left);
    traverse(root->right);
}
```

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def traverse(root: TreeNode):
    traverse(root.left)
    traverse(root.right)
```

Leetcode 124
```java
int res = Integer.MIN_VALUE;
int oneSideMax(TreeNode root) {
    if (root == null) return 0;
    int left = max(0, oneSideMax(root.left));
    int right = max(0, oneSideMax(root.right));
    
    res = Math.max(res, left + right + root.val);
    return Math.max(left, right) + root.val;
}
```

```cpp
int res = INT_MIN;
int oneSideMax(TreeNode* root) {
    if (root == nullptr) return 0;
    int left = max(0, oneSideMax(root->left));
    int right = max(0, oneSideMax(root->right));
    
    res = max(res, left + right + root->val);
    return max(left, right) + root->val;
}
```

```python
def oneSideMax(root: TreeNode) -> int:
    if not root:
        return 0
    left = max(0, oneSideMax(root.left)
    right = max(0, oneSideMax(root.right)
    res = max(res, left + right + root.val)
    return max(left, right) + root.val
```

Leedcode 105
```java
TreeNode build(int[] preorder, int preStart, int preEnd,
                int[] inorder, int inStart, int inEnd) {
    if (preStart > preEnd) {
        return null;
    }
    int rootVal = preorder[preStart];
    int index = 0;
    for (int i = inStart; i <= inEnd; i++) {
        if (inorder[i] == rootVal) {
            index = i;
            break;
        }
    }
    int leftSize = index - inStart;
    TreeNode root = new TreeNode(rootVal);

    root.left = build(preorder, preStart + 1, preStart + leftSize, 
                        inorder, inStart, index - 1);
    root.right = build(preorder, preStart + leftSize + 1, preEnd,
                        inorder, index + 1, inEnd);
    return root;
}
```

```cpp
TreeNode* build(vector<int>& preorder, int preStart, int preEnd,
                vector<int>& inorder, int inStart, inEnd) {
    if (preStart > preEnd) {
        return nullptr;
    }
    int rootVal = preorder[preStart];
    int index = 0;
    for (int i = inStart; i < inEnd; i++) {
        if (inorder[i] == rootVal) {
    index = i;
    break;
    }
    int leftSize = index - in Start;
    TreeNode* root = new TreeNode(rootVal);

    // build left and right tree
    root->left = build(preorder, preStart + 1, preStart + leftSize,
                    inorder, inStart, index - 1);
    root->right = build(preorder, preStart + leftSize + 1, preEnd,
                    inorder, index + 1, inEnd);
    return root;
}
```

```python
def build(preorder: List[int], preStart: int, preEnd: int,
            inorder: List[int], inStart: int, inEnd: int) -> TreeNode:
    if preStart > preEnd:
        return None
    rootVal = preorder[preStart]
    index = 0
    for i in range(inStart, inEnd, + 1):
        if inorder[i] == rootVal:
            index = i
            break
    leftSize = index - inStart
    root = TreeNode(rootVal)

    # build left and right trees
    root.left = build(preorder, preStart + 1, preStart + leftSize,
                        inorder, inStart, index - 1)
    root.right = build(preorder, preStart + leftSize + 1, preEnd,
                        inorder, index + 1, inEnd)
    return root
```

Leetcode 230: k-least element in a binary tree

```java
int res = 0;
int rank = 0;
void traverse(TreeNode root, int k) {
    if (root == null) {
        return;
    }
    traverse(root.left, k);
    rank++;
    if (k == rank) {
        res = root.val;
        return;
    }
    traverse(root.right, k);
}
```

```cpp
int res = 0;
int rank = 0;
void traverse(TreeNode* root, int k) {
    if (root == nullptr) {
        return;
    }
    traverse(root->left, k);
    rank++;
    if (k == rank) {
        res = root->val;
        return;
    }
    traverse(root->right, k);
}
```

```python
res = 0
rank = 0
def traverse(root: TreeNode, k: int) -> None:
    global res, rank
    if not root:
        return
    traverse(root.left, k)
    rank += 1
    if k == rank:
        res = root.val
        return
    traverse(root.right, k)
```

change problem: coins

```java
int dp(int[] coins, int amount) {
    if (amount == 0) return 0;
    if (amount < 0) return -1;

    int res = Integer.MAX_VALUE;
    for (int coin : coins) {
        int subProblem = dp(coins, amount - coin);
        if (subProblem == -1) continue;
        res = Math.min(res, subProblem + 1);
    }
    return res == Integer.MAX_VALUE ? -1 : res;
}
```

```cpp
int dp(vector<int>& coins, int amount) {
    if (amount == 0) return 0;
    if (amount < 0) return -1;

    int res = INT_MAX;
    for (int coin : coins) {
        int subProblem = dp(coins, amount - coin);
        if (subProblem == -1) continue;
        res = min(res, subProblem + 1);
    }
    return res = INT_MAX ? -1 : res;
}
```

```python
def dp(coins: List[int], amount: int) -> int:
    if amount == 0:
        return 0
    if amount < 0:
        return -1

    res = float('inf')
    for coin in coins:
        subProblem = dp(coins, amount - coin)
        if subProblem == -1:
            continue
        res = min(res, sub_problem + 1)
    return -1 if res == float('inf') else res
```

Permutation: backtracking

```java
void backtrack(int[] nums, LinkedList<Integer> track) {
    if (track.size() == nums.length) {
        res.add(new LinkedList(track));
        return;
    }
    
    for (int i = 0; i < nums.length; i++) {
        if (track.contains(nums[i])) continue;
        track.add(nums[i]);
        backtrack(nums, track);
        track.removeLast();
    }
}
```

```cpp
void backtrack(vector<int>& nums, list<int>& track, vector<list<int>>& res) {
    if (track.size() == nums.size()) {
        res.push_back(list<int>(track.begin(), track.end()));
        return;
    }
    for (int i = 0; i < nums.size(); i++) {
        if (find(track.begin(), track.end(), nums[i]) != track.end())
            continue;
        track.push_back(nums[i]);
        backtrack(nums, track, res);
        track.pop_back();
    }
}
```

```python
def backtrack(nums: List[int], track: List[int]) -> None:
    if len(track) == len(nums):
        res.append(track[:])
        return

    for i in range(len(nums)):
        if nums[i] in track:
            continue
        track.append(nums[i])
        backtrack(nums, track)
        track.pop()
```
