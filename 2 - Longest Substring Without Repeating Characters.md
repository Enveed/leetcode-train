* Most formal solution is to use Sliding Window algorithm.

``` c#
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        var letterIdx = new Dictionary<char, int>();
        int l = 0, r = 0, maxLength = 0;
        for(r = 0; r < s.Length; r++)
        {
            if(letterIdx.ContainsKey(s[r])) {
                l = Math.Max(l, letterIdx[s[r]] + 1);
            }

            letterIdx[s[r]] = r;

            maxLength = Math.Max(maxLength, r - l + 1);
        }
        return maxLength;
    }
}
```

* C# unique solution with list:
``` c#
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        var charList = new List<char>();
        int maxLength = 0;
        foreach (char c in s)
        {
            if(charList.Contains(c)) {
                var idx = charList.IndexOf(c);
                charList.RemoveRange(0, idx + 1);
            }
            charList.Add(c);
            maxLength = Math.Max(maxLength, charList.Count);
        }
        return maxLength;
    }
}
```

![[Sliding-Window-1.png]]