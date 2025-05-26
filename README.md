# Final-Project-Task-6


# Tasks 6

#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm>

int longestConsecutiveSequence(const std::vector<int>& nums) {
    if (nums.empty()) return 0;
    
    std::unordered_set<int> num_set(nums.begin(), nums.end());
    int max_length = 0;
    
    for (int num : num_set) {
        //count if this is the beginning of a sequence
        if (num_set.find(num - 1) == num_set.end()) {
            int current_num = num;
            int current_length = 1;
            
            //count consecutive numbers ONLY
            while (num_set.find(current_num + 1) != num_set.end()) {
                current_num++;
                current_length++;
            }
            
            max_length = std::max(max_length, current_length);
        }
    }
    
    return max_length;
}

int main() {
    std::vector<int> nums1 = {10, 5, 12, 3, 55, 30, 4, 11, 2};
    std::vector<int> nums2 = {19, 13, 15, 12, 18, 14, 17, 11};
    
    std::cout << "Array 1 longest consecutive sequence length: " 
              << longestConsecutiveSequence(nums1) << std::endl;
    std::cout << "Array 2 longest consecutive sequence length: " 
              << longestConsecutiveSequence(nums2) << std::endl;
    
    return 0;
}
