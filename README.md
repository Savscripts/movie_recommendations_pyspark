**BUAN 5315 02 Big Data Analysis Date: June 10, 2025**

**Savgun Kaur**

**Business Proposal Name**-  Personalized Recommendation Engine 

**Project URL -**
<https://www.codementor.io/@jadianes/building-a-recommender-with-apache-spark-python-example-app-part1-du1083qbw>

## Introduction:

A movie review-aggregation project was developed to enhance
user engagement and retention through personalized recommendations. The
project implements a collaborative filtering engine that generates
individualized movie suggestions based on user behavior patterns.


Inspired by the success of recommendation systems in major streaming
platforms, the project evaluates whether this system can deliver
similar benefits. Specifically, the goal is to assess how well
collaborative filtering adapts to different user profiles and how rating
thresholds (≥25 vs. ≥100) impact the quality and stability of
recommendations.

This evaluation involves analyzing the system's performance across two
users under two scenarios. The focus is on understanding how
personalization affects user satisfaction, content discovery, and
long-term retention

**Technical Details:**

This project uses **Apache Spark MLlib\'s ALS (Alternating Least
Squares)** to build a scalable movie recommendation system. Spark
enables efficient processing of the 27M+ ratings in the MovieLens Full
dataset.

To improve performance, the following tasks were pre-computed:

-   Loaded and parsed raw data into RDDs

-   Persisted RDDs for reuse

-   Trained the ALS model on the complete dataset

-   Saved the model for future recommendations without retraining

**Key ALS Parameters**:

-   rank: Latent features learned (e.g., 10--20)

-   iterations: Optimization rounds (typically 10)

-   lambda: Regularization to prevent overfitting

-   numBlocks: Controls parallelism (set to -1 for auto)

-   implicitPrefs: False (explicit rating data used)

The model was tested with new users under two filtering thresholds (≥25
and ≥100 ratings), using predictAll() to generate personalized
recommendations.

**Debugging Details**:

Several challenges were encountered and resolved during the project:

1.  Replaced urllib.urlretrieve with urllib.request.urlretrieve (Python
    3 compatibility)

2.  Updated print statements from Python 2 to Python 3

3.  Modified recommendation output to return top 15 instead of default
    25

4.  Fixed incorrect seed format (seed=0L to seed=0)

5.  Restarted Jupyter kernel after prediction issues for new users

6.  Added logic to delete model directory before saving if it already
    exists (to avoid overwrite errors)

**Achievements**:

-   Trained and evaluated four test cases across two scenarios using
    full MovieLens dataset

-   Integrated new user ratings seamlessly into model flow

**Key features of coding practices in this project**

-   **Scenario-Driven Testing Support**:\
    Additional logic was added to simulate real user behavior via custom
    ratings for two profiles. The model was retrained for each scenario,
    enabling controlled evaluation of personalization outcomes.

-   **Efficient Data Handling with Spark**:\
    The dataset was parsed and cached early in the process to minimize
    re-computation. Filtering logic ensured models only used relevant
    movie subsets based on rating count thresholds.

-   **Clarity and Maintainability**:\
    Code sections were clearly labeled and logically ordered -
    supporting reproducibility, adaptation, and seamless collaboration
    with business stakeholders

**Results:**

Four test cases were run:

**User 1 rated following movies:**

1.  (0,147542,4), \# Terminal (1996)

2.  (0,207313,1.5), \# Knives Out (2019)

3.  (0,220104,1.5), \# Drive (2019)

4.  (0,78039,1.5), \# Blue Valentine (2010)

5.  (0,45720,4), \# Devil Wears Prada, The (2006)

6.  (0,109487,4.5), \# Interstellar (2014)

7.  (0,134130,4.5), \# The Martian (2015)

8.  (0,116797,4.5), \# The Imitation Game (2014)

9.  (0,106002,3.5), \# Ender\'s Game (2013)

10. (0,192283,4), \# Crazy Rich Asians (2018)

-   **Scenario 1 (≥25 ratings) Results of User 1**

> TOP 15 recommended movies (with more than 25 reviews):

1.  (\'Mower Minions (2016)\', 4.4931411311453235, 42)

2.  (\'Flywheel (2003)\', 4.428797085077275, 31)

3.  (\'Fireproof (2008)\', 4.390744448603254, 264)

4.  (\'One Piece Film: GOLD (2016)\', 4.369903352972412, 42)

5.  (\'The Bible (2013)\', 4.369476398401672, 31)

6.  (\'Scusa ma ti chiamo amore (2008)\', 4.328424174781761, 39)

7.  (\'Minions: Orientation Day (2010)\', 4.325486897298378, 37)

8.  (\'One Piece: Stampede (2019)\', 4.274530072848607, 34)

9.  (\'Detective Conan: The Last Wizard of the Century (1999)\',
    4.264817454298781, 34)

10. (\'What a Beautiful Day (2011)\', 4.2519894353765135, 31)

11. (\'Facing the Giants (2006)\', 4.232164443918677, 204)

12. (\'Pollyanna (2003)\', 4.225019597916236, 33)

13. (\'Naruto Shippuden the Movie: Blood Prison (2011)\',
    4.22116338807817, 38)

14. (\'Minions: Banana (2010)\', 4.2173592576965735, 40)

15. (\'Shaadi Mein Zaroor Aana (2017)\', 4.212495911939958, 26)

-   **Scenario 2 (≥100 ratings) results of User 1**

> TOP 15 recommended movies (with more than 100 reviews):

1.  (\'Fireproof (2008)\', 4.390744448603254, 264)

2.  (\'Facing the Giants (2006)\', 4.232164443918677, 204)

3.  (\'Courageous (2011)\', 4.2023301615978115, 200)

4.  (\'Avengers: Infinity War - Part II (2019)\', 4.197911537965097,
    12845)

5.  (\'\"Ultimate Gift\', 4.1687549218220035, 316)

6.  (\'War Room (2015)\', 4.165887898819111, 108)

7.  (\'Avengers: Infinity War - Part I (2018)\', 4.136460675181281,
    16164)

8.  (\'Harry Potter and the Deathly Hallows: Part 2 (2011)\',
    4.096396917785892, 20837)

9.  (\'\"Avengers\', 4.062085288448504, 27495)

10. (\'Harry Potter and the Deathly Hallows: Part 1 (2010)\',
    4.061989039886199, 21781)

11. (\'Gifted Hands: The Ben Carson Story (2009)\', 4.056997781405625,
    153)

12. (\'Harry Potter and the Half-Blood Prince (2009)\',
    4.050700826355267, 21849)

13. (\'Harry Potter and the Order of the Phoenix (2007)\',
    4.03624641206706, 21900)

14. (\'Miracles from Heaven (2016)\', 4.031550934628362, 107)

15. (\'Kung Fu Panda: Secrets of the Masters (2011)\',
    4.028337015274499, 134)

**User 2 rated following movies:**

-   (0,103228,4), \# Pacific Rim (2013)

-   (0,115149,4.5), \# John Wick (2014)

-   (0,7454,3.5), \# Van Helsing (2004)

-   (0,84152,4.5), \# Limitless (2011)

-   (0,122916,4.5), \# Thor: Ragnarok (2017)

-   (0,201773,4), \# Spider-Man: Far from Home (2019)

-   (0,274053,5), \# Top Gun: Maverick (2022)

-   (0,177765,5), \# Coco (2017)

-   (0,72378,4), \# 2012 (2009)

-   (0,59315,4.5), \# Iron Man (2008)

-   **Scenario 1 (≥25 ratings) results of user 2**

> TOP 15 recommended movies (with more than 25 reviews):

-   (\'Band of Brothers (2001)\', 5.068602905238924, 2835)

-   (\'Planet Earth II (2016)\', 5.020846141996181, 2041)

-   (\'Planet Earth (2006)\', 5.015570009897525, 3015)

-   (\'\"Shawshank Redemption\', 5.004293973400436, 122296)

-   (\'Cosmos: A Spacetime Odissey\', 4.9976465599722655, 599)

-   (\'His Last Vow\', 4.941830866446576, 41)

-   (\'Three Men and a Leg (1997)\', 4.934922527691409, 29)

-   (\'Firefly (2002)\', 4.894696099539658, 895)

-   (\'Attack On Titan (2013)\', 4.8937120159325325, 263)

-   (\'Violet Evergarden: The Movie (2020)\', 4.88186981898267, 25)

-   (\'Spider-Man: Across the Spider-Verse (2023)\', 4.88018285501334,
    528)

-   (\'Twelve Angry Men (1954)\', 4.879578967336652, 332)

-   (\'Blue Planet II (2017)\', 4.879547543127085, 1267)

-   (\'Hornblower: The Even Chance (1998)\', 4.876003085797272, 33)

-   (\'Indictment: The McMartin Trial (1995)\', 4.874707446784466, 29)

-   **Scenario 2 (≥100 ratings) results of user 2**

> TOP 15 recommended movies (with more than 100 reviews):

-   (\'Band of Brothers (2001)\', 5.068602905238924, 2835)

-   (\'Planet Earth II (2016)\', 5.020846141996181, 2041)

-   (\'Planet Earth (2006)\', 5.015570009897525, 3015)

-   (\'\"Shawshank Redemption\', 5.004293973400436, 122296)

-   (\'Cosmos: A Spacetime Odissey\', 4.9976465599722655, 599)

-   (\'Firefly (2002)\', 4.894696099539658, 895)

-   (\'Attack On Titan (2013)\', 4.8937120159325325, 263)

-   (\'Spider-Man: Across the Spider-Verse (2023)\', 4.88018285501334,
    528)

-   (\'Twelve Angry Men (1954)\', 4.879578967336652, 332)

-   (\'Blue Planet II (2017)\', 4.879547543127085, 1267)

-   (\'Death Note: Desu nôto (2006--2007)\', 4.866705942701085, 509)

-   (\'The Rescue (2021)\', 4.856851050392313, 141)

-   (\'Human Planet (2011)\', 4.831120341250505, 498)

-   (\'Cosmos\', 4.828845388084188, 625)

-   (\'The Blue Planet (2001)\', 4.820387703031483, 1080)

**Key observations:**

-   **User 1 - Scenario 1A (\>= 25 Ratings)** The model surfaced niche
    and family-focused titles with strong emotional tones and moderate
    popularity:

```{=html}
<!-- -->
```
-   Mower Minions (2016), Flywheel (2003), Fireproof (2008)

-   One Piece anime films, The Bible (2013), Scusa ma ti chiamo amore
    > (2008)

```{=html}
<!-- -->
```
-   **User 1 - Scenario 1B (\>= 100 Ratings)** The recommendations
    leaned heavily on widely popular titles:

```{=html}
<!-- -->
```
-   Fireproof (2008), Facing the Giants (2006), Courageous (2011)

-   Avengers series, Harry Potter series, Ultimate Gift (2006)

**Interpretations:**

#### **Filtering Thresholds Shape the Recommendation Experience**

-   A broader threshold (≥25 ratings) surfaced niche, lesser-known
    > content resulting in expanding user discovery.

-   A stricter threshold (≥100 ratings) led to mainstream,
    > high-confidence suggestions, boosting trust and satisfaction.

#### **Personalization Works with Minimal Data**

-   Even with just 10 initial ratings, the model generated distinct,
    > tailored recommendations for each user.

#### **User Preferences Are Accurately Captured**

-   Each user's recommendations aligned well with their known tastes
    > like user 1 preferences matched emotional sci-fi while user 2
    > preferences leaned towards action-packed visuals.

#### **Scenario Flexibility Supports Different Engagement Goals**

-   Scenario 1 promoted content discovery, good for long-term
    > engagement.

-   Scenario 2 reinforced user confidence, ideal for onboarding or
    > retention.

#### **Consistency for Mainstream Preferences**

-   As seen with User 2, who favors popular, high-engagement content,
    > the top picks under both filters (≥25 and ≥100 ratings) overlapped
    > significantly.

### **Insights:**

-   The engine's ability to recommend highly relevant but unexpected
    > content (e.g., anime for a drama lover) creates a competitive
    > edge.

-   ALS-based collaborative filtering is effective even in cold-start
    > conditions.

-   Recommendation system moves beyond generic trending lists, it learns
    > individual behavior.

-   Recommendation system can strategically balance novelty and reliability
    > depending on user context.

-   The system can be flexible based on strategic platform goals:
    > explore vs. retain.

-   Recommendation system successfully models nuanced taste profiles.

-   Recommendation system's consistency for recommendations in mainstream
    > preferences builds trust and confirms that the recommendation
    > engine is stable and predictable when user preferences align with
    > widely rated content.

**Future Recommendations & Actionable Items**:

-   Add explainability (e.g., "Because you liked...") to improve
    > transparency.

-   Integrate implicit signals (e.g., watch time, clicks) for real-time
    > feedback.

-   Run A/B tests on filter settings to optimize engagement and
    > satisfaction.

-   Track user journeys to personalize discovery and retention
    > strategies.

**References:**

-   Collaborative filtering - RDD-based API. Collaborative Filtering -
    RDD-based API - Spark 4.0.0 Documentation. (n.d.).
    <https://spark.apache.org/docs/latest/mllib-collaborative-filtering.html>

-   Matrix factorization techniques for Recommender Systems \| Computer.
    (n.d.-d). <https://dl.acm.org/doi/10.1109/MC.2009.263>

-   Dianes, J. A. (n.d.). *Building a movie recommendation service with
    Apache Spark & Flask - Part 1*. Codementor.
    <https://www.codementor.io/@jadianes/building-a-recommender-with-apache-spark-python-example-app-part1-du1083qbw>

-   *Non-commercial, personalized movie recommendations.* MovieLens.
    (n.d.). <https://movielens.org/>

**Appendix**:

MovieLens Dataset Fields

1.  **ratings.csv** -- userId, movieId, rating, timestamp

2.  **movies.csv** -- movieId, title, genres

ALS model training parameters

1.  seed = 5

2.  iterations = 10

3.  regularization_parameter = 0.1

4.  ranks = 4

5.  tolerance = 0.02
