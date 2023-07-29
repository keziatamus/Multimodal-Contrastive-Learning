Please follow the flow below to run the code for Multimodal Clustering and Contrastive Learning. The notebooks can be executed directly by selecting "Cells -> Run All." However, you may also make some modifications according to your specific requirements. Details about the settings that can be adjusted are provided below.

Please note that the crawler for tweets is not included in this repository due to Twitter's decision to end free access to its API in February. Twitter launched paid tiers in March 2023. For more information, please refer to https://developer.twitter.com/

Flow:
1. Install the required packages used in the work: requirements.txt
	(1) Navigate to the correct directory path
	(2) Execute the command "pip install -r requirements.txt"

2. Identify candidate users: UserIdentification.ipynb
This notebook utilize logistic classifier train on 6230 tweets, validate on 1558  tweets, and test on 1947 tweets. Using the training dataset, the unlabeled scraped tweets are predicted for low self-esteem instances.
	(1) Check the directory path
	- Navigate the correct directory path of the file for "labeled_df.csv"
	- Navigate the correct directory path of the file for "scraped_df.csv"
	- Navigate the correct directory path of the file for "candidate_users.csv"
	(2) Modify settings in the file
	- Change the "train_size=0.8" to split the train and test data based on your necessity
	- Change the "max_features=1000" in the CountVectorizer to the number of tweets that occur the most you would like to select
	(3) Click "Cells" and "Run All" in the notebook.

3. Perform multimodal and contrastive learning: MultiContrastive.ipynb
This notebook read user files, extract seed keywords and related concepts, perform multimodal clustering and contrastive learning, and calculate the refined probability score.
	(1) Check the directory path
	- Navigate the correct directory path of the folder "/training/users/"
	- Navigate the correct directory path of the file for "%s_ref_filter.csv"
	(2) Modify settings in the file
	- Change the “filename = 'yutacaI’” to the username in the folder
	- Change the “df = df[:50]” to adjust the number of rows you would like to train
	- Change the "tfidf_scores.argsort()[-5:][::-1]" in the TfidfVectorizer to the number of top keywords you would like to select
	- Change the "limit_per_keyword=5" in the ConceptNet to number of top related concepts you would like to select
	- Change the "language == 'en'" to the language of the concepts extracted
	- Change the "model="facebook/bart-large-mnli"" to the NLI model from hugging face you would like to utilize
	(3) Click "Cells" and "Run All" in the notebook.

Contact Kezia (kezia.tamus@gmail.com) if there are any questions.