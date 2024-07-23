### Reachability
React Developer Community is a community of React developers. It allows developers to reach
out to others and discuss various topics around JS programming. This community has been
modelled as a directed social network graph.
Find Reachability
JS newbie A wants to check if he can reach out to a React expert B using his network.
### Input Format :
total members in React Developer Community
memberId1
MemberId2..........................MemberIdN
Total possible edges
.............................
Follower
Following
### Output Format :
"0" OR "1"
### Sample Testcase :
4
2
5
7
9
4
2 9
7 2
7 9
9 5
### Start and end :
7 5
### Testcase Output :
1
### Code :
``` java
package Problems.Graph;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;
public class Reachability {
private boolean found;
    void findReachabilityDFS(ArrayList<ArrayList<Integer>>list,ArrayList<Integer>path,boolean[]visited,int start,int end){
        path.add(start);
        visited[start]=true;
        if(start==end){
            found=true;
            return;
        }
        for(int i : list.get(start))
            if(!visited[i] && !found) findReachabilityDFS(list,path,visited,i,end);
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
            list.get(src).add(ip.nextInt());
        }
        int start=ip.nextInt();
        int end=ip.nextInt();
        System.out.println(list);
        ArrayList<Integer>path=new ArrayList<>();
        new Reachability().findReachabilityDFS(list,path,visited,start,end);
        System.out.println(path);
        System.out.println(path.get(path.size()-1)==end ? 1 : 0);
    }
}
```
