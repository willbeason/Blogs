So I found a data set that I'll find interesting. I'd like to optimize how quickly I can make changes to the Google codebase. I'll have to ask internally about the extent of the information I'll be able to share on this project, but here's my plan. If I'm lucky, I may be able to share my anonymized data and data analysis code.

Read more...

# The Problem

As a software developer, my productivity at Google is tied to how quickly I can make changes to the codebase (also called changelists or CLs). The general process is:

Find some change(s) which needs to be made.
Make the change(s)
Get code reviewed by a peer. If changes are suggested, go to 2.
Submit the code.
The biggest holdup for me is 3. Fortunately, at Google, we've got excellent tools for this so the actual reviewing is painless. Reviews do take time, and not only are people faster to review smaller changes, they are faster to *begin reviewing* smaller changes. Suppose it takes 20 minutes to review a change of 50 lines and 40 minutes to review a change of 100 lines. The reviewer will likely take several hours longer to even look at the change with 100 lines than the 50 line one. If this holds, then I can more quickly change 100 lines of code by submitting two 50-line CLs.

# The Data

The data I'll initially be using for my models have an asterisk next to them. My goal is to maximize (# of changed lines) / (time to review). So if it on average takes 5 hours to submit a 100 line CL, 2 hours for 50, and 1 hour for 20, I'll go for the 2 hours for 50 lines.

## Input

Almost none of these inputs have to be manually collected by me - it will be easy enough to write a script to collect/calculate the data. At first I'll only consider number of changed lines as a predictor of how long it takes the CL to be submitted.

### *Number of changed lines

The first input variable I'll be manipulating. This is the number of lines added, modified, or deleted. Fortunately this is already calculated for me by Google's internal code review stuff. Eventually this will split into the three components - additions, changes, and deletions since I imagine it's much easier to review a CL that is 500 deletions and 100 additions than 100 deletions and 500 additions.

### Displayed CL size

This will be important since it is what the code reviewer sees before anything else - the category of how large the CL is. These are represented as T-shirt sizes: XS, S, M, L, XL. I'll probably make this a discrete variable with five possible values rather than five binary variables because the effects on the outputs should be consistent (time to code submission will probably strictly increase depending on size category).

### Time and day of review request

Another input I won't initially include. People may be more likely to review code on certain days or at certain times of day. I can adapt my schedule around my findings. I imagine this will tie in well with the next variable.

### Reviewer

At some point, when I collect much more data, I'll create models for each person I commonly have review my code. I can only speculate for now - but I bet there will be clusters or some way of reducing the information required to represent the individual models.

### Submitter

It shouldn't be difficult for me to also collect data and create models for how other people write and review code. Much later down the line, I may be able to create individual models for how each person reviews each other person's code.

## Outputs

I'll initially only be trying to predict how long it takes my CLs to be submitted to the Google codebase.

### *Worked time until submission

I work about 8-9 hours between 8am and 5pm each day. For simplicity, I'll say each work day is 9 hours long and only count time during those hours towards this variable. So If I submit a CL on Friday at 4pm and it is first reviewed on Tuesday at 10am, I will count it as 12 hours. (1 hour Friday, 9 hours Monday, 2 hours Tuesday).

### Worked time until first response

Nearly as important to minimize as the above. The first response is rarely that the code should be submitted as-is and indicates that my CL has been looked over, but it means that the reviewer has looked at the code. Odds are, the lower I get this, the lower the time it takes to submit a CL.

### The Model

To make this easy on myself, I'll start with a Bayesian model and see where it takes me. Hopefully, more to follow once I've gotten guidance on this project.