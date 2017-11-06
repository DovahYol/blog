//TODO  
substring search（子字符串查找）  
formal languages（形式语言）  
finite automata（有限自动机）  
data compression（数据压缩）  

Java的char是两个byte，因为他是unicode
# 5.1 字符串排序 String sorts

* 低位优先 least-significant-digit LSD
* 高位优先 most-significant-digit MSD

## 键索引计数法 key-indexed counting

一种稳定的排序法

1. 频率统计
2. 将频率转化为索引
3. 数据分类
4. 回写

```java
int N = a.length;

String[] aux = new String[N];
int[] count = new int[R+1];

//计算出现频率
for(int i = 0; i < N; i++)
    count[a[i].key() + 1]++;
//将频率转换为索引
for(int r= 0; r < R; r++)
    count[r+1] += count[r];
//将元素分类
for(int i = 0; i < N; i++)
    aux[count[a[i].key()]++] = a[i];
//回写
for(int i = 0; i < N; i++)
    a[i] = aux[i];
```

## 低位优先的字符串排序 LSD string sort

用键索引计数法将定长字符串组`从右至左`排序w次

```java
public class LSD{
    public static void sort(String[] a, int W){
        //通过前W个字符将a[]排序
        int N = a.length;
        int R = 256;
        String[] aux = new String[N];

        for(int d = W - 1; d >= 0; d--){
            int[] count = new int[R+1];
            for(int i = 0; i < N; i++)
                count[a[i].charAt(d) + 1]++;
            for(int r = 0; r < R; r++)
                count[r+1] += count[r];
            for(int i = 0; i < N; i++)
                aux[count[a[i].charAt(d)]++] = a[i];
            for(int i = 0; i < N;i++)
                a[i] = aux[i];
        }
    }
}
```

## 高位优先的字符串排序 MSD string sort

在将一个字符串数组a[]排序时，首先根据它们的首字母用键索引计数法进行排序，然后（递归地）根据子数组中的字符串的首字母将子数组排序

[课程链接](http://algs4.cs.princeton.edu/51radix/)

## 三向字符串快速排序 Three-way string quicksort

在将字符串数组a[]排序时，根据它们的首字母进行三向切分，然后（递归地）将得到的三个子数组排序：一个含有所有首字母小于切分字符的字符串子数组，一个含有所有首字母等于切分字符的字符串的子数组（排序时忽略它们的首字母），一个含有所有首字母大于切分字符的字符串的子数组

# 5.2 字典树 TRIES

`每个节点都含有R条链接，其中R为字母表的大小`

字典树一般都含有大量的空链接，因此在绘制一棵字典树时一般会忽略空链接

每个节点都对应一个值，可以是空的也可以是符号表中的某个键所关联的值

`查找`
1. 尾字符节点的值非空，命中
2. 尾字符节点的值为空，未命中
3. 查找的过程中有空链接，未命中

`插入`
1. 存在尾字符节点，更新
2. 查找过程中有空链接，建立所有不存在的节点，并将值保存在尾节点

查找所有键 collect()
* DFS遍历所有节点，并将所有字符串加入集合

通配符匹配 wildcard match
* 改造collect()

最长前缀
* 记录查找路径上最长键的长度
* 遇到空链接或被查找字符串结束时终止

`删除`
* 在递归删除了某个节点x之后，如果该节点的值和所有的链接均为空则返回null，否则返回x

### 性质

字典树的形状与键的插入或删除无关：对于任意给定的一组键，其字典树都是唯一的

查找未命中的成本与键的长度无关

* 一棵字典树的链接总数在RN和RNw之间，其中w为键的平均长度
* 不要用其处理来自大型字母表的大量长键，空间消耗太大

## 三向单词查找树 Ternary search tries（TSTs）

`每个节点都含有一个字符、三条链接和一个值`

三条链接，从左至右依次变大

查找
* 如果键小于中儿子，则查找左儿子；若大于中儿子，则查找右儿子；若等于中儿子，则迭代下一字符

插入
1. 存在尾字符节点，更新
2. 查找过程中有空链接，建立所有不存在的节点，并将值保存在尾节点

### 性质

由N个平局长度为w的字符串构造的三向单词查找树中的链接总数在3N和3Nw之间


# 5.3 子字符串查找 SUBSTRING SEARCH

给定一段长度为N的文本和一个长度为M的模式字符串，在文本中找到一个和该模式相符的子字符串

## 暴力字符串查找算法 Brute-force substring search

```java
public static int search(String pat, String txt){
    int M = pat.length();
    int N = txt.length();
    for(int i = 0; i <= N - M; i++){
        int j;
        for(j = 0; j < M; j++)
            if(txt.charAt(i+j) != pat.charAt(j))
                break;
        if(j == M) return i;
    }
    return N;
}
```

KMP算法 Knuth-Morris-Pratt substring search

//TODO 很难理解

Boyer-Moore substring search

