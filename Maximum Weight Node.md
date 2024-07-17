### Maximum Weight Node
Problem Description : You are given a maze with N cells. Each cell may have multiple entry points
but not more than one exit (i.e. entry/exit points are unidirectional doors like valves).
The cells are named with an integer from 0 to N-1.
You have to find : Find the node number of maximum weight node (Weight of a node is the sum of all
nodes pointing to that node).
INPUT FORMAT :
1. The first line contains the number of cells N.
2. The second line has a list of N values of the edge[ ] array, where edge[i] conatins the cell
number that can be reached from cell 'i' in one step. edge[i] is -1 if the ith doesn't have ans
exit.
OUTPUT FORMAT :
1. First line denotes the node number with maximum weight node.
Sample Input :
23
4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21
Sample Output :
22
### Code :
``` java
package Problems.Graph;

import java.util.Arrays;
import java.util.Scanner;

public class MaximumNodeWeight {
    public static void main(String[] args) {
        Scanner ip = new Scanner(System.in);
        int num = ip.nextInt();
        int[] nodes = new int[num];
        int[] sum = new int[num];
        for (int i = 0; i < num; i++) nodes[i] = ip.nextInt();
        for (int i = 0; i < num; i++) {
            if(nodes[i]!=-1) sum[nodes[i]] += i;
            System.out.println("sum " + Arrays.toString(sum));
        }
        System.out.println();
    }
}

```
