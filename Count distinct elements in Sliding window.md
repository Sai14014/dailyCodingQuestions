### Problem Statement

Given an array arr of integers and a number K.

Find the count of distinct elements in every window of size K in the array.

Input Format
Input consists of two lines.

First line contains an integer n which is the size of the array and an integer K which is the size of the window.

Next line contains n spaced integers of the array.

Output Format
Print the distinct elements in each window of size K in the array separated by space.

Example 1
Input

7 4
1 2 1 3 4 2 3
Output

3 4 4 3
Explanation

Window 1 of size k = 4 is 1 2 1 3. Number of distinct elements in this window are 3.

Window 2 of size k = 4 is 2 1 3 4. Number of distinct elements in this window are 4.

Window 3 of size k = 4 is 1 3 4 2. Number of distinct elements in this window are 4.

Window 4 of size k = 4 is 3 4 2 3. Number of distinct elements in this window are 3.

Example 2
Input

3 2
4 1 1
Output

2 1
Explanation

Window 1 of size k = 2 is 4 1. Number of distinct elements in this window are 2.

Window 2 of size k = 2 is 1 1. Number of distinct elements in this window are 1.

Constraints
1 <= k <= n <= 10^5

1 <= arr[i] <= 10^3

```java
public class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		//your code here
                Scanner sc = new Scanner(System.in);
                int n = sc.nextInt();
                int k = sc.nextInt();
                int [] arr = new int[n];
                for(int i=0; i<n; i++){
                        arr[i]= sc.nextInt();
                }
                distinct(arr,k);
                // for(int i=0; i<n; i++){
                //       System.out.print(ans[i] + " ");
                // }
	}
        public static void distinct(int [] arr, int k){
                int n = arr.length;
                HashMap<Integer,Integer> map = new HashMap<>();
                for(int i=0; i<k; i++){
                        map.put(arr[i],map.getOrDefault(arr[i],0) + 1);
                }
                System.out.print(map.size() + " ");

                for(int i=k; i<n; i++){
                        if(map.get(arr[i-k]) == 1){
                                map.remove(arr[i-k]);
                        }
                        else{
                                map.put(arr[i-k],map.get(arr[i-k]) - 1);
                        }
                        map.put(arr[i],map.getOrDefault(arr[i], 0) + 1);

                        System.out.print(map.size()+ " ");
                }
        }
}
```
