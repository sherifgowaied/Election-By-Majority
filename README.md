# Election-By-Majority</br> </br>
“plurality vote” (also known as “first-past-the-post” or “winner take all”). In the plurality vote, every voter gets to vote for one candidate. At the end of the election, whichever candidate has the greatest number of votes is declared the winner of the election </br>

# Runoff </br>
Implement a program that runs a runoff election, per the below.</br> </br>

./runoff Alice Bob Charlie </br>
Number of voters: 5 </br>
Rank 1: Alice </br>
Rank 2: Bob </br>
Rank 3: Charlie </br>

Rank 1: Alice </br>
Rank 2: Charlie </br>
Rank 3: Bob </br>
 </br>
Rank 1: Bob </br>
Rank 2: Charlie </br>
Rank 3: Alice </br>

Rank 1: Bob </br>
Rank 2: Alice </br>
Rank 3: Charlie </br>

Rank 1: Charlie </br>
Rank 2: Alice </br>
Rank 3: Bob </br>

Alice </br>


# Understanding</br>
Let’s open up runoff.c to take a look at what’s already there. We’re defining two constants: MAX_CANDIDATES for the maximum number of candidates in the election, and MAX_VOTERS for the maximum number of voters in the election.</br>

Next up is a two-dimensional array preferences. The array preferences[i] will represent all of the preferences for voter number i, and the integer preferences[i][j] here will store the index of the candidate who is the jth preference for voter i.</br>

Next up is a struct called candidate. Every candidate has a string field for their name, and int representing the number of votes they currently have, and a bool value called eliminated that indicates whether the candidate has been eliminated from the election. The array candidates will keep track of all of the candidates in the election.</br>

The program also has two global variables: voter_count and candidate_count.</br>

Now onto main. Notice that after determining the number of candidates and the number of voters, the main voting loop begins, giving every voter a chance to vote. As the voter enters their preferences, the vote function is called to keep track of all of the preferences. If at any point, the ballot is deemed to be invalid, the program exits.</br>

Once all of the votes are in, another loop begins: this one’s going to keep looping through the runoff process of checking for a winner and eliminating the last place candidate until there is a winner.</br>

The first call here is to a function called tabulate, which should look at all of the voters’ preferences and compute the current vote totals, by looking at each voter’s top choice candidate who hasn’t yet been eliminated. Next, the print_winner function should print out the winner if there is one; if there is, the program is over. But otherwise, the program needs to determine the fewest number of votes anyone still in the election received (via a call to find_min). If it turns out that everyone in the election is tied with the same number of votes (as determined by the is_tie function), the election is declared a tie; otherwise, the last-place candidate (or candidates) is eliminated from the election via a call to the eliminate function.</br>

If you look a bit further down in the file, you’ll see that these functions — vote, tabulate, print_winner, find_min, is_tie, and eliminate — are all left to up to you to complete!</br>

# Specification</br>
Complete the implementation of runoff.c in such a way that it simulates a runoff election. You should complete the implementations of the vote, tabulate, print_winner, find_min, is_tie, and eliminate functions, and you should not modify anything else in runoff.c (and the inclusion of additional header files, if you’d like).</br>

# vote</br>
### the vote function.</br>

The function takes arguments voter, rank, and name. If name is a match for the name of a valid candidate, then you should update the global preferences array to indicate that the voter voter has that candidate as their rank preference (where 0 is the first preference, 1 is the second preference, etc.).
If the preference is successfully recorded, the function should return true; the function should return false otherwise (if, for instance, name is not the name of one of the candidates).</br>
You may assume that no two candidates will have the same name.</br>
Hints
tabulate</br>

# the tabulate function.
</br>
The function should update the number of votes each candidate has at this stage in the runoff.
Recall that at each stage in the runoff, every voter effectively votes for their top-preferred candidate who has not already been eliminated.
Hints</br>
# print_winner</br>
####  the print_winner function.
</br>
If any candidate has more than half of the vote, their name should be printed to stdout and the function should return true.
If nobody has won the election yet, the function should return false.</br>
Hints</br>
# find_min</br>
 the find_min function.</br>

The function should return the minimum vote total for any candidate who is still in the election.
Hints</br>
# is_tie</br>
 the is_tie function.</br>

The function takes an argument min, which will be the minimum number of votes that anyone in the election currently has.</br>
The function should return true if every candidate remaining in the election has the same number of votes, and should return false otherwise.</br>
Hints
# eliminate
### the eliminate function.</br>

The function takes an argument min, which will be the minimum number of votes that anyone in the election currently has.
The function should eliminate the candidate (or candidates) who have min number of votes.
Walkthrough </br>
