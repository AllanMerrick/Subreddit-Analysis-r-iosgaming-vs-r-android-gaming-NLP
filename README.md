### Project 3 - Subreddit Analysis: r/iosgaming vs r/androidgaming

#### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Model Score Summaries](#Model-Score-Summaries)
- [Sources](#Sources)

#### Problem Statement
##### r/androidgaming vs r/iosgaming
There is a constant divide between availability of ios games vs android gaming, however, there is a larger overlap of games that support both systems. Our game development company is, unfortunately, unable to develop for both platforms. As an independant company, we'd like to focus on community culture and release our game for that community first. However, we've found gamers are polarizing in hardware, software, and company support. We'd like to release to the community that appeals to our culture first, but plan for release to the other market.


We will look into posts from both subreddits to find trends and inferences that separate the two crowds. Once identified we can begin looking into methods and verbiage that identifies our target market without alienating the other.


#### Executive Summary
Despite gamer trends of polarizing identification preferences and company support, we found users of both r/iosgaming and r/android were harder to tell apart from scratch.

Our model trained and test scored with 99% accuracy opening up the resource of word and language trends between the two subreddits. With mroe time and research we can explore communication and community outreach practices that do not alienate either market as well as post-trends we can associate to game-types and releases.

With limited funding, our North American based game development company will look to release to the larger Android gaming market utilizing it's lower barrier of entry for game release and larger global popularity. As we found both subreddits to share both similar posting rules and have an overlapping game market, we are interested in utilizing further model findings within our Advertising team.

#### Data Dictionary
***Dataframes:***
- `df` : our full scrape of 1000 post pulls, looped 100 times. Total 36,200 submissions.
- `traindf` : temp dataframe variable created for cleaning
- `subsdf` : data frame of posts after being cleaned, with target categories 50/50 split
 - target column created: `'is_iosgaming'
    - r/iosgaming = 1
    - r/androidgaming = 0
- `droid_df` : temp android gaming-only subreddits we sampled from our scrape to match quantity of iosgaming posts
- `ios_df` : df of all r/iosgaming posts
- `testdf` : new data pulled for testing our model on.    

***Features, variables, and lists:***
- `date_time` : string format of date for epoch conversion.
- `pattern` : string format of date pattern conversion
- `epoch_start` : January 1st, 2020, we converted this date to an epoch as our starting date for post scraping
- `epoch_end` : April 1st, 2020, we converted this date to an epoch for 4 month scrape. Pushshift api handled a webscrape of post size over date range.
    - ultimately this was not used
- `base_url` : string of url to pusshift api on reddit submissions
- `subreddit` : list of our subreddits as a string
- `epoc` : manual entry of epoch_start integers
- `punct`, `extra_stops`, `stops` : list and list comprehension to build stopwords from stopwords library 'english'
    - included additional: punctuation, terms and symbols that initial stoplist missed
- `ios_list`, `ios_raw`, `ios_clean`, `ios_freq` : masks for lists and tokens generated for frequency comparison
- `droid_list`, `droid_raw`, `droid_clean`, `droid_freq` : masks for lists and tokens generated for frequency comparison
- `X, y, and variants` : These are our regression feature and variable assignments. code blocks will contain descriptions of each.

***Modeling***
- `Pipeline`, `GridsearchCV`, `DenseTransformer` : hyper parameter classes for transforming our features
- `KNeighborsClassifier`, `LogisticRegression`, `GaussianNB` : regression models selected for research
- `cvec` : temporary instance of CountVectorizer
- `tvec` : temporary instance of TfidfVectorizer
- `pipe` : pipeline mask instance for transformers and predictors
- `pipe_params` : dict format of hyperparameters we test in each model
- `gs` : mask for gridsearch
- `best_@@@` : iteration of our saved best estimator parameters for each model


***Functions***
- `reddit_posts`
- `freq_table`
- `freq_compare`

***Datasets***
- `subredditposts_table.csv` : raw scrape of posts; (36200, 4) shape
- `subs.csv` : data frame of posts after being cleaned
 - target converted into binary column `'is_iosgaming'` where ios_gaming subreddit = 1, droid = 0




#### Conclusions and Recommendations
We found both subreddits shared similar game interest, verbiage, and common posting habits. Our model scored over 99% on both our training and test sets. We then applied the model to new posts pulled from half a year earlier, the model scored over a 99% accuracy on the new data.

Using these parameters we can further explore common natural language trends.

Android gaming(Google PlayStore included) entry requirements and game upkeep are much less demanding than Apple. Apple is nefarious for it's strict update reviews, game release filters, and family-appropriate approach to game-content (mostly).

Currently, our model will allow us to dive deeper into the language culture of each market. For now, app management, release requirements, and Apple's high-priced products that support ios is what attracts and detracts users. Android gaming, with its wide-range of hardware support, larger quantity of game releases (good and bad), and lax development release process opens us to: more players, easier development response time.

With more time and research, we will explore our model to align our advertising and community outreach with the brand and culture we are trying to establish with our first release.

#### Sources
- [IOS Gaming Subreddit](#https://www.reddit.com/r/iosgaming/)
- [Android Gaming Subreddit](#https://www.reddit.com/r/androidgaming/)
- [Android vs iOS: Which Platform to Build Your App for First?](#https://themanifest.com/mobile-apps/android-vs-ios-which-platform-build-your-app-first)
- [iOS App Users are Spending More...](#https://www.businessinsider.com/ios-app-users-are-spending-more-2017-5)
