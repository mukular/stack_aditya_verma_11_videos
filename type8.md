# Rain Water Trapping :-

# Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

Input: arr[]   = {2, 0, 2}

Output: 2

> Structure is like below

>                    | |
>                    |_|
> We can trap 2 units of water in the middle gap.

Input: arr[]   = {3, 0, 0, 2, 0, 4}

Output: 10

Structure is like below
 >                        |
 >                   |    |
 >                   |  | |
 >                   |__|_| 
> We can trap "3*2 units" of water between 3 an 2, "1 unit" on top of bar 2 and "3 units" between 2 and 4.

```cpp

int mxl[size];
int mxr[size];

mxl = arr[0];

for(int i = 1; i < size; i++)
{
    mxl[i] = max(mxl[i-1], arr[i]);
}

mxr[size-1] = arr[size-1];

for(int i = size-2; i >= 0; i--)
{
    mxr[i] = max(mxr[i+1], arr[i]);
}

int water[size];

for(int i = 0; i < size; i++)
{
    water[i] = min(mxl[i], mxr[i]) - arr[i];
}

int sum = 0;
for(int i = 0; i < size; i++)
{
    sum = sum + water[i];
}

return sum;

```