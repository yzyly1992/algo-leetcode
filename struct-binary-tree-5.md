Can we recover a binary tree through pre-order / in-order / post-order serierlized data?
Answer: It depends. See if the pre-order traverse result whether contains information about empty pointer.
E.g. If a result [1,2,3,4,5] doesn't contains info about empty / null nodes, multiple situations can be satisfied.
If the result contains null pointer e.g. [1,2,3,#,#,4,#,#,5,#,#], then we can recover the only binary tree.

Leetcode 297: Binary tree serialization and deserialization
```java
```

