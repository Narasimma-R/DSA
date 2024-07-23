### Recursive Binary Search
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

### Example 1:

### Input:
nums = [-1,0,3,5,9,12], target = 9
### Output: 4
### Explanation: 
9 exists in nums and its index is 4
### Example 2:
### Input: 
nums = [-1,0,3,5,9,12], target = 2
### Output:
-1
### Explanation:
2 does not exist in nums so return -1
### Recursive Binary Search Code:
``` java
import java.util.Scanner;

public class BinarySearch {
    private int ans=-1;
    int recursiveBinarySearch(int[]arr,int target,int low,int high) {
        if (low > high) return -1;
        int mid = (low + high) / 2;
        if (arr[mid] == target){
            this.ans = mid;
            return ans;
        }
        if(arr[mid]<target) recursiveBinarySearch(arr,target,mid+1,high);
        if(arr[mid]>target) recursiveBinarySearch(arr,target,low,mid-1);
        return ans;
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int num=ip.nextInt();
        int[]arr=new int[num];
        for(int i=0;i<num;i++) arr[i]=ip.nextInt();
        int target=ip.nextInt();
        System.out.println(new BinarySearch().recursiveBinarySearch(arr,target,0,arr.length-1));
    }
}
```
