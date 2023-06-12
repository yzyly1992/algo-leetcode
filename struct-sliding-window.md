Sliding window big idea:
```java
int left = 0, right = 0;

while (left < right && right < s.size()) {
    window.add(s[right]);
    right++;

    while (while needs shrink) {
        window.remove(s[left]);
        left++;
    }
}
```

Sliding Window Framework:
```java
void slidingWindow(String s) {
    HashMap<Character, Integer> window = new HashMap<>();

    int left = 0, right = 0;
    while (right < s.length()) {
        char c = s.charAt(right);
        window.put(c, window.getOrDefault(c, 0) + 1);
        right++;

        while (left < right && window needs shrink) {
            char d = s.charAt(left);
            window.put(d, window.get(d) - 1);
            left++;
            ...
        }
    }
}
```

```cpp
void slidingWindow(string s) {
    unordered_map<char, int> window;

    int left = 0, right = 0;
    while (right < s.size()) {
        char c = s[right];
        window.add(c);
        right++;
        ...

        while (left < right && window needs shrink) {
            char d = s[left];
            window.remove(d);
            left++;
            ...
        }
    }
}
```

```python
def slidingWindow(s: str) -> None:
    window = dict()
    left = 0
    right = 0
    while right < len(s):
        c = s[right]
        if c not in window:
            window[c] = 1
        else:
            window[c] += 1
        right += 1
        ...

        while (left < right && window needs shrink) {
            d = s[left]
            left += 1
            ...
```

Leetcode 76 : Smallest substring

```java 
public String minWIndow(String s, String t) {
    Map<Character, Integer> need = new HashMap<>();
    Map<Character, Integer> window = new HashMap<>();

    for (char c : t.toCharArray())
        need.put(c, need.getOrDefault(c, 0) + 1);

    int left = 0, right = 0;
    int valid = 0;
    int start = 0, len = Integer.MAX_VALUE;
    while (right < s.length()) {
        char c = s.charAt(right);
        right++;
        if (need.containsKey(c)) {
            window.put(c, window.getOrDefault(c, 0) + 1);
            if (window.get(c).equals(need.get(c))) valid++;
        }

        while valid == need.size()) {
            if (right - left < len) {
                start = left;
                len = right - left;
            }
            char d = s.charAt(left);
            left++;
            if (need.containsKey(d)) {
                if (window.get(d).equals(need.get(d))) {
                    valid--;
                window.put(d, window.get(d) - 1);
            }
        }
    }

    return len == Integer.MAX_VALUE ? "" : s.substring(start, start + len);
}
```

```cpp
string minWIndow(string s, string t) {
    unordered_map<char, int> need, window;
    for (char c : t) need[c]++;

    int left = 0, right = 0;
    int valid = 0;
    int start =  0, len = INT_MAX;
    while (right < s.size()) {
        char c = s[right];
        right++;
        if (need.count(c)) {
            window[c]++;
            if (windw[c] == need[c])
                valid++;
        }

        while (valid == need.size()) {
            if (right - left < len) {
                start = left;
                len = right - left;
            }

            char d = s[left];
            left++;
            if (need.count(d)) {
                if (window[d] == need[d]) {
                    valid--;
                }
                window[d]--;
            }
        }
    }
    return len == INT_MAX ?
        "" : s.substr(start, len);
}
```

```python
def minWindow(s: str, t: str) -> str:
    from collections import defaultdict

    need, window = defaultdict(int), defaultdict(int)
    for c in t:
        need[c] += 1

    left, right = 0, 0
    valid = 0
    start, length =  0, float('inf')
    while right < len(s):
        c = s[right]
        right += 1
        if c in need:
            window[c] += 1
            if window[c] == need[c]:
                valid += 1

        while valid == len(need):
            if right - left < length:
                start = left
                length = right - left

            d = s[left]
            left += 1
            if d in need:
                if window[d] == need[d]:
                    valid -= 1
                window[d] -= 1

    return "" if length == float('inf') else s[start:start + length]
```

Leetcode 567: Check substring

```java
public boolean checkInclusion(String t, String s) {
    HashMap<Character, Integer> need = new HashMap<>();
    HashMap<Character, Integer> window = new HashMap<>();
    for (char c : t.toCharArray()) {
        need.put(c, need.getOrDefault(c, 0) + 1);
    }

    int left = 0, right = 0;
    int valid = 0, length = Integer.MAX_VALUE;

    // extend the window
    while (right < s.length()) {
        char c = s.charAt(right);
        right++;
        if (need.containsKey(c)) {
            window.put(c, window.getOrDefault(c, 0) + 1);
            if (window.get(c).equals(need.get(c))) {
                valid++;
            }
        }

        while (valid == need.size()) {
            if (t.length().equals(right - left)) return true;
            char d = s.charAt(left);
            left++;
            if (need.containsKey(d)) {
                if (window.get(d).equals(need.get(d))) {
                    valid--;
                }
                window.put(d, window.get(d) - 1);
            }
        }
    }

    return false;
}
```

```cpp
bool checkInclusion(string t, string s) {
    unordered_map<char, int> need, window;
    for (char c : t) need[c]++;

    int left = 0, right = 0;
    int valid = 0;
    while (right < s.size()) {
        char c = s[right];
        right++;
        if (t.count(c)) {
            window[c]++;
            if (window[c] == need[c]) {
                valid++;
            }
        }

        while (right - left >= t.size()) {
            if (valid == need.size()) {
                return true;
            }
            char d = s[left];
            left++;

            if (need.count(d)) {
                if (window[d] == need[d]) {
                    valid--;
                }
                window[d]--;
            }
        }
    }
    return false;
}
```

```python
def checkInclusion(t: str, s: str) -> bool:
    from collection import defaultdict
    need, window = defaultdict(int), default(int)
    for c in t:
        need[c] += 1

    left, right = 0, 0
    valid = 0
    while right < len(s):
        c = s[right]
        right += 1
        if window[c] == need[c]:
            valid += 1

        while right - left >= len(t):
            if valid == len(need):
                return True
            d = s[left]
            left += 1
            if d in need:
                if window[d] == need[d]:
                    valid -= 1
                window[d] -= 1
    return False
```

Leetcode 438: Find Anagrams

```java
public List<Integer> findAnagrams(String s, String t) {
    List<Integer> result = new ArrayList<>();
    if (t.length() >= s.length()) return result;

    Map<Character, Integer> need = HashMap<>();
    Map<Character, Integer> window = HashMap<>();

    for (char c : t.toCharArray()) {
        need.put(c, need.getOrDefault(c, 0) + 1);
    }
    
    int left = 0, right = 0;
    int valid = 0;

    while (right < s.length()) {
        char c = s.charAt(right);
        right++;
        if (need.containsKey(c)) {
            window.put(c, window.getOrDefault(c, 0) + 1);
            if (window.get(c).equals(need.get(c)) {
                valid++;
            }

            while (left - right >= t.length()) {
                if (valid == need.size()) {
                    result.add(left);
                }
                char d = s.charAt(left);
                left++;

                if (need.containsKey(d)) {
                    if (need.get(d).equals(window.get(d))) {
                        valid--;
                    }
                    window.put(d, window.getOrDefualt(d, 0) - 1);
                }
            }
        }
    }
    return result;
}
```

Leetcode 3: Find Longest Substring with No Repeat Character

```java
int lengthOfLongestSubstring(String s) {
    if (s.length() <= 1) return s.length();
    HashMap<Character, Integer> window = new HashMap<>();

    int left = 0, right = 0;
    int valid = 0;
    int result = 0;

    while (right < s.length()) {
        char c = s.charAt(right);
        right++;
        if (!window.containsKey(c)) {
            valid++;
            window.put(c, 1);
            if (valid == right - left) {
                if (valid > result) {
                    result = valid;
                }
            }
        }
        else if (window.get(c) == 1) {
            valid--;
            window.remove(c);
        } else {
            window.put(c, window.get(c) - 1);
        }

        while (left - right >= valid) {
            char d = s.charAt(left);
            left++;
            if (window.get(d) == 1) {
                valid--;
                window.remove(d);
            } else {
                window.put(d, window.get(d) - 1);
                if (window.get(d) == 1) {
                    valid++;
                    if (valid == right - left) {
                        if (result < valid) {
                            result = valid;
                        }
                    }
                }
            }
        }
    }
    return result;
}
```

Simple solution:
```java
int lengthOfLongestSubstring(String s) {
    Map<Character, Integer> window = new HashMap<>();

    int left = 0, right = 0;
    int res = 0;
    while (right < s.length()) {
        char c = s.charAt(right);
        right++;
        window.put(c, window.getOrDefault(c, 0) + 1);
        while (window.get(c) > 1) {
            char d = s.charAt(left);
            left++;
            window.put(d, window.get(d) - 1);
        }
        res = Math.max(res, right - left);
    }
    return res;
}
```




