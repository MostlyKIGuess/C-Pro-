```c
void insertionSort(int arr[], int n){
    int i, key, j;
    for (i = 1; i < n; i++) {
        key = arr[i];
	        j = i - 1;
		      while (j >= 0 && arr[j] > key) {
	            arr[j + 1] = arr[j];
					j--;
              }
            arr[j + 1] = key;
    }
}
```
- The philosophy is if you want to insert an element into a sorted array and that's exactly how we insert that particular element into the "sorted" array.

- This works because we take the index j as i-1 and use it to swap "up to" key is smaller than the j.  We then put the key on it's place where initially i-1 was.
**Step 1** − If it is the first element, it is already sorted. return 1;
**Step 2** − Pick next element
**Step 3** − Compare with all elements in the sorted sub-list
**Step 4** − Shift all the elements in the sorted sub-list that is greater than the 
                value to be sorted
**Step 5** − Insert the value
**Step 6** − Repeat until list is sorted