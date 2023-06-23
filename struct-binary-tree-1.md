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



