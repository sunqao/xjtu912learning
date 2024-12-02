
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


```cpp
int q[n];
int s[n];
int w[n];

void radix_sort(int d, int r){
	int radix = 1;
	for(int i = 1; i <= d; i ++){
		for(int j = 0; j < r; j ++) s[j] = 0;
		for(int j = 0; j < n; j ++) s[q[j] / radix % r] ++;
		for(int j = 1; j < r; j ++) s[j] += s[j - 1];
		for(int j = n - 1; j >= 0; j --){
			int index = s[q[j] / radix % r] - 1;
			w[index] = q[j];
			s[q[j] / radix % r] --;
		}
		for(int j = 0; j < n; j ++) q[j] = w[j];
		
		radix *= r;
	}
}
```

```cpp
int q[n];
int sz = n;

void down(int u){
	int t = u;
	if(u * 2 <= sz && q[u * 2] > q[t]) t = u * 2;
	if(u * 2 + 1 <= sz && q[u * 2 + 1] > q[t]) t = u * 2 + 1;
	
	if(u != t){
		swap(q[u], q[t]);
		down(t);
	}
}

void heap_sort(){
	for(int i = n / 2; i >= 1; i --) down(i);
	
	for(int i = 1; i <= n; i ++){
		swap(q[1], q[sz]);
		sz --;
		down(1);
	}
}
```

```cpp
void quick_sort(int q[], int l, int r){
	
	if(l >= r) return;
	
	int i = l - 1, j = r + 1, x = q[l + r >> 1];
	
	while(i < j){
		do i ++; while(q[i] < x);
		do j ++; while(q[j] > x);
		swap(q[i], q[j]);
	}
	
	quick_sort(q, l, j);
	quick_sort(1, j + 1, r);
}
```

```cpp
void shell_sort(){
	for(int d = n / 2; d; d /= 2){
		for(int start = 0; start < d; start ++){
			for(int i = start + 1; i < n; i += d){
				int t = q[i];
				int j = i;
				while(j > start && q[j] > t){
					q[j] = q[j - d];
					j -= d;
				}
				
				q[j] = t;
			}
		}
	}
}
```

```cpp
int q[n];
void insert_sort(){
	for(int i = 1; i < n ; i ++){
		int t = q[i];
		int j = i;
		while(j > 0 && q[j] > t){
			q[j - 1] = q[j];
			j --;
		}
		q[j] = t;
	}
}
```

```cpp
bool check(){

}

void bsearch(int l, int r, int t){
	while(l < r){
		int mid = l + r >> 1;
		if(check(mid)) r = mid;
		else l = mid + 1;
	}
	
	return l;
}
```

```cpp
bool check(){}

void bsearch(int l, int r, int t){
	while(l < r){
		int mid = l + r + 1 >> 1;
		if(check(mid)) l = mid;
		else r = mid - 1;
	}
	
	return l;
}
```

```cpp
int q[n];
void binsert_sort(){
	for(int i = 1; i < n; i ++){
		if(q[i - 1] <= q[j]) continue;
		int t = q[i];
		//int j = i;
		
		int l = 0, r = i - 1;
		while(l < r){
			int mid = l + r >> 1;
			if(q[mid] > t) r = mid;
			else l = mid + 1;
		}
		
		for(int j = i; j > l; j --){
			q[j] = q[j - 1];
		}
		q[l] = t;
	}
}
```

```cpp
void bubble_sort(){
	for(int i = 0; i <= n - 1; i ++){
		bool is_swap = false;
		
		for(int j = n - 1; j > i; j --){
			if(q[j-1] > q[j]){
				swap(q[j - 1], q[j]);
				is_swap = true;
			}
		}
		
		if(!is_swap) break;
	}
}
```

```cpp
void select_sort(){
	for(int i = 0; i < n - 1; i ++){
		int k = i;
		
		for(int j = i + 1; j <= n - 1; j ++){
			if(q[j] < q[k]) k = j;
		}
		
		swap(q[i], q[k]);
	}
}
```


```cpp
void insert_sort(){
	for(int i = 1; i < n; i ++){
		int t = q[i];
		int j = i;
		while(j > 0 && q[j - 1] > q[j]){
			q[j] = q[j - 1];
			j --;
		}
		
		q[j] = t;
	}
}

void binsert_sort(){
	for(int i = 1; i < n; i ++){
		if(q[i - 1] <= q[i]) continue;
		
		int t = q[i];
		
		int l = 0, j = i - 1;
		while(l < j){
			int mid = l + r >> 1;
			if(q[mid] > t) r = mid;
			else l = mid + 1;
		}
		for(int j = i; j > l; j --){
			q[j] = q[j - 1];
		}
		q[l] = t;
	}
}

void bubble_sort(){
	for(int i = 0; i < n - 1; i ++){
		bool is_swap = false;
		
		for(int j = n - 1; j > i; j --){
			if(q[j - 1] > q[j]){
				swap(q[j - 1], q[j]);
				is_swap = true;
			}
			
		}
		
		if(!is_swap) break;
	}
}

void select_sort(){
	for(int i = 0; i < n - 1; i ++){
		int k = i;
		for(int j = i + 1; j < n; j ++){
			if(q[j] < q[k]) k = j;
		}
		swap(q[i], q[j]);
	}
}
```

```cpp
void shell_sort(){
	for(int d = n / 2; d; d /= 2){
		for(int start = 0; start < d; start ++){
			for(int i = start + d; i < n; i += d){
				int t = q[i];
				int j = i;
				while(j > start && q[j - d] > t){
					q[j] = q[j - d];
					j -= d;
				}
				q[j] = t;
			}
		}
	}
}
```