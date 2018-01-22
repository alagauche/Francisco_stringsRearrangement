Student:        Francisco McGee
Github:         https://github.com/alagauche/Francisco_stringsRearrangement
Assignment:     Strings Rearrangement from CodeFights

PROBLEM:        Strings Rearrangement
Given an array of equal-length strings, check if it is possible to rearrange 
the strings in such a way that after the rearrangement the strings at 
consecutive positions would differ by exactly one character.


SOLUTION:       Hamming Function
Solution leverages "Hamming function," which calculates the "Hamming distance" 
or "minimum edit distance."


ASSUMPTIONS:
Array of strings will be of equal length.


IMPORTS: itertools, copy
The function hamming() used here was implemented using itertools, as allowed 
in class. If we run hamming(string1, string2), it will return an integer, which
is the minimum number of substitutions required to change one string into the 
other.

Copy was used to make a deepcopy() for validation purposes.


OVERVIEW:
The overall strategy is to remove words from input_list[] and add them into 
output_list[] provided that:
    hamming_function(string1, string2) == 1

By the end, output_list[] should have all of the strings adjacent to each other
with hamming distance = 1; i.e., they are only 1 character different.


STOP CONDITIONS:
If hamming_function returns 0, then a duplicate has been identified in input[] 
and we return False.


RESULTS:
Passed all five test cases.


ISSUES:
I'm pretty sure my runtime is at best exponential. This problem seems similar 
to the Hamming Traveling Salesman (HTSM) problem, and is therefore likely 
to be NP-Complete. 
Forum Discussion:
https://cs.stackexchange.com/questions/82621/rearranging-strings-so-that-the-hamming-distance-between-them-is-1
Research paper on HTSM as NP-Complete:
http://www.diku.dk/hjemmesider/ansatte/jyrki/Paper/EKP85.pdf


FUNCTIONS:

stringRearrangement(input_list)
# basically acts like main()
# return: returns False if list cannot be rearranged so that consecutive words 
    are 1 character different from each other; 
    i.e., hamming distance = 1 between each consecutive word


process_lists(input_list, output_list)
# primary workhorse function
# called by stringRearrangement()
# loops through input_list, pulling items out and adding them to output_list
# pops out words from input_list that are 1 hamming distance from a word 
    already in output_list
# nestle(): this function "nestles" the word into output_list if it is decided 
    it should go in
# if a duplicate is found, return False
# return: process_lists will return whatever is left of input_list, and also 
    the output_list 


hamming(str1, str2)
# called by process_lists()
# return: compares str1 to str2, returns the minimum edit distance
# minimum edit distance = the integer number of minimum edits needed to turn 
    one string into the other


nestle(word, output_list)
# "nestles" the word where it belongs in output_list, either at beginning 
    or end


validate(input_list, output_list)
# validates the output_list
# returns True if rearrangement successful
# returns False if unsuccessful, and also a list of any errors identified



