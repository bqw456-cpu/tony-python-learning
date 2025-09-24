
# 📝 Tony 的 Leetcode 筆記 - 2025-09-24

---

## ✅ 題目一：Duplicate Zeros

### 題目說明：
將陣列中的每個 0 都重複一次，並將後面的元素往右移，但不能改變陣列長度。

### 解法邏輯：
1. 計算會被複製的 0 數量。
2. 從後往前複製元素與 0，避免覆蓋原本的值。
3. 特殊處理最後一個 0 卡在邊界的情況。

### 程式碼：
```python
class Solution:
    def duplicateZeros(self, arr):
        n = len(arr)
        zeros = 0

        for i in range(n):
            if i + zeros >= n:
                break
            if arr[i] == 0:
                if i + zeros == n - 1:
                    arr[n - 1] = 0
                    n -= 1
                    break
                zeros += 1

        i = n - 1 - zeros
        j = n - 1
        while i >= 0:
            arr[j] = arr[i]
            if arr[i] == 0:
                j -= 1
                arr[j] = 0
            i -= 1
            j -= 1
```

### 學習重點：
- 理解 in-place 操作的意義。
- 學會從尾端開始複製陣列元素。
- 熟悉邊界條件與 index 控制。

---

## ✅ 題目二：Merge Sorted Array

### 題目說明：
將兩個已排序的陣列合併成一個排序陣列，並儲存在 nums1 中。
注意：nums1 的長度是 m + n，足夠容納所有元素。

### 解法邏輯：
1. 使用三個指標 i, j, k 從尾端開始合併。
2. 每次比較 nums1[i] 和 nums2[j]，把大的放到 nums1[k]。
3. 從後往前填入，避免覆蓋原本的值。

### 程式碼：
```python
class Solution:
    def merge(self, nums1, m, nums2, n):
        i = m - 1
        j = n - 1
        k = m + n - 1

        while j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
```

### 學習重點：
- index 是用來控制「誰要搬」、「搬什麼」、「搬到哪裡」。
- `i = m - 1` 是 nums1 最後一個有效元素的位置。
- `k = m + n - 1` 是 nums1 最後一個空位的位置。
- 從尾端開始合併可以避免覆蓋原本的值。

---

📘 今天學習重點整理：
- 熟悉 in-place 陣列操作技巧。
- 強化 index 控制與邏輯理解。
- 學會從尾端開始合併與複製元素。
