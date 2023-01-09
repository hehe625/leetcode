```
给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。


class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode cur = head;//当前节点
        ListNode tem = head;//保存下一个节点
        ListNode pre = null;//前一个节点
        while (cur != null) {//当前节点不为空
           tem = cur.next;
           cur.next = pre;//反转
           pre = cur;//更新pre
           cur = tem;//更新cur
        }
        return pre;
    }
}
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode heads = reverseList(head);
        ListNode dumm = new ListNode();
        dumm.next = heads;
        ListNode cur = dumm;
        while(n-- > 1) {
            cur = cur.next;
        }
        cur .next = cur.next.next;
        heads = reverseList(dumm.next);
        return heads;
    }
     public ListNode reverseList(ListNode head) {
        ListNode cur = head;//当前节点
        ListNode tem = head;//保存下一个节点
        ListNode pre = null;//前一个节点
        while (cur != null) {//当前节点不为空
           tem = cur.next;
           cur.next = pre;//反转
           pre = cur;//更新pre
           cur = tem;//更新cur
        }
        return pre;
    }
}
//双指针
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dumm = new ListNode();
        dumm.next = head;
        ListNode fast = dumm;
        ListNode low = dumm;
        while (n-- >= 0 ) {
            fast = fast.next;
        }
        while (fast != null) {
            fast = fast.next;
            low = low.next;
        }
        low.next = low.next.next;
        return dumm.next;

    }
}
给定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。
步骤：快慢指针找出交汇点
      只要两个相交，取两个指针，一个指向头，一个指向fast,每次走一步,不断循环，直到相等
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        //只要fast不为空以及fast.next不为空
        while ((fast != null) && (fast.next != null)) {
            slow = slow .next;
            fast = fast.next.next;
            //只要两个相交，取两个指针，一个指向头，一个指向fast,每次走一步,不断循环，直到相等
            if (fast == slow){
                ListNode linkfast = fast;
                ListNode linkhead = head;
                while (linkhead != linkfast) {
                    linkhead = linkhead.next;
                    linkfast = linkfast.next;
                } 
                return linkfast;
            }
        }
        return null;
    }
}

```

