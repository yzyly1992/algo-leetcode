Leetcode 226: Invert Binary Tree
```java
TreeNode invertTree(TreeNode root) {
    traverse(root);
    return root;
}

void traverse(TreeNode root) {
    if (root == null) {
        return;
    }

    TreeNode tmp = root.left;
    root.left = root.right;
    root.right = tmp;

    traverse(root.left);
    traverse(root.right);
}
```

D&C Method
```java
TreeNode invertTree(TreeNode root) {
    if (root == null) {
        return null;
    }

    TreeNode left = invertTree(root.left);
    TreeNode right = invertTree(root.right);

    root.left = right;
    root.right = left;

    return root;
}
```

Leetcode 116: Fill the right pointer
```java
Node connect(Node root) {
    if (root == null) return null;
    traverse(root.left, root.right);
    return root;
}

void traverse(Node node1, Node node2) {
    if (node1 == null || node2 == null) {
        return;
    }

    node1.next = node2;

    traverse(node1.left, node1.right);
    traverse(node2.left, node2.right);
    traverse(node1.right, node2.left);
}
```

Leetcode 114: Unfold binary tree to a linkedlist
```java
TreeNode dummy = new TreeNode(-1);
TreeNode p = dummy;

void traverse(TreeNode root) {
    if (root == null) {
        return;
    }

    p.right = new TreeNode(root.val);
    p = p.right;

    traverse(root.left);
    traverse(root.right);
}
```

Divide & Conquer
```java
void flatten(TreeNode root) {
    if (root == null) return;

    flatten(root.left);
    flatten(root.right);

    TreeNode left = root.left;
    TreeNode right = root.right;
    root.left = null;
    root.right = left;

    TreeNode p = root;
    while (p.right != null) {
        p = p.right;
    }
    p.right = right;
}
```


