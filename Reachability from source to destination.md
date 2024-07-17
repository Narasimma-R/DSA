### Find Reach-ability
This problem asks you to check for a given graph if a destination node is
reachable from a given Source node .
### Sample Input:
23

4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21

2 5

### Output:

true
### Code:
``` java
package Problems.Graph;

import java.util.ArrayList;
import java.util.Scanner;

public class Reachability {
    boolean canReach (int[]nodes,int source,int target){
        ArrayList<Integer>list=new ArrayList<>();
        list.add(source);
        getPath(source,target,nodes,list);
        System.out.println(list);
        return list.get(list.size()-1)==target;
    }
    void getPath(int source, int target, int[]nodes, ArrayList<Integer>list){
        if(source==nodes.length) return;
        if(source==-1) return;
        if(list.contains(nodes[source])) return;
        if(source == target) return;
        list.add(nodes[source]);
        if(list.get(0).equals(list.get(list.size()-1))) return;
        getPath(nodes[source],target,nodes,list);
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int num=ip.nextInt();
        int[]nodes=new int[num];
        for(int i=0;i<num;i++) nodes[i]=ip.nextInt();
        int source=ip.nextInt();
        int target=ip.nextInt();
        System.out.println(new Reachability().canReach(nodes,source,target));
    }
}
```
