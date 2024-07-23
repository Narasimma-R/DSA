### BFS traversal in graph
BFS traversal
### input:
23

4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21

2
### Output:

2 1 4 13 11 9 8 0 
### Code:
``` java
package Problems.Graph;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class BFS {
    ArrayList<Integer> doBSF(ArrayList<ArrayList<Integer>>list,boolean[]visited,int start){
        ArrayList<Integer>bfs=new ArrayList<>();
        Queue<Integer> queue=new LinkedList<>();
        queue.add(start);
        visited[start]=true;
        while(!queue.isEmpty()){
            int node=queue.poll();
            bfs.add(node);
            for(int j : list.get(node)){
                if(!visited[j]){
                    visited[j]=true;
                    queue.add(j);
                }
            }
        }
        return bfs;
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        ArrayList<ArrayList<Integer>> list=new ArrayList<>();
        int num=ip.nextInt();
        int max=0;
        int[]arr=new int[num];
        for(int i=0;i<num;i++){
            arr[i]=ip.nextInt();
            if(max<arr[i]) max=arr[i];
        }
        boolean[]visited=new boolean[max+1];
        int vertex=ip.nextInt();
        for(int i=0;i<=max;i++) list.add(new ArrayList<>());
        for(int i=0;i<vertex;i++){
            int src=ip.nextInt();
            int destination=ip.nextInt();
            list.get(src).add(destination);
            list.get(destination).add(src);
        }
        int start=ip.nextInt();
        System.out.println(list);
        System.out.println(new BFS().doBSF(list,visited,start));
    }
}
```
