### Prefix Difference

```java
class Difference {
    private int[] diff;

    public Difference(int[] nums) {
        assert nums.length > 0;
        diff = new int[nums.length];
        diff[0] = nums[0];
        for (int i = 1; i < nums.length; i++) {
            diff[i] = nums[i] - nums[i - 1];
        }
    }

    public void increment(int i, int j, int val) {
        diff[i] += val;
        if (j + 1 < diff.length) {
            diff[j + 1] -= val;
        }
    }

    public int[] result() {
        int[] res = new int[diff.length];
        res[0] = diff[0];
        for (int i = 1; i < diff.length; i++) {
            res[i] = res[i - 1] + diff[i];
        }
        return res;
    }
}
```
```cpp
class Difference {
    private:
        int* diff;
    public:
        Difference(int* nums, int length) {
            assert(length > 0);
            diff = new int[length]();
            diff[0] = nums[0];
            for (int i = 1; i < length; i++) {
                diff[i] = nums[i] - nums[i - 1];
            }
        }

        void increment(int i, int j, int val) {
            diff[i] += val;
            if (j + 1 < sizeof(diff) / sizeof(diff[0])) {
                diff[j + 1] -= val;
            }
        }

        int* result() {
            int* res = new int[sizeof(diff) / sizeof(diff[0])]();
            res[0] = diff[0];
            for (int i = 1; i < sizeof(diff) / sizeof(diff[0]); i++) {
                res[i] = res[i - 1] + diff[i];
            }
            return res;
        }
}
```
```python
class Difference:
    def __init__(self, nums: List[int]):
        assert len(nums) > 0
        self.diff = [0] * len(nums)
        self.diff[0] = nums[0]
        for i in range(1, len(nums)):
            self.diff[i] = nums[i] - nums[i - 1]

    def increment(self, i: int, j: int, val: int) -> None:
        self.diff[i] += val
        if j + 1 < len(self.diff):
            self.diff[j + 1] -= val

    def result(self) -> List[int]:
        res = [0] * len(self.diff)
        res[0] = self.diff[0]
        for i in range(1, len(self.diff)):
            res[i] = res[i - 1] + diff[i]
        return res
```

Leetcode 370: Range Addition
```java
int[] getModifiedArray(int length, int[][]updates) {
    int [] nums = new int[length];
    Difference df = new Difference(nums);
    for (int[] update: updates) {
        int i = update[0];
        int j = update[1];
        int val = update[2];
        df.increment(i, j, val);
    }
    return df.result();
}
```

Leetcode 1109: Fligth Reservation
```java
int[] corpFlightBookings(int[][] bookings, int n) {
    int[] nums = new int[n];
    Difference df = new Difference(nums);
    for (int[] booking: bookings) {
        int i = booking[0] - 1;
        int j = booling[1] - 1;
        int val = booking[2];
        df.increment(i, j, val);
    }
    return df.return();
}
```

Leetcode 1094: Car Pooling
```java
boolean carPooling(int[][] trips, int capacity) {
    int[] nums = new int[1001];
    Difference df = new Difference(nums);
    for (int[] trip : trips) {
        int val = trip[0];
        int i = trip[1];
        int j = trip[2] - 1;
        df.increment(i, j, val);
    }
    int[] res = df.result();
    for (int i = 0; i < res.length; i++) {
        if (capacity < res[i]) {
            return false;
        }
    }
    return true;
}
```

