I do machine learning (ML) for a living, but I've never applied it to my everyday life. I sold my car when moving to the Bay Area so now I use buses for my commute to work and to get to and from San Francisco. I rarely have better than a 15 minute window of when I think I'll arrive because bus schedules don't often hold up to reality. We can use machine learning to change that.

Read more...

# Prerequisites

## Data

All ML learning models need data. There's no getting around it. So it will take some investment on my part before I start seeing any kind of return. The most obvious type of data I can take is time. I'm not going to dedicate my entire hour of commute both ways to collecting data. What I am willing to do is take note of the time when I arrive at stops. The bus makes a loud sound as the doors open that'll catch my attention.

My morning commute isn't particularly interesting - I've got no stops between where I'm picked up and where I get off:

- Depart: 8:05 AM
- Arrive: 8:57 AM

It will make an easily digestible case - if there's something wrong with my ML model it'll show up there first.

My evening commute is more interesting. There are four intermediate stops:

- Depart: 4:17 PM
- A: 4:20 PM
- B: 4:24 PM
- C: 5:21 PM
- D: 5:26 PM
- Arrive: 5:36 PM

From past experience stop C is really closer to 5:11 PM and on average I arrive just a bit before 5:36 PM. I'd like to know when stopping at C within a couple minutes of when I should arrive.

## Model

Data isn't any good unless there's some way to interpret it. Most ML models require more than a few data points, but there are some statistical methods I can use to analyze the data until I've got more. Next week I'll have four data points to play around with. I'll see what I can do with them.