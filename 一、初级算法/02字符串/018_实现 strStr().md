### 实现 strStr()

**KMP**

题目：

实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。



例1：

```
输入: haystack = "hello", needle = "ll"
输出: 2
```



例2：

```
输入: haystack = "aaaaa", needle = "bba"
输出: -1
```



题解：

```c++
class Solution {
public:
    int strStr(string haystack, string needle) {
		int hSize = haystack.size();
		int nSize = needle.size();

		if (hSize < nSize)
		{
			return -1;
		}

		if (nSize == 0 || haystack == needle)
		{
			return 0;
		}

		for (int i = 0; i < hSize - nSize + 1; i++)
		{
			string s;
			for (int j = i; j < nSize + i; j++)
			{
				s += haystack[j];
			}

			if (s == needle)
			{
				return i;
			}
		}

		return -1;
    }
};
```



KMP:

https://leetcode-cn.com/problems/implement-strstr/solution/zhe-ke-neng-shi-quan-wang-zui-xi-de-kmp-8zl57/

https://leetcode-cn.com/problems/implement-strstr/solution/bang-ni-ba-kmpsuan-fa-xue-ge-tong-tou-ming-ming-ba/





https://leetcode-cn.com/problems/implement-strstr/