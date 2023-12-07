# assignment

Question:
Easy 1
Given a string s consisting of words and spaces, return the length of the last word in the string.
A word is a maximal 
substring consisting of non-space characters only.

Code :
class Solution {
public:
    int lengthOfLastWord(string s) {
        int siz=s.size(),kount=0,flag=0;
        for(int i=siz-1;i>=0;i--){
            if(s[i]==' '&&flag)break;
            if(s[i]!=' '){
                flag=1;
                kount++;
            }
        }
        return kount;
    }
};

ExplanationThis C++ code defines a class Solution with a member function lengthOfLastWord. The function takes a string s as input and returns an integer, representing the length of the last word in the given string.

1. int siz = s.size(), kount = 0, flag = 0;: Declare and initialize three variables - siz to store the size of the input string s, kount to keep track of the length of the last word, and flag as a flag variable to indicate if non-space characters have been encountered.

2. for(int i = siz-1; i >= 0; i--): Iterate through the characters of the string in reverse order, starting from the last character.

3. Inside the loop:
   - if(s[i] == ' ' && flag) break;: If a space character is encountered and flag is set (meaning non-space characters have been encountered before), exit the loop. This is to ensure we only count the last word.
   - if(s[i] != ' '): If the current character is not a space, set flag to 1 (indicating non-space characters have been encountered) and increment kount to count the characters of the last word.

4. Finally, return kount;: Return the length of the last word.

In summary, the code efficiently iterates through the input string in reverse, counting the characters of the last word until a space character is encountered after the last word. The count is then returned as the result.


2nd question
medium 2nd one
#include <iostream>
#include <vector>
#include <unordered_map>

using namespace std;
class Solution {
public:
    int majorityElement(vector<int>& nums) {
         
      
       int n=nums.size();
       unordered_map<int,int>mp;
       for(int i=0;i<n;i++)
       {
          mp[nums[i]]++;
       }

       int k=(n/2);
       for(auto i:mp)
       {
           if(i.second>k)
           {
               return i.first;
           }
       }

 
          return -1;





    }
};

explanation
This C++ code defines a class Solution with a member function majorityElement that takes a vector of integers nums as input and returns the majority element. The majority element is the one that appears more than n/2 times in the vector, where n is the size of the vector.

Here's a step-by-step explanation:

1. *Function Signature:*
   cpp
   int majorityElement(vector<int>& nums)
   
   The function takes a reference to a vector of integers (nums) and returns an integer.

2. *Variable Declaration:*
   cpp
   int n = nums.size();
   unordered_map<int, int> mp;
   
   - n stores the size of the vector.
   - mp is an unordered map that will be used to store the count of each unique element in the vector.

3. *Counting Occurrences:*
   cpp
   for(int i = 0; i < n; i++) {
      mp[nums[i]]++;
   }
   
   This loop iterates through each element in the vector and updates the count in the unordered map.

4. *Finding Majority Element:*
   cpp
   int k = (n / 2);
   for(auto i : mp) {
       if(i.second > k) {
           return i.first;
       }
   }
   
   It calculates the threshold (k) for the majority element. Then, it iterates through the unordered map and checks if the count of any element is greater than the threshold. If found, it returns that element as the majority element.

5. *Default Return:*
   cpp
   return -1;
   
   If no majority element is found, the function returns -1.

In summary, the code uses an unordered map to count the occurrences of each element and then checks for a majority element by comparing the count with a threshold. If a majority element is found, it is returned; otherwise, -1 is returned.

3rd one
Hard 3rd one

code:
class Solution {
public:
    int getlen(int n){
        if(n == 0)
        return 0;
        int len = 0;

        while(n > 0){
            n = n/10 ;
            len++;
        }
        return len;
    }
    int countDigitOne(int n) {
        if(n <= 0)
        return 0;

        if(n < 10)
        return 1;

        int len = getlen(n);
        int base = pow(10, len-1);

        int firstdigit = n/base;
        int rem = n%base;
        int oneInBase = 0;

        if(firstdigit == 1){
            oneInBase = n-base + 1;
        }
        else{
            oneInBase = base;
        }

        return oneInBase + firstdigit*countDigitOne(base-1) + countDigitOne(rem);
    }
};

explanation:
This C++ code defines a class Solution with a member function countDigitOne. The function takes an integer n as input and returns the count of digit '1' occurring in all numbers from 1 to n.

Here's a step-by-step explanation:

1. *Helper Function getlen:*
   cpp
   int getlen(int n) {
       if (n == 0)
           return 0;
       int len = 0;

       while (n > 0) {
           n = n / 10;
           len++;
       }
       return len;
   }
   
   This function calculates and returns the number of digits in the given integer n.

2. *Main Function countDigitOne:*
   cpp
   int countDigitOne(int n) {
       if (n <= 0)
           return 0;

       if (n < 10)
           return 1;
   
   The function checks for base cases: if n is less than or equal to 0, it returns 0; if n is less than 10, it returns 1.

   cpp
       int len = getlen(n);
       int base = pow(10, len - 1);

       int firstdigit = n / base;
       int rem = n % base;
       int oneInBase = 0;
   
   It calculates the length of the number n and sets the base to 10 raised to the power of len - 1. It then extracts the first digit of n and the remainder.

   cpp
       if (firstdigit == 1) {
           oneInBase = n - base + 1;
       } else {
           oneInBase = base;
       }
   
   Checks if the first digit is 1. If yes, calculates the count of '1' in the current base. If not, the count is the entire base.

   cpp
       return oneInBase + firstdigit * countDigitOne(base - 1) + countDigitOne(rem);
   }
   
   Recursively calculates the count of '1' in the current base, the count in the remaining digits, and adds them up. The recursive calls handle the range from 1 to the remaining digits and from the remaining digits to the end.

In summary, the code recursively calculates the count of digit '1' in a given range of numbers (from 1 to n) by breaking it down into subproblems based on the first digit, base, and remaining digits
