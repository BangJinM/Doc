### Hamming Distance

根据位的运算计算得到：
与：0010&0011得到0010；
4&1=0000 0000 0000 0000 0000 0000 0000 0000
或：4|1=0000 0000 0000 0000 0000 0000 0000 1001
异或：5=0000 0000 0000 0101^7=0000 0000 0000 0111 = 0000 0000 0000 0010

##### 想法1
```C++
	int num=0;
        if(x<y)
        {
            int temp=x;
            x=std::move(y);
            y=std::move(temp);
        }
        int all=1;
        for (int i = 0; all<=x&&i<=31; i++) {
            if(i==0);
            else
                all=all*2;
            if(((y >> i)&1)!=((x >> i)&1))
            {
                num++;
            }

        }
        return num;
```
设计初期想要减少for循环，带入了x<=all的算法，但是大大增加了算法运算时间，再leetcode上面的运行时间为6ms

#### 想法2
```language
	for (int i = 0; i<=31; i++) {
            if(((y >> i)&1)!=((x >> i)&1))
            {
                num++;
            }
        }
```
以为这种方式会比思想1调用速度更慢，没想到却比想法1快了3ms。

#### 想法3
```language
		int i=x^y;
        int num=0;
        for(int j=0;j<31;j++)
        {
            if(((i>>j)&1)==1){
                num++;
            }
        }
        return num;
```
可惜还是3ms