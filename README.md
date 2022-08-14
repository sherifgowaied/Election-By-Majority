# Election-By-Majority
“plurality vote” (also known as “first-past-the-post” or “winner take all”). In the plurality vote, every voter gets to vote for one candidate. At the end of the election, whichever candidate has the greatest number of votes is declared the winner of the election


# Getting Started


Execute cd ~ (or simply cd with no arguments) to ensure that you’re in your home directory). <br />
Execute mkdir pset3 to make (i.e., create) a directory called pset3. <br />
Execute cd pset3 to change into (i.e., open) that directory. <br />
Execute mkdir plurality to make (i.e., create) a directory called plurality in your pset3 directory. <br />
Execute cd plurality to change into (i.e., open) that directory. <br />
Execute ls. You should see this problem’s distribution code, in a file called plurality.c. <br />
Understanding <br />
Let’s now take a look at plurality.c and read through the distribution code that’s been provided to you.

The line #define MAX 9 is some syntax used here to mean that MAX is a constant (equal to 9) that can be used throughout the program. Here, it represents the maximum number of candidates an election can have.

The file then defines a struct called a candidate. Each candidate has two fields: a string called name representing the candidate’s name, and an int called votes representing the number of votes the candidate has. Next, the file defines a global array of candidates, where each element is itself a candidate.

Now, take a look at the main function itself. See if you can find where the program sets a global variable candidate_count representing the number of candidates in the election, copies command-line arguments into the array candidates, and asks the user to type in the number of voters. Then, the program lets every voter type in a vote (see how?), calling the vote function on each candidate voted for. Finally, main makes a call to the print_winner function to print out the winner (or winners) of the election.

If you look further down in the file, though, you’ll notice that the vote and print_winner functions have been left blank. This part is up to you to complete!

# Specification
Complete the implementation of plurality.c in such a way that the program simulates a plurality vote election.

Complete the vote function.
vote takes a single argument, a string called name, representing the name of the candidate who was voted for. <br />
If name matches one of the names of the candidates in the election, then update that candidate’s vote total to account for the new vote. The vote function <br /> in this case should return true to indicate a successful ballot.
If name does not match the name of any of the candidates in the election, no vote totals should change, and the vote function should return false to indicate an invalid ballot. <br />
You may assume that no two candidates will have the same name. <br />
Complete the print_winner function. <br />
The function should print out the name of the candidate who received the most votes in the election, and then print a newline.
It is possible that the election could end in a tie if multiple candidates each have the maximum number of votes. In that case, you should output the names of each of the winning candidates, each on a separate line. <br />
You should not modify anything else in plurality.c other than the implementations of the vote and print_winner functions (and the inclusion of additional header files, if you’d like). <br />

# Usage
Your program should behave per the examples below.

$ ./plurality Alice Bob <br />
Number of voters: 3 <br />
Vote: Alice <br />
Vote: Bob <br />
Vote: Alice <br />
Alice <br />
$ ./plurality Alice Bob <br />
Number of voters: 3 <br />
Vote: Alice <br />
Vote: Charlie <br />
Invalid vote. <br />
Vote: Alice <br />
Alice <br />
$ ./plurality Alice Bob Charlie <br />
Number of voters: 5 <br />
Vote: Alice <br />
Vote: Charlie <br />
Vote: Bob <br />
Vote: Bob <br />
Vote: Alice <br />
Alice <br />
Bob <br />
