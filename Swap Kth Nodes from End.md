### Problem Statement
Given a singly linked list of size N, and an integer K. You need to swap the Kth node from beginning and Kth node from end in linked list.

Note: You need to swap the nodes through the links and not changing the content of the nodes.

Input Format
The first line contains N, number of nodes in linked list and K, the nodes to be swapped.\

The second line contains the elements of the linked list.

Output Format
Print the linked list in a new line.

Example 1
Input

5 3
1 2 3 4 5
Output

1 2 3 4 5 
Explanation

Here k = 3, hence after swapping the 3rd node from beginning and end the new list will be 1 2 3 4 5.

Example 2
Input

4 4
1 2 3 4
Output

4 2 3 1
Explanation

Here k = 4, hence after swapping the 4th node from beginning and end the new list will be 4 2 3 1.

Constraints
1 <= N <= 10^3

1 < K < N

### Solution
```Java
public class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		//your code here
                Scanner sc = new Scanner(System.in);
                int n = sc.nextInt();
                int k = sc.nextInt();
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
                swap(head,k);
	}
        public static void print(Node head){
                Node ptr = head;
                while(ptr != null){
                        System.out.print(ptr.data + " ");
                        ptr = ptr.next;
                }
        }
        public static int length(Node head){
              Node ptr = head;
                int count = 0;
                while(ptr != null){
                        count++;
                        ptr = ptr.next;
                }
                return count;
        }
        public static void swap(Node head, int k){
                int n = length(head);

                if(n<k){
                        return;
                }
                if(2*k-1 == n) {
                        return;
                }

                Node v = head;
                Node v_prev = null;
               for(int i=1; i<k; i++){
                        v_prev = v;
                        v = v.next;
                }

                Node m = head;
                Node m_prev = null;
               for(int i=1; i<n-k+1; i++){
                        m_prev = m;
                        m = m.next;
                }

               if(v_prev != null){
                       v_prev.next = m;
               }
                if(m_prev != null) {
                        m_prev.next = v;
                }

                Node temp = v.next;
                v.next = m.next;
                m.next = temp;

                if(k == 1){ 
                        head = m;
                }
                if(k == n) {
                        head = v;
                }

                print(head);
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
