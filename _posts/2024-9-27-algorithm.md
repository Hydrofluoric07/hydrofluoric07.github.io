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

