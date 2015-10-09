# Project description
This is a course project where we build a very simple search engine using bing api and improve the search result by expanding the original query.

# Author
Xiwei Feng (xf2140)
Yihong Dai (yd2300)

# Submit files
src/SimpleSearchEngine.java lib/commons-codec-1.10.jar  lib/json-simple-1.1.1.jar makefile

# Execution instruction
Run "make" to compile java file.
Run "make run" to execute.

# Design description
Use the vector model mentioned in class to tune the weight vector of query with related and unrelated searching results. 

q_{t+1} = \alpha * q_{t} + \beta * \sum_{Relevant}{d} - \gamma * \sum_{irrelevant}{d}

where \alpha = 1, \beta = 0.75, \gamma = 0.15

Add two words with most weights to form a new query every turn.

Calculate the relative position of the newly-added words, where we search around places where newly-added words appear in the related documents with a range of 3 words. Find the most recent word and record its relative position. Vote the results over all relative documents and then insert newly-added words to proper positions to form a new query.

Specifically, we have a initial vector of length n with initial value 0, where n is the length of previous query. If the nearest word appears before the newly-joined word, then add the corresponding value in the vector by 1. If it is behind, then decrease by 1. If such a word doesn't exist, then do nothing. For each newly-joined word, pick the word with largest absolute value as its neighbour word and insert to the proper position according to its corresponding value in the vector. 

# Bing Search Account Key
hOVysMk4Ynb2GSI7COBxmjJf+GXpgKMP0xcy3RpYVY4

# Additional Info
To modify query, account key or accuracy, please modify the corresponding value in makefile. 

Have a good day :)
