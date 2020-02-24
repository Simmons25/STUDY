# 问题
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:

输入: "()"
输出: true
示例 2:

输入: "()[]{}"
输出: true
示例 3:

输入: "(]"
输出: false
示例 4:

输入: "([)]"
输出: false
示例 5:

输入: "{[]}"
输出: true
# c++(普通做法)
```
class Solution {
public:
    bool isValid(string s) {
        int w=0;
        if(s[0]!=')'&&s[0]!='}'&&s[0]!=']')
        {


        for(int i=1;i<s.size();i++)
        {
            if(s[i]==')')
            {
                for(int j=i-1;j>=0;j--)
                {
                if(s[j]=='['||s[j]=='{')
                {
                    w=1;
                }
                if(w==1)
                break;
                {
                    if(s[j]=='(')
                    {
                        s[i]='!';
                        s[j]='!';
                        break;
                    }
                }

            }}
            if(s[i]=='}')
            {
                for(int j=i-1;j>=0;j--)
                {
                 if(s[j]=='['||s[j]==')')
                {
                    w=1;
                }
                if(w==1)
                break;
                
                    if(s[j]=='{')
                    {
                        s[i]='!';
                        s[j]='!';
                        break;
                    }
                }
            }
            if(s[i]==']')
            {
                for(int j=i-1;j>=0;j--)
                {
                 if(s[j]=='('||s[j]=='{')
                {
                    w=1;
                }
                if(w==1)
                break;
                
                    if(s[j]=='[')
                    {
                        s[i]='!';
                        s[j]='!';
                        break;
                    }
                }
            }}}
            for(int i=0;i<s.size();i++)
            {
                if(s[i]!=' '&&s[i]!='!')
                {
                    return false;
                }
            }
            return true;
        


    }
};
```
# c++(栈)
```
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        if(s.size()==0)
        return true;
        else if(s.size()%2==1)
        return false;
        else if(s[0]==')'||s[0]==']'||s[0]=='}')
        return false;
        else
        {st.push(s[0]);
        for(int i=1;i<s.size();i++)
        {
            if(s[i]==')'&&st.top()=='(')
            st.pop();
            else if(s[i]==']'&&st.top()=='[')
            st.pop();
            else if(s[i]=='}'&&st.top()=='{')
            st.pop();
            else
            st.push(s[i]);
        }
        if(st.empty())
        return true;
        else
        return false;
        }
    }
};
```

# 笔记
1.普通做法中要注意隐藏的很深的夹的括号。

