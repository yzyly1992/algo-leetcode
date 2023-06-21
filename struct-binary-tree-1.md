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


