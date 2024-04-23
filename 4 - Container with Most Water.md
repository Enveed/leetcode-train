* In order to approach this problem, we need to use **Two Pointers** approach.

``` c#
public class Solution {
    public int MaxArea(int[] height) {
        int res = 0, l = 0, r = height.Count() - 1;
        while (l != r)
        {
            var maxHeight = Math.Min(height[r], height[l]);
            res = Math.Max(res, maxHeight * (r - l));
            if (height[l] > height[r]) r--;
            else l++;
        }
        return res;
    }
}
```