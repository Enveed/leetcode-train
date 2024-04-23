* Most formal solution is the Hashmap approach, which is to navigate through the array once while storing the elements that have been navigated through in a Hashmap (Dictionary) and looking it up through each iteration.

* Hashmap-based solution:
``` c#
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
        Dictionary<int, int> prevMap = new Dictionary<int, int>();

        for(int i = 0; i < nums.Length; i++) {
            int diff = target - nums[i];
            if(prevMap.ContainsKey(diff)) return new int[]{prevMap[diff], i};
            prevMap[nums[i]] = i;
        }
        return new int[]{0,0};
    }
}
```


* Array IndexOf solution (C#-based solution) (BEST SOLUTION FOR C#):
``` c#
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
        for(int i = 0; i < nums.Length - 1; i++) {
            int indexRemainder = Array.IndexOf(nums, target - nums[i], i + 1);
            if (indexRemainder != -1) return new int[] {i, indexRemainder};
        }
        return new int[]{0,0};
    }
}
```

![[Hashmap-1.png]]
![[Hashmap-2.png]]