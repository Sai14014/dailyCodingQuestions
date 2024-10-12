### Problem Statement

Given a singly linked list, delete the middle node of the linked list. If there are even nodes, then there would be two middle nodes. We need to delete the second middle element.

After deleting the node, return the head of the linked list.

In the case of a single node, print the head of a linked list containing only one node, which has a value of -1.

You need to complete the given function with the pointer to the head of the linked list.

Input Format
The first line contains the number of test cases.

For each test case: The first line contains an integer N denoting the number of nodes in the linked list.

The second line contains N space-separated integers denoting elements of the linked list.

Output Format
For each test case, return the head of the modified, linked list.

Example 1
Input

1
4
1 2 3 4
Output

1 2 4
Explanation

The Initial Linked List looks like this:

1 -> 2 -> 3 -> 4

There are two middle nodes, 2 and 3.

The second middle node gets deleted, i.e., 3 is deleted.

The Linked List after the operation looks like this:

1 -> 2 -> 4
Example 2
Input

1
5
1 3 5 2 6
Output

1 3 2 6
Explanation

The Initial Linked List looks like this:

1 -> 3 -> 5 -> 2 -> 6

There is only one middle node, 5, which gets deleted.

The Linked List after the operation looks like this:

1 -> 3 -> 2 -> 6
Constraints
1 <= T <= 10

1 <= N <= 10000

1 <= L[i] <= 100000

### Solution

```Java

public class Main {
    public static void main(String args[]) {
        //your code here
            Scanner sc =new Scanner(System.in);
            int n = sc.nextInt();
            Node head = null;
            Node ptr = head;
            for(int i=0; i<n; i++){
               Node temp = new Node(sc.nextInt());
                if(head == null){
                        head = temp;
                        ptr = head;
                        continue;
                }    
                  ptr.next = temp;
                  ptr = ptr.next;
        }
            head = delete(head);
            print(head);
    }
        public static void print(Node head){
                Node ptr = head;
                while(ptr != null){
                    System.out.print(ptr.data + " ");
                     ptr = ptr.next;   
                }
        }

        public static Node delete(Node head){
                if(head.next == null){
                        System.out.println(-1);
                                return null;
                        }
                // this approch is hear and tortoise approch.
                Node ptr1 = head; // ptr1 move is one step
                Node ptr2 = head; // ptr2 move to two step
                Node temp = head;
                while(ptr2 != null &&  ptr2.next != null){
                        ptr2 = ptr2.next.next;
                        temp = ptr1;
                        ptr1 = ptr1.next;
                }
                // reach here the ptr1 is point to middle node and this node delete.
                temp.next = ptr1.next;
                ptr1.next = null;
                return head;
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




