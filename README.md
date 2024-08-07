# MIE1622_Assignment_3
 
This assignment aims to model a credit-risky portfolio of corporate bonds. 

Conditions:
Consider a structural model for portfolio credit risk described in class. Using the data for 100 counterparties,
simulate 1-year losses for each corporate bond. You will need to generate 3 sets of scenarios:

Monte Carlo approximation 1: 5000 in-sample scenarios (N = 1000 x 5 = 5000 (1000 systemic
scenarios and 5 idiosyncratic scenarios for each systemic), non-normal distribution of losses);

Monte Carlo approximation 2: 5000 in-sample scenarios (N = 5000 (5000 systemic scenarios
and 1 idiosyncratic scenario for each systemic), non-normal distribution of losses);

True distribution: 100000 out-of-sample scenarios (N = 100000 (100000 systemic scenarios
and 1 idiosyncratic scenario for each systemic), non-normal distribution of losses).

The out-of-sample scenarios represent the true distribution of portfolio losses. Two in-sample non-
Normal datasets are used for evaluating sampling error and performing portfolio optimization

To evaluate model error (if we wrongly assumed that counterparty losses follow Normal distri-
bution), compute mean loss and standard deviation of losses for each corporate bond from the
3 scenario sets (N=1000 x 5, 5000, 100000). This 3 in-sample sets are referred as in-sample Normal
model.

Evaluate VaR and CVaR at quantile levels 99% and 99.9% for the two portfolios:

(1) one unit invested in each of 100 bonds;
(2) equal value (dollar amount) is invested in each of 100 bonds;

For each portfolio, compute VaR and CVaR at quantile levels 99% and 99.9% for each of the six
datasets (non-normal with N=1000x5, 5000, 100000; and Normal with mean/standard deviation
computed from N=1000x5, 5000, 100000). Compare each in-sample VaR and CVaR to out-of-
sample VaR and CVaR. Explain the effects of sampling error and model error.

To better evaluate sampling and model errors, experiment 100 times in the following
way: generate in-sample datasets with N=1000x5 and 5000 (non-normal and Normal) one hundred
times and compute VaR and CVaR. Keep the out-of-sample scenario set unchanged. Perform
analysis of the results for the 100 trials, e.g., compute averages of the results for 100 trials, analyze
standard deviation over 100 trials, etc.

Step 1:

Transform Uncorrelated Normal Random Variable Into Correlated Normal Random Variable

Cholesky decomposition is a method to generate correlated random numbers with specific correlation structures from uncorrelated random numbers by the following 2 steps:

1.   Decompose the desired covariance matrix into the product of a lower triangular matrix (L) and its transpose (LT) using the Cholesky factorization.
2.   Multiply the generated independent Normal random variables by the lower triangular matrix (L) to obtain a set of correlated Gaussian random variables.

Each bond has a risk of changing credit state, ranging from AAA to default (8 states):

8 = AAA, 7 = AA, 6 = A, 5 = BBB, 4 = BB, 3 = B, 2 = CCC, 1 = default

Find the credit state for each counterparty: The current bond is the bond with the highest probability

Compute credit-state boundaries: scipy.special.ndtri is used to return the argument x for which the area under the Gaussian probability density function equals y.

Monte Carlo is used to estimate the bond transition state.

Two scenarios are 1 unit in each, and equal $ in each.

Results:

Portfolio 1:

Out-of-sample: VaR 99.0% = $82696853.28, CVaR 99.0% = $123389989.06
In-sample MC1: VaR 99.0% = $84168413.52, CVaR 99.0% = $124234846.56
In-sample MC2: VaR 99.0% = $85050766.71, CVaR 99.0% = $125489858.78
In-sample No: VaR 99.0% = $46366497.88, CVaR 99.0% = $52204462.00
In-sample N1: VaR 99.0% = $46840656.05, CVaR 99.0% = $52739514.74
In-sample N2: VaR 99.0% = $47256573.09, CVaR 99.0% = $53208982.55

Out-of-sample: VaR 99.9% = $174144664.76, CVaR 99.9% = $212730444.31
In-sample MC1: VaR 99.9% = $175382157.59, CVaR 99.9% = $217105880.96
In-sample MC2: VaR 99.9% = $176110425.39, CVaR 99.9% = $215929958.52
In-sample No: VaR 99.9% = $59526641.86, CVaR 99.9% = $64296326.87
In-sample N1: VaR 99.9% = $60138070.70, CVaR 99.9% = $64957507.29
In-sample N2: VaR 99.9% = $60674703.77, CVaR 99.9% = $65537891.96


Portfolio 2:

Out-of-sample: VaR 99.0% = $73348811.38, CVaR 99.0% = $116266854.05
In-sample MC1: VaR 99.0% = $74753668.62, CVaR 99.0% = $116767847.31
In-sample MC2: VaR 99.0% = $76270338.94, CVaR 99.0% = $118382526.99
In-sample No: VaR 99.0% = $42782078.58, CVaR 99.0% = $48115955.60
In-sample N1: VaR 99.0% = $43151429.66, CVaR 99.0% = $48531521.06
In-sample N2: VaR 99.0% = $43644854.34, CVaR 99.0% = $49090084.60

Out-of-sample: VaR 99.9% = $175928347.73, CVaR 99.9% = $210293929.72
In-sample MC1: VaR 99.9% = $172192044.23, CVaR 99.9% = $213633516.27
In-sample MC2: VaR 99.9% = $172993636.57, CVaR 99.9% = $213957542.18
In-sample No: VaR 99.9% = $54805891.68, CVaR 99.9% = $59163731.63
In-sample N1: VaR 99.9% = $55279420.84, CVaR 99.9% = $59675018.48
In-sample N2: VaR 99.9% = $55919683.84, CVaR 99.9% = $60368500.69

![image](https://github.com/user-attachments/assets/9011ef66-df73-4e63-be3e-5fd4d60da8dd)

![image](https://github.com/user-attachments/assets/6fce5498-860f-4791-ac59-c1738158678a)

![image](https://github.com/user-attachments/assets/6b1164b3-8019-404f-8c10-8c39cb2992ee)

![image](https://github.com/user-attachments/assets/8bf8f3e3-8794-4fbd-b37c-b6c183acfe2b)

![image](https://github.com/user-attachments/assets/3a7bfb2f-7fd3-4a62-ba0f-38d9558d199a)

![image](https://github.com/user-attachments/assets/30055070-b627-4ad5-89cf-ccb712db3abf)

Monte Carlo Sampling Error:

![image](https://github.com/user-attachments/assets/41dbb4cd-1ed1-4052-82db-ff51ec277733)

Normal Distribution Sampling Error:

![image](https://github.com/user-attachments/assets/6c5ff34f-636b-4776-9fdc-cf53cbd440ad)

Comparing the error between the true distribution and the two methods of Monte Carlo simulations for both portfolios, the non-normal approximations of VaR and CVaR for both confidence levels are very similar to the true distribution. The first Monte Carlo simulation strategy (1000 systematic scenarios and 5 idiosyncratic scenarios for each systematic) does better than 1 idiosyncratic scenario with 5000 systematic scenarios. It’s using very little data points to calculate the values at 99.9% confidence levels (1 point vs 5 points). The sampling error between the two Monte Carlo approximations is very small.

If we wrongly assume that the data follows a normal distribution. We can compare the difference between losses against the true distribution. For both portfolios, we can observe that the values of VaR and CVaR are significantly underestimated for both values of alphas compared to the true estimated loss. This is very important since we would be underestimating our losses and assume our portfolio will perform much better than it is. The normal distribution model does not have long flat tails like the true loss distribution. The normal distribution underestimates the 99% VaR and CVaR loss (true loss is doubled) and the 99.9% by significantly more (true loss is tripled the estimated loss).

If you report the in-sample VaR and CVaR to decision-makers in your bank, what consequences for the bank capital requirements have?

If the in-sample non-normal approximations of VaR and CVar are reported to the decision-makers in the bank, they will have an accurate prediction/representation of the true estimated credit risks and losses. This will allow them to make correct risk strategies. The bank will not be using underestimated loss as if they were to use the normal approximation. This may potentially lead to significant losses in terms of a financial crisis where many uncertainties happen (Being more risk-averse without understanding the actual risk tolerance).

However, the difference between VaR and CVaR varies significantly, where CVaR is almost 1.5x of VaR for the 99% confidence interval and 1.3x of VaR for the 99.9% confidence interval. With such a large difference between VaR and CVaR, it will drastically affect the amount of capital the bank will have to keep within the bank for risk management.
Can you suggest techniques for minimizing the impacts of sampling and model errors?

From part 2, we can observe that the impact of sampling error is not a huge concern (Within 2% error). To minimize the impacts of sampling errors, we can increase the sampling size and the number of trials. By increasing the number of idiosyncratic scenarios as well as the number of systematic scenarios, we can reduce sampling error.
To minimize the modeling errors, we should not assume a type of distribution without taking a further look at the data. By running a quick Monte Carlo simulation of randomly generating the scenarios and plotting the losses, we can see which distribution pattern it fits and then choose a model it likely fits to perform more calculations and save computation.
