# Implementing a Min Stack :-

# Design a Data Structure SpecialStack that supports all the stack operations like push(), pop(), isEmpty(), isFull() and an additional operation getMin() which should return minimum element from the SpecialStack. All these operations of SpecialStack must be O(1). To implement SpecialStack, you should only use standard Stack data structure and no other data structure like arrays, list, .. etc.

```cpp

stack<int> s;
stack<int> ss;

void push(int a)
{
    s.push(a);
    if(s.size() == 0 || ss.top() >= a)
    {
        ss.push(a);
        return ;
    }
}

int pop()
{
    if(s.size() == 0)
    {
        return -1;
    }

    int ans = s.top();
    s.pop();
    if(ss.top() == ans)
    {
        ss.pop();
    }

    return ans;
}

int getmin()
{
    if(ss.size() == 0)
    {
        return -1;
    }
    return ss.top();
}

```