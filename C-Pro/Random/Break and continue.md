#Cpro 
if(){
break;
}
we use **break** to exit out of a loop.

We use **continue** to skip the iteration, it skips to the next iteration of the loop and doesn't let the code under it run.

for(int i=0;i<4;i++){

if(i == 2){
continue;
}

printf("%d",i);

}

here output will be
0 1 3



