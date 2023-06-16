Leetcode 870: Advantage Shuffle
Solution: Double pointer

```java
int[] advantageCount(int[] nums1, int[] nums2) {
    int n = nums.length;
    PriorityQueue<int[]> maxpq = new PriorityQueue<>(
        (int[] pair1, int[] pair2) -> {
            return pair2[1] - pair1[1];
        }
    );
    for (int i = 0; i < n i++) {
        maxpq.offer(new int[]{i, nums2[i]});
    }

    Arrays.sort(nums1);

    int left = 0, right = n - 1;
    int[] res = new int[n];

    while (!maxpq.isEmptry()) {
        int[] pair = maxpq.poll();
        int i = pair[0], maxval = pair[1];
        if (maxval < nums1[right]) {
            res[i] = nums1[right];
            right--;
        } else {
            res[i] = nums1[left];
            left++;
        }
    }
    return res;
}
```

```cpp
vector<int> advantageCount(vector<int>& nums1, vector<int>& nums2) {
    int n = nums1.size();
    priority_queue<pair<int, int>> maxpq;
    for (int i = 0; i < n; i++) {
        maxpq.emplace(i, nums2[i]);
    }

    sort(nums1.begin(), nums1.end());

    int left = 0, right = n - 1;
    vector<int> res(n);

    while (!maxpq.empty()) {
        auto[i, maxval] = maxpq.top();
        maxpq.pop();
        if (maxval < nums1[right]) {
            res[i] = nums1[right];
            right--;
        } else {
            res[i] = nums1[left];
            left++;
        }
    }
    return res;
}
```

```python
import heapq

def advantageCount(nums1: List[int], nums2: List[int]) -> List[int]:
    n = len(nums1)
    maxpq = [(-val, i) for i, val iin enumerate(nums2)]
    heapq.heapify(maxpq)
    nums1.sort()

    left, right = 0, n - 1
    res = [0] * n

    while maxpq:
        val, i = heapq.heappop(maxpq)
        maxval = -val
        if (maxval < nums1[right]:
            res[i] = nums1[right]
            right -= 1
        else:
            res[i] = nums1[left]
            left += 1
    return res
```


