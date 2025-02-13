# [275. H 指数 II](https://leetcode-cn.com/problems/h-index-ii)

[English Version](/solution/0200-0299/0275.H-Index%20II/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给你一个整数数组 <code>citations</code> ，其中 <code>citations[i]</code> 表示研究者的第 <code>i</code> 篇论文被引用的次数，<code>citations</code> 已经按照 <strong>升序排列 </strong>。计算并返回该研究者的 <strong><code>h</code><em> </em>指数</strong>。</p>

<p><a href="https://baike.baidu.com/item/h-index/3991452?fr=aladdin" target="_blank">h 指数的定义</a>：h 代表“高引用次数”（high citations），一名科研人员的 h 指数是指他（她）的 （<code>n</code> 篇论文中）<strong>总共</strong>有 <code>h</code> 篇论文分别被引用了<strong>至少</strong> <code>h</code> 次。且其余的 <em><code>n - h</code> </em>篇论文每篇被引用次数 <strong>不超过 </strong><em><code>h</code> </em>次。</p>

<p><strong>提示：</strong>如果 <code>h</code><em> </em>有多种可能的值，<strong><code>h</code> 指数 </strong>是其中最大的那个。</p>

<p>请你设计并实现对数时间复杂度的算法解决此问题。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入<code>：</code></strong><code>citations = [0,1,3,5,6]</code>
<strong>输出：</strong>3 
<strong>解释：</strong>给定数组表示研究者总共有 <code>5</code> 篇论文，每篇论文相应的被引用了 0<code>, 1, 3, 5, 6</code> 次。
     由于研究者有 <code>3 </code>篇论文每篇<strong> 至少 </strong>被引用了 <code>3</code> 次，其余两篇论文每篇被引用<strong> 不多于</strong> <code>3</code> 次，所以她的<em> h </em>指数是 <code>3</code> 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>citations = [1,2,100]
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == citations.length</code></li>
	<li><code>1 <= n <= 10<sup>5</sup></code></li>
	<li><code>0 <= citations[i] <= 1000</code></li>
	<li><code>citations</code> 按 <strong>升序排列</strong></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

二分查找。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def hIndex(self, citations: List[int]) -> int:
        n = len(citations)
        left, right = 0, n
        while left < right:
            mid = (left + right) >> 1
            if citations[mid] >= n - mid:
                right = mid
            else:
                left = mid + 1
        return n - left
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public int hIndex(int[] citations) {
        int n = citations.length;
        int left = 0, right = n;
        while (left < right) {
            int mid = (left + right) >>> 1;
            if (citations[mid] >= n - mid) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return n - left;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int n = citations.size();
        int left = 0, right = n;
        while (left < right) {
            int mid = left + right >> 1;
            if (citations[mid] >= n - mid) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return n - left;
    }
};
```

### **Go**

```go
func hIndex(citations []int) int {
	n := len(citations)
	left, right := 0, n
	for left < right {
		mid := (left + right) >> 1
		if citations[mid] >= n-mid {
			right = mid
		} else {
			left = mid + 1
		}
	}
	return n - left
}
```

### **...**

```

```

<!-- tabs:end -->
