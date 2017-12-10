#### 283. Move Zeroes

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.
Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.

```language
        void moveZeroes(vector<int>& nums) {
        /*int temp=0;
        for(int i=0;i<nums.size();)
        {
            if(!nums[i])
            {
                nums.erase(nums.begin()+i);
                ++temp;
            } else
                ++i;
        }
        for (int j = 0; j <temp ; ++j) {
            nums.push_back(0);
        }*/
        for (int i = 0, j = 0; i < nums.size(); i++)
            if (nums[i])
                swap(nums[i], nums[j++]);

        for(auto num:nums)
        {
            cout<<num<<ends;
        }
    }
```