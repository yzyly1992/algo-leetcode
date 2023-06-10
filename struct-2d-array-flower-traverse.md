Leetcode 48: Rotate Image
```java
public void rotate(int[][] matrix) {
    int n = matrix.length;
    // reverse the 2d array in diagonal direction
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    // then reverse verticly
    for (int[] row : matrix) {
        reverse(row);
    }
}

void reverse(int[] arr) {
    int i = 0, j = arr.length - 1;
    while (j > i) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++;
        j--;
    }
}
```

```cpp
void rotate(vector<vector<int>>& matrix) {
    int n = matrix.size();
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
}

void reverse(vector<int>& arr) {
    int i = 0, j = arr.size() - 1;
    while (i < j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++;
        j--;
    }
}
```

```python
def rotate(matrix: List[List[int]]) -> None:
    n = len(matrix)
    for i in range(n):
        for j in range(i, n):
            temp = matrix[i][j]
            matrix[i][j] = matrix[j][i]
            matrix[j][i] = temp

    for i in range(n):
        reverse(matrix[i])

def reverse(arr: List[int]) -> None:
    i = 0
    j = len(arr) - 1
    while i < j:
        temp = arr[i]
        arr[i] = arr[j]
        arr[j] = temp
        i += 1
        j -= 1
```

Leetcode 54: Spiral Traverse 2D Array

```java
List<Integer> spiralOrder(int[][] matrix) {
    int m = matrix.length, n = matrix[0].length;
    int upper_bound = 0, lower_bound = m - 1;
    int left_bound = 0, right_bound = n - 1;
    List<Integer> res = new LinkedList<>();

    while (res.size() < m * n) {
        if (upper_bound <= lower_bound) {
            for (int j = left_bound; j <= right_bound; j++) {
                res.add(matrix[upper_bound][j]);
            }
            upper_bound++;
        }

        if (left_bound <= right_bound) {
            for (int i = upper_bound; i <= lower_bound; i++) {
                res.add(matrix[i][right_bound]);
            }
            right_bound--;
        }

        if (upper_bound <= lower_bound) {
            for (int j = rigth_bound; j >= left_bound; j--) {
                res.add(matrix[lower_bound][j]);
            }
            lower_bound--;
        }

        if (left_bound <= right_bound) {
            for (int i = lower_bound; i >= upper_bound; i--) {
                res.add(matrix[i][left_bound]);
            }
            left_bound++;
        }
    }
    return res;
}
```
```cpp
vector<int> spiralOrder(vector<vector<int>>& matrix) {
    int m = matrix.size(), n = matrix[0].size();
    int upper_bound = 0, lower_bound = m - 1;
    int left_bound = 0, right_bound = n - 1;
    vector<int> res;

    while (res.size() < m * n) {
        if (upper_bound <= lower_bound) {
            for (int j = left_bound; j <= right_bound; j++) {
                res.push_back(matrix[upper_bound][j]);
            }
            upper_bound++;
        }

        if (left_bound <= right_bound) {
            for (int i = upper_bound; i <= lower_bound; i++) {
                res.push_back(matrix[i][right_bound]);
            }
            right_bound--;
        }

        if (upper_bound <= lower_bound) {
            for (int j = right_bound; j >= left_bound; j--) {
                res.push_back(matrix[lower_bound][j]);
            }
            lower_bound--;
        }

        if (left_bound <= right_bound) {
            for (int i = lower_bound; i >= upper_bound; i--) {
                res.push_back(matrix[i][left_bound]);
            }
            left_bound++;
        }
    }
    return res;
}
```

Leetcode 59: Spiral Traverse II

```java
int[][] generateMatrix(int n) {
    int [][] matrix = new int[n][n];
    int upper_bound = 0, lower_bound = n - 1;
    int left_bound = 0, right_bound = n - 1;

    int num = 1;

    while (num < n * n) {
        if (upper_bound <= lower_bound) {
            for (int j = left_bound; j <= right_bound; j++) {
                matrix[upper_bound][j] = num++;
            }
            upper_bound++;
            for (int i = upper_bound; i <= lower_bound; i++) {
                matrix[i][right_bound] = num++;
            }
            right_bound--;
        }
        if (upper_bound <= lower_bound) {
            for (int j = right_bound; j >= left_bound; j--) {
                matrix[lower_bound][j] = num++;
            }
            lower_bound--;
            for (int i = lower_bound; i >= upper_bound; i--) {
                matrix[i][left_bound) = num++;
            }
            left_bound++;
        }
    }
    return matrix;
}
```


        }
