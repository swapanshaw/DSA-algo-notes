# DSA-algo-notes

### Problems
####  Longest Substring Without Repeating Characters
            -- loop over character of input string
            -- check if temp string has currect char 
            -- append the char in the temp string
            -- if yes then slide the windoe, temp.substring(temp.indexOf(char)
            -- max = Math.max(max, temp.length()
            
### Implement the myAtoi(string s)
            -- remove all leading ' ' char
            -- set the sign based on + or _ char
            -- Interate over the while idx < len(input string)
              -- digit = inputStr.charAt(i) - '0'
              -- check for over flow res>Integer.MAX_VALUE/10 || (res==Integer.MAX_VALUE/10 && digit>Integer.MAX_VALUE%10)
              -- res = res*10 +digit
