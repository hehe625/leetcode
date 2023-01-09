```
给你一个链表的头节点 head 和一个整数 val ，请你删除链表中所有满足 Node.val == val 的节点，并返回 新的头节点 。
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummp = new ListNode();
        dummp.next = head;
        ListNode cur = dummp;
        while(cur.next != null) {
            if (cur.next.val == val) {
                cur.next = cur.next.next;
            }else{
                cur = cur.next;
            }
        }
        head = dummp.next;
        return head;
    }
}


class MyLinkedList {
    ListNode dumm;
    int size;
    public MyLinkedList() {
        size = 0;
        dumm = new ListNode();
    }
    /**他get的是不需要到cur的前面，所以等于index + 1，可以自己画画
     */
    public int get(int index) {
        if (index < 0 || index > (size - 1) ) {
            return -1;
        } 
        ListNode cur = new ListNode();
        cur = dumm;
        while (index-- >= 0) {
            cur = cur.next;
        }
        return cur.val;
    }
    
    public void addAtHead(int val) {
        ListNode addNode = new ListNode(val);
        addNode.next = dumm.next;
        dumm.next = addNode;
        size++;
    }
    
    public void addAtTail(int val) {
        ListNode cur = new ListNode();
        ListNode add = new ListNode(val);
        cur = dumm;
        while (cur.next != null) {
            cur = cur.next;
        }
        cur.next = add;
        size++;
        
    }
    /**添加某个元素，必须停留在要添加元素的前一个，所以是index-- > 0,插入删除没那么麻烦，就是新元素的next指向cur所在的next，自己的next指向cur的next的next
     */
    public void addAtIndex(int index, int val) {
        ListNode add = new ListNode(val);
        if (index > size) {
            return;
        }
        /*if (index < 0 || index == 0) {
            addAtHead(val);
        }
        if (index == size - 1) {
            addAtTail(val);
        }*/
        ListNode cur = new ListNode();
        cur = dumm;
        while (index-- > 0) {
            cur = cur.next;
        }
       add.next = cur.next;
       cur.next = add;
        size++;

    }
    
    public void deleteAtIndex(int index) {
        if (index < 0 || index >= size ) {
            return;
        }
        ListNode cur = new ListNode();
        cur = dumm;
    //和添加同理
        while(index-- > 0) {
            cur = cur.next;
        }
        cur.next = cur.next.next;
        size--;
    }
}
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
    ListNode() {
        this.val = 0;
        this.next = null;
    }
}
```

