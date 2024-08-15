# Nearest Greater to right :-

# Given an array, print the Next Greater Element (NGE) for every element. The Next greater Element for an element x is the first greater element on the right side of x in array. Elements for which no greater element exist, consider next greater element as -1.

Ex. arr = [1, 3, 0, 0, 1, 2, 4]

Output:- ans = [3, 4, 1, 1, 2, 4, -1]
---

```cpp
vector<int> v;
stack<int> s;

for(int i = size-1; i >= 0; i--)
{
    if(s.size() == 0)
    {
        v.push_back(-1);
    }
    else if(s.size() > 0 && s.top() > arr[i])
    {
        v.push_back(s.top());
    }
    else if(s.size() > 0 && s.top() <= arr[i])
    {
        while(s.size() > 0 && s.top() <= arr[i])
        {
            s.pop();
        }
        if(s.size() == 0)
        {
            v.push_back(-1);
        }
        else
        {
            v.push_back(s.top());
        }
    }

    s.push(arr[i]);
}

// finally v ko reverse kar dena

```