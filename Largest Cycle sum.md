### Largest Cycle sum
Given a maze with N cells. Each cell may have multiple entry points but not more than one exit(i.e entry/exit points are unidirectional doors like valves).
You are given an array Edge[] of N integers, where Edge[i] contains the cell number that can be reached from of cell i in one step. Edge[i] is -1 if the ith cell doesn't have an exit. 
The task is to find the largest sum of a cycle in the maze(Sum of a cycle is the sum of the cell indexes of all cells present in that cycle).

Note:The cells are named with an integer value from 0 to N-1. If there is no cycle in the graph then return -1.

### Input:
N = 4
Edge[] = {1, 2, 0, -1}
### Output: 
3
### Explanation: 
There is only one cycle in the graph.
(i.e 0->1->2->0)
Sum of the cell index in that cycle 
= 0 + 1 + 2 = 3.
### Code :
``` java
package Problems.Graph;

import java.util.Scanner;
import java.util.ArrayList;
public class LargestCycleSum {
    int findMax(int i,int[]nodes,ArrayList<Integer>list,int sum){
        if(i==nodes.length) return sum;
        if(i==-1) return sum;
        if(list.contains(nodes[i])){
            list.add(nodes[i]);
            sum+=nodes[i];
            return sum;
        }
        list.add(nodes[i]);
        if(list.get(0).equals(list.get(list.size()-1))) return sum;
        return findMax(nodes[i],nodes,list,sum+nodes[i]);
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int num=ip.nextInt();
        int[]nodes=new int[num];
        int max=-1;
        for(int i=0;i<num;i++) nodes[i]=ip.nextInt();
        for(int i=0;i<num;i++){
            ArrayList<Integer>list=new ArrayList<>();
            list.add(i);
            int temp=0;
            temp=new LargestCycleSum().findMax(i,nodes,list,temp);
            System.out.println(list);
            System.out.println("Sum : "+temp);
            if(list.get(0).equals(list.get(list.size()-1)))
                if(max<temp) max=temp;
        }
        System.out.println("Max : "+max);
    }
}
```
