# Nearest Smaller to right :-

# Given an array of integers, find the closest (not considering distance, but value) smaller on rightof every element. If an element has no smaller on the right side, print -1.

Ex. arr = [4, 5, 2, 10, 8]

Output:- ans = [2, 2, -1, 8, -1]

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

// finally reverse vector v

```