# cognitive-offloading-llm
Analyzing how LLM adoption has changed human communication patterns using Reddit data

Cognitive Offloading & LLM Adoption: Evidence from 100,000 Reddit Comments

Akshaya Perni | UC Berkeley | Economics & Molecular Biology, Minor in Data Science
Contact: aperni06@berkeley.edu


Abstract

In this study, I attempted to determine whether the mainstream use of LLMs has led to changes in the pattern of human communication consistent with cognitive offloading – delegating the cognitive burden to an external device – as a psychological phenomenon. This paper uses a dataset of 100,000 Reddit comments made before and after the advent of ChatGPT and employs natural language processing approaches such as sentiment analysis, custom uncertainty lexicon score calculation, and hypothesis testing to detect behavioral traces of cognitive offloading facilitated by artificial intelligence. It turns out that the use of LLMs is associated with a doubling of the number of uncertain statements; there is a 36% increase in the length of the comments with a simultaneous increase in the frequency of help seeking. These findings suggest that LLM adoption is quietly restructuring how people form and express opinions online which is a behavioral shift with implications for decision-making, critical thinking, and the long-term relationship between humans and AI tools.

1. Background & Motivation

1.1 Cognitive Offloading: A Brief Overview

Cognitive offloading means employing tools of either physical or digital nature to lessen the burden on the human brain. This phenomenon originates from the idea of the extended mind theory (Clark & Chalmers, 1998), which states that cognition is not limited to the human brain and expands into the environment through the use of tools and artifacts. Examples of this are when one writes the shopping list to offload his/her memory, uses a calculator for calculations, or uses GPS instead of forming the spatial map himself/herself.

The effects of cognitive offloading on behavior have been scientifically proven. For example, studies about the use of GPS have found decreased involvement of the hippocampus in the process of learning as well as declining in the spatial memory in people who often used it. Studies about Internet searching behavior have proven what has been referred to as the "Google effect," i.e., people tend to remember the location of the needed information rather than the information itself because of the Internet.

1.2 LLMs as a Novel Cognitive Tool

Large Language Models (LLMs) are an entirely new type of cognitive tool compared to what has come before. Unlike a calculator (that performs a limited set of operations) and search engines (that retrieve pre-existing knowledge), LLMs can reason in creative ways, synthesize complicated concepts, provide opinions, write arguments, and even mimic open-ended thinking, something that had until now been the prerogative of human cognition alone. Such a high degree of generality is what allows LLMs to take on cognitive tasks in unprecedented fashion.

Since the release of ChatGPT to the general public in November 2022, LLM adoption has been incredibly swift. In just two months of being released, ChatGPT has acquired 100 million users – faster adoption than any other consumer technology in history. This provides us with a perfect opportunity to perform a "natural experiment" – namely, an unambiguous point in time where a new cognitive tool became available to the masses. If LLM adoption leads to cognitive offloading, this should show up in our data.

1.3 Why Reddit?

Reddit represents a particularly interesting dataset for analyzing natural human-to-human interaction. Unlike Twitter, where posts have character limits, and Facebook, where posts are largely filtered through a social filter, Reddit features lengthy topic-based posts within a huge variety of communities. Moreover, there is a particularly large and lively community of Reddit users who engage in discussion of ChatGPT (r/ChatGPT) that spontaneously formed in response to the launch of the model and currently stands as one of the largest online communities focused on artificial intelligence.


2. Hypotheses

Based on cognitive offloading theory, I expected to find the following patterns in post-LLM Reddit communication compared to pre-LLM communication:

H1: Post-LLM comments will contain significantly more uncertainty and help-seeking language, reflecting a reduced tendency to form and assert independent conclusions.

H2: Post-LLM comments will show evidence of greater verbosity without greater confidence — more words used to ask questions rather than assert opinions.

H3: The emotional landscape of post-LLM discourse will differ from pre-LLM discourse, potentially showing reduced emotional conviction as users defer to AI rather than forming strong personal views.


3. Data & Methods

3.1 Data Sources

Two publicly available Kaggle datasets were used:

Post-LLM dataset: chatgpt-reddit-comments.csv — a collection of 52,416 comments scraped from r/ChatGPT, representing naturalistic discourse from a community of active LLM users in the post-ChatGPT era (2023 onwards).

Pre-LLM dataset: kaggle_RC_2019-05.csv — a broad sample of 1,000,000 Reddit comments from May 2019, representing general Reddit communication more than three years before the public release of ChatGPT.

To ensure a balanced and computationally tractable comparison, 50,000 comments were randomly sampled from each dataset (random seed = 42 for reproducibility), yielding a final analytical dataset of 99,999 comments (one row dropped due to null text).

3.2 Sentiment Analysis

Sentiment scoring was performed using VADER (Valence Aware Dictionary and sEntiment Reasoner), a tool specifically designed for social media text that accounts for capitalization, punctuation emphasis, and negation. Each comment received a compound score between -1 (maximally negative) and +1 (maximally positive).

3.3 Uncertainty Language Scoring

I constructed a custom lexicon of 15 phrases associated with uncertainty and help-seeking behavior — including "should i," "don't know," "help me," "just ask," and "asked chatgpt" — and scored each comment by counting how many appeared in the lowercased text. This approach prioritizes interpretability and direct alignment with the theoretical construct.

3.4 Comment Length & Polarization Analysis

Word count was computed by splitting each comment on whitespace. Strong opinions were defined as comments with an absolute sentiment score ≥ 0.5, and proportions of strong positive, strong negative, and neutral comments were computed by era.

3.5 Statistical Testing

A two-sample independent t-test was used to assess whether the difference in mean uncertainty scores between eras was statistically significant (threshold: p < 0.05).


4. Results

4.1 Uncertainty Language Doubled Post-LLM

The mean uncertainty score in post-LLM comments was 0.043, compared to 0.021 in pre-LLM comments — a 2x increase that was confirmed as statistically significant (p < 0.05). This finding directly supports H1: people in the post-LLM era use significantly more help-seeking and uncertainty language in their online communication.

Word-level analysis revealed that this increase was not driven by any single phrase but was broadly distributed across the lexicon. The largest absolute increases were observed in "don't know" (+~140 comments), "can you" (+~195 comments), "tell me" (+~190 comments), and "just ask" (+~165 comments). Most strikingly, "asked chatgpt" appeared 115 times in post-LLM comments and essentially zero times in pre-LLM comments — representing an entirely new linguistic behavior in which users explicitly reference delegating cognition to an AI system within their own comments.

4.2 More Words, Less Confidence

The average number of words per post-LLM comment was 39.6, while for pre-LLM comments it was 29.1 – an increase of 36%. There was a notable right-skewing trend in the length distribution in the post-LLM period, as there were many more long comments (over 100 words). This result provides partial support for H2 but with some interesting twists: instead of shorter and lazier messages, post-LLM users just write more, but their message length is due to lack of certainty rather than confidence.

4.3 Sentiment: Higher Average, Different Distribution

Average Sentiment was higher in the post-LLM period (0.167 vs 0.078) — most probably because of the enthusiasm inherent to a community that selected itself based on excitement about new technology. What was more informative than the average, though, was the sentiment distribution, since post-LLM comments contained a strikingly higher number of perfectly neutral comments (compound score ≈ 0) than the pre-LLM ones, which were evenly distributed across the emotional range. It means that there was a substantial amount of posts with no emotion at all — something that may be expected when human discussion is substituted by an automated AI search.

4.4 Emotional Polarization: A Bifurcated Landscape

Contrary to Hypothesis 3, the total percentage of strong opinions did not change much between eras (39.1% after LLM vs 39.4% before LLM). But what changed was the nature of these strong opinions – the share of strong positive opinions dropped, but strong negative opinions went up. Instead of homogenizing people into an emotionally sterile discourse, it seems that the introduction of the LLM technology divided people into two camps – the more enthusiastic adopters and the critical skeptics.


5. Discussion

5.1 Interpreting the Findings Through a Behavioral Economics Lens

Combined, these results reveal a pattern of a group at the early stage of cognitive offloading adaptation. The increase in usage of uncertainty language, the clear mention of AI consultation through comments, transactional neutrality, and increased help-seeking verbosity all conform to expectations based on cognitive offloading theory after the introduction of an effective reasoning tool.

The thing about this result that is especially intriguing for behavioral economics is that this effect happens stealthily. The users of these datasets probably did not notice themselves changing their patterns of language use. In the same manner as people using GPS navigation cease developing mental maps unconsciously, people who use LLMs seem to be outsourcing uncertainty resolution unconsciously.

5.2 The Bifurcation Finding

This is where the polarization analysis brings an interesting dimension to the simplistic idea of "AI making people less active." Emotional outbursts did not reduce in number; only their distribution changed. This shows that the use of LLMs is not homogenising human discourse, but rather dividing people into two camps, depending on how they interact with the new technology. On one hand, there are people who actively embrace AI as a cognitive companion, while on the other, people oppose it.

5.3 Limitations

Several important limitations should be noted when interpreting these results:

Selection bias: r/ChatGPT users self-selected into a community based on interest in AI, which likely inflates uncertainty language independent of LLM adoption broadly. A more controlled study would track the same communities before and after LLM adoption.

Subreddit context mismatch: The pre and post-LLM datasets come from different community contexts. Some observed differences may reflect community norms rather than era-level behavioral shifts.

Correlation vs causation: This analysis identifies association, not causation. LLM adoption and changes in uncertainty language may share common causes (e.g. broader cultural shifts, demographic differences between subreddits).

Lexicon limitations: The uncertainty lexicon was constructed theoretically rather than empirically validated. A more rigorous approach would involve human annotation of a sample to validate lexicon performance.


6. Conclusion

The analysis presented here presents some early evidence that the adoption of LLMs is resulting in measurable signs of cognitive offloading in the context of online communication. There has been a doubling of uncertainty expressions, increased verbosity when asking for help, transactional emotional expression, and even the emergence of an entirely new form of linguistic behavior: the explicit reference to seeking advice from AI. All this is occurring stealthily, largely under the radar of the people experiencing the change.

With the continued increase in the capability of LLMs and their integration into our everyday lives, gaining an understanding of the behavioral impacts of LLM adoption is ever more important — not to make arguments about the technology, but rather to be more intentional in using the technology. 

7. Repository Structure

cognitive-offloading-llm/
│
├── Reddit AI Project.ipynb          # Full analysis notebook
├── README.md                        # This file
├── cognitive_offloading_results.png # Main sentiment & uncertainty charts
├── comment_length.png               # Comment length distribution
├── work_breakdown.png               # Word level uncertainty breakdown
└── polarization.png                 # Emotional polarization analysis


8. References & Further Reading

Clark, A., & Chalmers, D. (1998). The extended mind. Analysis, 58(1), 7–19.
Risko, E. F., & Gilbert, S. J. (2016). Cognitive offloading. Trends in Cognitive Sciences, 20(9), 676–688.
Sparrow, B., Liu, J., & Wegner, D. M. (2011). Google effects on memory: Cognitive consequences of having information at our fingertips. Science, 333(6043), 776–778.
Hutto, C., & Gilbert, E. (2014). VADER: A parsimonious rule-based model for sentiment analysis of social media text. ICWSM.
