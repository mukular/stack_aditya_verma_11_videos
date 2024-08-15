# Maximum area of histogram :-

# Find the largest rectangular area possible in a given histogram where the largest rectangle can be made of a number of contiguous bars. For simplicity, assume that all bars have same width and the width is 1 unit.

```cpp

// code of nsl(next smaller to left)

vector<int> left;
stack<pair<int, int>> s;
int pseudoindex = -1;

for(int i = 0; i < size; i++)
{
    if(s.size() == 0)
    {
        left.push_back(pseudoindex);
    }
    else if(s.size() > 0 && s.top().first < arr[i])
    {
        left.push_back(s.top().second);
    }
    else if(s.size() > 0 && s.top().first >= arr[i])
    {
        while(s.size() > 0 && s.top().first >= arr[i])
        {
            s.pop();
        }
        if(s.size() == 0)
        {
            left.push_back(-1);
        }
        else
        {
            left.push_back(s.top().second);
        }
    }

    s.push(arr[i]);
}

// code of nsr(next smaller to right)

vector<int> right;
stack<pair<int, int>> s2;
int pseudoindex2 = size;

for(int i = size-1; i >= 0; i--)
{
    if(s2.size() == 0)
    {
        right.push_back(pseudoindex2);
    }
    else if(s2.size() > 0 && s2.top().first < arr[i])
    {
        right.push_back(s2.top().second);
    }
    else if(s2.size() > 0 && s2.top().first >= arr[i])
    {
        while(s2.size() > 0 && s2.top().first >= arr[i])
        {
            s2.pop();
        }
        if(s2.size() == 0)
        {
            right.push_back(pseudoindex2);
        }
        else
        {
            right.push_back(s2.top().second);
        }
    }

    s2.push(arr[i]);
}

// reverse right vector

// make a width array
for(int i = 0; i < size; i++)
{
    width[i] = right[i] - left[i] - 1;
}

// make an area array
for(int i = 0; i < size; i++)
{
    area[i] = arr[i] * width[i];
}

// ans is maximum in area array

```