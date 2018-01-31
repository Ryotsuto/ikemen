# ikemen
nandemonaiya

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:
Input: 123
Output:  321

Example 2:
Input: -123
Output: -321

Example 3:
Input: 120
Output: 21

处理溢出的情况是重点，查了一下，可以long long来避免溢出。
自己做的时候用了除以10取余的方法，后来看到有的答案将数字转化为字符串再倒序输出，很方便的样子，之后会再试试。
以及找到了这样的代码：
    int reverse(int x) {
        int t=0;
        while(x!=0)
        {
            if(t>INT_MAX/10||t<(INT_MIN)/10)
                return 0;  
            t=t*10+x%10;
            x/=10;
        }
    return t;
}

之后又去了解了一下INT_MAX和INT_MIN
摘了一段别人的解释：
    INT_MIN在标准头文件limits.h中的定义 
    #define INT_MAX 2147483647 
    #define INT_MIN (-INT_MAX - 1)这里没有简单地将INT_MIN赋值成-2147483647，是因为-2147483648对于编译器而言是个表达式，而2147483648对于32-bit整数是无法表示的， 
    所以经过这个表达式的结果是未定义的。在GCC上直接写-2147483648后，编译器给出了警告，说结果是unsigned。
    
  遇到最大值最小值之类的问题可以用INT_MAX和INT_MIN作最初的比较数字。
