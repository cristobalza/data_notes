# Decision Trees Notes

## Introduction 
Say I want to buy a house and wish to borrow a loan from the bank. Now before giving me the loan, the bank is going to look at my history record like my credit, what has it been like in the past? How much money do I make? (and maybe some other information) and use them to determine whether loaning me money is a risky thing or not (whether I'm going to default). So how can the bank do this with decision trees?

**Definititon**: Decision Trees (DT) are a data structures that are formed by a collection of rules - **if-then** statements - based on variables availables from the data set. 

For example, using the above credit hypothetical scenario:

```
if Credit = excellent then
    Outcome = Yes
else if Credit = poor then
    if Income = high then
        Outcome = Yes
    else if Income = low then
        Outcome = No

```

**How it works?** The algorithm starts from the top of the tree (**root node**), then it traverse down the **branches** asking a series of questions. At the end, when it reaches the **leaf node** of a branch, it will encounter the final outcome. For example, if somebody has a credit that's poor and his/her income is high, then the bank will say Yes and will give him/her the loan.

**How do you construct a DT?** A DT can be learned by splitting the dataset into subsets based on the input features/ attribyutes' value. This process is repeatead on each derived subset in a recursive manner such that:

1. Start at the tree's root node
2. Select the ebst rule/feature that split the data into two subsets (child node) for the current node.
3. Repeated *Step 2* on each of the derived subset until the tree can't be further splitted. We can set restrictions to decide when to stop the DT.

**How to pick a rule/feature to split on?** There is a splitting criteria based o maximizing the the information on each split (**Information Gain**). In order to maximize the information we need to minimize the impurity or noise of the data at each recursive step. There two impouritty measures: **Entropy** and **Gini Index**.

## Splitting Criteria

The first question is what is the best rule/ feature to split on and how do we measure that?

We determine the split by measuring how much information can be maximize using **Information Gain** such that: 

$$IG(D_{p}, a) = I(D_{p}) - p_{left} I(D_{left}) - p_{right} I(D_{right})$$

### Impurities

#### Entropy 

It is defined as 

$$ I_E(t) = - \sum_{i =1}^{C} p(i \mid t) \;log_2 \,p(i \mid t) $$

**What are the possible values?** Ranges from $0$ to $1$.

If entropy is $0$, then all samples at the node belong to the same class.

If entropy is $1$, thne we have an uniform class distribution.

For example, in a binary class setting, the entropy is 0 if  $p(i =1 \mid t) =1$  or   $p(i =0 \mid t) =1$ . And if the classes are distributed uniformly with   $p(i =1 \mid t) =0.5$  and   $p(i =0 \mid t) =0.5$ the entropy is 1.

#### Gini Index

It is defined as 

$$I_G(t) = 1 - \sum_{i =1}^{C} p(i \mid t)^2$$

**What are the possible values?** Ranges from $0$ to $0.5$.

If Gini Index is lower, then there is only one class represented in a node (A node with a lower Gini index is said to be more "pure")

If Gini Index is $0.5$, then the classes are perfectly balanced in the node.


