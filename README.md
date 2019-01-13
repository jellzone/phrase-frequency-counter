# Phrase Frequency Counter

This repo contains a sophisticated metric for evaluating the quality of eloquence and used vocabulary and the eloquence in text datasets like a collection of messages or entire
mailboxes. The hirsch-index is adapted as measure for the eloquence of phrases. It is an useful parameter in terms of assessing the datas usefulness for the training of Neural Networks in NLP. The metric is mainly based on the frequency of recurring phrases within the single text documents.

The core algorithm is implemented in C and also in Cython.
It can be chosen to count phrases on message or on sentence level (meaning, that we don't allow
phrases to consist of more than one sentence).
The procedure for finding and counting a phrase obeys the following the rules:
1. Start with the longest possible phrase length (= number of words in message/sentence) as `phr_len`
2. Search for a recurring sequence of words of this length
3. If found, mark the sequences, so that they can't be part of shorter phrases, and count their number of occurrence.
4. Continue with step 2 for `phr_len = phr_len - 1`

### Return values
1. `matrix`, numpy-matrix with 3 columns: phrase length, number of different phrases with this length, sum of numbers
   of occurrences of all phrases with this length
2. `tuples`, list of collected phrases with its number of occurrence

From tuples the hirsch-index (https://en.wikipedia.org/wiki/H-index) can be computed and 
a plotting function for the matrix is provided in order to visialize the phrase eloquence.


## Getting Up-And-Running

Here are some instructions for getting your own Verne running on your local computer.

### Prerequisites
1. Make sure you have python 2.7
2. For the C-implementation of the algorithm a C-compiler is required

### Python requirements:
1. numpy
2. spacy
3. cython (only required for the implementation in C)

### Installation and Configuration
1. `git clone` this repo
2. From the root of the repo, run `python cythonize_numerics.py build_ext --inplace` to precompile the c core.

### Running the script
To start the phrase counting on a given mailbox / collection of messages/texts, run

```sh
$ python counter.py <<path_to_mailbox_folder>>
```



### Support my projects :gift_heart:

I love open-source! And I try to reply everyone needing help using my projects. Also, you are of cause free to integrate and my project in your applications. However, if you get some profit from this or just want to encourage me to continue creating stuff, there are few ways you can do it:
 - Starring and sharing projects you like
 - :stew: [Share your next meal][sharemeal] with these unfortunate, because there is no reason not to do so!
 - :book: [Buy me a book][amazon]: I love books and I will always remember you :wink:
 - **Bitcoin**: You can send me bitcoins at this address:
 `xpub6DUNko8GTPePPgtbK1qfpiLCoujQXUBTi1qtfw7V2oBCdnk1H9d3if3pazmCy9QgENKSNPpHAXRZp8HLSG7pWwba5HRcHLC3TjbXYXXZh57`

Thanks! :heart:


[amazon]: http://amzn.eu/hRo9sIZ
[sharemeal]: https://sharethemeal.org/en/index.html
