Binary Tree - Brief Intro
Quick Sort is pre-order traverse of a binary tree;
Merge Sort is post-order traverse of a binary tree;

Quick Sort Framework:
```java
void sort(int[] nums, int lo, int hi) {
    int p = partition(nums, lo, hi);
    sort(nums, lo, p - 1);
    sort(nums, p + 1, hi);
}
```
Merge Sort Framework:
```java
void sort(int[] nums, int lo, int hi) {
    int mid = (lo + hi) / 2;
    sort(nums, lo, mid);
    sort(nums, mid + 1, hi);
    merge(nums, lo, mid, hi);
}
```

Binary Tree Framework:
```java
void traverse(TreeNode root) {
    if (root == null) {
        return;
    }

    traverse(root.left);
    traverse(root.right);
}
```


Two Major Methods for Binary Tree Problem
 - Backtracking Method
 - Dynamic Programming

Leetcode: 104
```java
int res = 0;
int depth = 0;
int maxDepth(TreeNode root) {
    traverse(root);
    return res;
}

void traverse(TreeNode root) {
    if (root == null) {
        return;
    }
    // pre-order position
    depth++;
    if (root.left == null && root.right == null) {
        res = Math.max(res, depth);
    }
    traverse(root.left);
    traverse(root.right);
    depth--;
}
```
Leetcode 104 Method 2
```java
int maxDepth(TreeNode root) {
    if (root == null) {
        return 0;
    }

    int leftMax = maxDepth(root.left);
    int rightMax = maxDepth(root.right);
    int res = Math.max(leftMax, rightMax) + 1;
    return res;
}
```

Pre-order traverse == root node + left tree traverse result + right tree traverse result
```java
List<Integer> preorderTraverse(TreeNode root) {
    List<Integer> res = new LinkedList<>();
    if (root == null) {
        return res;
    }

    res.add(root.val);
    res.addAll(preorderTraverse(root.left));
    res.addAll(preorderTraverse(root.right));
    return res;
}
```

In-order traverse can be used in BST (binary search tree), it can traverse the node in order.


Leetcode 543: Diameter for binary tree
```java
class Solution {
    int maxDiameter = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return maxDiameter;
    }

    int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int leftMax = maxDepth(root.left);
        int rightMax = maxDepth(root.right);
        int myDiameter = leftMax + rightMax;
        maxDiameter = Math.max(maxDiameter, myDiameter);
        return 1 + Math.max(leftMax, rightMax);
    }
}
```

Dynamic Programming / Backtracking / DFS

DP focuses on divde a big problem to some small problems
Backtracking focuses on the branches between nodes
DFS focuses on the nodes

DP Example: Count total nodes on binary tree
```java
int count(TreeNode root) {
    if (root == null) {
        return 0;
    }
    int leftCount = count(root.left);
    int rightCount = count(root.right);
    return leftCount + rightCount + 1;
}
```
DP Example: fibnacci number
```java
int fib(int N) {
    if (N == 1 || N == 2) return 1;
    return fib(N - 1) + fib(N - 2);
}
```

Backtracking Example: print out the traverse process
```java
void traverse(TreeNode root) {
    if (root == null) return;
    printf("from %s enter %s", root, root.left);
    traverse(root.left);
    printf("from %s return %s", root.left, root);

    printf("from %s enter %s", root, root.right);
    traverse(root.right);
    printf("from %s return %s", root.left, root);
}
```

Backtracking Example: n-ary tree traverse
```java
class Node {
    int val;
    Node[] children;
}

void traverse(Node root) {
    if (root == null) return;
    for (Node child : root.children) {
        printf("from %s enter %s, root, child);
        traverse(child);
        printf("from %s return %s, child, root);
    }
}
```

Backtracking framework
```java
void backtracking(...) {
    for (int i = 0; i < ...; i++) {
        // do sth
        ...
        // enter next level
        backtrack();
        // return from the next level
        ...
    }
}
```

Backtracking example: permutation
```java
void backtrack(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        used[i] = true;
        track.addLast(nums[i]);
        backtrack(nums);
        track.removeLast();
        used[i] = false;
    }
}
```

DFS Example: Add one to all the tree nodes
```java
void traverse(TreeNode root) {
    if (root == null) return;
    root.val++;
    traverse(root.left);
    traverse(root.right);
}
```

DFS Example: Island/Grid Problem
```java
void dfs(int[][]grid, int i, int j) {
    int m = grid.length, n = grid[0].length;
    if (i < 0 || j < 0 || i >= m || j >= n) {
        return;
    }
    if (grid[i][j] == 0) {
        return;
    }

    grid[i][j] = 0;
    dfs(grid, i + 1, j);
    dfs(grid, i, j + 1);
    dfs(grid, i - 1, j);
    dfs(grid, i, j - 1);
}
```

Traverse by layer
```java
void levelTraverse(TreeNode root) {
    if (root == null) return;
    Queue<TreeNode> q = new LinkedList<>();
    q.offer(root);

    while (!q.isEmpty()) {
        int sz = q.size();
        for (int i = 0; i < sz; i++) {
            TreeNode cur = q.poll();
            if (cur.left != null) {
                q.offer(cur.left);
            }
            if (cur.right != null) {
                q.offer(cur.right);
            }
        }
    }
}
```


