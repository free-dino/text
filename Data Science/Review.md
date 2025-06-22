# 1. Hypothesis Testing
**Purpose**: To answer a question about a process or the world by testing 2 hypothesis, a null and an alternative. 
"Null hypothesis": The world/process works this way
"Alternative hypothesis":  The world/process does not work that way

## 2. Step
1. Precisely state the null and alternative hypothesis
2. Decide on a test statistic
	1. If the data is categorical, a good test statistic might be the TVD
	2. Other tests
3. Calculate the observed value of the test statistic, using the original sample of data. Use this value to calculate the p-value.
4. Simulate all possible values of the test statistic under the null hypothesis.
	1. Find all possible values.
	2. Steps:
		1. Create and empty array
		2. *For loop*: either one that runs the given number of repetitions, or if no number is specified, 10,000 times.
		3. Under the for loop, simulate under the null hypothesis
		4. Calculate the value of the test statistic for that resample and append that value to your results array outside the loop