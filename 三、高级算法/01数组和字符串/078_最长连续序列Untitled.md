### 最长连续序列

题目：

给定一个未排序的整数数组 `nums` ，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。



**进阶：**你可以设计并实现时间复杂度为 `O(n)` 的解决方案吗？



例1：

```
输入：nums = [100,4,200,1,3,2]
输出：4
解释：最长数字连续序列是 [1, 2, 3, 4]。它的长度为 4。
```



例2：

```
输入：nums = [0,3,7,2,5,8,4,6,0,1]
输出：9
```



**提示：**

- `0 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`



题解：

**并查集**：

````C++
class Solution {
public:
    unordered_map<int, int> a;

	int longestConsecutive(vector<int>& nums) {

		for (int& num : nums)
		{
			a[num] = num + 1;
		}

		int nResult = 0;
		for (int& num : nums)
		{
			int n = find(num + 1);
			nResult = max(nResult, n - num);
		}

		return nResult;
	}

	int find(int x)
	{
		return a.count(x) ? a[x] = find(a[x]) : x;
	}
};
````



https://leetcode-cn.com/problems/longest-consecutive-sequence/