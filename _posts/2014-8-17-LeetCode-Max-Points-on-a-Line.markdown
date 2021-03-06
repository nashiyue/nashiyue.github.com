---
layout: post
title:  "Max Points on a Line"
date:   2014-8-17 19:13:17
categories: leetcode
---

{% highlight java %}
package com.lw.leet3;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Map.Entry;


/**
 * @ClassName:Solution
 * @Description:Max Points on a Line 
 *         Given n points on a 2D plane, find the maximum number of points that 
 *         lie on the same straight line.
 * @Author LiuWei
 * @Date 2014年8月17日下午2:51:08
 * @Mail nashiyue1314@163.com 
 */

/**
 * Definition for a point.
 * class Point {
 *     int x;
 *     int y;
 *     Point() { x = 0; y = 0; }
 *     Point(int a, int b) { x = a; y = b; }
 * }
 */

public class Solution {

    public int maxPoints(Point[] points) {
        int max = 0;
        if(points.length <= 2){
            max = points.length;
        }
        else{
            for(int i = 0; i < points.length; i++){
                int equalNum = 0;
                Map<Double, Integer> map = new HashMap<Double, Integer>();
                for(int j = i+1; j < points.length; j++ ){
                    if(points[i].x == points[j].x && points[i].y == points[j].y){
                        equalNum ++;
                        continue;
                    }
                    
                    double k = 0;
                    if(points[i].x == points[j].x){
                        k = Double.MAX_VALUE;
                    }
                    else{
                        k = ((double)(points[i].y - points[j].y)/(points[i].x - points[j].x));
                        /**
                         * Submission Result: Wrong Answer
                         * Input:    [(2,3),(3,3),(-5,3)]
                         * Output:    2
                         * Expected:3
                         * 
                         * avoid k = +0.0 -0.0
                         * */
                        if(k == 0){
                            k = 0; 
                        }
                    }
                    
                    if(map.containsKey(k)){
                        map.put(k, map.get(k)+1);
                    }
                    else{
                        map.put(k, 2);
                    }
                }
                
                /**
                 * Submission Result: Wrong Answer
                 * Input:    [(1,1),(1,1),(1,1)]
                 * Output:    0
                 * Expected:3
                 * 
                 * avoid the points are all equal
                 * */
                if(equalNum > max){
                    max = equalNum + 1 ;
                }
                Iterator<Entry<Double, Integer>> iter = map.entrySet().iterator();
                while(iter.hasNext()){
                    Entry<Double, Integer> entry = iter.next();
                    int num = entry.getValue();
                    if( num + equalNum > max){
                        max = num + equalNum; 
                    }
                }
            }
        }
        return max;
    }
    
    public static void main(String[] args){
        Point[] p = {new Point(2, 3),new Point(3,3),new Point(-5,3)};
//        Point[] p = {new Point(1, 1),new Point(1,1),new Point(1,1)};
        
        Solution s = new Solution();
        System.out.println(s.maxPoints(p));
        
    }
    
}
{% endhighlight %}

自己写的时候，出了以下几点问题：

1.与x轴平行情况下，Map区分+0.0与-0.0，导致数据出错，但是不管+0.0与-0.0值是相等的，就是用+0.0 == -0.0条件判断的时候，是true。

2.当所有的点都一样的时候，由于map的Size为0，不进入循环，但是这若干个也算作在一条直线上。所以在前面进行了处理~

总体思想：
利用平面中，点+斜率确定一条直线的思想。当固定某一个顶点的时候，如果斜率相等，那么这个直线唯一确定。
请注意下，变量equalNum


由于Map在Put数据的时候，对Key的判断是进行equal运算，而从下面的Double类的equal源码可以看到，它并不是简简单单的比较两个数据的值是否相等，而是将其调用doubleToLongBits方法，比较该方法返回的值是否相等。将这两个值输出，如下所示：
-9223372036854775808
0
由此，不难理解Map为什么区分+0.0与-0.0~
