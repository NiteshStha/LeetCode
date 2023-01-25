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

  code {
    border-radius: 10px;
  }
---

# Leet Code

###### Medium Problems

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

#### 28. Find the Index of the First Occurrence in a String

```c#
public class Solution {
    public int StrStr(string haystack, string needle) {
        return haystack.IndexOf(needle);
    }
}
```

---

# GGs
