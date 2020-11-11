# Measuring-Software-Engineering
## Introduction
Measuring employee performance is a practice in every industry. Managers will often schedule periodic performance reviews to evaluate if their team-member is meeting a required standard. Metrics are an essential part of this evaluation, often being the central point of analysis and discussion (AIHR Analytics, 2020). For most roles in large companies, the gathering and study of these metrics is relatively simple. For example, when measuring the performance of a technical recruiter, it is clear that the number of successful hires that they contribute to the company is a useful metric when determining if they are succeeding in their role. The number of sales that a salesperson makes is an indication of their job performance. While the above examples are not too robust, they illustrate that for some roles, there are clear employee metrics that are useful when determining employee performance.  

In the case of software engineering, we cannot use traditional metrics (TechBeacon, 2020). The nature of software engineering allows for the measurement of an abundance metrics, such as the number of commits per day, the average size of commits, the number of pull requests merged, etc. While these metrics can be somewhat useful in determining the productivity of a software engineer, they are not always the most unambiguous indication of their job performance. This report will discuss why some traditional metrics don't work, some modern metrics that are more beneficial to analyse and the ethical implications of these metrics. 

## Traditional Metrics
### Source Lines of Code
#### What is it?
Source Lines of Code (SLOC or LOC) is a metric used to measure the size of a computer program that is widely used in the evaluation of software engineers. SLOC is measured by counting the number of lines in a project's codebase (Nguyen, et al., 2007). Traditionally, SLOC is used to predict the amount of effort and time a project takes to build, as well as to estimate the productivity of software engineers.  

There are two main variations of SLOC measures: physical SLOC and logical SLOC. Physical SLOC counts the number of lines of text in a program while logical SLOC counts the number of executable expressions (PVS-Studio, 2020). Have a look at the following example:  

```
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) print(i)
```
The above code snippet has two physical SLOC and two logical SLOC (the loop operator for and the function call operator print). The comment line is included in the physical SLOC. Now have a look at the following example:

```
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) 
{
    print(i)
}
```
The above code snippet performs the exact same operations as the first example given. Yet, it contains five physical SLOC instead of the previous two. There is no defined standard for using SLOC and usage of physical and logical SLOC vary from company to company and person to person.

#### Why doesn't it work?

-----
### Bibliography
AIHR Analytics, 2020. 21 Employee Performance Metrics | AIHR Analytics. [Online] 
Available at: https://www.analyticsinhr.com/blog/employee-performance-metrics/
[Accessed 11 November 2020].
Nguyen, V., Deeds-Rubin, S., Tan, T. & Boehm, B., 2007. A SLOC Counting Standard. Center for Systems and Software Engineering: University of Southern California.
PVS-Studio, 2020. Source Lines of Code. [Online] 
Available at: https://www.viva64.com/en/t/0086/
[Accessed 11 November 2020].
TechBeacon, 2020. Why metrics don't matter in software development. [Online] 
Available at: https://techbeacon.com/app-dev-testing/why-metrics-dont-matter-software-development-unless-you-pair-them-business-goals
[Accessed 11 November 2020].







