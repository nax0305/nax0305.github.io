# 找出数组中第 k 个最大的数

## 题目链接

## 解题思路

先将数组排序，然后使用双指针固定其距离为 k，遍历结束便可的到倒数第 k 大的数

## 解题代码

```java
public int findKthLargest(int[] nums, int k) {
    int n = nums.length;
    Arrays.sort(nums);
    int l=0, r=0;
    for (int i=0; i<n; i++){
        if(r-l+1 < k){
            r++;
            continue;
        }
        l++;
        r++;
    }
    return nums[l-1];
}
```

## 重点

双指针太好用了！！！
