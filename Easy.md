---
marp: true
theme: uncover
class: invert
math: mathjax
style: |
  .columns {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1rem;
  }
---

# Leet Code

---

#### 1. Two Sum

```c#
public class Solution
{
    public int[] TwoSum(int[] nums, int target)
    {
        for (int i = 0; i < nums.Length; i++)
        {
            for (int j = i + 1; j < nums.Length; j++)
            {
                if (i != j && nums[i] + nums[j] == target)
                {
                    return new int[] { i, j };
                }
            }
        }

        return new int[] { 0, 0 };
    }
}
```

---

#### 9. Palindrome Number

```c#
public class Solution {
    public bool IsPalindrome(int x) {
        int temp = x;
        int sum = 0;
        while (temp > 0)
        {
            int rem = temp % 10;
            temp /= 10;
            sum = sum * 10 + rem;
        }

        if (sum == x)
            return true;
        else
            return false;
    }
}
```

---

#### 13. Roman to Integer

```c#
public class Solution {
    public int RomanToInt(string s) {
        Dictionary<char, int> romanMapping = new Dictionary<char, int>()
        {
            { 'I', 1 },
            { 'V', 5 },
            { 'X', 10 },
            { 'L', 50 },
            { 'C', 100 },
            { 'D', 500 },
            { 'M', 1000 }
        };

        int sum = 0;
        for (int i = 0; i < s.Length; i++)
        {
            int value = romanMapping[s[i]];
            if (i + 1 < s.Length && romanMapping[s[i + 1]] > value)
            {
                sum -= value;
            }
            else
            {
                sum += value;
            }
        }

        return sum;
    }
}
```

---

#### 14. Longest Common Prefix

```c#
public class Solution
{
    public string LongestCommonPrefix(string[] strs)
    {
        string first = strs[0];
        string str = "";
        string cs = "";
        int totalStrings = strs.Length;

        for (int i = 0; i < first.Length; i++)
        {
            if (i == 0)
                cs = first[i].ToString();

            int count = 0;
            for (int j = 0; j < strs.Length; j++)
            {
                if (strs[j].StartsWith(cs))
                {
                    count++;
                }
            }
            if (count == totalStrings)
            {
                str += first[i];

                if (i + 1 < first.Length)
                    cs += first[i + 1];
            }
            else
            {
                break;
            }
        }

        return str;
    }
}
```

---

#### 15. 3Sum

```c#
public class Solution {
    public IList<IList<int>> ThreeSum(int[] nums) {
        IList<IList<int>> list = new List<IList<int>>();
            Array.Sort(nums);

            for (int i = 0; i < nums.Length; i++)
            {
                if (i > 0 && nums[i - 1] == nums[i])
                {
                    continue;
                }

                int j = i + 1;
                int k = nums.Length - 1;

                while (j < k)
                {
                    int sum = nums[i] + nums[j] + nums[k];
                    if (sum > 0)
                    {
                        k--;
                    }
                    else if (sum < 0)
                    {
                        j++;
                    }
                    else
                    {
                        list.Add(new List<int>() { nums[i], nums[j], nums[k] });
                        j++;
                        while (nums[j - 1] == nums[j] && j < k)
                        {
                            j++;
                        }
                    }
                }
            }

            return list;
    }
}
```

---

#### 20. Valid Parentheses

```c#
public class Solution
{
    public bool IsValid(string s)
    {
        Dictionary<string, string> bracketMapping = new Dictionary<string, string>()
        {
            { "(", ")" },
            { "{", "}" },
            { "[", "]" },
        };

        if (s.Length % 2 != 0)
            return false;

        Stack<string> brackets = new Stack<string>();
        for (int i = 0; i < s.Length; i++)
        {
            if (brackets.Any())
            {
                if (bracketMapping.ContainsValue(s[i].ToString()))
                {
                    if (brackets.ElementAt(0) == bracketMapping.FirstOrDefault(x => x.Value == s[i].ToString()).Key)
                    {
                        brackets.Pop();
                    }
                    else
                    {
                        return false;
                    }
                }
                else
                {
                    brackets.Push(s[i].ToString());
                }
            }
            else
            {
                brackets.Push(s[i].ToString());
            }
        }

        if (brackets.Count > 0)
            return false;

        return true;
    }
}
```

---

#### 27. Remove Element

```c#
public class Solution {
    public int RemoveElement(int[] nums, int val) {
        int count = 0, e = nums.Length;
            for (int i = 0; i < e; i++)
            {
                if (nums[i] != val)
                {
                    nums[count++] = nums[i];
                }
            }
            return count;
    }
}
```
