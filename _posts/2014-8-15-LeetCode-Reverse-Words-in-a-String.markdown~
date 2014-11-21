---
layout: post
title:  "Reverse Words in a String"
date:   2014-8-15 19:13:17
categories: leetcode
---

{% highlight ruby %}
package com.lw.leet1;

import java.util.Stack;

/**
 * @ClassName:Solution
 * @Description:
 *         Reverse Words in a String 
 *         Total Accepted: 26194 Total Submissions: 187094 My Submissions
 *         Given an input string, reverse the string word by word.
 * 
 *         For example
 *             Given s = "the sky is blue"
 *             return "blue is sky the".
 * 
 *         Clarification:
 *             What constitutes a word?
 *             A sequence of non-space characters constitutes a word.
 *         Could the input string contain leading or trailing spaces?
 *             Yes. However, your reversed string should not contain leading or trailing spaces.
 *         How about multiple spaces between two words?
 *             Reduce them to a single space in the reversed string.
 * 
 * @Author LiuWei
 * @Date 2014年8月15日下午7:48:48
 * @Mail nashiyue1314@163.com 
 */
public class Solution {
    
    public String reverseWords(String word){
        Stack<String> sstack = new Stack<String>();
        int flag = 0;
        for(int i= 0; i<word.length(); i++){
            while(i<word.length() && word.charAt(i)==' '){
                i++;
            }
            flag = i;
            while(i<word.length() && word.charAt(i)!=' '){
                i++;
            }
            if(flag != i){
                sstack.push(word.substring(flag, i));
            }
        }
        String res = "";
        while(!sstack.isEmpty()){
            res += sstack.pop()+" ";
        }
//        The input string which is made up of space
        if(res.length()==0){
            return "";
        }
        return res.substring(0, res.length()-1);
    }
    
    public String reverseWords2(String word){
        String res ="";
        int flag = 0;
        for(int i= 0; i<word.length(); i++){
            while(i<word.length() && word.charAt(i)==' '){
                i++;
            }
            flag = i;
            while(i<word.length() && word.charAt(i)!=' '){
                i++;
            }
            if(flag != i){
                res = word.substring(flag, i)+" "+res;
            }
        }
//        The input string which is made up of space
        if(res.length()==0){
            return "";
        }
        return res.substring(0, res.length()-1);
    }
    
    public static void main(String[] args){
        Solution s = new Solution();
        System.out.println(s.reverseWords2("   hello world    "));
    }
}

{% endhighlight %}


