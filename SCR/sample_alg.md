## Example script problem

### Problem name
Sam and candies

### Problem Statement
Sam loves candies. He is in candyland. He found n bags of candies there. The bags are labelled from 1 to n.He can bring home only 2 bags of candies from there. What is the maximum number of candies which he can take home?

### Input format
The 1st line will contain **n**, the number of bags.  
The second line will contain **n** space separated integers **a<sub>i</sub>**, which are the number of candies in i<sup>th</sup> bag.

### Output format
A single line containing the maximum number of candies

### Limits
1 <= n <= 10<sup>5</sup>  
0 <= a<sub>i</sub> <= 10<sup>5</sup>

### Sample test cases

### Input
```
2
4 5
```
### Output
```
9
```
### Explanation
Only 2 bags are there, so we will take those bags.  

### Input
```
5
1 2 2 4 3
```
### Output
```
4 5
```
### Explanation
Bag 4 and bag 3

### Tags
Easy, Sorting

### Editorial
You can find the maximum number of candies by finding the two bags which have the maximum candies

### Solution

``` cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    int n;
    vector <int> bag;

    cin >> n;

    bag.resize(n);

    for (int i=0; i<n; i++)
    {
        cin >> bag[i];
    }

    if (n == 1)
    {
        cout << bag[0];
    }
    else if (n == 2)
    {
        cout << bag[0]+bag[1];
    }
    else
    {
        // sort in decreasing order
        sort(bag.rbegin(), bag.rend());
        cout << bag[0]+bag[1];
    }
}
```
