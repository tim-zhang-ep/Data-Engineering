- 什么是
函数调用出现在调用者函数的尾部，因为是尾部， 所以根本没有必要去保存任何局部变量，直接让被调用的函数返回时越过调用者， 返回到调用者的调用者去。
尾调用原则上都可以通过简化函数调用栈的结构而获得性能优化。


- 情景
https://segmentfault.com/a/1190000024122724



斐波那契
```
function Fibonacci (n) {
  if ( n <= 1 ) {return 1};

  return Fibonacci(n - 1) + Fibonacci(n - 2);
}


//尾递归
function Fibonacci2 (n , ac1 = 1 , ac2 = 1) {
  if( n <= 1 ) {return ac2};

  return Fibonacci2 (n - 1, ac2, ac1 + ac2);
}

// dp
dp = [0 for _ in range(N + 1)]
dp[1] = 1
dp[2] = 1
for i in range(3, N + 1):
    dp[i] = dp[i - 1] + dp[i - 2]


```



factorial
```
function factorial(n) {
  if (n === 1) return 1;
  return n * factorial(n - 1);
}

factorial(5) // 120



//尾递归
function factorial(n, total) {
  if (n === 1) return total;
  return factorial(n - 1, n * total);
}

factorial(5, 1) // 120
```





- 代码优化
sugar

