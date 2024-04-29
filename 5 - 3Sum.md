* In order to solve this problem, we need to use **Sorting** and **Two Pointers** approach. The most optimal time complexity should be: n<sup>2</sup> .

* **C# TIP**: Avoid using **Array.IndexOf** and **Array.LastIndexOf** as it will actually take more time than **while** loop.

``` c#
public class Solution {
    public IList<IList<int>> ThreeSum(int[] nums) {
        IList<IList<int>> resArr = new List<IList<int>>();
        Array.Sort(nums);
        int l, r, target;
        for (int i = 0; i < nums.Length - 2;)
        {
            target = nums[i] * -1;
            l = i + 1;
            r = nums.Length - 1;

            while (l < r)
            {
                if (nums[l] + nums[r] > target)
                    --r;
                else if (nums[l] + nums[r] < target)
                    ++l;
                else
                {
                    var tempList = new List<int>() {nums[i], nums[l], nums[r]};
                    resArr.Add(tempList);
                    while (l < r && nums[l] == tempList[1]) ++l;
                    while (l < r && nums[r] == tempList[2]) --r;
                }
            }
            int currentTargetNum = nums[i];
            while(i < nums.Length - 2 && nums[i] == currentTargetNum) ++i;
        }
        return resArr;
    }
}
```

![[Three-Sum-1.png]]