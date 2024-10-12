### Problem Statement

Compare the data in the nodes of the linked lists to check if they are equal. If all data attributes are equal and the lists are of same length, print 1. Otherwise, print 0.

Input Format
The first line contains two integers m and n, the number of nodes in the first linked list and second linked list respectively.

Second line contains m spaced integers, each a value for a data attribute of list 1.

Third line contains n spaced integers, each a value for a data attribute of list 2.

Output Format
Compare the two linked lists and print 1 if the lists are equal. Otherwise, print 0.

Example 1
Input

2 1
1 2
1
Output

0
Explanation

Linked list 1= 1->2->NULL

Linked list 2= 1->NULL

It is clearly visible that the two linked lists are not equal. Therefore, print 0.

Example 2
Input

4 4
1 2 3 4
1 2 3 4
Output

1
Explanation

Linked list 1= 1->2->3->4->NULL

Linked list 2= 1->2->3->4->NULL

It is clearly visible that the two linked lists are equal. Therefore, print 1.

Constraints
1<=n,m<=1000

1<=llist1[i],llist2[i]<=1000

### Solution 

```Java
public class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		//your code here
      Scanner sc = new Scanner(System.in);
      int m = sc.nextInt();
      int n = sc.nextInt();

      Node head1 = null;
      Node ptr = null;
    for(int i=0; i<m; i++){
      Node temp = new Node(sc.nextInt());
      if(head1 == null){
        head1 = temp;
        ptr = temp;
        continue;
      }
      ptr.next = temp;
      ptr = ptr.next;
    }
      ptr = null;
      Node head2 = null;
      for(int i=0; i<n; i++){
        Node temp = new Node(sc.nextInt());
        if(head2 == null){
          head2 = temp;
          ptr = temp;
          continue;
        }
        ptr.next = temp;
        ptr = ptr.next;
      }
      System.out.println(compare(head1, head2));
	}

  public static int compare(Node head1, Node head2){
    Node ptr1 = head1;
    Node ptr2 = head2;

    while(ptr1 != null && ptr2 != null){
      if(ptr1.data != ptr2.data){
        return 0;
      }
      ptr1 = ptr1.next;
      ptr2 = ptr2.next;
    }
    if(ptr1 != null || ptr2 != null){
      return 0;
    }
    return 1;
  }
}

class Node{
  int data;
  Node next;
  Node(int data){
    this.data = data;
    next = null;
  }
}
```



