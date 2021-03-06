# 高级动态规划
* dp 顺推模板
  ```js
  function DP() {
    let dp = [][] // ⼆维情况   
    for (let i = 0; i < M; i++ {
        for (let j = 0; j < N; j++) {
            dp[i][j] = _Function(dp[i’][j’]…)
        }
    }
    return dp[M][N];
  }
  ```
* 关键点
  * **动态规划**和**递归**或者**分治**没有根本上的区别（关键看有无最优的子结构） 
  * 拥有共性：找到重复子问题
  * 差异性：最优子结构、中途可以淘汰次优解

# 高级字符串算法
* Longest common sequence（最长子序列）
    ```js
    if (s1[i-1] == s2[j-1]) 
        dp[i][j] = dp[i-1][j-1] + 1;
    else 
        dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
    ```
* Longest common substring (最长子串）
    ```js
    if (s1[i-1] == s2[j-1])
        dp[i][j] = dp[i-1][j-1] + 1;
    else
        dp[i][j] = 0;
    ``` 
# 字符串匹配算法
* Rabin-Karp 算法
  
  * 在朴素算法中，我们需要挨个比较所有字符，才知道目标字符串中是否包含子串。为了避免挨个字符对目标字符串 和子串进行比较，可以尝试一次性判断两者是否相等。因此，我们需要一个**好的哈希函数（hash function）**。通过哈希函数，我们可以算出**子串的哈希值**，然后将它和**目标字符串中的子串的哈希值进行比较**。 这个方法在速度上**比暴力法有显著提升**。
  * 核心思想
    * 假设子串的长度为 M (pat)，目标字符串的长度为 N (txt)
    * 计算子串的 hash 值 hash_pat
    * 计算目标字符串txt中每个长度为 M 的子串的 hash 值（共需要计算 N-M+1 次）
    * 比较 hash 值：如果 hash 值不同，字符串必然不匹配; 如果 hash 值相同， 还需要使用朴素算法再次判
* KMP 算法
  * 核心思想：
    * 当子串与目标字符串不匹配时，其实已经知道了前面已经匹配成功那一部分的字符（包括子串与目标字符串）。比如，当空格与 D 不匹配时，其实知道前面六个字符是 “ABCDAB”。
    * 设法利用这个已知信息，不要把“搜索位置” **移回已经比较过**的位置，继续把它向后移，提高效率
