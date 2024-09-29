---
title: 算法笔记
date: 2024-09-27 18:57:53 +0800
categories: [note, algorithm]
tags: [algorithm, note]     # TAG names should always be lowercase
typora-copy-images-to: ./..\assets\img\2024-9-27-algorithm
typora-root-url: ./..
---

## 二分

```java
public int binarySearch(int[] nums,int targer){
    int l=0,r=nums.length;
    while(l<r){
        int mid=l+(r-l)/2;
        if(nums[mid]<target){
            l=mid+1;
        }else r=mid;
    }
    return l;
}
```

## 单调栈

### [每日温度](https://leetcode.cn/problems/daily-temperatures/solutions/2470179/shi-pin-jiang-qing-chu-wei-shi-yao-yao-y-k0ks/)

![image-20240928195708109](/assets/img/2024-9-27-algorithm/image-20240928195708109.png)

从左到右：1入栈，4入栈是1的下一个更大温度，记录答案且1无用了，删除，3入，5入，4和3的下一个更大温度就是5，4和3无用了，删除......形成一个单调递增栈结构

从右往左：6入，3入，2入，5入，往右遍历，6是答案，5比2和3大，所以不可能是前面的数的答案了，删除......形成一个单调递减栈的结构

及时去掉无用元素，维护栈内元素有序

### [接雨水](https://leetcode.cn/problems/trapping-rain-water/)

![image-20240928202106363](/assets/img/2024-9-27-algorithm/image-20240928202106363.png)

横着计算，面积由当前元素（放入栈中打破单调严格递减的元素）下标，栈顶元素下标、栈顶下的元素下标决定，若栈顶元素出栈后栈为空则退出，否则计算答案并累加

```java
class Solution {
    public int trap(int[] height) {
        int ans = 0;
        Stack<Integer> st = new Stack<>();
        for (int i = 0; i < height.length; i++) {
            while (!st.empty() && height[i] >= height[st.peek()]) {
                int bottomH = height[st.pop()];
                if (st.empty()) {
                    break;
                }
                int left = st.peek();
                int dh = Math.min(height[left], height[i]) - bottomH;
                ans += dh * (i - left - 1);
            }
            st.push(i);
        }
        return ans;
    }
}
```

## 滑动窗口

[长度最小的子数组]( https://leetcode.cn/problems/minimum-size-subarray-sum/solution/biao-ti-xia-biao-zong-suan-cuo-qing-kan-k81nh/)

[无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/solution/xia-biao-zong-suan-cuo-qing-kan-zhe-by-e-iaks/)

[乘积小于 K 的子数组]( https://leetcode.cn/problems/subarray-product-less-than-k/solution/xia-biao-zong-suan-cuo-qing-kan-zhe-by-e-jebq/)

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int ans=0,n=s.length();
        char[] ch=s.toCharArray();
        int[] hash=new int[128];
        int l=0;
        for(int i=0;i<n;i++){
            hash[ch[i]]++;
            while(hash[ch[i]]>1){
                hash[ch[l++]]--;
            }
            ans=Math.max(ans,i-l+1);
        }
        return ans;
    }
}
```

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int n=nums.length;
        int ans=n+1;
        int sum=0;
        int l=0;
        for(int i=0;i<n;i++){
            sum+=nums[i];
            while(sum>=target){
                ans=Math.min(ans,i-l+1);
                sum-=nums[l];
                l++;
            }
        }
        return ans>n?0:ans;
    }
}
```

利用所有数都是正整数，遍历到的当前数导致整个子数组不满足条件时，左指针右移并移除相关元素，进行计算
