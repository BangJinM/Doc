####Submission Details

第5天  第11题
######题目
	You're now a baseball game point recorder.

	Given a list of strings, each string can be one of the 4 following types:

	1.Integer (one round's score): Directly represents the number of points you get in this round.
	
	2."+" (one round's score): Represents that the points you get in this round are the sum of the last two valid round's points.
	
	3."D" (one round's score): Represents that the points you get in this round are the doubled data of the last valid round's points.
	
	4."C" (an operation, which isn't a round's score): Represents the last valid round's points you get were invalid and should be removed.
	
	Each round's operation is permanent and could have an impact on the round before and the round after.

You need to return the sum of the points you could get in all the rounds.

######Example 1:
	Input: ["5","2","C","D","+"]
    
	Output: 30
    
	Explanation:
    
	Round 1: You could get 5 points. The sum is: 5.
    
	Round 2: You could get 2 points. The sum is: 7.
    
	Operation 1: The round 2's data was invalid. The sum is: 5.
    
	Round 3: You could get 10 points (the round 2's data has been removed). The sum is: 15.
    
	Round 4: You could get 5 + 10 = 15 points. The sum is: 30.
    
######Example 2:
	Input: ["5","-2","4","C","D","9","+","+"]
    
	Output: 27
    
	Explanation:
    
	Round 1: You could get 5 points. The sum is: 5.
    
	Round 2: You could get -2 points. The sum is: 3.
    
	Round 3: You could get 4 points. The sum is: 7.
    
	Operation 1: The round 3's data is invalid. The sum is: 3.	
    
	Round 4: You could get -4 points (the round 3's data has been removed). The sum is: -1.
    
	Round 5: You could get 9 points. The sum is: 8.
    
	Round 6: You could get -4 + 9 = 5 points. The sum is 13.
    
	Round 7: You could get 9 + 5 = 14 points. The sum is 27.
######Note:
	The size of the input list will be between 1 and 1000.
	Every integer represented in the list will be between -30000 and 30000.
    
###### 代码
第一次写：
```language
		vector<int> vector{};

        for (auto iterOps = ops.begin(); iterOps != ops.end(); ++iterOps) {
            if (*iterOps == "+") {
                vector.push_back(vector.back() + *(vector.end() - 2));
            }
            else if (*iterOps == "D") {
                vector.push_back((vector.back() * 2));
            }
            else if (*iterOps == "C") {
                vector.erase(vector.end() - 1);
            }
            else {
                int i=stoi(*iterOps);
                vector.push_back(i);
            }

        }
        int num=0;
        for (auto it=vector.begin();it!=vector.end();it++) {
            cout<<*it<<endl;
            num+=*it;
        }
        cout << num;
        return vector.back();
```
在之前基础上修改：
```language
	int calPoints(vector<string> &ops) {
		vector<int> vector{};
        int num=0;
        int n=0;
        for (auto iterOps = ops.begin(); iterOps != ops.end(); ++iterOps) {
            if (*iterOps == "+") {
                n=vector.back() + *(vector.end() - 2);
                vector.push_back(n);
                num+=n;
            }
            else if (*iterOps == "D") {
                n=(vector.back() * 2);
                vector.push_back(n);
                num+=n;
            }
            else if (*iterOps == "C") {
                num-=vector.back();
                vector.erase(vector.end() - 1);
            }
            else {
                int i=stoi(*iterOps);
                vector.push_back(i);
                num+=i;
            }
        }return  num;
     }
```