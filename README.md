Minimum number of merge operations required to make an array palindrome in C
Here, in this page we will discuss the program to find Minimum number of merge operations required to make an array palindrome in C programming language. We are given with an array and we need to print an integer value denoting the number of operations required.

Minimum number of merge operations in C
Example :
Input : arr[5] : {15, 4, 6, 15}
Output : 1
Explanation : We need to merge 4 and 6 so, array will become, arr[3] : {15, 10, 15}. Now, the array become palindromic, hence we need to do 1 merging operation to make the given array palindromic.
Method Discussed :
Method 1 : Using Iteration
Method 2 : Using Recursion
Method 1 :
Declare a variable say, count=0, that will count the required merging operation.
Take two variables, i=0, and j=n-1.
Now, run a loop till i<j, inside loop check if (arr[i]==arr[j]), then increase the value of i by 1 and decrease the value of j by 1.
Else if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and decrease the value of j and increase the value of count by 1.
Else set, arr[i+1] = arr[i]+arr[i+1] and increase the value of i and count by 1.
After the traversal print the value of count.
Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Method 1 : Code in C
Run
#include<stdio.h> 

int main(){

   int arr[] = {1, 4, 5, 9, 1};
   int n = sizeof(arr)/sizeof(arr[0]), count = 0;

   int i = 0, j = n-1;

   while(iarr[j])
       {
            arr[j-1] = arr[j]+arr[j-1];
            j--;
            count++;
        }
     else{
       arr[i+1] = arr[i]+arr[i+1];
       i++;
       count++;
     }
   }

   printf("Required Minimum Operations : %d", count);
}
Output :
Required Minimum Operations : 1
Related Pages
Given an array which consists of only 0, 1 and 2

Find the “Kth” max and min element of an array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2 (Using Recursion) :
Create a recursive function say, fun() pass arr and two values 0 and n-1.
In the fun(), return 0, if(i==j or i>j)
Otherwise, check if (arr[i]==arr[j]), then return(1+fun(arr, i+1, j-1))
Else check if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and return(1+fun(arr, i, j-1))
Else set, arr[i+1] = arr[i]+arr[i+1] and return(1+fun(arr, i+1, j)).
Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Method 2 : Code in C
Run
#include<stdio.h>

int fun(int arr[], int i, int j){

      if( i==j || i>j )
         return 0;

     if(arr[i]==arr[j])
         return fun(arr, i+1, j-1);

     else if(arr[i]>arr[j]){
          arr[j-1] = arr[j]+arr[j-1];
          return (1+fun( arr, i, j-1));
     }
     else{
          arr[i+1] = arr[i]+arr[i+1];
          return (1+fun( arr, i+1, j)); 
     }

}

int main(){

   int arr[] = {1, 4, 5, 9, 1};
   int n = sizeof(arr)/sizeof(arr[0]);

   printf("Required Minimum Operations : %d", fun(arr, 0, n-1));
}
Output :
Required Minimum Operations : 1
