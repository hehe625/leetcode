你正在探访一家农场，农场从左到右种植了一排果树。这些树用一个整数数组 fruits 表示，其中 fruits[i] 是第 i 棵树上的水果 种类 。

你想要尽可能多地收集水果。然而，农场的主人设定了一些严格的规矩，你必须按照要求采摘水果：

你只有 两个 篮子，并且每个篮子只能装 单一类型 的水果。每个篮子能够装的水果总量没有限制。
你可以选择任意一棵树开始采摘，你必须从 每棵 树（包括开始采摘的树）上 恰好摘一个水果 。采摘的水果应当符合篮子中的水果类型。每采摘一次，你将会向右移动到下一棵树，并继续采摘。
一旦你走到某棵树前，但水果不符合篮子的水果类型，那么就必须停止采摘。
给你一个整数数组 fruits ，返回你可以收集的水果的 最大 数目。

 

来源：力扣（LeetCode）
链接：https://leetcode.cn/problems/fruit-into-baskets
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```
class Solution {
    public int totalFruit(int[] fruits) {
       int bask1 = 0;
       int bask2 = 0;
       int ln = fruits[bask1];
       int rn = fruits[bask2];
       int max = 0;
       for (int fast = 0; fast < fruits.length; fast++ ) {
           if (fruits[fast] == ln || fruits[fast] == rn) {
               bask2 = fast;
               max = bask2 -bask1 + 1 > max? bask2 - bask1 + 1:max; 
           }else{
               bask1 = fast -1;
               while (bask1  > 0 && fruits[bask1-1] == fruits[fast-1]) bask1--;
               ln = fruits[bask1];
               bask2 = fast;
               rn = fruits[bask2];
               max = bask2 -bask1 + 1 > max? bask2 - bask1 + 1:max; 
           }
       }
       return max;
    }
}
算法思想：快慢指针，两个指针，遍历数组，当等于篮子的其中一个的时候，将快指针的下标更新到数组遍历到的地方，快指针减去慢指针+1,比较看是否更新，否则，快篮子找到了不同篮子的下标，慢指针只能从快指针后面一个，向后遍历，找到重复数字的最后一个，然后进行比较是否更新max。注意一点，快慢指针的数是不断跟新的，所以存在快慢指针相等的时候，单纯使用指针是会出问题的，比如 112211，快慢指针会有相等的时候，第一个if语句会出问题。
class Solution {
    public int[][] generateMatrix(int n) {
        int loop = n / 2;
        int startx = 0;
        int starty = 0;
        int count = 1;
        int[][] a = new int[n][n];
        int offset = 1;
        while (loop-- != 0) {
            int i = startx;
            int j = starty;
            for (; j < startx + n -offset; j++) {
                a[i][j] = count++;
            }
            for (; i < starty + n -offset;i++){
                a[i][j] = count++;
            }
            for (;j > startx ; j--) {
                a[i][j] = count++;
            }
            for (; i > starty; i--) {
                a[i][j] = count++;
            }
            startx++;
            starty++;
            offset += 2;
        }
        if(n % 2 != 0){
            a[n/2] [n/2] = n*n;
        }
        return a;
    }
}

螺旋数组

给你一个正整数 n ，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的 n x n 正方形矩阵 matrix 。
class Solution {
    public int[][] generateMatrix(int n) {
        int loop = n / 2;//遍历几圈
        int startx = 0;//起始位置
        int count = 1;//放的数字
        int[][] a = new int[n][n];
        int offset = 1;//边界
        while (loop-- != 0) {
            int i = startx;
            int j = startx;
            for (; j < startx + n -offset; j++) {//第一维不变，第二维从起始位置开始到边界-1，第二轮数字少二，但是需要加上起始位置
                a[i][j] = count++;
            }
            for (; i < startx + n -offset;i++){
                a[i][j] = count++;
            }
            for (;j > startx ; j--) {//回到起始位置
                a[i][j] = count++;
            }
            for (; i > startx; i--) {//回到起始位置
                a[i][j] = count++;
            }
            startx++;
            offset += 2;
        }
        if(n % 2 != 0){
            a[n/2] [n/2] = n*n;
        }
        return a;
    }
}
```

