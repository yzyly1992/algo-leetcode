Leetcode 654: Biggest Binary Tree
```java
TreeNode constructMaximumBinaryTree(int[] nums) {
    return build(nums, 0, nums.length - 1);
}

TreeNode build(int[] nums, int lo, int hi) {
    if (lo > hi) {
        return null;
    }

    int index = -1, maxVal = Integer.MIN_VALUE;
    for (int i = lo; i < hi; i++) {
        if (maxVal < nums[i]) {
            index = i;
            maxVal = nums[i];
        }
    }

    TreeNode root = new TreeNode(maxVal);
    root.left = build(nums, lo, index - 1);
    root.left = build(nums, index + 1, hi);

    return root;
}
```


