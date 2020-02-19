---
layout: post
title:  "leetCode 刷题记 [001] 两数之和"
date:   2020-02-19 20:30:13 +0800
categories: leetCode
tags: leetCode
---

leetCode 刷题记，从此开始。


#### 001 两数之和

[题目传送门](https://leetcode-cn.com/problems/two-sum/) <br />

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。
例：

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```
golang 实现思路，使用 map 结构，存储 key 为遍历值的 value 值
{% highlight golang linenos %}
func twoSum(nums []int, target int) []int {
	numMap := make(map[int]int)
	for i := 0; i < len(nums); i++ {
		diff := target - nums[i]
		if v, ok := numMap[diff]; ok {
			return []int{v, i}
		} else {
			numMap[nums[i]] = i
		}
	}
	return []int{}
}
{% endhighlight %}

php 使用了另一种实现思路，直接两重循环
{% highlight php linenos %}
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $target
     * @return Integer[]
     */
    function twoSum($nums, $target) {
        $temp = $nums;
        $result = [];
        foreach ($nums as $key => $num) {
            $res = $target - $num;
            unset($temp[$key]);
            if (in_array($res,$temp)) {
                foreach ($nums as $k => $n) {
                    if ($n == $res) {
                        $result = [$key,$k];
                    }
                }
            }
        }
        return $result;
    }
}
{% endhighlight %}

用python也试试
{% highlight python linenos %}
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashdict = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in hashdict and i != hashdict[complement]:
                return [i, hashdict[complement]]
            hashdict[num] = i
        
        return hashdict
{% endhighlight %}
