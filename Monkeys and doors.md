### Monkey and Doors
There are 100 doors in a row, all doors are initially closed. A person walks through all doors multiple times and toggle (if open then close, if close then open) them in the following way: 

In the first walk, the person toggles every door 

In the second walk, the person toggles every second door, i.e., 2nd, 4th, 6th, 8th, … 

In the third walk, the person toggles every third door, i.e. 3rd, 6th, 9th, … 

Likewise,

In the 100th walk, the person toggles the 100th door.
### Input:
100
### output:
10
### Code:
``` java
package Problems;

public class MonkeysAndDoors {

    public static void main(String[] args) {
        boolean[]door=new boolean[25];
        for(int i=1;i<=door.length;i++)
            for(int j=0;j<door.length;j++)
                if((j+1)%i==0) door[j]=!door[j];
        int count=0;
        for(boolean b: door) if(b) count++;
        System.out.println(count);
    }
}
```
