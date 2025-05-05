# 🧮 Two Sum - Java Solution

## 📌 Problem Statement

You are given an array of integers `nums` and an integer `target`.  
Return **indices of the two numbers** such that they add up to `target`.

> - Each input has **exactly one solution**.  
> - You **cannot use the same element twice**.  
> - You can return the answer in **any order**.

---

## ✅ Example

### Input
```java
nums = [2, 7, 11, 15]
target = 9
```

### Output
```java
[0, 1]
```

### Explanation
Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

---

## 💡 Solution Idea

We use a **HashMap** to store the numbers we've seen so far along with their indices.  
For each number `nums[i]`, we calculate its complement as `target - nums[i]`.

- If the complement is already in the map, we've found the pair.
- Otherwise, we store `nums[i]` in the map with its index.

This approach allows us to solve the problem in **one pass** with optimal time and space.

---

## 🧠 Step-by-Step Walkthrough

### Given:
```java
nums = [2, 7, 11, 15]
target = 9
```

1. Initialize an empty map:
   ```java
   map = {}
   ```

2. Iterate through the array:

- `i = 0`, `nums[i] = 2`  
  → `complement = 9 - 2 = 7`  
  → `7` not in map → Add `2` to map  
  ```java
  map = {2: 0}
  ```

- `i = 1`, `nums[i] = 7`  
  → `complement = 9 - 7 = 2`  
  → `2` is in map (index 0)  
  ✅ Return `[0, 1]`

---

## 🧾 Java Code

```java
import java.util.HashMap;

public class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            
            map.put(nums[i], i);
        }
        
        return new int[] {}; // Will never reach here if exactly one solution exists
    }
}
```

---

## 🕒 Time and Space Complexity

| Complexity | Explanation         |
|------------|---------------------|
| ⏱ Time     | O(n) - One pass     |
| 💾 Space   | O(n) - For HashMap  |

---

## 🧪 More Examples

### Example 2
```java
Input: nums = [3, 2, 4], target = 6
Output: [1, 2]
```

### Example 3
```java
Input: nums = [3, 3], target = 6
Output: [0, 1]
```

---

## 🙌 Final Notes

This solution is optimal for time and space.  
HashMap ensures **constant-time lookups**, making it perfect for this kind of pair-search problem.
