#### 448. Find All Numbers Disappeared in an Array

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

Example:

Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]

```language
	vector<int> findDisappearedNumbers(vector<int>& nums) {
         int size=nums.size();
         set<int> numsSet{};
         numsSet.insert(nums.begin(),nums.end());
         nums.erase(nums.begin(),nums.end());
         for(int i=1;i<=size;++i)
         {
             if(numsSet.count(i)==0)
                 nums.push_back(i);
         }
         for (auto num:nums) {
             cout<<num<<endl;
         }
         return nums;
     }

```

```language
	vector<int> findDisappearedNumbers(vector<int>& nums) {
       int size=nums.size();
       vector<int> result{};
       vector<int > vector1{};
       for(int i=1;i<=size;++i){
           result.push_back(i);
       }
       for(auto num:nums)
       {
           result[num-1]=-1;
       }
       for(int i=0;i<size;++i)
       {
            if(result[i]!=-1)
                vector1.push_back(i+1);

       }
       return vector1;
    }
```