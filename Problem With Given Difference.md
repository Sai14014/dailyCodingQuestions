### Problem Statement

Given an one-dimensional unsorted array A containing N integers.

You are also given an integer B. Find if there exists a pair of elements in the array whose difference is B.

Print 1 if any such pair exists else print 0.

Input Format
First line contains n (size of the array)

Second line contains n elements of the array

Third line contains integer B.

Output Format
Print 1 if any such pair exists else print 0.

Example 1
Input

6
5 10 3 2 50 80
78
Output

1
Explanation

Pair (80, 2) gives a difference of 78.

Example 2
Input

2
20 -10
30
Output

1
Explanation

Pair (20, -10) gives a difference of 30 i.e 20 - (-10) => 20 + 10 => 30

Constraints
1 <= N <= 100000
-10000 <= A[i] <= 10000
-20000 <= B <= 20000

### Solution

```Java
public class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
                Scanner sc = new Scanner(System.in);
                int n = sc.nextInt();
                int [] arr = new int[n];
                for(int i=0; i<n; i++){
                        arr[i] = sc.nextInt();
                }
                int k = sc.nextInt();

                int ans = difference(arr,k);
                System.out.println(ans);
	}

        public static int difference(int [] arr, int k){
                int n = arr.length;
                HashSet<Integer> set = new HashSet<>();
                int ans = 0;
                for(int i=0; i<n; i++){
                        set.add(arr[i]); // store the all element in set.
                }
                for(int i=0; i<n; i++){ // iterate all array
                        // that means (x - y = target)
                        // over find the set in (target + y == x)
                        // if x present in the set then return 1, another return 0.
                        if(set.contains(k + arr[i])){ 
                                ans = 1;
                        }
                }
                return ans;
        }
}
```
