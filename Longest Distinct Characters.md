### Problem Statement
Given a string str, find length of the longest substring with all distinct characters.

Input Format
Input consists of one line

The first line is a string str.

Output Format
Length of longest substring with all distinct characters

Example 1
Input

geeksforgeeks
Output

7
Explanation

eksforg is the longest substring with all distinct characters.

Example 2
Input

aaa
Output

1
Explanation

a is the longest substring with all distinct characters.

Constraints
1 <= |S| <= 105

### Solution
```java
public class Main
{
    public static void main (String[] args) throws java.lang.Exception
    {
        //your code here
                Scanner sc = new Scanner(System.in);
                String  str = sc.next();
                // int [] arr = new int[n];
                // for(int i=0; i<n; i++){
                //   arr[i] = sc.nextInt();
                // }
                
                int ans = longest(str);
                System.out.println(ans);
    }

        public static int longest(String str){
                int n = str.length();
                int maxLen = 0;
                int s = 0;
                int e = 0;

                HashMap<Character,Integer> map = new HashMap<>();
                for(e=0; e<n; e++){
                        if(map.containsKey(str.charAt(e))){
                                s = Math.max(s,map.get(str.charAt(e)) +1);
                        }
                        map.put(str.charAt(e),e);
                        maxLen = Math.max(maxLen,e-s+1);
                }
                return maxLen;
        }
}
```
