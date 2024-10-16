### Problem Statement

You are given three integers `a`, `b`, and `c` representing the number of occurrences of the letters `'a'`, `'b'`, and `'c'` respectively. Your task is to generate the longest possible happy string that satisfies the following conditions:

1. The string only contains the letters `'a'`, `'b'`, and `'c'`.
2. The string does not contain any of the substrings `"aaa"`, `"bbb"`, or `"ccc"`.
3. The string contains at most `a` occurrences of the letter `'a'`.
4. The string contains at most `b` occurrences of the letter `'b'`.
5. The string contains at most `c` occurrences of the letter `'c'`.

If there are multiple longest happy strings, return any of them. If no such string can be generated, return the empty string.

### Input Format
- The input consists of three integers, `a`, `b`, and `c` (representing the counts of `'a'`, `'b'`, and `'c'` respectively).

### Output Format
- Print the longest possible happy string, or return an empty string if it is not possible.

### Example 1
Input:
1 1 7

Output:
ccaccbcc

### Example 2
Input:
7 1 0

Output:
aabaa

### Constraints
- `0 <= a, b, c <= 100`
- `a + b + c > 0`

### Solution

```java
import java.util.PriorityQueue;

public class Main {

    public static String longestDiverseString(int a, int b, int c) {
        // Priority queue to sort based on the number of remaining characters.
        PriorityQueue<int[]> pq = new PriorityQueue<>((g, h) -> h[0] - g[0]);

        // Add the counts of 'a', 'b', 'c' to the queue if they are non-zero.
        if (a != 0) pq.add(new int[]{a, 0});
        if (b != 0) pq.add(new int[]{b, 1});
        if (c != 0) pq.add(new int[]{c, 2});

        StringBuilder result = new StringBuilder();
        int prevChar = -1;

        while (!pq.isEmpty()) {
            int[] first = pq.poll();

            // Check if adding two of the same character is allowed.
            if (result.length() >= 2 && result.charAt(result.length() - 1) == result.charAt(result.length() - 2) && result.charAt(result.length() - 1) == (char) ('a' + first[1])) {
                // If not allowed, we need to use the second most frequent character.
                if (pq.isEmpty()) {
                    break;
                }
                int[] second = pq.poll();
                result.append((char) ('a' + second[1]));
                second[0]--;
                if (second[0] > 0) {
                    pq.add(second);
                }
                pq.add(first); // Put the first one back to be used later.
            } else {
                result.append((char) ('a' + first[1]));
                first[0]--;
                if (first[0] > 0) {
                    pq.add(first);
                }
            }
        }

        return result.toString();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();
        int c = sc.nextInt();

        System.out.println(longestDiverseString(a, b, c));
    }
}