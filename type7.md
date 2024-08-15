# Maximum Area of Rectangle in Binary Matrix :-

# Given a binary matrix, find the maximum size rectangle binary-sub-matrix with all 1’s.

Example:

Input :   

          0 1 1 0
          1 1 1 1
          1 1 1 1
          1 1 0 0

Output :  

          1 1 1 1
          1 1 1 1

```cpp

// MAH means maximum area of histogram
vector<int> v;
for(int j = 0; j < m; j++)
{
    v.push_back(arr[0][j]);
}

int mx = MAH(v);

for(int i = 1; i < n; i++)
{
    for(int j = 0; j < m; j++)
    {
        if(arr[i][j] == 0)
        {
            v[j] = 0;
        }
        else
        {
            v[j] = v[j] + arr[i][j];
        }
    }
    mx = max(mx, MAH(v));
}

return mx;

```