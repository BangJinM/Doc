#### Distribute Candies

第5天 第10题


Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain.

######Example 1:
	Input: candies = [1,1,2,2,3,3]
	Output: 3
######Explanation:

	There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
	Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too.
	The sister has three different kinds of candies.

######Example 2:


	Input: candies = [1,1,2,3]

	Output: 2
	Explanation: For example, the sister has candies [2,3] and the brother has candies [1,1].
	The sister has two different kinds of candies, the brother has only one kind of candies.

######代码
```language
    int distributeCandies(vector<int>& candies) {
        unordered_map<int, int> map{};

        for (auto candiesIter = candies.begin(); candiesIter != candies.end(); candiesIter++)
        {
            if(map.count(*candiesIter)==0)
            {
                map[*candiesIter]=1;
            } else{
                map[*candiesIter]++;
            }
        }
        if(map.size()>=(candies.size()/2))
            return candies.size()/2;
        else return map.size();
    }
```
```language
unordered_map<int, int> map(candies.size());

        for (auto candiesIter = candies.begin(); candiesIter != candies.end()
        &&map.size()>=(candies.size()/2); candiesIter++)
        {
            if(map.count(*candiesIter))
            {
                map[*candiesIter]=1;
            } else{
                map[*candiesIter]++;
            }
        }
        if(map.size()>=(candies.size()/2))
            return candies.size()/2;
        else return map.size();
```