### Number of elements to remove to obtain String
String: No. of characters to be removed to convert the given string to “Juspay”
### Input : 
jJusPpay
### Output :
2
### Code : 
``` java
package Problems;

import java.util.Scanner;

public class StringCanForm {
    int canForm(String str,int i,int j){
        String org="jusPay".toLowerCase();
        int count=0;
        if(str.length()<org.length()) return -1;
        while(i<str.length()) {
            if (j < org.length()) {
                if (str.charAt(i) == org.charAt(j)) {
                    i++;
                    j++;
                    count++;
                } else {
                    i++;
                }
            }else break;
        }
        return count==org.length() ? str.length()-count : -1;
    }
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        String str=ip.nextLine().toLowerCase();
        System.out.println(new StringCanForm().canForm(str,0,0));
    }
}
```
