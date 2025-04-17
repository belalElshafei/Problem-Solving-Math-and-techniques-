## Pair Counting Mathematics

### General Formulas

#### 1. Counting All Possible Unordered Pairs
\[
\text{Total pairs} = \frac{n(n-1)}{2}
\]

**Example**: For array `[1,2,3,4,5,1]` (n=6)
\[
\frac{6 \times 5}{2} = 15 \text{ pairs}
\]

#### 2. Counting Only Identical Pairs
\[
\text{Identical pairs} = \sum \frac{f_x(f_x - 1)}{2}
\]
where \( f_x \) = frequency of element \( x \).

**Example Calculation**:
- Element `1`: appears 2 times → \( \frac{2 \times 1}{2} = 1 \) pair
- Other elements: 0 pairs
- **Total identical pairs = 1**

### C++ Implementations

#### Count All Pairs
```cpp
int countAllPairs(const vector<int>& nums) {
    int n = nums.size();
    return n * (n - 1) / 2;
}

int countIdenticalPairs(const vector<int>& nums) {
    unordered_map<int, int> freq;
    for (int num : nums) freq[num]++;
    
    int identical_pairs = 0;
    for (auto& [num, count] : freq) {
        identical_pairs += count * (count - 1) / 2;
    }
    return identical_pairs;
}
