Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:

	All letters in this word are capitals, like "USA".
	All letters in this word are not capitals, like "leetcode".
	Only the first letter in this word is capital if it has more than one letter, like "Google".

Otherwise, we define that this word doesn't use capitals in a right way.

Example 1:
Input: "USA"
Output: True

Example 2:
Input: "FlaG"
Output: False

```language
//效率低下
    bool detectCapitalUse(string word) {
     	const regex pattern("^[A-Z][a-z]{1,}$|^[A-Z]+$|^[a-z]+$");
        return regex_match(word,pattern);
    }
```

```language
	//写法虽然复杂，但是效率高
	bool detectCapitalUse(string word) {
        auto iter=word.begin();
        bool low=islower(*iter);
        ++iter;
        if(low)
        {
            while(iter!=word.end())
            {
                bool temp=islower(*iter);
                ++iter;
                if(low!=temp)
                    return false;
            }
        } else{
            if(iter==word.end())
                return true;
            bool temp=islower(*iter);
            ++iter;
            while(iter!=word.end()){
                bool temp2=islower(*iter);
                if(temp2!=temp)
                    return false;
                ++iter;
            }
        }
        return true;
    }
```

