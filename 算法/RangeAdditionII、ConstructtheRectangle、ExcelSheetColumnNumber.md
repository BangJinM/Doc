###RangeAdditionII、ConstructtheRectangle、ExcelSheetColumnNumber
####ExcelSheetColumnNumber
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28
```language
 	/*
     * 171. Excel Sheet Column Number
     */


    int titleToNumber(string s) {
        int maxSize=s.size();
        int result=0;
        for(auto ite=s.begin();ite!=s.end();++ite)
        {
            float p=maxSize-(ite-s.begin()+1);
            double num=pow(26,p);
            int temp=*ite-'A'+1;
            result+=temp*num;
        }
        cout<<result;

        int pow=1;
        result=0;
        for(int i=1;i<=s.size();++i)
        {
            int temp=*(s.end()-i)-'A'+1;
            result+=temp*pow;
            pow*=26;
        }

        cout<<result;

        return result;
    }
```

####Construct the Rectangle
For a web developer, it is very important to know how to design a web page's size. So, given a specific rectangular web page’s area, your job by now is to design a rectangular web page, whose length L and width W satisfy the following requirements:

1. The area of the rectangular web page you designed must equal to the given target area.

2. The width W should not be larger than the length L, which means L >= W.

3. The difference between length L and width W should be as small as possible.
You need to output the length L and the width W of the web page you designed in sequence.
Example:
Input: 4
Output: [2, 2]
Explanation: The target area is 4, and all the possible ways to construct it are [1,4], [2,2], [4,1]. 
But according to requirement 2, [1,4] is illegal; according to requirement 3,  [4,1] is not optimal compared to [2,2]. So the length L is 2, and the width W is 2.
Note:
The given area won't exceed 10,000,000 and is a positive integer
The web page's width and length you designed must be positive integers.
```language
	/*
     * 492. Construct the Rectangle
     */
    vector<int> constructRectangle(int area) {

        int length=0;
        int width=0;

        int temp=sqrtf(area);
        for(int i=temp;i>0;--i)
        {
            if(area%i==0)
            {
                length=area/i;
                width=i;
                break;
            }
        }
        vector<int> result{};
        result.push_back(length);
        result.push_back(width);

        for (auto item=result.begin(); item !=result.end() ; ++item) {
            cout<<*item<<ends;
        }
        return result;
    }
```

####RangeAdditionII
Given an m * n matrix M initialized with all 0's and several update operations.

Operations are represented by a 2D array, and each operation is represented by an array with two positive integers a and b, which means M[i][j] should be added by one for all 0 <= i < a and 0 <= j < b.

You need to count and return the number of maximum integers in the matrix after performing all the operations.

Example 1:
Input: 
m = 3, n = 3
operations = [[2,2],[3,3]]
Output: 4
Explanation: 
Initially, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

After performing [2,2], M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

After performing [3,3], M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

So the maximum integer in M is 2, and there are four of it in M. So return 4.
```language
	 /*
     * 598.RangeAdditionII
     */
    int maxCount(int m, int n, vector<vector<int>>& ops) {

        if(ops.size()==0)
            return m*n;
        for(int i=0;i<ops.size();++i)
        {
            vector<int > row=*(ops.begin()+i);
            if(row[0]<m)
                m=row[0];
            if(row[1]<n)
                n=row[1];
        }
        cout<<n*m;
        return n*m;
    }
```