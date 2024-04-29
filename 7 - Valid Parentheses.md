* In order to solve this problem, we need to utilize a **Stack** approach.

``` c#
public class Solution {
    public bool IsValid(string s) {
        var parenthesisDict = new Dictionary<char, char>(){
            {'(', ')'},
            {'{', '}'},
            {'[', ']'},
        };
        var stack =  new Stack<char>();
        
        foreach (char c in s) {
            if(parenthesisDict.ContainsKey(c))
                stack.Push(c);
            else if(stack.Count > 0 && parenthesisDict[stack.Peek()] == c)
                stack.Pop();
            else
                return false;
        }
        return stack.Count == 0;
    }
}
```