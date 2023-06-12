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


