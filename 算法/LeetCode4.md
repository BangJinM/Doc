###LeetCode： Reverse Words in a String III
######题目
Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
#######例子
Example 1:
```language
```
Input: "Let's take LeetCode contest"

Output: "s'teL ekat edoCteeL tsetnoc"
```
######提示
Note: In the string, each word is separated by single space and there will not be any extra space in the string.

######代码
```language
	string reverseWords(string s) {
        auto temp=s.begin();
        for(auto iter=s.begin();iter!=s.end();iter++)
        {
            if(*iter==' ')
            {
                reverse(temp,iter);
                temp=iter+1;
            }
        }
        reverse(temp,s.end());
        cout<<s;
        return s;
    }
```
```language
	string reverseWords(string s) {
        stack<char> str{};
        string out;
        auto sitr = s.begin();
        while (sitr != s.end()) {
            if (*sitr != ' ') {
                str.push(*sitr);
            } else {
                while (!str.empty()) {
                    out += str.top();
                    str.pop();
                }
                out += ' ';
            }
            sitr++;
        }
        while (!str.empty()) {
            out += str.top();
            str.pop();
        }
        cout << out << endl;
        return out;
    }
```