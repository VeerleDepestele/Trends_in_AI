# explainability - interpretability

## 1. Introduction

Interpretable machine learning is the subfield of machine learning that tries to make models more understandable by humans. It is often opposed to the concept of "black box models" where it is hard to justify why a model makes a certain prediction. Nowadays, this field is more and more referred to as explainable artificial intelligence (XAI). This interest comes from the fact that machine learning is becoming an integral part of a lot of decision support systems and is, therefore, more and more present in our everyday life. As this importance keeps increasing, questions arise about the justification that can be obtained regarding these models, and researchers start to focus on more interpretable models.

Indeed, for certain problems, getting the prediction from our models is not enough, an explanation is also required.

In fraud detection for example, models are usually complex. Mostly, human investigators will process the machine-learned alarms. Knowing why a transaction leads to an alarm is clearly an added value. 

Interpretability also provides helpful tools for 
- debugging,
- increasing model acceptance,
- and providing justifications during audits.

This lesson is divided into three sections, followed by a summary. 

The approaches are sorted by the effort required to open the box, from the explanation obtained in one line of code to an in-depth explanation for each prediction of a model.

- The section "Feature importance - explainability in one line" discusses two one-line sklearn commands allowing to ''open the box'' easily.
- The section "Global Interpretability" discusses a family of global methods that focus on explaining a few considered features.
- In the section "Local interpretability", Each individual prediction receives an explanation.
- In the section "Summary", all these explainers are summarized and compared.

Before introducing some interpretability approaches, let us shortly review the different classes of approaches and their taxonomy. 

### 1.1 Taxonomy
#### 1.1.1 Global vs. local explainability/interpretability

A first property of interpretabilty methods is their scope: 
- **global methods** focus on the model level: "What features contribute to the model?"
- **local methods** focus on a specific prediction (for example a transaction) or a group of predictions: "How do the values of the features influence the model prediciton for a particular observation?"

Both are equally important.

Global methods are covered in sections "Feature importance - explainability in one line" and "Global Interpretability". Local methods are covered in the section "Local interpretability".

#### 1.1.2 Pre-Model vs. In-Model vs. Post-Model

Interpretability methods can take place before (pre-model), during (in-model), or after (post-model) building the ML model.

**Pre-model interpretability** techniques are independent of the model and take place before model selection (during the data exploration phase): They focus on the data level. For example, sparsely selecting a low number of intuitive features can help to achieve data interpretability. As this approach requires more a-priori knowledge and is problem dependant, it was less studied than the other two.

The most popular pre-model techniques are visualization methods: PCA (Principal Component Analysis), t-SNE (t-Distributed Stochastic Neighbor Embedding), UMAP (Uniform Manifold Approximation and Projection for Dimension Reduction), and clustering methods.

**In-model interpretability** refers to models that are already sufficiently explainable by themselves: the so-called white-box models. 
- Tree-based classifiers, for example are easily interpretable (ref. Gini feature importance (Global) & TreeSHAP (Local)).
- regression models are easily interpretable (for example the Lasso regression model). 

**Post-model interpretability** is often built on top of a black-box model: A post-hoc explainer is added to improve the interpretability of the black-box model. It allows, for instance, the interpretation of models that are already running in production. 

#### 1.1.3 Model-specific vs. model-agnostic

Can a post-model interpreter handle all possible ML models? 

- If no, this interpreter is said to be **model-specific**.
- Otherwise, it is said to be **model-agnostic**.

Model-specific interpretations have their range limited to certain model classes because they are based on some specific model’s internals  For example, SHAP TreeExpainer is only devoted to decision trees-based algorithms, as it uses their properties to build its post-hoc explainer.
Also, a large part of model-specific interpreters is devoted to Deep Neural Networks and computer vision (for example "saliency mapping")

On the contrary, model-agnostic methods can be applied to any ML model (black box or not) and are applied after the model has been trained (post hoc). These methods rely on analyzing pairs of features' input and output. Usually, model-agnostic explainers are also post-models, sometimes refered to as surrogate models.

Suppose a black box model is too complex to be interpreted. In that case, a workaround solution can be to build a white box model, called the surrogate model, which tries to globally approximate the black-box model as faithfully as possible. It is then easier to interpret the surrogate model. As discussed in section "Lobal interpretability", LIME and SHAP train local surrogate models for each individual prediction to be explained.

#### 1.1.4 white box models and black box models

**white box models**

- like logistic regression models and decision trees
- outcome easy to understand by decision makers
- used in credit risk modelling, medical diagnosis

**black box models**

- like random forests and neural networks
- more complex models
- the focus is on estimating the target as accurately, without necessarily wondering how the model came to that prediction
- example: fraud detection, response modeling

 ## 3. global explainability
 
Different techniques exist to estimate which features are important according to the machine learning model:
 
### 3.1 inspecting the mean decrease in impurity. 
This is commonly done in tree-based ensembles, like random forest models.

- Is is model dependent (it is different in random forest models and gradient boosted models)
- We can gauge the importance of a feature by looking at the position of the feature (cfr. random forest model: features near to the top are more important)
    
### 3.2 drop feature importance
Drop a feature from the model, train it again, inspect the impact on the model performance. This requires multiple retraining runs of the machine learning model and can thus be slow.

This method is model agnostic.

### 3.3 permutation based feature importance
This is a more powerfull method to evaluate feature importance. It is model agnostic and considered to be the best approach.

Here is how it works:

- Start from a trained machine learning model on a given dataset and a performance measure of interest (AUC, accuracy, profit, ...)
- Randomly permute the feature under review.
- Use the trained machine learning model to predict the observations again.
- Calculate the feature importance as the difference in performance between the model on the original data and on the permuted data.

Permutation based feature importance indicates which features are important, but not how these features influence the outcome or prediction (positive, negative, relation with other features).

Note that this also takes into account interactions, as the shuffling breaks down the interaction effect.
When permuting, the correlation between features is broken.

This can be used for feature selection: train on the top N selected features only (Boruta feature selection).
Correlated features are likely to share importance which might lead to misinterpretation. 
(check for correlation)

One can also perform permutations on several features at once, to zoom in on interation effects.

Perform the permutation exercise, both on the training and test data set,

- train: understand the importance for the feature in the model,
- test: understand if there was overfitting of the machine learning model on the training dataset.

### 3.4 partial dependence plots
Aim: understand how a feature impacts the outcome of a machine learning model.

Idea: keep the feature under study fixed and impute all the others with the median or mode over all observations.

The trained machine learning model is then used to make predictions on the new dataset. Then plot the predicted probalilities for the different values of the feature under study.

Interation effects might not show up in a PDP. However, a partial dependence plot could be used to detect interation effects.
We could observe patterns in the data, and contract those with the PDP. 

Say, we are building a model for churn prediction. Suppose that we've learnt from the data that the probability of churning decreases in the age category of 30-40 years (i.e. the probability of churning is lower in that age category than in the surrounding age categories). Suppose that the PDP shows that the probability of churning is equal over all age categories. This would be a sign that there is an interaction of the age categories with other features used in the model.

When using this methode, you can choose to combine several features (as it is the case for permutation based feature importance).

Frequently used vizualization methods are contour or 3d-plots.

## 4. Local explainability
### 4.1 Individual conditional expectation (ICE) plots

Individual conditional expectation (ICE) plots are similar to partial dependency plots (PDPs). 

This is less clear here, based on the intuïtive description for a PDP above. It is more clear in the "les9_4_local_interpretability.ipynb".

The key idea is not to replace features with the median or mode, but keep each feature as is.

Create new observations based on the values of the feature under study.
Or, a grid based range can be defined to the feature under study, between its observed min and max.

Ice plots are well suited to show the behaviour of a feature accross the entire dataset.

It is recommended to explore ICE plots for the important features only.

Also, compare training and test.

By using ICE plots for the training set, it allows to understand how a machine learning model actually relied on each feature.

By doing ICE plots on the test set, we can verify whether the feature impacts are similar as on the training set, and whether there was no overfitting of the machine learning model on the training set.

### 4.2 LIME
Local, Interpretable, Model Agnostic Explanations.

Idea: LIME implements a local surrogate model to provide predictions.
Goal: it helps to explain single individual predictions.

I.e. not the data, a feature (like PDP) or the model as a whole.

It is model agnostic, i.e. it works on any type of black box model: neural networks, SVM's, XGBoost, enz.

It works with tabular and other types of data, such as text and images.

Suppose we have trained a blackbox classifier b(), we want to explain the prediction of an instance, x_i, by that classifier.

b(x_i) = p(y=1|x_i) = 0.78

Main idea:
- create a new dataset containing permuted samples around x_i,
- have the blackbox model b() provide predictions for the data in the new dataset,
- train a 'local', interpretable model on this dataset and use it to offer explanations
- this 'local' model is weighted by taking a sample based on the proximity of permuted instances around x_i.)
- commonly used models are LASSO regression or regression tree.
 
Bv, je hebt een binary classifier.
Kies er een punt uit, neem sample data rond dat punt.
Geef gewichten aan de datapunten, hoe dichter bij het "uit te leggen" punt, hoe groter het gewicht.
(Most LIME implementations use an exponential smoothing kernel to do this).

Op die dataset laat je je black box model zijn predicties doen (calculate it's probabilities).
Uiteindelijk: sample from the perturbed dataset based on the weights.

A simple ML algorithm is trained on this sample. Use for example LASSO regression. The output of this is a continous value representing the predicted probailities of the black box model. This provides us with a local decision boundary which can be easily inspected.

Lime can also be applied on non-tabular data such as text or images. Non-tabular data changes how the perturbation is performed. 
In case of text data, new texts are created by randomly removing words from the original text for example.
For images, perturbing individual pixels does not make a lot of sence.
Instead, groups of pixels in the image are perturbed at once by blanking them, in other words, removing them from the image.
(Original LIME paprer Ribiero et. al)

LIME is easy to understand and works on tabular data, text and images.

ref. Python lime, Python eli5
ref. R ...

### 4.3 Shapley values
We explain the use of Shapley values to interprete feature contributions in a black box machine learning model.

This is not the origin of the Shapley value. 
Shapley was an economist intrerested in game theory.
We will focus on the game theoretical context first, to get a grasp of how it works.

The Shapley value represents the payout for every player in a cooperative game. It can also be used to measure the contribution of a feature to a ML model.

FI, Shapley won the Noble price for his contribution to game theory.

It tries to access each player's contribution in a cooperative game.
For example: an indoor soccer team. The goal is to find out how much each player contributes to the team.
In game theory: this would be the "playoff". We will call it: "the marginal gain" or "contribution of each player".

Assume, we have a characteristic function to assess the value of a soccer team.

Adding one player A will give the team a value of 6.
v({A}) = 6, where v is calles 'characteristic function'.

We can try to complete the team by adding extra players.
Adding extra players will increase the value of the team.
However, players can have overlapping skill sets.

Say that adding player B with player A, give us a value of the characteristic funtion of 10.
- add player B
  - v({A})=6,
  - v({A, B}) = 10,
  - B has a marginal contribution of 4.
- add player C
  - v({A, B, C}) = 12,
  - C contributes 2 to the team.
 
Player C only contributes 2 to the team. 
However, if this small value is due to player B, already being in the team before C, then we should take into account what would happen if he came in first.

This is the only fair way to address all players payoffs.
So, if we add C first, her marginal contribution is 4 and that of B is reduced to 2.

If we want to be perfectly fair in our assessment, we should then look at all possible teams we can form with player C to know what value she really adds to the team.

In other words, to know the contribution of C, we need to average her contribution in all formations of the team.

To explain this, we need some combinatorial theory.
Let's first go over some extra intuitions.

1. It is important to see that only the players that were already in the team before C, matter. Not the order in which these were added. Whether A came first in the team, it doesn't matther. Thus, we only need to know hte value of adding C to a team with A and B once and weigh it with the number of teams we can form with A and B.
2. All players that come after C are not important. But, we need to take into account that we could add players D and E in a different order an d it would not impact the marginal contribution of adding C to a team with A and B.

Translate the intuition to a mathematical formula.

relevant documentation.
https://christophm.github.io/interpretable-ml-book/pdp.html

















 