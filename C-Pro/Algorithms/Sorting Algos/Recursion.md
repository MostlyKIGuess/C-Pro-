```c
int fibo(int a){
	if(a==0)return 0;
	else if(a==1)return 1;
		else{
			int b = fibo(a-1);
			int c = fibo(a-2);
			return b+c;
	}
}
```

- Recursion is used for creating algorithms and works with $2^n$ complexity.
- They have a very small codes.

![[recursion.excalidraw]]

[[Backtracking]] is useful via recursion.

[[Closed Permutation using String]]

