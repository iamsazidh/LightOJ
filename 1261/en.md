
# LOJ-1261: K-SAT Problem

#### Problem breakdown
In this problem, there are n numbers of people. Now, each person has k wishes. In one wish, they either want us to take a number or to ignore a number. If we grant one of his wishes, he will be happy.

The numbers we are taking are already given to you. You have to just verify if it is possible to make everyone happy with those numbers.

#### How it works?
**input**: First we have to take all the inputs for each testcase (t).
In each test case, there are given 3 numbers (n, m, k) in the first line. n denotes the number of people, after that m (I don't think we need m), and k denotes how many wishes a person has. After that, there are given n lines, and each has exactly k non-zero integers. I am using a 2D array to store it. Here, if an integer is positive, that means the person wants us to take that number, and if it's negative, he wants us to avoid that. After n lines, there is an integer p. After that, we have p integers, which we are taking.

**Let's do it:** After talking about all the inputs, we will use a loop (index-based), which will iterate over each line. After that, we are having another loop (index j-based) for checking if we are granting JTH. As we are granting p numbers, we will use another loop for iterating over each number we are granting.

Now,

- We will use some bool variable for identifying the state. At first we will have a bool for the main result initialized as true.
- In the i-based loop we will have a bool with a default value of true to check if we are granting ith person's atleast one wish. (If we are not granting any of them, then simply we will make it false. And also we will break the loop because the entire result is false as we have to make everyone happy.)
- In the j-based loop we are going to declear two bools. one for checking if we took that the absolute value of that jth number and another for checking if we don't.
- After that, if it seems we took that absolute value, then we will check if that was bigger than 0. If yes, that means we have granted one of his wishes. On the other hand, if we didn't grant, we will check if it was less than 0. If yes, that means we granted that wish.
- If we have granted it, then we can say that this person is happy. And we can go to the next person.
- If it seems that this person is not happy, then we should make the main bool false and break all the loops.
- Print the result based on the main bool.

### C++
-----
```cpp
#include <iostream>
#include <cmath>  //Because of abs() function
using namespace std;

int main(){
    int t;
    cin >> t;
    for(int cs = 1; cs <= t; cs++){
        int n, m, k, p; cin >> n >> m >> k;
        int wishes[n][k];
        bool isPossible = true;
        for(int i = 0; i < n; i++){
            for(int j = 0; j < k; j++){
                cin >> wishes[i][j];
            }
        }
        cin >> p;
        int granted[p];
        for(int a = 0; a < p; a++) cin >> granted[a];
        //Inut Completed for current testcase-------------

        for(int i = 0; i < n; i++){
            bool isSatisfield = false;
            for(int j = 0; j < k; j++){
                bool taken = false;
                bool notTaken = true;
                for(int a = 0; a < p; a++){
                    if(granted[a] == abs(wishes[i][j])){
                        taken = true;
                        notTaken = false;
                    }
                }
                if(wishes[i][j] < 0 && notTaken) isSatisfield = true;
                else if(wishes[i][j] > 0 && taken) isSatisfield = true;

            }
            if(isSatisfield == false){
                isPossible = false;
                break;
            }
        }

        if(isPossible) cout << "Case " << cs << ": Yes" << endl;
        else cout << "Case " << cs << ": No" << endl;
    }
    return 0;
}
```
Happy Coding...


Contributor : [Sazid Hasan]([https://github.com](https://www.linkedin.com/in/iamsazidh/))
