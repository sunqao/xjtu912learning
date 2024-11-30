
![](https://typora-1310242472.cos.ap-nanjing.myqcloud.com/typora_img/image-20241130134514624.png)

sdf 
1. sfas
2. 2faf
	1. sf sa f
	2. saf 
		1. sf asf 
			1. asfd a

```cpp
void merge_sort(int l, int r){
	if(l >= r) return;
	int mid = l + r >> 1;
	merge_sort(l, mid);
	merge_sort(mid + 1, r);
	int i = l;
	int j = mid + 1;
	while(i <= mid && j <= r){
		if(q[i] <= q[j]) w[k ++] = q[i ++];
		else w[k ++] = q[j ++];
		
	}
	while(i <= mid) w[k ++] = q[i ++];
	while(j <= r) w[k ++] = q[j ++];
	for(int i = l, j = 0; j < k; j ++, i ++) q[i] = w[j];
}
```