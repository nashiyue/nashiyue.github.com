---
layout: post
title:  "Insertion Sort List"
date:   2014-8-20 19:13:17
categories: leetcode
---

{% highlight java %}
package com.lw.leet5;

/**
 * @ClassName:Solution
 * @Description:
 *         Insertion Sort List 
 *         Sort a linked list using insertion sort.
 * @Author LiuWei
 * @Date 2014年8月20日下午7:50:07
 * @Mail nashiyue1314@163.com 
 */
public class Solution {

    public ListNode insertionSortList(ListNode head) {
        // if only one or two elements ,return head
        if(head == null || head.next == null){
            return head;
        }
        ListNode cur = head.next;
        ListNode tmp = null;
        while(cur != null){
            tmp = head;
            //get the insertion position
            while(tmp != cur && tmp.val < cur.val){
                tmp = tmp.next;
            }
            //if need insert, switch the value
            if(tmp != cur){
                int num1 = cur.val;
                int num2 ;
                while(tmp != cur){
                    //store the tmp value
                    num2 = tmp.val;
                    tmp.val = num1;
                    num1 = num2;
                    tmp = tmp.next;
                }
                //init cur
                tmp.val = num1;
            }
            cur = cur.next;
        }
        return head;
    }

    public static void main(String args[]) {
        int[] arr = {10,3,2,4,0,0,-1,2,-2};
         ListNode head = new ListNode(arr[0]);
         ListNode curr = head;
         for(int i=1; i<arr.length; i++){
             ListNode node = new ListNode(arr[i]);
             curr.next = node;
             curr = curr.next;
         }
        
        ListNode tmp  = new Solution().insertionSortList(head);
        while(tmp != null){
            System.out.println(tmp.val);
            tmp = tmp.next;
        }
    }

}
{% endhighlight %}


