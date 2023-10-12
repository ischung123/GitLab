# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

### Sources:
1. https://initialcommit.com/blog/git-mv --> Used for learning how to rename git files using git mv
2. https://www.simplilearn.com/what-is-git-rebase-command-article#:~:text=BootcampExplore%20Program-,What%20Does%20Git%20Rebase%20Do%3F,it%20to%20the%20specified%20base.
Used for learning how git rebase works.

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)

Answer: 9b257

2. What is the SHA for the last commit associated with line 9 of this file?

Answer: b2ed3

3. What did line 12 of this file say in commit d1d83?

Answer: I should really finish writing this.

4. What changed between commit e474c and 82045?

Answer: gross_sort changed from gross_sort = lambda x : x["Gross"] to gross_sort = lambda x : int(x["Gross]).
We also see that top_five changed from top_five = rows[:-5:-1] to rows[:-6:-1].

## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N
```

Answer: Executing these commands will make it so that the changes in the branch top_N will be
applied to the test branch. However, the top_N branch will be unaltered. Hence, only the test
branch would change (by receiving the changes made in the top_N branch) while the top_N branch
remains unchanged.


6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```

Answer: The answer is pretty similar to Question 6 where the changes in the branch test will be applied to the 
top_ten branch. This will leave the test branch unaltered. Hence, only the top_ten branch would change (by 
receiving the changes made in the test branch) while the test branch remains unchanged.


7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```

Answer: Since we are using rebase, the commit history of the test branch will change to incorporate the commits from the
top_ten and top_N branches. The top_ten and top_N branches will not be altered. However, there will be a merge conflict when 
performing the two rebase commands! During the first rebase, git didn't know which lines should be kept and which lines shouldn't
 as we didn't add a specifier. This caused git to throw an error. Hence, the second rebase command didn't work either. 
