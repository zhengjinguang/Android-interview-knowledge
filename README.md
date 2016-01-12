# Android-interview-knowledge
Android 知识点：
1.touch 事件传递
2. ListView 的优化
3. Android内序列化的方式
4. 广播的几种方式
5. service生命周期，启动方式，优点，用途
6. 进程的优先级
7. view的绘制过程
8. android 实现异步调用的几种方式。
9. handler实现
10. MAT的使用
11. traceView 的使用
12. fragment 的作用
13. 应用间调用的几种方式
14. launchMode 模式和区别，flag 有哪些
15. synchronized 作用，修饰不同的时候的作用
16. GC算法
17.Android应用开发之所有动画使用详解
18.图解Android - Android GUI 系统 (1) - 概论
19.Android性能优化
20.Android Material Design
GCRoot 都有哪些？
1、 Class:由系统的类加载器加载的类对象
2、 Static Fields
3、 Thread:活着的线程
4、 Stack Local: java方法的局部变量或参数
5、 JNI Local: JNI方法中的局部引用
6、 JNI Global: 全局的JNI引用
7、 Monitor used: 用于同步的监控对象
8、Help by VM: 用于JVM特殊目的由GC保留的对象
17. android中应用的设计模式
18. LruCache 怎么实现（LRU Cache）
[LeetCode] LRU Cache
LRU Cache leetcode java

19. https原理
a. HTTP协议（超文本传送协议）详解--超经典
b. Https通讯原理
20. aidl 实现机制，怎么使用
21. android 中 IPC 方式
a.Android进程间通信（IPC）机制Binder简要介绍和学习计划 
22. 怎么查找内存泄露
23. 怎么解决启动黑屏时间太长
24. 怎么解决耗电问题
a.Optimizing Battery Life
b.Transferring Data Without Draining the Battery

25. AsyncTask的实现
a.Android AsyncTask完全解析，带你从源码的角度彻底理解   
b.Android实战技巧：深入解析AsyncTask 
26. Hash算法
a.了解hash算法

算法题：
1. 随机打乱一个数组
2. 树的先中后序排序，非递归
3. 快排，单链表快排
Java各种排序算法总结
public static void quickSort(int[] data, int i, int j){
    if(i >= j){
     return;     
         }
           int start = i + 1;
            int end = j
          int pivot = data[i];
          while( start < end){
              while( data[start] < pivot){
                     start++;
               }
              while( data[end] >= pivot){
                       end --;
              }
              if( start < end ){
                  int tmp = data[start];
                   data[start] = data[end];
                   data[end] = tmp;
             }
         }
             data[i]=data[end];
           data[end] = pivot;
           quickSort(data, i, end -1);
           quickSort(data, end+1, j);
}
4. 二分查找
public static int binarySearch(int[] srcArray, int des){   
      
        int low = 0;   
        int high = srcArray.length-1;   
        while(low <= high) {   
            int middle = (low + high)/2;   
            if(des == srcArray[middle]) {   
                return middle;   
            }else if(des <srcArray[middle]) {   
                high = middle - 1;   
            }else {   
                low = middle + 1;   
            }  
        }  
        return -1;  
   } 

5. 链表倒序 - 递归，非递归（Reverse Linked List）
JAVA中关于链表的操作和基本算法
/**
* Definition for singly-linked list.
* public class ListNode {
* int val;
* ListNode next;
* ListNode(int x) { val = x; }
* }
*/
public class Solution {
public static ListNode reverseList(ListNode head){
if(head==null||head.next==null)return head;
ListNode pre=null;
ListNode nex=null;
while(head!=null){
nex=head.next;
head.next=pre;
pre=head;
head=nex;
}
return pre;
}
}
//递归
public class Solution {
public static Node reverseListRec(ListNode head){
if(head==null||head.next==null)return head;
Node reHead=reverseListRec(head.next);
head.next.next=head;
head.next=null;
return reHead;
}
}
6. 给定数组 给出全排列（Permutations Permutations II）
递归解决全排列生成算法
7. 树的深度(Maximum Depth of Binary Tree)
java二叉树深度
public void getDepthOfBinaryTree( TreeNode root ){
              if(null == root) {
                    return 0;
                }
               int leftChildDepth = getDepthOfBinaryTree (root.leftChild);
               int rightChildDepth = getDepthOfBinaryTree (root.rightChild);
               return leftChildDepth > rightChildDepth ? leftChildDepth + 1 : rightChildDepth + 1;
 }
8. 给定数组 求全子集(Subsets  Subsets II)
Leetcode Subset I & II
9. 二维数组的螺旋遍历(Spiral Matrix  Spiral Matrix II)
[LeetCode] Spiral Matrix I, II


10. 数组的最长连续子序列和
public int findMaxSumOfSubArray(int[] data){
          if ( null == data || data.length <= 0 ) {
              throw IleagalArgumentsException("data can not be null or empty").
           }
          int curSum = 0;
          int maxSum = Integer.MIN_VALUE;
           for( int i = 0; i< data.length; i ++){
                     if(curSum < 0){
                          curSum = data[i];    
                     } else {
                           curSum += data[i];
                     }
                      if( curSum > maxSum){
                         maxSum = curSum;
                     }
             }
          return maxSum;
}
11. 两个栈实现一个队列(Implement Queue using Stacks)

[LeetCode] Implement Queue using Stacks

java-57-用两个栈实现队列&&用两个队列实现一个栈


12. 如何判断树是一颗完全二叉树
完全二叉树的判定
pulic static isCompleteBinaryTree(TreeNode root){
    if(null == root){
       return false;
     }
    LinkList<TreeNode> list = new LinkList<>();
    list.add(root);
    boolean mustHaveNoChild = false;
       boolean result = true;
    while(list.size()>0){
        TreeNode node = list.removeFirst();
        if(mustHaveNoChild){
            if(node.left !=null || node.right !=null){
                 result = false;
                 break;
             }
         } else {
              if(node.left != null && node.right !=null ){
                  list.add(node.left);
                  list.add(node.right);
              } else if(node.left ==null && node.right !=null){
                   result = false;
                   break;  
              } else if(node.left!=null){
                    list.add(node.left);
                    mustHaveNoChilde =true;
              } else{
                    mustHaveNoChild = true;  
               }
         }
     }
     list.clear();
     return result;
}

13. 最大公约数，一个小数变分数
14. 遍历一个二叉树，要求 第一层从左至右，第二层从右至左
15. 找到二叉查找树中任意两节点的最近公共父亲节点（Lowest Common Ancestor of a Binary Tree 、Lowest Common Ancestor of a Binary Search Tree）
16. 一个数组有正数负数，输出一个负数在前面，正数在后面的数组
public int[] reorderNegativePositive(int[] data){
          if ( null == data || data.length <= 0 ) {
               return data;
           }
          int start = 0;
          int end =  data.length -1 ;
           while ( start < end ) {
                   while(start < end  && data[start] < 0){
                            ++ start;
                     }
                   while(start < end  && data[end] >= 0){
                            -- end;
                     }
                     if( start < end){
                           int temp = start;
                            start  = end;
                            end  = temp;
                     }
             }
          return data;
}

17. 求一个数组的最大元素差，要求减数的index 大于 被减数的index（Maximum Gap）
数组中数对差最大
public int findMaxMinus( int[] data){
          if ( null == data || data.length < 2 ) {
              throw IleagalArgumentsException("data can not be null or empty").
           }
           int max = data[0];
            int maxMinus = Integer.MIN_VALUE;
            for( int i = 1; i< data.length; i ++){
                    if( maxMinus < max - data[i]) {
                          maxMinus = max - data[i];
                     }
                     if(max < data[i]){
                         max = data[i];
                     }
             }
              return maxMinus;
}
18.堆排序：
