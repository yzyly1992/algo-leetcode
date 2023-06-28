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

Leetcode 105: Construct binary tree from preorder and inorder traverse
```java
TreeNode build(int[] preorder, int preStart, int preEnd, int[] inorder, int inStart, int inEnd) {
    if (preStart > preEnd) {
        return null;
    }

    int rootVal = preoder[preStart];
    int index = valToIndex.get(rootVal);
    int leftSize = index - inStart;

    TreeNode root = new TreeNode(rootVal);
    root.left = build(preorder, preStart + 1, preStart + leftSize,
                    inorder, inStart, index - 1);

    root.right = build(preorder, preStart + leftSize + 1, preEnd, inorder, index +  1, inEnd);

    return root;
}
```


