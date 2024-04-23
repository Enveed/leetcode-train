* For this problem, we need to solve it with Expand Around Center approach:

``` c#
public class Solution {
    public string LongestPalindrome(string s) {
        var longestPalindromeIndices = new int[]{0, 0};
        for (int i = 0; i < s.Length; i++) {
            int[] currentPalindromeIndices;
            currentPalindromeIndices = ExpandAroundCenter(s, i, i);
            if (CompareIndicesLength(currentPalindromeIndices, longestPalindromeIndices)) {
                longestPalindromeIndices = currentPalindromeIndices;
            }

            if (i + 1 < s.Length && s[i] == s[i + 1])
            {
                currentPalindromeIndices = ExpandAroundCenter(s, i, i+1);
                if (CompareIndicesLength(currentPalindromeIndices, longestPalindromeIndices)) {
                longestPalindromeIndices = currentPalindromeIndices;
                }
            }
        }
        return s.Substring(longestPalindromeIndices[0], longestPalindromeIndices[1] - longestPalindromeIndices[0] + 1);
    }

    public static bool CompareIndicesLength(int[] currentIndices, int[] longestIndices)
    {
        return currentIndices[1] - currentIndices[0] > longestIndices[1] - longestIndices[0] ? true : false;
    }
    
    public static int[] ExpandAroundCenter(string s, int l, int r)
    {
        while(l >= 0 && r < s.Length && s[l] == s[r])
        {
            l--;
            r++;
        }
        return new int[]{l + 1, r - 1};
    }
}
```

![[Expand-Around-Center-1.png]]

