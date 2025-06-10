# Leetcode---3442
Maximum Difference Between Even and Odd Frequency I", 
//code in java 
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int maxDiff(String s) {
        Map<Character, Integer> charCounts = new HashMap<>();
        for (char c : s.toCharArray()) {
            charCounts.put(c, charCounts.getOrDefault(c, 0) + 1);
        }

        int maxOdd = 0;
        int minEven = s.length();
        
        for (int count : charCounts.values()) {
            if (count % 2 == 0) {
                minEven = Math.min(minEven, count);
            } else {
                maxOdd = Math.max(maxOdd, count);
            }
        }
        
        if (maxOdd == 0 || minEven == s.length())
            return 0;

        return maxOdd - minEven;
    }
}
