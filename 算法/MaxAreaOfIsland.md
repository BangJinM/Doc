####Max Area of Island



```language
	//实现1
    void ergodic(int y, int x, vector<vector<int>> &grid, set<int> &close, unordered_map<int, int> &number, int key) {
        int xMax = (*grid.begin()).size();
        int yMax = grid.size();
        int cl=(y) * xMax + (x);
        if (x < 0 || x >= xMax || y < 0 || y >= yMax)
            return;
        if (close.count(cl) > 0)
            return;
        if (grid[y][x] == 0) {
            close.insert(cl);
            return;
        }
        if (number.count(key) == 0)
            number[key] = 0;
        number[key] = number[key] + 1;
        close.insert(cl);
        //cout<<((y+1) * grid.size() + (x+1))<<endl;
        ergodic( y,x + 1, grid, close, number, key);

        ergodic(y + 1,x,  grid, close, number, key);

        ergodic(y - 1,x,  grid, close, number, key);

        ergodic( y,x - 1, grid, close, number, key);


    }

    int maxAreaOfIsland(vector<vector<int>> &grid) {
        int key = 0;
        unordered_map<int, int> number{};
        set<int> close{};

        for (int y = 0; y < grid.size(); y++) {
            for (int x = 0; x < (*grid.begin()).size(); ++x) {
                if (grid[y][x] == 1) {
                    int i=((y) * grid.size() + (x));
                    cout<<i<<endl;
                    if (close.count(i) == 0) {

                        ergodic(y, x, grid, close, number, key);
                        ++key;
                    }
                }
            }
        }

        if (number.size() > 0) {
            int max = 0;
            for (auto iter = number.begin(); iter != number.end(); ++iter) {
                if ((*iter).second > max)
                    max = iter->second;
            }
            return max;
        }
        return 0;
    }
```
```language
	//优化
    void ergodic(int y, int x, vector<vector<int>> &grid, set<int> &close,int& areaMax) {
        int xMax = (*grid.begin()).size();
        int yMax = grid.size();
        int cl=(y) * xMax + (x);
        if (x < 0 || x >= xMax || y < 0 || y >= yMax)
            return;
        if (close.count(cl) > 0)
            return;
        if (grid[y][x] == 0) {
            close.insert(cl);
            return;
        }
        ++areaMax;
        close.insert(cl);
        //cout<<((y+1) * grid.size() + (x+1))<<endl;
        ergodic( y,x + 1, grid, close,areaMax);

        ergodic(y + 1,x,  grid, close,areaMax);

        ergodic(y - 1,x,  grid, close,areaMax);

        ergodic( y,x - 1, grid, close,areaMax);

    }

    int maxAreaOfIsland(vector<vector<int>> &grid) {
        set<int> close{};

        int areaMax=0;
        int tempMax=0;
        for (int y = 0; y < grid.size(); y++) {
            for (int x = 0; x < (*grid.begin()).size(); ++x) {
                if (grid[y][x] == 1) {
                    int i=((y) * grid.size() + (x));
                    cout<<i<<endl;
                    if (close.count(i) == 0) {
                        ergodic(y, x, grid, close,tempMax);
                        if(tempMax>areaMax)
                            areaMax=tempMax;
                        tempMax=0;
                    }
                }
            }
        }
        return areaMax;
    }
```
