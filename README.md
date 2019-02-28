## K-anonymity and Differential Privacy


[TOC]

#### 1. K-anonymity

##### 1.1 Generalization Hierarchy

Generalization hierarchy is defined in files in `conf` folder.

##### 1.2 Heuristic program

I implement the datafly heuristic algorithm, which pseudo code is below:

![](https://ws4.sinaimg.cn/large/006tKfTcly1g0krnjtttwj30qw0dmjut.jpg)

The detailed comments for each function can be found in file `k_anonymity.py`.

##### 1.3 Evaluation

I evaluate the result for `k = [5, 10, 50, 100]`, and calculate the distoration and precision. The calculation of distoration and precision is the same as given in lecture, where distortion is:

![](https://ws4.sinaimg.cn/large/006tKfTcly1g0ksdvufmpj30ij07a74y.jpg)

and precision is:

![](https://ws4.sinaimg.cn/large/006tKfTcly1g0ksdvufmpj30ij07a74y.jpg)


#### 2. Differential Privacy

##### 2.1 Laplace Mechanism

###### 2.1.1 Query for e=0.5 and e = 1

Query `1000` times for `e` in `[0.5, 1]`.


###### 2.1.2 0.5-Indistinguishable Proof

To prove the indistinguishable of two queries, I use bucket to gather outputs into 20 buckets, then calculate the probability for each bucket. Then calculate the quotient over each bucket probability. For two query result, `query1` and `query2`, I calculate both probability of `query1` over probability over `query2`, and also probability of `query2` over probability over `query1. We can see in both cases, the quotient is smaller than $exp^{\epsilon}$, which proves the $\epsilon$-indistinguishable.


######2.1.3 1-Indistinguishable Proof

The proof is same as 0.5-indistinguishable proof. We can see for each case, the $1$-indistinguishable holds.



###### 2.1.4 Distortion

To calculate the distortion, I used the RMSE as metric. Firstly I calculate the groundtruth, which is the true average age greater than 25 without adding noise. Then I calculate the RMSE of query result with groundtruth. We can see when $\epsilon = 1$, the RMSE is smaller than $\epsilon=0.5$, which proves the distortino of $\epsilon = 1$ is smaller than  $\epsilon=0.5$.



##### 2.2 Exponential Mechanism

###### 2.2.1 Query for e=0.5 and e = 1

Query `1000` times for `e` in `[0.5, 1]`.



###### 2.2.2 0.5-Indistinguishable Proof

To prove the $\epsilon$-indistinguishable, I firstly count the frequency of each education value in the query results. Then calculate the probability for each education value. Indistinguishability can be proved by showing the probability quotient of two adjacent tables is smaller than $\exp^{\epsilon}$. We can see for each case, the indistinguishability holds.


###### 2.2.3 1-Indistinguishable Proof

The proof is same with $\epsilon=0.5$. We can see for each case, the indistinguishability holds.


###### 2.2.4 Distortion 

The metric I used here is `1-precision`. `Precision` is calculated by #results which is the groudtruth / total query numbers. `1-precision` is a measure for distortion, as higher precison implies lower distortion. We can  see when $\epsilon = 1$, the distortion is smaller than $\epsilon=0.5$, which proves the distortino of $\epsilon = 1$ is smaller than  $\epsilon=0.5$.

