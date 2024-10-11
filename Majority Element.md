### Problem Statement

Given an array, arr of size n. Your task is to find the majority element. The majority element is the element that appears more than ceil(n/2) times.

Note: You may assume that the array is non-empty and the majority element always exists in the array.

Input Format
The first line contains an integer n, the size of the array.

The second line contains n space-separated integers, the elements of the array.

Output Format
The output will consist of only 1 integer which will be the majority element of the array.

Example 1
Input

5
1 2 2 2 3
Output

2
Explanation

1 and 3 are present for 1 time. ceil (5/2) = 3. So 1 and 3 cannot be the majority elements. 2 is present 3 times and 3 is greater than 2. So 2 will be our answer.

Example 2
Input

7
3 4 4 4 3 3 4
Output

4

Explanation

ceil (7/2) = 4. 4 is present for 4 times. 3 is present 3 times. As the frequency of 4 is equal to the ceil value (7/2) so 4 will be the answer.

Constraints
1 <= n <= 10^5

1 <= arr[i] <= 10^5

### Solution

```java
public class Main
{
    public static void main (String[] args) throws java.lang.Exception
    {
        //your code here
                Scanner sc = new Scanner (System.in);
                int n = sc.nextInt();
                int [] arr = new int[n];
                for(int i=0; i<n; i++){
                        arr[i] = sc.nextInt();
                }

                int ans = majority(arr);
                System.out.println(ans);
    }

public static int majority(int [] arr){
        int cnt = 0;
        int freq = 0;
        for(int n : arr){
            if(cnt == 0) freq = n;

            if(n == freq) cnt++;
            else cnt--;
        }
        return freq;
    }
}
```

