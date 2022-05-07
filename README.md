# Median-of-two-sorted-array
Median of two sorted array without using extra space

import java.io.*;
import java.util.*;

class Main{
    public static void main(String[] args){
        int arr1[] = {1,3,5};
        int arr2[] = {2,4,6};
       double median =  Median(arr1 , arr2);
        System.out.print(median);
        
    }
    public static double Median(int arr1[], int arr2[]){
        int m = arr1.length;
        int n = arr2.length;
        
        if (m>n){
            return Median(arr2, arr1);
        }
        int s1 = 0;
        int e1 = m;
        
        while (s1<=e1){
            int mid1 = (s1+e1)/2;
            int mid2 = (m+n+1)/2 - mid1;
            
            int LeftMax1 = (mid1 == 0) ? Integer.MIN_VALUE : arr1[mid1-1];
            int RightMin1 = (mid1 == m) ? Integer.MAX_VALUE : arr1[mid1];
            int LeftMax2 = (mid2 == 0) ? Integer.MIN_VALUE : arr2[mid2-1];
            int RightMin2 = (mid2 == n) ? Integer.MAX_VALUE : arr2[mid2];
            
            if (LeftMax1 <= RightMin2 && LeftMax2 <= RightMin1){
                if ((m+n)%2 == 0){
                    int LeftMax = Math.max(LeftMax1 , LeftMax2);
                    int RightMin = Math.min(RightMin1, RightMin2);
                    
                    return (double)(LeftMax+RightMin)/2;
                }
                else {
                    int LeftMax = Math.max(LeftMax1 , LeftMax2);
                    return (double)LeftMax;
                }
            }
            else if (LeftMax1 > RightMin2)
                    e1 = mid1-1;
            else 
                s1 = mid1+1;
        }
        return 0;
    }
}
