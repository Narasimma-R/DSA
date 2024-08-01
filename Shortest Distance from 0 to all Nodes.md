### Shortest Path in Directed Acyclic Graph
Given a DAG, find the shortest path from the source to all other nodes in this DAG. In this problem statement, we have assumed the source vertex to be ‘0’. You will be given the weighted edges of the graph.

### Note: What is a DAG ( Directed Acyclic Graph)?

A Directed Graph (containing one-sided edges) having no cycles is said to be a Directed Acyclic Graph.

### Examples:

### Example 1:
### Input:
n = 6, m= 7
edges =[[0,1,2],[0,4,1],[4,5,4],[4,2,2],[1,2,3],[2,3,6],[5,3,1]]
### Output: 
0 2 3 6 1 5
###  Explanation:  
The above output list shows the shortest path 
to all the nodes from the source vertex (0), 

### Input:
n = 7, m= 8
Edges =[[0,4,2],[0,5,3],[5,4,1],[4,6,3],[4,2,1],[6,1,2],[2,3,3],[1,3,1]]
### Output: 
0 7 3 6 2 3 5
### Code:
``` java
package Problems.Graph.Weighted;

import java.util.ArrayList;
import java.util.Scanner;

public class Weight {
    static int min=Integer.MAX_VALUE;
    public int findPath(int i,int end,int weight,ArrayList<Integer>path,ArrayList<ArrayList<Pair>>list){
        if(i==end){
            min=Math.min(weight,min);
            path.add(i);
            return weight;
        }
        if(path.contains(i)){
            return weight;
        }
        path.add(i);
        for(Pair j:list.get(i)){
            weight=findPath(j.getEnd(),end,weight+j.getWeight(),path,list);
            if(!path.isEmpty()) path.remove(path.size()-1);
            weight-=j.getWeight();
        }
        return weight;
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int vertex=ip.nextInt();
        ArrayList<ArrayList<Pair>>list=new ArrayList<>();
        int edges=ip.nextInt();
        for(int i=0;i<vertex;i++) list.add(new ArrayList<>());
        for(int i=0;i<edges;i++){
            int start=ip.nextInt();
            int end=ip.nextInt();
            int weight=ip.nextInt();
            list.get(start).add(new Pair(end,weight));
        }
        ArrayList<Integer>path=new ArrayList<>();
        int start=ip.nextInt();
        int end=ip.nextInt();
        new Weight().findPath(start, end, 0, path, list);
        System.out.println(min);
        for(int i=0;i<vertex;i++) {
            min=Integer.MAX_VALUE;
            path.clear();
            new Weight().findPath(start, i, 0, path, list);
            System.out.println("Minimum Distance form "+start+" to "+i+" : "+(min==Integer.MAX_VALUE ? -1 : min));
        }
    }
}
```
### Pair Class :
``` java
package Problems.Graph.Weighted;

public class Pair {
    private final int end;
    private final int weight;
    Pair(int end,int weight){
        this.end=end;
        this.weight=weight;
    }
    public int getEnd(){
        return end;
    }
    public int getWeight(){
        return weight;
    }
}
```
