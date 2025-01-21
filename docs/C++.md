---
title: "C++"
---

# C++
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## `include <vector>`

### 初始化

```cpp
vector<bool> visited;
visited.resize(n, false);
```

### 二维初始化

```cpp
vector<vector<int>> vec2 = vector<vector<int>>(line_num, vector<int>(row_num)) = {
    {0,0,0,0}, {1,2,3,4}
};
```

### 二维数组转 vector

```cpp
// 定义二维数组
int array_size = 1000;
double **array = (double **)malloc(sizeof(double *) * array_size);
for (int i = 0; i < array_size; i++)
    array[i] = (double *)malloc(sizeof(double) * array_size);

for (int i = 0; i < array_size; i++)
    for (int j = 0; j < array_size; j++)
        array[i][j] = i * array_size + j;

// 转vector
vector<vector<double>> t(array_size, vector<double>(array_size));
for (int i = 0; i < array_size; i++)
{
	// 方法1：直接定义一个一维的vector，其首地址为数组的起始地址，末尾地址为最后的地址。
	t[i] = vector<double>(array[i], array[i] + array_size);
    // 方法2：直接使用memcpy进行复制
    // memcpy(&ttt[i][0], &array[i][0], array_size * sizeof(double));
}
```
