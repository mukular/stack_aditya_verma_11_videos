# Nearest Smaller to left :-

# Given an array of integers, find the closest (not considering distance, but value) smaller on left of every element. If an element has no smaller on the left side, print -1 . 

Ex. arr = [4, 5, 2, 10, 8]

Output:- ans = [-1, 4, -1, 2, 2]
---

```cpp

vector<int> v;
stack<int> s;

for(int i = 0; i < size; i++)
{
    if(s.size() == 0)
    {
        v.push_back(-1);
    }
    else if(s.size() > 0 && s.top() < arr[i])
    {
        v.push_back(s.top());
    }
    else if(s.size() > 0 && s.top() >= arr[i])
    {
        while(s.size() > 0 && s.top() >= arr[i])
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

```