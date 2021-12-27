# FibonacciSeries

#### Attempt #1
```
  static long FibonacciSeries(int n) {    
      if (n <= 2) return n <= 0 ? 0 : 1;
      long l = 1, o = 1;    
      for(int i = 3; i <= n; i++)
      {
          o += l;
          l = o - l;
      }
      return o;
  }
```
