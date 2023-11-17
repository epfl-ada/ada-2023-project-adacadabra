# Project : Decoding YouTube's Collaboration Web
Team : ADAcadabra
Team members : Lou De Bel-Air, Jiacheng Yang, Mats Hansen Frydenberg
Dataset : [YouNiverse](​​https://zenodo.org/records/4650046)

## Abstract
Ever wondered about the dynamics of channel popularity on YouTube?

Our study aims to explore the role of collaboration in boosting channel growth and revealing the intricate network of YouTube creators. Our goal is to offer a perspective on YouTube's collaborative landscape, equipping creators with insights to foster collaborations that align with evolving viewer trends.

Leveraging the 'YouNiverse' dataset, we will analyze video metadata and descriptions to find collaborations and channel mentions. We will use viewer engagement metrics like views and likes to gauge the immediate and lasting impacts of these collaborations. What is the difference before/after collaborations? We are interested in whether collaborations spur growth and, if so, whether partnering with top channels in the same or different categories is more beneficial.

Our study period is 2016-2019. We are focusing on categories like gaming, how-to-style, and people and blogs, where real interactions and collaborations are most evident.


## Research questions 
1. Is there a difference in popularity between collaborating and non-collaborating channels? Is there a correlation between video frequency and views/subscriptions that could potentially bias the study?
2. How are YouTube channels interconnected, and what does this connectivity indicate about their influence and reach? 
3. How long do most popular channels stay at the top? When in the life of a channel do most collaborations happen? 
4. What is happening before and after collaborations? Is the number of viewers increasing? Can collaborations prolong the life of a channel?
5. Do collaborations within and outside of a category influence channels differently than collaborations within the same category?
6. Is there a correlation between the number of subscribers of collaborators and the number of subscribers a channel gains after a collaboration?

## Methods 
We use a dataset that includes data on YouTube channels and videos. This dataset includes channel statistics, chronological data on views and subscribers, and video metadata. We will focus first on channels in the Gaming category, then analyze the How-To and People & Blogs categories.
The first step is the preprocessing, which consists in ensuring that all datasets (channel, timeseries and metadata) are properly aligned in terms of time frames. The data needs to be cleaned to handle missing values, outliers, and any anomalies.  


**Collaboration Impact Analysis:**

We will evaluate the impact of collaborations on channel metrics such as views, subscribers and number of videos. First, we need to filter collaborators in the Gaming category, using link templates in the description and identifying the channel's link types:
1.          youtube.com/channel/youtubecreators
2.          youtube.com/@youtubecreators
3.          youtube.com/c/YouTubeCreators
4.          youtube.com/user/YouTube

We know that for URL 1) and 4) we can find the channel ID whereas in URL 2) and 3) we will find the channel names. Then channels are categorized into collaborators and non-collaborators based on their mention of other channels.

We will then do a comparison of popularity between people that collaborate and people who do not with t-tests (either Welch's t-test (insensitive to variance) or the Mann-Whitny U-test (non-parametric)). We will analyses the ten channels with the highest number of subscribers relative to the others to determine whether the differences in number of subscribers are significant for a greater number of collaborations. Plot the collaboration and non-collaboration graphs, with distribution graphs to examine skewness.


**Correlation between video frequency and views/subscribers?**

We will use visualizations, such as scatter plots, to initially assess the relationship between the number of videos posted and channel views/subscriptions. Then we will calculate the basic statistics, examine the correlation, using Pearson's correlation coefficient. 
Is there a cause-and-effect relationship?  To answer this question we plan to examine linear regression to see how changes in video quantity affect views and subscribers.  When analyzing the top ten subscribers, we will use effect size measures (such as Cohen's) to understand the practical significance of differences, not just statistical significance.


**Network Analysis within Gaming Category:**

We plan to identify key influencers and collaboration patterns in the Gaming category. The objective is to construct a network graph representing channels as nodes and collaborations as edges.
Then we will determine centrality measures to identify influential channels and analyze the frequency and scope of collaborations. To identify influential nodes and sub-networks in the games category we can use graph-theoretic measures (Louvain Community Detection). Visualization can be done through the application of NetworkX.

Sources: 
- https://memgraph.com/blog/community-detection-algorithms-with-python-networkx
- https://towardsdatascience.com/community-detection-algorithms-9bd8951e7dae


**Channel Lifecycle and Collaboration Timing:** 

Our aim here is to understand a channel's lifecycle and identify when collaborations are most frequent. We can start by finding channels in 2016 with a low number of views/subscriptions, then follow them over a time series to see their growth, and those that are left behind.
To this end, we will plot the evolution of the channels over time and identify the different phases (growth, plateau, decline). 
When the maximum number of views reaches a plateau, we can examine the normal duration of this plateau. We will have to find the outliers, first plot and look at the distribution, then gather the top ten quartiles and see if they collaborated more than the others, had more videos etc.
We plan to use Kaplan-Meier curves to estimate the survival function of a channel's 'top' status. 
[Source](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3932959/)

If the data distribution is normal we can compare growth rates using a paired-samples t-test. If it is not, we can instead consider a non-parametric alternative such as the [Wilcoxon signed-rank test](https://en.wikipedia.org/wiki/Wilcoxon_signed-rank_test).


**Effect of Collaborations on Channel Growth:**

Here, we will evaluate whether collaborations contribute to faster chain growth, using time series analysis. We will normalize time to collaboration events (t=0), in order to compare growth rates before and after collaborations. Then we will use difference-in-differences analysis, comparing video growth measurements with and without collaborations, from the same channel. Confidence intervals can be used to determine whether post-collaboration growth is statistically significant. 
What happens if chains collaborate with other categories? We need to look at engagement metrics (views, likes, comments) to assess the differences in impact of collaboration. The use of difference-in-differences allows to examine the effect of collaborations within or outside the category. Comparative graphs highlight differences in engagement depending on the type of collaboration.

Next we will look at when collaborations occur in a channel's lifecycle. We will use the lifecycle series previously computed to create interactive graphs showing the evolution of the channel and the timing of collaborations, and to show what happened next.
Finally we will use some channels lifetime to determine whether collaborations can help you grow faster or extend the lifetime at the top? We want to know if there is an increase if channels collaborate with the ten most popular people?

To solve this problem, we need to define the average growth rate, then examine the change after a collaboration, using an asymmetric distribution to test whether the new growth is statistically higher for the channel.

**Correlation between Collaborator's Views/subscribes and Channel's Views:**

We will calculate Pearson's correlation coefficient and run a regression analysis to explore the relationship between contributor views/subscriptions and channel view/subscription gain. We will then try to see if there are other covariates, such as the number of videos published, and we can use the propensity score to understand the different covariates.


## Timeline
17/11 : Final preprocessing, and start of analysis, clear definition of the project 

24/11 : Homework 2

31/11 : Start treating all of the research questions

07/12 : Notebook should be final (all of research questions treated, different methods explored, storyline)

14/12 : Website/article should be finished

21/12 : Week to solve problems if any


## Organization within the team
|          | Lou                     | Jiacheng | Mats |
| -------- | --------------------------------| --| --| 
| 17/11    | Organize the README (Milestone 2)|Organize the notebook  (Milestone 2)| Do some research on the methods we can use | 
| 24/11    |  Homework 2| Homework 2| Homework 2 |
| 31/11    |  Question 1 and 2 (Project)| Question 3 and 4 (Project)| Question 5 and 6 (Project) |
| 07/12    |  Design of the website| Finalize notebook| Define data story |
| 14/12    |  Finish website (design)| Finish website (graphs)| Finish website (data story) |
| 21/12    |  Solve problems / finalization| Solve problems / finalization| Solve problems / finalization |

## Question for the TAs 
How should we define the average growth rate of a channel? Using linear assumption (between to points) or the function of Kaplan-Meier ?





