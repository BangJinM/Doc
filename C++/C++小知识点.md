###C++
####小知识点
######右值引用
```language
MyList(MyList && rhs){}
```
MyList && rhs 是一个右值引用。右值表达式为int a=10;左边是变量，右边是常量。右值引用就是引用的值是常量。
######C++中const在函数名前面和函数后面的区别
```language
	Object & front()const {	//这个函数体里面不能修改对象的任何属性
        return  *begin();
    }
    Object & front(){		//这个函数体里面可以修改对象的任何属性
        return  *begin();
    }
```