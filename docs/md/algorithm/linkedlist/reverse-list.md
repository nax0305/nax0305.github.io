# 反转链表

leetcode题目连接：https://leetcode.cn/problems/reverse-linked-list/

## 思路

1. `头插法`：额外增加一个头结点，在遍历链表的时候，将当前结点添加在头结点后
2. `迭代法`：每次遍历链表的时候，将当前结点指向前一个结点
3. `递归法`：利用栈保存每个结点的信息

## 题目解答

### 头插法
```java
public ListNode reverseList(ListNode head){
    ListNode ans = new ListNode(-1, null);
    while(head != null){
        ListNode p = head;
        head = head.next;
        p.next = ans.next;
        ans.next = p;
    }
    return ans.next;
}
```

### 迭代法
```java
public ListNode reverseList(ListNode head){
    ListNode prev = null;
    ListNode curr = head;
    while(head != null){
        ListNode next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}
```

### 递归法
```java
public ListNode reverseList(ListNode head){
    if(head == null || head.next == null){
        return head;
    }
    ListNode ans = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return ans;
}
```
## 理解总结
头插法和迭代法都是很好的理解的，
头插法保存的固定的位置，而迭代法是保存当前结点前一个和后一个的地址，是一个动态的相关位置。
递归法，其实说来也简单，当保存到倒数第二个结点时，开始出栈，将尾结点（即反转后链表的头结点）保存在ans中，从链表尾部开始局部的改变结点指向。
