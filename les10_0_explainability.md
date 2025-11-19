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
 
- 3.1 inspecting the mean decrease in impurity. 
- 3.2 drop feature importance
- 3.3 permutation based feature importance
- 3.4 partial dependence plots

## 4. Local explainability
- 4.1 Individual conditional expectation (ICE) plots
- 4.2 LIME
- 4.3 Shapley values

## 5. reading (optional)
https://christophm.github.io/interpretable-ml-book/pdp.html

















 