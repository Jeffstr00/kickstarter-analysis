# Kickstarting with Excel

## Overview/Purpose of Project

Louise is a brand new playwright who is looking to launch her very first play, *Fever*.  She plans to use Kickstarter to raise the more than $10,000 she projects this to cost, so she is understandably nervous.  We used Microsoft Excel to analyze thousands of Kickstarter campaigns to see how likely she would be to succeed and if there was anything she could do in order to improve her liklihood of success.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

We decided to break down the data to see if when a Kickstarter was launched played a role in its liklihood of success.  We first filtered the data to just look at theater projects since that is what Louise is dealing with.  We took the start date, which was given as an Epoch timestamp, and converted it to a more readable date using the function:`=(((Ji/60)/60)/24)+DATE(1970,1,1)`.  A pivotable was created which filtered the results into outcomes by month, and from this a chart was made in order to make it easily viewed and understood by humans.

### Analysis of Outcomes Based on Goals

We also decided to look at the success rate of campaigns based on the size of the project's goal.  First of all, it might not make much sense to compare her $10,000 project to one with a budget 100 times its size, and also she might want to consider altering how much money to ask for depending on how it might impact its outcome.  We broke goals down into $5,000 increments and then counted how many plays of each bunch were successful, failed, or canceled using the following COUNTIF function: `=COUNTIFS(Kickstarter!$D:$D, "<1000",Kickstarter!$F:$F, "successful",Kickstarter!$R:$R, "plays")`.

### Challenges and Difficulties Encountered

One challenge we faced was that the dates were given in an accurate (but difficult to deal with) Epoch timestamp.  However, we were able to convert that to a stardard time format by using the aformentioned conversion function.  From there, we were able to put that data into a table where it could be sorted and displayed via months and years.

While it ended up not being a problem, it seemed suspicious that plays had 0% canceled for every single block of goals.  It seemed like some sort of mistake was made, but I manually looked through the data and it turned out to be accurate.

Finally, when I initially created the Outcomes Based on Goal table, it included data from all of the different genres of Kickstarters.  Since we just wanted to focus in on plays, I added `Kickstarter!$R:$R, "plays"` to each COUNTIF function in the table, which filtered out all of the other type which were not relevant to us.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

IMAGE

In order to maximize her success, if possible, she should start her campaign in May or June, as these months have a roughly 2:1 success rate, which is clearly better than what is found at any other time of year.  On the other end of the spectrum, she should do whatever she could to avoid kicking things off at the end of the year.  Whether it's because people are focused on the holidays, other charities, or something else entirely, the success rate plummets during this time.  The absolute worst is in December, the only month to have a higher chance of failure/cancellation than success.

- What can you conclude about the Outcomes based on Goals?

![Outcomes vs Goals](https://github.com/Jeffstr00/kickstarter-analysis/blob/main/Outcomes_vs_Goals.png)

Just going off of the size of her ask and comparing it to other campaigns in the same $10-15k ballpark, it seems more likely than not that her project will succeed, but only barely so.  While this is only mildly optimistic, it seems that she is positioned in a decent spot.  Projects with $15k+ budgets no longer are more likely to succeed than not (ignoring the $30-40k range with very small sample sizes), so asking for more money means that her project is more likely to fail.  While asking for less money would increase her odds of success, the $5-10k bracket is barely more successful than the $10-15k group in which she currently resides.  Unless she could cut her budget all the way down under $5,000, it's unlikely that she would see a worthwhile increase in success.

- What are some limitations of this dataset?

As good and as thorough as this dataset may be, it still clearly has limitations.  Many factors go into determining whether or not a campaign will be successful that are not (and realistically could not be) included in this data.  Plays produced by more established playwrights would seemingly find more success than those by first-timers like Louise.  While $100,000 might be an outrageous ask for someone like Louise, that might be more reasonable for a play that will feature a Hollywood star like Daniel Radcliffe or Usher.  It also doesn't take into account how good the push behind the Kickstarter will be or good the idea itself is.

- What are some other possible tables and/or graphs that we could create?

Further analysis might want to look at how successful plays are that end up being Staff Picks vs those that aren't and ones in the Spotlight vs ones that aren't.  Unless she has reason to believe that her play will receive those boosts, it might not be a good idea to compare hers versus ones that have benefitted from it.  Also, it might be a good idea to create a table and chart to show how success is influenced by average donation size.  Some plays might aim to offer big rewards to substantial backers while others might take a more grassroots approach and try to secure a higher number of smaller donations.
