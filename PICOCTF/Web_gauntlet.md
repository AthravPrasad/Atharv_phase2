# Web Gauntlet
Can you beat the filters?
Additional details will be available after launching your challenge instance.

## My Solve:
1. To begin the analysis, the goal is to alter the initial SQL query to execute successfully as 'admin', regardless of the password check.
2. The query structure must be bypassed using the filter's weaknesses.
3.	Because Round 1 filtered the OR keyword, we used the SQL comment operator to eliminate the password check.
4.	Inject ' -- into the username field to close the initial quote and comment out the rest of the query.
5.	Because Round 2 blocked the comment operator (--) and the equals sign (=), the simple quote closure was sufficient.
6.	Inject ' into the username field; this satisfies the first condition and terminates the string, bypassing the remaining, now unnecessary, query logic.
7.	Because Round 3 added filters for more comparison operators (<, >), no new action was necessary.
8.	The prior simple quote-closing bypass already avoided these characters.
9.	Because Round 4 blocked the literal string admin, a more complex injection was required.
10.	We switched strategy to use a UNION SELECT to select the desired admin user from the database without naming them explicitly.
11.	Because the system filtered spaces, the UNION SELECT statement could not be written normally.
12.	Replace all spaces in the SQL statement with the SQL block comment /**/ to satisfy the parser while bypassing the filter.
13.	To complete the Round 4 injection, inject the payload '/**/union/**/select/**/1/**/from/**/users/**/limit/**/1-- (using a dummy username like 'bob').
14.	This forces the database to combine the dummy login with the first user result, which is assumed to be admin.
15.	Because Round 5 blocked the UNION keyword, the previous strategy was rendered useless.
16.	We must find a way to make the final username equal to "admin" without typing it.
17.	To bypass the literal string filter, use the SQL string concatenation operator (`
18.	To achieve the final successful login, the concatenation successfully tricks the query into searching for username = 'admin', completing the challenge.


*Flag:*   picoCTF{y0u_m4d3_1t275cea1159781d5b3ef3f57e70be664a}

## Concepts Leant:
Bypassing SQL FIlters.

## Notes:
None as such.
