Leetcode 380: RandomizedSet - Insert, delete, and get random number in constant time.
```java
class RandomizedSet {
    List<Integer> nums;
    Map<Integer, Integer> valToIndex;

    public RandomizedSet() {
        nums = new ArrayList<>();
        valToIndex = new HashMap<>();
    }

    public boolean insert(int val) {
        if (valToIndex.containsKey(val)) {
            return false;
        }

        valToIndex.put(val, nums.size());
        nums.add(val);
        return true;
    }

    public boolean remove(int val) {
        if (!valToIndex.containsKey(val)) {
            return false;
        }

        int index = valToIndex.get(val);
        valToIndex.put(nums.get(nums.size() - 1), index);
        Collections.swap(nums, index, nums.size() - 1);
        nums.remove(nums.size() - 1);
        valToIndex.remove(val);
        return true;
    }

    public int getRandom() {
        return nums.get((int) (Math.random() * nums.size()))
    }
}
```

```cpp
class RandomizedSet {
public:
    vector<int> nums;
    unordered_map<int, int> valToIndex;

    bool insert(int val) {
        if (valToIndex.count(val)) {
            return false;
        }

        valToIndex[val] = nums.size();
        nums.push_back(val);
        return true;
    }

    bool remove(int val) {
        if (!valToIndex.count(val)) {
            return false;
        }

        int index = valToIndex[val];
        valToIndex[nums.back()] = index;
        swap(nums[index], nums.back());
        nums.pop_back();
        valToIndex.erase(val);
        return true;
    }

    int getRandom() {
        return nums[rand() % nums.size()];
    }
};
```

```python
import random

class RandomizedSet:
    def __init__(self):
        self.nums = []
        self.valToIndex = {}
    
    def insert(self, val: int) -> bool:
        if val in self.valToIndex:
            return False

        self.valToIndex[val] = len(self.nums)
        self.nums.append(val)
        return True

    def remove(self, val: int) -> bool:
        if val not in self.valToIndex:
            return False
        
        index = self.valToIndex[val]
        self.valToIndex[self.nums[-1]] = index
        self.nums[index], self.nums[-1] = self.nums[-1], self.nums[index]
        self.nums.pop()
        del  self.valToIndex[val]
        return True

    def getRandom(self) -> int:
        return random.choice(self.nums)
```

Leetcode 710: Random number in blacklist
```java
class Solution {
    int sz;
    Map<Integer, Integer> mapping;

    public Solution(int N, int[] blacklist) {
        sz = N - blacklist.length;
        mapping = new HashMap<>();
        for (int b : blacklist) {
            mapping.put(b, 666);
        }

        int last = N - 1;
        for (int b : blacklist) {
            if (b >= sz) {
                continue;
            }
            while (mapping.containsKey(last)) {
                last--;
            }
            mapping.put(b, last);
            last--;
        }
    }

    public int pick() {
        int index = (int)(Math.random() * sz);
        if (mapping.containsKey(index)) {
            return mapping.get(index);
        }
        return index;
    }
}
```


