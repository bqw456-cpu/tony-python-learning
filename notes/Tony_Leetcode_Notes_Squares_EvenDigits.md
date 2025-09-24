
# 📘 Tony 的 Leetcode 筆記 - 2025-09-24

---

## ✅ 題目一：Squares of a Sorted Array

### 題目說明：
給定一個已排序的整數陣列 `nums`，回傳一個新的陣列，內容是每個元素的平方，並且排序後的結果。

### 解法邏輯：
- 使用雙指標從左右兩端開始比較絕對值。
- 將較大的平方值從尾端填入結果陣列。

### 程式碼：
```python
class Solution:
    def sortedSquares(self, nums):
        n = len(nums)
        result = [0] * n
        left, right = 0, n - 1
        pos = n - 1

        while left <= right:
            if abs(nums[left]) > abs(nums[right]):
                result[pos] = nums[left] ** 2
                left += 1
            else:
                result[pos] = nums[right] ** 2
                right -= 1
            pos -= 1
        return result
```

### 學習重點：
- 雙指標技巧可以避免額外排序。
- 從尾端填入結果是處理最大值的好方法。

---

## ✅ 題目二：Find Numbers with Even Number of Digits

### 題目說明：
給定一個整數陣列 `nums`，找出其中有偶數位數的數字個數。

### 解法邏輯：
- 對每個數字轉成字串，判斷長度是否為偶數。

### 程式碼：
```python
class Solution:
    def findNumbers(self, nums):
        count = 0
        for num in nums:
            if len(str(num)) % 2 == 0:
                count += 1
        return count
```

### 學習重點：
- 使用 `str()` 可以快速取得數字的位數。
- 判斷偶數位數只需用 `len % 2 == 0`。

---

📘 今天學習重點整理：
- 熟悉雙指標處理排序問題。
- 練習字串與數字轉換的應用。
- 強化對題目邏輯的拆解能力。
