# Nearest Greater to left :-

# Given an array of integers, find the closest (not considering distance, but value) greater on left of every element. If an element has no greater on the left side, print -1 . 

Ex. arr = [1, 3, 2, 4]

Output:- ans = [-1, -1, 3, -1]
---

```cpp

// Pichle wali problem ki tarah hi h but yeh changes h keval:-

// 1. yaha left se traverse karna h
// 2. No need to reverse vector

vector<int> v;
stack<int> s;

for(int i = 0; i < size; i++)
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


```