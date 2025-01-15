The literator uses JavaScript to extract information from your favorite books. Facts such as most used or least used words. 
In addition, it allows for search functionality, allowing a user to search for a specific word and highlight its first instance and frequency. 

To put it simply, I used objects(dictionary, map, ...) in javascript to count uncommon words in the book (skipping 'the', 'or' ...) to display 
some interesting stats. I've included a more detailed explanation below. 

Try it out:
https://juicy-rice.surge.sh/


1) Splitting the text into words:

text.match(/\b\S+\b/g) scans through the entire text once, giving O(n) complexity.
Filtering out stop words (filterStopWords):

Building a common words object is proportional to the number of stop words (a fixed list), which is essentially O(1) in practical terms.
Looping through all n words and checking set membership (commonObj[word]) is O(n), assuming a hash/lookup in O(1).



2) Building the frequency dictionary:

Inserting each of the filtered words into wordDictionary is O(1) per word on average, done n times, so O(n) total.


3) Sorting the word frequency array (sortProperties):

Sorting k distinct words in descending order of frequency, Worst case, if all words are distinct, k = n, so sorting is O(n log n).
This is typically the most expensive step if k is large.



Highlighting/searching:

The RegExp replace on the entire text again scans n words/characters, so roughly O(n) (actual complexity depends on the regex engine, but typically linear with a well-implemented search).
