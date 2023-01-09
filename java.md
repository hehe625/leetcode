# java核心技术

1.关键字final表示这个变量只能被赋值一次，一旦被赋值之后，就不能再更改了，类似const

2.字符串的常见方法

3.对于较小的字符串构建字符串，如果构建新的string会浪费资源

```
        StringBuilder builder = new StringBuilder();
        char ch = 'a';
        String str = "adb";
        builder.append(ch);
        builder.append(str);
        String completedString = builder.toString();
```

4.读取一个密码使用Console类

```
Console cons = System.console();
String username = cons.readline("User name");
char[] passwd = cons.readPassword("Passward:");
```

5.文件的输入输出

```
//if file path name have '\',you must add other one '\'
Scanner in = new  Scanner(Paths.get("myfile.txt"));
//if file is not exist , system will build this file with this name
PrintWriter out = new PrintWriter("myfile.text");         
```

6.利用Arrays的toString方法，调用Arrays.toString(a)

```
int[] smallPrimes = {1,2,3,45,6};
System.out.println(Arrays.toString(smallPrimes));
```

7.数组的拷贝

```
int[] smallPrimes = {1,2,3,45,6};
int[] copysmallPrimes = new int[8];
copysmallPrimes = Arrays.copyOf(smallPrimes , copysmallPrimes.length);
System.out.println(Arrays.toString(copysmallPrimes));
```

8.当比较字符串是否相等，为了避免对象为空常常使用，常量调用方法

```
b = "admin".equalsIgnoreCase(str);
```

9.二维数组的打印

```
for(int[] row : number){
    for(int value : row){
        System.out.print(value);
    }
}
System.out.println(Arrays.deepToString(number));
```

10.当需要产生不规则数组

```
int[][] odds = new int[11][];
for (int n = 0; n < 10; n++) {
    odd[n] = new int[n + 1];
}
```

