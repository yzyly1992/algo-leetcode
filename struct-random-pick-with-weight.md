Leetcode 528: Random Pick with Weigth
Solution: Presum + Binary Search
```java
class Solution {
    private int[] preSum;
    private Random rand = new Random();

    public Solution(int[] w) {
        int n = w.length;
        preSum = new int[n + 1];
        preSum[0] = 0;
        for (int i = 1; i <= n; i++) {
            preSum[i] = preSum[i - 1] + w[i - 1];
        }
    }

    public int pickIndex() {
        int n = preSum.length;
        int target = rand.nextInt(preSum[n - 1]) + 1;
        return leftBound(preSum, target) - 1;
    }

    private int leftBound(int[] nums, int target) {
        // see binary search
    }
}
```

{1},{2,3,4},{5,6}

