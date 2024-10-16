# Find All Palindromic Substrings

Given two strings `s` and `p`, return an array of all the start indices of palindromic substrings in `s` that are permutations of `p`.

A **Palindromic Substring** is a sequence of characters in a string that reads the same backward as forward.

**Note:** Each palindrome in the result must use all characters of `p` exactly once, meaning the length of each palindromic substring should equal the length of `p`. The palindromic substring does not have to match `p` directly but must be a rearrangement of `p` that forms a palindrome.

### Input Format:
- The first line contains string `s`.
- The second line contains string `p`.

### Output Format:
- Return all the starting indices of palindromic substrings of `s` that are permutations of `p` in sorted order.

### Example 1

#### Input
s = "racecaranna"
p = "car"

#### Output
1 3

### Explanation
- The substring with start index `1` is `ace`, which can be rearranged to form the palindrome `eca`.
- The substring with start index `3` is `car`, which can be rearranged to form the palindrome `rac`.

### Example 2

#### Input
s = "leveldeed"
p = "eve"

#### Output
1 3

### Example 3

#### Input
s = "abcdefg"
p = "abc"

#### Output
0 2 4


### Explanation
- The substring with start index `1` is `eve`, which itself is a palindrome.
- The substring with start index `3` is `ede`, which can be rearranged to form `ede` again as a palindrome.

### Constraints
- \(1 \leq s.length, p.length \leq 3 \times 10^4\)
- `s` and `p` consist of lowercase English letters.

### Solution Outline
To solve this problem:
1. Use a sliding window approach similar to the anagram-finding method but add a check to ensure that each substring can be rearranged to form a palindrome.
2. Use frequency counters for `p` and each window in `s`, and check for palindromic conditions:
    - A string can form a palindrome if, for its frequency of characters, at most one character has an odd frequency.

```java
import java.util.*;
import java.io.*;

class Solution {
    public List<Integer> findPalindromicSubstrings(String s, String p) {
        // Write code here
        List<Integer> result = new ArrayList<>();
        int m = s.length();
        int n = p.length();
        if (n > m) {
            return result;
        }
        int[] pFreq = new int[26];
        for (int i = 0; i < n; i++) {
            pFreq[p.charAt(i) - 'a']++;
        }
        int[] sFreq = new int[26];
        for (int i = 0; i < n; i++) {
            sFreq[s.charAt(i) - 'a']++;
        }
        if (canFormPalindrome(sFreq, pFreq)) {
            result.add(0);
        }
        for (int i = n; i < m; i++) {
            sFreq[s.charAt(i) - 'a']++;
            sFreq[s.charAt(i - n) - 'a']--;
            if (canFormPalindrome(sFreq, pFreq)) {
                result.add(i - n + 1);
            }
        }
        return result;
    }

    private boolean canFormPalindrome(int[] sFreq, int[] pFreq) {
        int oddCount = 0;
        for (int i = 0; i < 26; i++) {
            if ((sFreq[i] + pFreq[i]) % 2 != 0) {
                oddCount++;
            }
            if (oddCount > 1) {
                return false;
            }
        }
        return true;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();
        String p = sc.next();
        Solution solution = new Solution();
        List<Integer> res = solution.findPalindromicSubstrings(s, p);
        for (int index : res) {
            System.out.print(index + " ");
        }
        System.out.println();
    }
}
