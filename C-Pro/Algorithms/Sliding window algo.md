- Basically using a singular loop rather than using 2 loops by storing a sum or something.
- We can also iterate it from **right rather than left ,** for eg. in the question to find leader(here leader is defined as an element who is larger than all other elements on the right of it).
```c
#include <stdio.h>



int  main(){

  

  int arr[5]={4,2,10,1,3};

  int sumtf = 14; //sumtf= sum to be found

  int sum = 0;

  int flag = 0;

  int start = 0;

  for(int i=0;i<5;i++){

      sum+=arr[i];

      while(sum>sumtf && start<i){

        sum = sum - arr[start];

        start++;

      }

      if(sum==sumtf){

            flag=1;

            printf("%d %d\n",start,i);

            break;

      }

  }

  if(flag==0){

    printf("didn't find sum, cry ABOUT IT!");

  }

  

  return 0;

}
```

[[Two Pointers Approach]]
