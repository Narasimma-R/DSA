### Nearest Meeting Cell
### Problem Description :
You are given a maze with N cells. Each cell may have multiple entry points but not more than one
exit (i.e. entry/exit points are unidirectional doors like valves). The cells are named with an integer
from 0 to N-1.
You have to find :
Nearest meeting cell : Given any two cells - C1, C2, find the closest cell Cm that can be reached
from both C1 and C2.
### INPUT FORMAT :
1. The first line contains the number of cells N.
2. The second line has a list of N values of the edge[ ] array, where edge[i] conatins the cell
number that can be reached from cell 'i' in one step. edge[i] is -1 if the ith doesn't have an
exit.
3. Third line for each testcase contains two cell numbers whose nearest meeting cell needs to
be found. (return -1 if there is no meeting cell from two given cells)
### OUTPUT FORMAT :
Output a single line that denotes the nearest meeting cell (NMC).
### Sample Input :
23

4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21

9 2
### Sample Output :
4
### Code :
``` java
package Problems.Graph;

import java.util.Scanner;
import java.util.ArrayList;

public class NearestMeetingPoint {
    public ArrayList<Integer> findMeetingPoint(ArrayList<Integer>list,int[]nodes,int i,int target){
        if(i==nodes.length) return null;
        if(i==-1) return null;
        if(list.contains(nodes[i])){
            list.add(nodes[i]);
            return null;
        }
        if(nodes[i]==target){
            list.add(nodes[i]);
            return list;
        }
        list.add(nodes[i]);
        if(list.get(0).equals(list.get(list.size()-1))) return null;
        return findMeetingPoint(list,nodes,nodes[i],target);
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int num=ip.nextInt();
        int[]nodes=new int[num];
        for(int i=0;i<num;i++) nodes[i]=ip.nextInt();
        int start1=ip.nextInt();
        int start2=ip.nextInt();
        ArrayList<Integer> list1=new ArrayList<>();
        ArrayList<Integer> list2=new ArrayList<>();
        list1.add(start1);
        new NearestMeetingPoint().findMeetingPoint(list1,nodes,start1,start2);
        list2.add(start2);
        new NearestMeetingPoint().findMeetingPoint(list2,nodes,start2,start1);
        System.out.println(list1);
        System.out.println(list2);
        for (Integer integer : list1)
            if (list2.contains(integer)) {
                System.out.println(integer);
                break;
            }
    }
}

```
