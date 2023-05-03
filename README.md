# fictometer
Fictometer is an Algorithm for text classification whether a piece of text is fictional or non-fictional. That is why to predict the outcome we have used Logistic Regression. It is a type of regression analysis that models the probability of the binary outcome as a function of the predictor variables.
Predictor variables in our analysis - 1) Adjective/pronoun 2)Adverb/Adjective
Binary Outcome in our analysis - 1) 0 - fictional 1 - Non-fictional or (vice versa)
The reason why logistic regression is giving such a whooping accuracy of 96% is because of our selection of Predictor variables and obviously the selection of the classified outcome ( fictional or non-fictional). The simple intuition behind it is that generally a fictional text ( which in our case comprises fiction, mystery, science fiction, adventure, and romance) there will be a high number of pronouns & adverbs used for a given amount of adjectives.  While on the other hand the non-fictional text(which in our cases comprises news, reviews, hobbies, and government ) there will be a high number of adjectives compared to a given amount of pronouns and adverbs. 
Now comes how to implement the Algorithm 
1) Data Preparation 
2) Application of Logistic Regression 

Data Preparation - 
a) UPOS tagging (Penn Treebank Tag to simplified universal tag)
These are a series of functions for part-of-speech tagging and categorization of words in a given text. 
The n_adj function takes in a list of words tagged with their part of speech and returns the number of adjectives in the text.
The n_noun function takes in a similar list and returns the number of nouns, excluding compound nouns.
The n_verb function takes in the same list and returns the number of verbs.
The n_pronoun function takes in the list and returns the number of pronouns.
The n_adv function takes in the list and returns the number of adverbs.
The func_utag function takes in a Penn Treebank tag and returns a simplified universal tag. 
The universal tags used are ADJ for adjectives, NOUN for nouns, VERB for verbs, PRON for pronouns, and ADV for adverbs.
The func_is5tag function takes in a universal tag and returns a boolean value indicating whether the tag is one of the five recognized tags or not.
b) Calculation of the number of different POS 
Then we create a  script that creates a Pandas DataFrame called brown-postable with columns for category, filename, and the counts of adjectives, adverbs, nouns, verbs, and pronouns in the text file.
Then we iterate over each category in the Brown Corpus and for each category iterate over each file in the category. For each file, it obtains the part-of-speech tags using the tagged_words ( present  in the NLTK library) 
It then extracts the counts of adjectives, adverbs, nouns, verbs, and pronouns using the previously defined functions n_adj, n_adv, n_noun, n_verb, and n_pronoun. Finally, it appends the obtained information to the brown-postable DataFrame.
c) Calculate the ratios of adjective/pronoun and adverb/adjective.
d) Several subcategories were converted to two broad classifications - Fiction or Non - Fiction 
So our Data Preparation is completed. 

Now comes the Training using Logistic regression 
a) We need two columns for our Predictor Variables i.e ('RADJPRON' & 'RADVADJ') so we drop the other columns.train_test_split function from sci-kit-learn to split the data into training and testing sets, with 80% of the data used for training and 20% for testing.
The 'lbfgs' solver fits the model to the training data using the fit method.
b) Then finally computing the accuracy of the logistic regression model on the training and testing data.

Practical Applications - According to me the Fictometer can have high-level Applications. 
It can be used to know whether a person is a fictional reader or a non-fictional reader. The fictometer can be installed in various libraries. It can tell a piece of text under which class it belongs. So when the librarian wants to keep the books back on the shelf from a mixed pile of books. He would simply scan the soft copy pages through fictometer and assign the book its place on the shelf. It would save time and efficiency. Maybe we can update this idea and set the predictor variables according to our need.
