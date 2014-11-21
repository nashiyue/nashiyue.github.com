---
layout: post
title:  "Sort List"
date:   2014-8-18 19:13:17
categories: leetcode
---

{% highlight java %}
package com.lw.leet4;

/**
 * @ClassName:Solution
 * @Description:
 *         Sort List 
 *         Sort a linked list in O(n log n) time using constant space complexity.
 * @Author LiuWei
 * @Date 2014年8月18日上午10:17:45
 * @Mail nashiyue1314@163.com 
 */

/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
     public ListNode getMiddleNode(ListNode head){
         ListNode slow = head;
         ListNode fast = head;
         while(fast.next != null && fast.next.next != null){
             slow = slow.next;
             fast = fast.next.next;
         }
         return slow;
     }
     
     public ListNode mergeList(ListNode list1,ListNode list2){
         ListNode newHead = new ListNode(-1);
         ListNode curNode = newHead;
         while(list1 != null && list2 != null){
             if(list1.val<= list2.val){
                 curNode.next = list1;
                 list1 = list1.next;
             }
             else{
                 curNode.next = list2;
                 list2 = list2.next; 
             }
             curNode = curNode.next;
         }
         if(list1 == null){
             curNode.next = list2;
         }
         else{
             curNode.next = list1;
         }
         return newHead.next;
     }
     
     public ListNode sortList(ListNode head) {
         if(head == null || head.next == null){
             return head;
         }
         ListNode middleNode  = getMiddleNode(head);
         ListNode nextNode = middleNode.next;
         middleNode.next = null;
         return mergeList(sortList(head), sortList(nextNode));
     }
     
     public static void main(String[] args){
         int[] arr = {4,19,14,5,-3,1,8,5,11,15};
         ListNode head = new ListNode(arr[0]);
         ListNode curr = head;
         for(int i=1; i<arr.length; i++){
             ListNode node = new ListNode(arr[i]);
             curr.next = node;
             curr = curr.next;
         }
         
         ListNode tmp = new Solution().sortList(head);
         while(tmp != null){
             System.out.println(tmp.val);
             tmp = tmp.next;
         }
     }
}
{% endhighlight %}


