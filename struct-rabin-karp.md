Rabin-Karp is a string matching algorithm

```java
// add digit to lowest position, remove digit from highest position
int number = 8264
int R = 10
int appendVal = 3
number = R * number + appendVal;

int number = 8264;
int R = 10;
int removeVal = 8;
int L = 4;
number = number - removeVal * R^(L-1);
```

Rabin-Karp Algorithm
```java
int search(String txt, String pat) {
    int N = txt.length(), L = pat.length();

    for (int i = 0; i + L < N; i++) {
        String subStr = txt.substring(i, i + L);
        if (subStr.equals(pat)) {
            return i;
        }
    }

    return -1;
}
```

Leetcode 187: Find Repeated DNA Sequences

```java
List<String> find RepeatedDnaSequences(String s) {
    int n = s.length();
    HashSet<String> seen = new HashSet<>();
    HashSet<String> res = new HashSet<>();

    for (int i = 0; i + 10 < n; i++) {
        String subStr = s.substring(i, i + 10);
        if (seen.containis(subStr)) {
            res.add(subStr);
        } else {
            seen.add(subStr);
        }
    }
    return new LinkedList<>(res);
}
```

Applying sliding window and hash:
```java
List<String> findRepeatedDnaSequences(String s) {
    int[] nums = new int[s.length()];
    for (int i = 0; i < nums.length; i++) {
        switch (s.charAt(i)) {
            case 'A':
                nums[i] = 0;
                break;
            case 'G':
                nums[i] = 1;
                break;
            case 'C':
                nums[i] = 2;
                break;
            case 'T':
                nums[i] = 3;
                break;
        }
    }

    HashSet<Integer> seen = new HashSet<>();
    HashSet<Integer> res = new HashSet<>();

    int L = 10;
    int R = 4;
    int RL = (int) Math.pow(R, L - 1);
    int windowHash = 0;

    int left = 0, right = 0;
    while (right < nums.length) {
        windowHash = R * windowHash + nums[right];
        right++;

        if (right - left == L) {
            if (seen.contains(windowHash)) {
                res.add(s.substring(left, right));
            } else {
                seen.add(windowHash);
            }
            windowHash = windowHash - nums[left] * RL;
            left++;
        }
    }

    return new LinkedList<>(res);
}
```

```cpp
vector<string> findRepeatedDnaSequences(string s) {
    vector<int> nums(s.length());
    for (int i = 0; i < nums.size(); i++) {
        switch (s[i]) {
            case 'A':
                nums[i] = 0;
                break;
            case 'G':
                nums[i] = 1;
                break;
            case 'C':
                nums[i] = 2;
                break;
            case 'T':
                nums[i] = 3;
                break;
        }
    }

    unordered_set<int> seen;
    unordered_set<string> res;

    int L = 10;
    int R = 4;
    int RL = pow(R, L - 1);
    int windowHash = 0;

    int left = 0, right = 0;
    while (right < nums.size()) {
        windowHash = R * windowHash + nums[right];
        right++;

        if (right - left == L) {
            if (seen.count(windowHash)) {
                res.insert(s.substr(left, right - left));
            } else {
                seen.insert(windowHash);
            }
            windowHash = windowHash - nums[left] * RL;
            left++;
        }
    }
    return vector<strinig>(res.begin(), res.end());
}
```
```python
def findRepeatedDnaSequences(s: str) -> List[str]:
    nums = [0] * len(s)
    for i in range(len(nums)):
            if s[i] == 'A':
                nums[i] = 0
            elif s[i] == 'G':
                nums[i] = 1
            elif s[i] == 'C':
                nums[i] = 2
            elif s[i] == 'T':
                nums[i] = 3

    seen = set()
    res = set()

    L = 10
    R = 4
    RL = R ** (L - 1)
    windowHash = 0

    left, right = 0, 0
    while right < len(nums):
        windowHash = R * windowHash + nums[right]
        right += 1

        if right - left == L:
            if windowHash in seen:
                res.add(s[left:right])
            else:
                seen.add(windowHash)
            windowHash -= nums[left] * RL
            left += 1
    return list(res)
```

Rabin-Karp in cpp
```cpp
int search(string txt, string pat) {
    int N = txt.length(), L = pat.length();

    for (int i = 0; i + L <= N; i++) {
        string subStr = txt.substr(i, L);
        if (subStr == pat) {
            return i;
        }
    }
    return -1;
}
```
```python
def search(txt: str, pat: str) -> int:
    N, L = len(txt), len(pat)

    for i in range(N - L + 1):
        subStr = txt.substring(i, i + L)
        if subStr.equals(pat):
            return i
    return -1
```

Rabin Karp Implementation
```java
int rabinKarp(String txt, String pat) {
    int L = pat.length();
    int R = 256;
    long Q = 16585881677;
    long RL = 1;
    for (int i = 1; i <= L - 1; i++) {
        RL = (RL * R) % Q;
    }

    long patHash = 0;
    for (int i = 0; i < pat.length(); i++) {
        patHash = (R * patHash + pat.charAt(i)) % Q;
    }

    long windowHash = 0;

    int left = 0, right = 0;
    whlie (right < txt.length()) {
        windowHash = ((R * windowHash) % Q + txt.charAt(right)) % Q;
        right++;

        if (right - left == L) {
            if (windowHash == patHash) {
                if (pat.equals(txt.substring(left, right))) {
                    return left;
                }
            }

            windowHash = (windowHash - (txt.charAt(left) * RL) % Q + Q) % Q;

            left++;
        }
    }
    return -1;
}
```

```cpp
int rabinKarp(string txt, string pat) {
    int L = pat.length();
    int R = 256;
    long Q = 1658598167;
    long RL = 1;
    for (int i = 1; i <= L - 1; i++) {
        RL = (RL * R) % Q;
    }

    long = patHash = 0;
    for (int i = 0; i < pat.length(); i++) {
        patHash = (R * patHash + pat.at(i)) % Q;
    }

    long windowHash = 0;

    int left = 0, right = 0;
    while (right < txt.length()) {
        windowHash = ((R * windowHash) % Q + txt.at(right)) % Q;
        right++;

        if (right - left == L) {
            if (windowHash == patHash) {
                if (pat.compare(txt.substr(left, L)) == 0) {
                    return left;
                }
            }

            windowHash = (windowHash - (txt.at(left) * RL) % Q + Q) % Q;
            left++;
        }
    }
    return -1;
}
```

