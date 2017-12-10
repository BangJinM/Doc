


#######代码
想法一:在二维数组中，他的地址是有序、处于同一个内存空间的，{{1，2}，{3，4}}，在地址中表示相当与{1，2，3，4}。原想以这种方式来解决vector的重塑矩阵问题。

但是在vector中，每一个新的vector都会动态的分配一个空间，所以前一个vector和后一个vector不可能会在一个内存空间中。想法1宣告失败。只能将vector中的值赋予数组中，再进行操作。


```language
		//基于想法一的实现
        vector<vector<int>> matrixReshape(vector<vector<int>> &nums, int r, int c) {
        //判断是否相等，否返回nums
        const int row = nums.size();
        const int count = (*nums.begin()).size();
        if ((r * c) != (row * count))
            return nums;
        cout<<row<<count;

        int numArray[row][count];
        int *p=&numArray[0][0];
		//将vector中的数据填充到数组中
        for (auto it = nums.begin(); it != nums.end(); it++) {
            for (auto iter = (*it).begin(); iter != (*it).end(); iter++) {
                *p=*iter;
                p++;
            }
        }

		//将数组中的数据反填到新的vector中
        vector<vector<int>> numsRow{};
        int *z=&numArray[0][0];
        for (int i=0;i<r;i++) {
            vector<int> numsCout(z,z+c);
            numsRow.push_back(numsCout);
            z+=c;
        }
        return numsRow;
    }
```