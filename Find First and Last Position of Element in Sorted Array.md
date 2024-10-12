### Problem Statement


Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, print[-1, -1].

You must write an algorithm with O(log n) runtime complexity.

Input Format
The first line contains two integers n (number of elements in the array) and target.

The second line contains n integers (value of elements in the array).

Output Format
Print two space separated integers denoting the first and last index of target.

Example 1
Input

 6 8
 5 7 7 8 8 10
Output

 3 4
Explanation

8 occurs for the first time at index 3 and at index 4 for the last time.

Example 2
Input

 6 6
 5 7 7 8 8 10
Output

 -1 -1
Explanation

6 doesn't occur in the given array, hence we return -1 -1

Constraints
0 <= nums.length <= 10^5

-10^9 <= nums[i] <= 10^9

nums is a non-decreasing array.

-10^9 <= target <= 10^9

### Solution

```java
public class Main
{
  public static int fname(int arr[], int k){
    // this function find target to left to right.
      for(int i=0; i<arr.length; i++){
        if(arr[i] == k){
          return i;
        }
      }
    return -1; //  if not find target thay  return -1.
  }  

  public static int sname(int arr[], int k){
    // tihs function find target to right to left.
    for(int i=arr.length -1; i>=0; i--){
      if(arr[i] == k){
        return i;
      }
    }
    return -1; // if not find target thay  return -1.
  }
	public static void main (String[] args) throws java.lang.Exception
	{
		//your code here
      Scanner sc = new Scanner(System.in);
      
      int n = sc.nextInt();
      int target = sc.nextInt();
      
      int [] arr = new int[n];
      
      for(int i=0; i<n; i++){
        arr[i] = sc.nextInt();
      }
      int ans1 = fname(arr, target); // first index terget
      int ans2 = sname(arr, target); // second index target
      
      int [] ans = new int[2]; // this for store to two ans.
      ans[0] = ans1;
      ans[1] = ans2;
      
      for(int i=0; i<2; i++){ // this for print to two ans.
        System.out.print(ans[i] + " ");
      }
      
	}
}
```
