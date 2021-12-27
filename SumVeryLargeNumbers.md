# SumVeryLargeNumbers

My various attempts to create the simple code for this method.

### Assumptions
User has provided the two strings with numbers only.

#### Attempt #2
A more optimzed version, eliminating the additional 2 string variables 'large' and 'small' instead utilizing the 'output' variable to interchange the inputs to determine bigger number.

```
  public static string SumVeryLargeNumbers(string a, string b)
  {
      string output = a;        
      if (b.Length > a.Length)
      {
          a = b;
          b = output;
      }
      output = string.Empty;
      int carry = 0;
      for(int i = a.Length - 1; i >= 0; i--) {            
          int sum = carry + int.Parse(a[i].ToString())
                  + (i - (a.Length - b.Length) >= 0
                  ? int.Parse(b[i-(a.Length - b.Length)].ToString())
                  : 0);
          output = sum % 10 + output;
          carry = sum >= 10 ? sum / 10 : 0;
      }
      return carry > 0 ? carry + output : output;
  }
```

#### Attempt #1
Basically getting string inputs from the user, the 
```
  public static string SumVeryLargeNumbers(string a, string b)
  {
      string output = string.Empty;

      int[] aa = a.pushIntoArray();
      int[] bb = b.pushIntoArray();

      int[] large = a.Length > b.Length ? aa : bb;
      int[] small = a.Length <= b.Length ? aa : bb;

      int carry = 0;
      int d  = large.Length - small.Length;
      for(int i = large.Length - 1; i >= 0; i--) {            
          int sum = carry + large[i] + (i - d >= 0 ? small[i-d] : 0);
          output = sum % 10 + output;
          carry = sum >= 10 ? sum / 10 : 0;
      }
      output = carry > 0 ? carry + output : output;
      return output;        
  }


  private static int[] pushIntoArray(this string value) {
      int[] output = new int[value.Length];
      for(int i = 0; i<value.Length; i++)
          output[i] = int.Parse(value[i].ToString());
      return output;
  }
```
