# Stock Span Problem :-

# The stock span problem is a financial problem where we have a series of n daily price quotes for a stock and we need to calculate span of stock’s price for all n days. The span Si of the stock’s price on a given day i is defined as the maximum number of consecutive days just before the given day, for which the price of the stock on the current day is less than or equal to its price on the given day.

## For example, if an array of 7 days prices is given as {100, 80, 60, 70, 60, 75, 85}, then the span values for corresponding 7 days are {1, 1, 1, 2, 1, 4, 6}

```cpp

vector<int> v;
stack<pair<int, int>> s;

for(int i = 0; i < size; i++)
{
    if(s.size() == 0)
    {
        v.push_back(-1);
    }
    else if(s.size() > 0 && s.top().first > arr[i])
    {
        v.push_back(s.top().second);
    }
    else if(s.size() > 0 && s.top().first <= arr[i])
    {
        while(s.size() > 0 && s.top().first <= arr[i])
        {
            s.pop();
        }
        if(s.size() == 0)
        {
            v.push_back(-1);
        }
        else
        {
            v.push_back(s.top().second);
        }
    }

    s.push(arr[i]);
}

for(int i = 0; i < v.size(); i++)
{
    v[i] = i - v[i];
}

return v;

```