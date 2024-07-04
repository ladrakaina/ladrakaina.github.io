---
layout: article
title: How to calculate mortgage loan interest and payment?
custom_css: article.css
include_mathjax: true
---
In China, there are two methods for mortgage loan payment:

+ Method 1: Equal principal
+ Method 2: Equal monthly payment

## Method 1: Equal principal ##

Every month, the debtor pays back an equal amount of principal, plus interest. Interest equals to the unpaid principal multiplied by interest rate.

$$
X_{n} = \frac{P}{12y} + P(1-(\frac{n-1}{12y}))(\frac{R}{12})
$$

$X_{n}$: n month's payment

$P$: The principal that is borrowed from the bank

$y$: Number of years for the mortage loan

$R$: Yearly interest rate

After the loan is completely paid off under method 1, how much in total ($T_{I}$) have you paid to the bank?

$$
T_{I} = P + \sum_{i=1}^nP(1-(\frac{n-1}{12y}))(\frac{R}{12})
$$
  
If we assume that you took a $100,000$-dollar and $20$-year loan from the bank with $5$% yearly interest rate, let's look at with time how $X_{n}$ changes. 

From Figure 1, we can see the monthly payment (green line) decreases linearly with time; The principal paid monthly (yellow line) stays constant; The interest paid monthly (purple line) decreases linearly with time. 


    
![png](/assets/images/2024-06-28-how-to-calculate-mortage-loan-interest_files/2024-06-28-how-to-calculate-mortage-loan-interest_4_0.png)
    


In Figure 2, we calculated the total amount of money paid up till nth month. When the loan is completely paid off, the total Payment under method one is:

$$
T_{I} = 150208.33
$$


    
![png](/assets/images/2024-06-28-how-to-calculate-mortage-loan-interest_files/2024-06-28-how-to-calculate-mortage-loan-interest_7_0.png)
    


## Method 2: Equal monthly payment ##


### Monthly payment ###


Every month, the debtor pays back an equal payment, i.e. sum of principal and interest.

This method is more complicated to calculate than the first one, so I will explain in detail.

$L$: The rest of the principal that needs to be paid to the bank

$P$: The total principal borrowed from the bank

$r$: Monthly interest rate, $r = R/12$, $R$ is yearly interest rate

$X$: Monthly payment to the bank

$Y$: The number of years for the loan

At the end of the `1st month`, after the first payment, the amount of loan left:

$$
L_{1}= P(1+r) - X
$$


`2nd month`, the amount of loan left: 

$$
L_{2} = L_{1}(1+r) - X = (P(1+r) - X)(1+r) - X = P(1+r)^2 - X(1+(1+r))
$$

`3rd month`: 

$$
L_{3} = L_{2}(1+r) - X = {P(1+r)^2 - X(1+(1+r))}(1+r) - X = P(1+r)^3 - X(1+(1+r)+(1+r)^2)
$$

or 

$$
L_{3} = P(1+r)^3 - X(1+(1+r)+(1+r)^2)
$$

`4th month`:

$$
L_{4} = P(1+r)^4 - X(1+(1+r)+(1+r)^2+(1+r)^3)
$$

...

`Nth month`:

$$
L_{n} = P(1+r)^n - X(1+(1+r)+(1+r)^2+...+(1+r)^{n-1})
$$

Let's observe the second part of the equation $X(1+(1+r)+(1+r)^2+...+(1+r)^{n-1})$ contains a geometric series. Let's briefly review the formula of geometric series:

$$
S_{n} = a + aj + aj^2 + aj^3 + ... + aj^{n-1}
$$

$$
jS_{n} = aj + aj^2 + aj^2 + aj^3 + ... + aj^{n-1} + aj^n
$$

$$
(1-j)S_{n} = a - aj^n
$$

$$
S_{n} = \frac{a(1-j^n)}{1-j}
$$


therefore we can further simplify the above loan equation:

$$
L_{n} = P(1+r)^n + X{\frac{1-(1+r)^n}{r}}
$$

When the loan is completely paid off, i.e. $n = 12Y, L_{12Y} = 0$, and since $P$ and $r$ are known, we can finally  calculate monthly payment $X$:

$$
X = \frac{rP(1+r)^n}{(1+r)^n-1}
$$

And we can also replace the monthly interest rate $r$ with yearly rate $R$, which is normally given by the banks:

$$
X = \frac{\frac{R}{12}P(1+\frac{R}{12})^n}{(1+\frac{R}{12})^n-1}
$$

After calculating monthly payment $X$, let's see how much interest and principal the debtor is paying to the bank every month.


### Monthly Interest ###


The interest equals to the money (principal) the debtor still owes the bank multiplied by interest rate. 

At the end of the `1st month`:

$$
I_{1} = P \times r
$$

`2nd month`

$$
I_{2} = L_{1} \times r
$$

`3rd month`

$$
I_{3} = L_{2} \times r
$$

...

`Nth month`

$$
I_{n} = L_{n-1} \times r  
$$


### Monthly Principal ###


Since we have already calculated monthly payment $X$ and interest $I$, it's easy to calculate the principal the debtor is paying every month.

$$
P_{n} = X - I_{n}
$$

Let's look at an example of a mortgage loan payment under method 2. We'll continue to use the example from method 1: assume that you took a $100,000$-dollar and $20$-year loan from the bank with $5$% yearly interest rate, let's look at with time how monthly payment, interest and principal changes.

In Figure 3, the monthly payment is constant; the monthly interest decreases with time; the monthly principal paid to the bank increases with time. In the beginning, the interest is higher than the principal paid back to the bank, which means in your monthly payment, majority of what you are paying is interest.


    
![png](/assets/images/2024-06-28-how-to-calculate-mortage-loan-interest_files/2024-06-28-how-to-calculate-mortage-loan-interest_11_0.png)
    


Now let's look at under method 2, when the loan is completely paid off, how much have you paid?

$$
T_{II} = X \times 12y
$$

When the loan is completely paid off, the total Payment under method two is:

$$
T_{II} = 157729.42
$$

and 

$$
T_{I} = 150208.33
$$

Obviously the total payment of the first method is lower than that of the second method. 

## Conclusion ##

Method 1:

+ Pros:
  + Monthly payment decreases with time, which will lower the pressure of the debtor in the future.
  + Lower total amount paid to the bank than method 2.

+ Cons:
  + A higher monthly payment during the first a few years than method 2, which might be too much pressure for some debtors.

Method 2:

+ Pros:
  + Monthly payment in the first a few years is lower than method 1, which will lower the pressure of the debtor.
  + Monthly payment is constant, which is stable for some debtors.

+ Cons:
  + Higher total amount paid to the bank than method 1


Banks tend to recommend method 2 to most people, because it has a lower income requirement for the debtors, which then allows banks to have more debtors. Moreover, in total, banks receive more interest with method 2.

