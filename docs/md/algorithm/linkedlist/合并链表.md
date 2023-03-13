# 合并链表

## 题目链接

url🔗：https://leetcode.cn/problems/merge-two-sorted-lists/

## 解题思路

利用头节点！！!非常好用的链表题目解题技巧

```java
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
    ListNode head = new ListNode(-1, null);
    ListNode pre = head;
    while(list1 != null && list2 != null){
        if(list1.val <= list2.val){
            pre.next = list1;
            list1 = list1.next;
        }else{
            pre.next = list2;
            list2 = list2.next;
        }
        pre = pre.next;
    }
    pre.next = list1 == null ? list2 : list1;
    return head.next;
}
```

此题还有一个很巧妙的地方就是在于，设置了一个 pre，也即下一个节点的前置节点，这样，`围绕着尾插法构建链表的思路`来实现算法
