
Pet Finder 

Purpose of the task is to predict the speed of adoption
of a pet. Pets are dogs and cats.

AdoptionSpeed (Target Variable):

Contestants are required to predict this value. The value is determined by how quickly, if at all, a pet is adopted. The values are determined in the following way:
0 - Pet was adopted on the same day as it was listed.
1 - Pet was adopted between 1 and 7 days (1st week) after being listed.
2 - Pet was adopted between 8 and 30 days (1st month) after being listed.
3 - Pet was adopted between 31 and 90 days (2nd & 3rd month) after being listed.
4 - No adoption after 100 days of being listed. (There are no pets in this dataset that waited between 90 and 100 days). 

Accuracy metric used for scoring: (quadratic weighted cohen kappa)[https://www.kaggle.com/c/petfinder-adoption-prediction/overview/evaluation]

Approach 1:
Categorical variables: One hot encoding
Continuous variables: No preprocessing

Models: Tree based

Best performer: Gradient Boosted Tree with Cohen Kappa: 0.30

Approach 2:
Same as approach one but used term frequency - inverse document frequency (tf-idf) to process "Description". This returned a large matrix. The column dimension was reduced using Truncated Singular Valued Decomposition (SVD). This was concatenated to the original data frame. The "Name" column was also preprocessed. Additional column "has_name" was created which had value 1 for data point that had a name 0 otherwise.

Models: Tree Based 

Both Gradient Boosted Tree and Random Forest had Cohen Kappa: 0.38 (slight improvement to the precious approach)

Approach 3:
The "Description" column which had information about the pet was preprocesed as approach 2. The categorical variables were transformed using embedding layer from PyTorch. (Embedding layer)[https://pytorch.org/docs/stable/generated/torch.nn.Embedding.html]

Models: Tree Based 

Best Performer: Random forest with Cohen Kappa of 0.41

