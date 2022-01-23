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
            -- if s[i] < s[i+1]
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
### Mutiply 2 string 
            for(int i = n-1; i>=0; i--) {
                        for(int j=m-1;j>=0; j--) {
                            res[i+j+1]+= (num1.charAt(i) - '0')*(num2.charAt(j) - '0');
                            int curr = res[i+j+1];
                            res[i+j] += curr/10;
                            res[i+j+1]=curr%10;

                        }
            }
### Group Anagram
            -- compute the char[26] array for each str in String[]
            -- put in hasmap where key is computed char[26] array annd value is List<Str>
            -- repeat above for all str in str[]            
### Add two binary number
        BigInteger x = new BigInteger(a, 2);
        BigInteger y = new BigInteger(b, 2);
        BigInteger zero = new BigInteger("0",2);
        
        while(y.compareTo(zero) != 0) {
            BigInteger ans = x.xor(y);
            y = x.and(y).shiftLeft(1);
            x = ans;
        }
        return x.toString(2);
        
 ### merge sorted array
      public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m-1;
        int j = n-1;
        for(int k = m+n-1; k >=0; k--) {
            if(j < 0) {
                break;
            }
            if(i >=0 && nums1[i] > nums2[j]) {
                nums1[k] = nums1[i--];
            } else {
                 nums1[k] = nums2[j--];
            }
        }
    }
### valid palindram
            -- two pointer approach,
            -- remove the unwanted character, use Character.isLetterOrDigit()
            
### Subarray sum equals k
            map.put<prefixSum, index>
            if(map.contains(prefixSum -k) then start = map.get(prefixSum -k) +1, end =i
            
### permutation II
          private void permuteUniqueHelper(Map<Integer, Integer> map, Integer[] p, int i, List<List<Integer>> result) {
            if (i == p.length)
                result.add(Arrays.asList(Arrays.copyOf(p, p.length)));
            for (int key : map.keySet()) {
                if (map.get(key) > 0) {
                    map.put(key, map.get(key) - 1);
                    p[i] = key;
                    permuteUniqueHelper(map, p, i + 1, result);
                    map.put(key, map.get(key) + 1);
                }
            }
        }
        
### Combination Sum
     private void combinationSumUtil(int[] arr, int idx, List<Integer> local, List<List<Integer>> ans, int target){
        if(target == 0) {
            if(!ans.contains(local))
                ans.add(new ArrayList(local));
            return;
        }
        if(target < 0) return;
        
        for(int i=idx; i<arr.length; i++) {
            
            if(i > idx && arr[i] == arr[i-1]) continue;
            
            local.add(arr[i]);
            combinationSumUtil(arr, i+1, local, ans, target-arr[i]);
            local.remove(local.size() -1);
        }
    }
    
### privious smaller elements
 
             int[] previousSmallerElement(int arr[]) {
                Stack<Integer> stack = new Stack<>();
                int len = arr.length;
                if (len == 0) return null;
                int pse[] = new int[len];
                stack.push(arr[0]);
                pse[0] = -1;

                for (int i = 1; i < len; i++) {
                  while (!stack.isEmpty() && arr[i] <= arr[stack.peek()]) {
                    stack.pop();
                  }
                  if (stack.isEmpty()) {
                    pse[i] = -1;
                  } else {
                    pse[i] = stack.peek();
                  }
                  stack.push(i);
                }
                return pse;
              }
              
 ### Largest. area histogram
          int largestRectangleHistogram(int[] arr) {
            int[] pse = previousSmallerElement(arr);

            int[] nse = nextSmallerElement(arr);
            int maxArea = Integer.MIN_VALUE;
            for (int i = 0; i < arr.length; i++) {
                        maxArea = Math.max(maxArea, (nse[i] - pse[i] - 1) * arr[i]);
            }
            return maxArea;
          }
          
### generate subset
               // TC - O(n*2^n)
              static void generateSubSet(int idx, int[] nums, List<Integer> local, List<List<Integer>> ans) {
                ans.add(new ArrayList<>(local));
                for (int i = idx; i < nums.length; i++) {
                  local.add(nums[i]);
                  generateSubSet(i + 1, nums, local, ans);
                  local.remove(local.size() - 1);
                }
              }
              
 ### remove K digit to make smaller number
 
    Stack<Character> stack = new Stack<>();
    for (int i = 0; i < n; i++) {
      Character c = str.charAt(i);
      while (!stack.isEmpty() && k > 0 && stack.peek() > c) {
        k--;
        stack.pop();
      }
      stack.push(c);
    }
    while (!stack.isEmpty() && k > 0) {
      stack.pop();
      k--;
    }
    
### Rat in a maze
              private static boolean solvemazeUti(int[][] maze, int n, int i, int j, int[][] sol) {
                // Base condition, when it reached at the end,
                if (i == n - 1 && j == n - 1 && maze[i][j] == 1) {
                  sol[i][j] = 1;
                  return true;
                }
                // do in the different direction, (i+1,j), (i-1,j), (i, j-1), (i, j+1)
                if (isSafe(maze, n, i, j, sol)) {
                  sol[i][j] = 1;
                  if (solvemazeUti(maze, n, i - 1, j, sol))
                    return true;
                  if (solvemazeUti(maze, n, i + 1, j, sol))
                    return true;
                  if (solvemazeUti(maze, n, i, j - 1, sol))
                    return true;
                  if (solvemazeUti(maze, n, i, j + 1, sol))
                    return true;
                  // if non of the above works then backtrack
                  sol[i][j] = 0;
                  return false;
                }
                return false;
              }
