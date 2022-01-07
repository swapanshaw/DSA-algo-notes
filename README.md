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
              
### Roman to Integer
            -- Buid a map <roman_char, corresponding_int>
            -- Loop from back to front on input string
            -- if s[i] < s[i+1'
                   -- res-=map.get(s[i])
               else
                   -- res+=map.get(s[i])
### 3 sum
            -- sort and 2 point

### Remove duplicate from sorted array
            -- interate over the array from 0 to n-1
            -- skip the num if a[i] == a[i+1] else increemt counter;
            
### Next permutation
            -- traverse the string from right to left and find idx where a[i]<a[i+1]
            -- for i = idx+1 to n find k where a[i]>a[idx]
            -- swap(nums, idx,k)
            -- reverse(nums, idx+1, n)
            ex:
            1,5,8,4,7,6,5,3,1
             idx = 3 which is 4
             next imediate number > than 4 in righ side is 5, at index 6
             swap(4,5) -- 1,5,8,5,7,6,4,3,1
             reverse(4, 8)-- 1,5,8,5,1,3,4,6,7
