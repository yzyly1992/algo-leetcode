Leetcode 303: Search in range

```java
class NumArray {
    private int[] preSum;

    public NumArray(int[] nums) {
        preSum = new int[nums.length + 1];
        for (int i = 1; i < preSum.length; i++) {
            preSum[i] = preSum[i - 1] + nums[i - 1];
        }
    }

    public int sumRange(int left, int right) {
        return preSum[right + 1] - preSum[left];
    }
}
```

```cpp
class NumArray {
    private:
        vector<int> preSum;

    public:
        NumArray(vector<int>& nums) {
            preSum.resize(nums.size() + 1);
            for (int i = 1; i < preSum.size(); i++) {
                preSum[i] = preSum[i - 1] + nums[i - 1];
            }
        }

        int sumRange(int left, int right) {
            return preSum[right + 1] - preSum[left];
        }
};
```

```python
class NumArray:
    def __init__(self, nums: List[int]):
        self.nums = nums
        self.preSum = [0] * (len(nums) + 1)
        for i in range(1, len(self.preSum)):
            self.preSum[i] = self.preSum[i - 1] + nums[i - 1]

    def sumRange(self, left: int, right: int) -> int:
        return self.preSum[right + 1] - self.preSum[left]
```

Leetcode 304: prefix sum in 2d array

```java
class NumMatrix {
    private int[][] preSum;

    public NumMatrix(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        if (m == 0 || n == 0) return;
        preSum = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                preSum[i][j] = preSum[i-1][j] + preSum[i][j-1] + matrix[i - 1][j - 1] - preSum[i - 1][j - 1];
            }
        }
    }

    public int sumRegion(int x1, int y1, int x2, int y2) {
        return preSum[x2 + 1][y2 + 1] - preSum[x1][y2 + 1] - preSum[x2 + 1][y1] + preSum[x1][y1];
    }
}
```


