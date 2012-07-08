--- 
title: "OpenOffice's Power Law Regression: Where did it come from?"
layout: post
---
I was poking around the source of [OpenOffice 2.x](http://www.openoffice.org/) the other day and I came across its equation regression package. Inside, there is a set of functions to support regressing to a power law function. I found the [recalculateRegression() function](http://graphics.openoffice.org/source/browse/graphics/chart2/source/tools/PotentialRegressionCurveCalculator.cxx?rev=1.5&view=markup) very interesting. I broke down the math involved in this function's operation to the following:

![](/images/ooeq1.png)

![](/images/ooeq2.png)

![](/images/ooeq3.png)

![](/images/ooeq4.png)

![](/images/ooeq5.png)

![](/images/ooeq6.png)

![](/images/ooeq7.png)

![](/images/ooeq8.png)

...where _m_ is the slope, _b_ is the intercept and _R_ is the coefficient of correlation. 

I checked Microsoft Excel and it gets the exact same answers that this formula does when it fits a power law, indicating that it, too, may be using this technique.

My question is, does anybody know where this formula came from? It looks as if they are doing a least-squares fit on a logarithmic scale, but is that right? I also haven't seen that mentioned anywhere else in my travels. E.g. [R](http://www.r-project.org/) has a package called `igraph` with a `power.law.fit()` function that uses a different technique (and strangely only yields one return value). Anybody know anything about this formula?
