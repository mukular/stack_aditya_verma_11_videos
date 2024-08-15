# Min stack Implementation in O(1) space

# Design a Data Structure SpecialStack that supports all the stack operations like push(), pop(), isEmpty(), isFull() and an additional operation getMin() which should return minimum element from the SpecialStack. All these operations of SpecialStack must be O(1). To implement SpecialStack, you should only use standard Stack data structure and no other data structure like arrays, list, .. etc.

```cpp

int minEle;

int getmin()
{
    if(s.size() == 0)
    {
        return -1;
    }
    return minEle;
}

void push(int x)
{
    if(s.size() == 0)
    {
        s.push(x);
        minEle = x;
    }
    else
    {
        if(x >= minEle)
        {
            s.push(x);
        }
        else if(x < minEle)
        {
            s.push(2*x - minEle);
            minEle = x;
        }
    }
}

void pop()
{
    if(s.size() == 0)
    {
        return -1;
    }
    else
    {
        if(s.top() >= minEle)
        {
            s.pop();
        }
        else if(s.top() < minEle)
        {
            minEle = 2*minEle - s.top();
            s.pop();
        }
    }
}

int top()
{
    if(s.size() == 0)
    {
        return -1;
    }
    else 
    {
        if(s.top() >= minEle)
        {
            return s.top();
        }
        else if(s.top() < minEle)
        {
            return minEle;
        }
    }
}

```