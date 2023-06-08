## 1. Fast and Slow Pointers

Leetcode 26: Delete duplicates in ordered array

```java
int removeDuplicates(int[] nums) {
    if (nums.length <= 1) return nums.length;

    int slow = 0;
    int fast = 0;
    
    while (fast <= nums.length) {
        if (nums[slow] != nums[fast]) {
            slow++;
            nums[slow] = nums[fast];
        }
        fast++;
    }

    return slow + 1;
}
```

```cpp
int removeDuplicates(vector<int>& nums) {
    if (nums.size() <= 1) {
        return nums.size();
    }

    int slow = 0, fast = 0;
    while (fast < nums.size()) {
        if (nums[slow] != nums[fast]) {
            slow++;
            nums[slow] = nums[fast];
        }
        fast++;
    }

    return slow + 1;
}
```

```python
def removeDuplicates(nums: List[int]) -> int:
    if len(nums) <= 1:
        return len(nums)

    slow = 0
    fast = 0
    while fast < len(nums):
        if nums[slow] != nums[fast]:
            slow += 1
            nums[slow] = nums[fast]
        fast += 1
    return slow + 1
```

Leetcode 27: remove element in place

```java
int removeElement(int[] nums, int val) {
    if (nums.length == 0) return 0;

    int slow = 0, fast = 0;
    
    while (fast < nums.length) {
        if (nums[fast] != val) {
            nums[slow] = nums[fast];
            slow++;
        }
        fast++;
    }

    return slow;
}
```

```cpp
int removeElement(vector<int>& nums, int val) {
    if (nums.size() == 0) {
        return 0;
    }

    int slow = 0, fast = 0;

    while (fast < nums.size()) {
        if (nums[fast] != val) {
            nums[slow] = nums[fast];
            slow++;
        }
        fast++;
    }
    return slow;
}
```

```python
def removeElement(nums: List[int], val: int) -> int:
    if len(nums) == 0:
        return 0

    slow = 0
    fast = 0

    while fast < len(nums):
        if nums[fast] != val:
            nums[slow] = nums[fast]
            slow += 1
        fast += 1
    return slow
```

## Left and Right Pointers

Binary Search Framework

```java
int binarySearch(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = (right + left) / 2;
        if (nums[mid] == target) return mid;
        else if (nums[mid] < target)
            left = mid + 1;
        else if (nums[mid] > target) 
            right = mid - 1;
    }
    return -1;
}
```

```cpp
int binarySearch(vector<int>& nums, int target) {
    int left = 0, right = nums.size() - 1;
    while (left <= right) {
        int mid = (right + left) / 2;
        if (nums[mid] == target) return mid;
        else if (nums[mid] < target):
            left = mid + 1;
        else if (nums[mid] > target):
            right = mid - 1;
    }
    return -1;
}
```

```python
def binarySearch(nums: List[int], target: int) -> int:
    left, right = 0, len(nums)
    while left <= right:
        mid = (right - left) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid - 1
    return -1
```

Leetcode 167: Two sum II

```java
int[] twoSum(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left < right) {
        int sum = nums[left] + nums[right];
        if (sum == target) {
            return new int[]{left + 1, right + 1};
        } else if (sum < target) {
            left++;
        } else if (sum > target) {
            right--;
        }
    }
    return new int[]{-1, -1};
}
```

```cpp
vector<int> twoSum(vector<int>& nums, int target) {
    int left = 0, right = nums.size() - 1;
    while (left < right) {
        int sum = nums[left] + nums[right];
        if (sum == target) {
            return {left + 1, right + 1};
        } else if (sum < target) {
            left++;
        } else if (sum > target) {
            right--;
        }
    }
    return {-1, -1};
}
```

```python
def twoSum(nums: List[int], target: int) -> List[int]:
    left, right = 0, len(nums) - 1
    while left < right:
        sum = nums[left] + nums[right]
        if sum == target:
            return [left + 1, right + 1]
        elif sum > target:
            right -= 1
        elif sum < target:
            left += 1
    return [-1, -1]
```

## Reverse Array
Leetcode 344: reverse string

```java
void reverseString(char[] s) {
    int left = 0, right = s.length - 1;
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }
}
```

```cpp
void reverseString(vector<char>& s) {
    int left = 0, right = char.size() - 1;
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }
}
```

```python
def reverseString(s: List<str>) -> None:
    left = 0
    right = len(s) - 1
    while left < right:
        temp = s[left]
        s[left] = s[right]
        s[right] = temp
        left += 1
        right -= 1
```

## 4. Check palindrome
Leetcode 5: longest palindrome
```java
String palindrome(String s, int l, int r) {
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
        l--; r++;
    }
    return s.substring(l + 1, r);
}

String longestPalindrome(String s) {
    String res = "";
    for (int i = 0; i < s.length(); i++) {
        String s1 = palindrome(s, i, i);
        String s2 = palindrome(s, i, i + 1);
        res = res.length() > s1.length() ? res : s1;
        res = res.length() > s2.length() ? res : s2;
    }
    return res;
}
```

```cpp
string palindrome(string s, int l, int r) {
    while (l >= 0 && r < s.length() && s[l] == s[r]) {
        l--; r++;
    }

    return s.substr(l + 1, r - l - 1);
}

string longestPalindrome(string s) {
    string res = "";
    for (int i = 0; i < s.length(); i++) {
        string s1 = palindrome(s, i, i);
        string s2 = palindrome(s, i, i + 1);
        res = res.length() > s1.length() ? res : s1;
        res = res.length() > s2.length() ? res : s2;
    }
    return res;
}
```

```python
def palindrome(s: str, l: int, r: int) -> str:
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    return s[l+1, r]

def longestPalindrome(s: str) -> str:
    res = ""
    for i in range(len(s)):
        s1 = palindrome(s, i, i)
        s2 = palindrome(s, i, i + 1)
        res = res if len(res) > len(s1) else s1;
        res = res if len(res) > len(s2) else s2;
    return res
```

