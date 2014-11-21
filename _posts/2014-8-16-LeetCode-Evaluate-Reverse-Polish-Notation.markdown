---
layout: post
title:  "Evaluate Reverse Polish Notation"
date:   2014-8-16 19:13:17
categories: leetcode
---

{% highlight java %}
package com.lw.leet2;

/**
 * @ClassName:Solution
 * @Description:
 *         Evaluate the value of an arithmetic expression in Reverse Polish Notation.
 *         Valid operators are +, -, *, /. Each operand may be an integer or another expression.
 *     
 *         Some examples:
 *             ["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
 *             ["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6
 * 
 * @Author LiuWei
 * @Date 2014年8月16日上午11:31:05
 * @Mail nashiyue1314@163.com 
 */
public class Solution {
    
    private boolean isOper(String s){
        if(s.equals("+")){
            return true;
        }
        if(s.equals("-")){
            return true;
        }
        if(s.equals("*")){
            return true;
        }
        if(s.equals("/")){
            return true;
        }
        return false;
    }
    
    private String getOperRes(String num1,String num2,String oper){
        if(oper.equals("+")){
            return Integer.valueOf(num1)+Integer.valueOf(num2)+"";
        }
        else if(oper.equals("-")){
            return Integer.valueOf(num1)-Integer.valueOf(num2)+"";
        }
        else if(oper.equals("*")){
            return Integer.valueOf(num1)*Integer.valueOf(num2)+"";
        }
        else{
            return Integer.valueOf(num1)/Integer.valueOf(num2)+"";
        }
    }
    
    public int evalRPN(String[] tokens) {
        String[] resArr = new String[tokens.length];
        int index =0;
        for(int i=0;i<tokens.length;i++){
            if(isOper(tokens[i])){
                String num1 = resArr[index-1];
                String num2 = resArr[index-2];
                resArr[index-2] = getOperRes(num2, num1, tokens[i]);
                index--;
            }
            else{
                resArr[index] = tokens[i];
                index ++;
            }
        }
        return Integer.valueOf(resArr[0]);
    }
    
    public static void main(String[] args){
        Solution s = new Solution();
//        String [] tokens = {"4", "13", "5", "/", "+"};
        String [] tokens = {"2", "1", "+"};
        System.out.println(s.evalRPN(tokens));
    }
}
{% endhighlight %}


