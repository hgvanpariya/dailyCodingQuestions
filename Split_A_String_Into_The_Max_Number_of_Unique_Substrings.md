import java.util.HashSet;

public class Solution {
    public int helper(String s, HashSet<String> hs, int i) {
        // Base case: if we reach the end of the string, return the size of the set
        if (i == s.length()) return hs.size();

        String temp = "";
        int maxSplit = 0;

        // Iterate through the string starting from index 'i'
        for (int k = i; k < s.length(); k++) {
            temp += s.charAt(k);
            
            // If 'temp' is already in the set, skip it
            if (hs.contains(temp)) continue;

            // Add 'temp' to the set and recursively call helper function
            hs.add(temp);
            int currentSplit = helper(s, hs, k + 1);

            // Update the maximum split count if the current is greater
            maxSplit = Math.max(maxSplit, currentSplit);

            // Remove 'temp' to backtrack and try other splits
            hs.remove(temp);
        }

        return maxSplit;
    }

    public int maxUniqueSplit(String s) {
        HashSet<String> hs = new HashSet<>();
        return helper(s, hs, 0);
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        // Test case 1
        String s1 = "ababccc";
        int result1 = solution.maxUniqueSplit(s1);
        System.out.println("Input: " + s1);
        System.out.println("Output: " + result1); // Expected: 5

        // Test case 2
        String s2 = "aba";
        int result2 = solution.maxUniqueSplit(s2);
        System.out.println("Input: " + s2);
        System.out.println("Output: " + result2); // Expected: 2

        // Test case 3
        String s3 = "aa";
        int result3 = solution.maxUniqueSplit(s3);
        System.out.println("Input: " + s3);
        System.out.println("Output: " + result3); // Expected: 1
    }
}
