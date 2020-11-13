# Measuring-Software-Engineering
## Introduction
Measuring employee performance is a practice in every industry. Managers will often schedule periodic performance reviews to evaluate if their team-member is meeting a required standard. Metrics are an essential part of this evaluation, often being the central point of analysis and discussion (AIHR Analytics, 2020). For most roles in large companies, the gathering and study of these metrics is relatively simple. For example, when measuring the performance of a technical recruiter, it is clear that the number of successful hires that they contribute to the company is a useful metric when determining if they are succeeding in their role. The number of sales that a salesperson makes is an indication of their job performance. While the above examples are not too robust, they illustrate that for some roles, there are clear employee metrics that are useful when determining employee performance.  

In the case of software engineering, we cannot use traditional metrics (TechBeacon, 2020). The nature of software engineering allows for the measurement of an abundance metrics, such as the number of commits per day, the average size of commits, the number of pull requests merged, etc. While these metrics can be somewhat useful in determining the productivity of a software engineer, they are not always the most unambiguous indication of their job performance. This report will discuss why some traditional metrics don't work, some modern metrics that are more beneficial to analyse and the ethical implications of these metrics.  

## Traditional In-Process Metrics

### Source Lines of Code (SLOC)

#### What is it?
Source Lines of Code (SLOC or LOC) is a metric used to measure the size of a computer program that is widely used in the evaluation of software engineers. SLOC is measured by counting the number of lines in a project's codebase (Nguyen, et al., 2007). Traditionally, SLOC is used to predict the amount of effort and time a project takes to build, as well as to estimate the productivity of software engineers.  

There are two main variations of SLOC measures: physical SLOC and logical SLOC. Physical SLOC counts the number of lines of text in a program, while logical SLOC counts the number of executable expressions (PVS-Studio, 2020). Have a look at the following example:  
```java
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) System.out.println(i);
```
The above code snippet has two physical SLOC and two logical SLOC (the loop operator for and the function call operator print). The comment line is included in the physical SLOC. Now have a look at the following example:
```java
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) 
{
    System.out.println(i);
}
```
The above code snippet performs the same operations as the first example given. Yet, it contains five physical SLOC instead of the previous two. There is no defined standard for using SLOC and usage of physical and logical SLOC vary from company to company and person to person.

#### Why doesn't it work?
Bill Gates once said, "Measuring programming progress by lines of code is like measuring aircraft building progress by weight" (Goodreads, 2020). The issue with SLOC is that it is an easy metric to game, and it encourages bad practices. Take the following piece of code that we looked at before:  
```java
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) System.out.println(i);
```
Previously, we established that this code snippet has two physical SLOC and two logic SLOC. Let us compare this example to the following, which performs the same operations:  
```java
// Print the number 1
System.out.println(1);
// Print the number 2
System.out.println(2);
// Print the number 3
System.out.println(3);
// Print the number 4
System.out.println(4);
// Print the number 5
System.out.println(5);
// Print the number 6
System.out.println(6);
// Print the number 7
System.out.println(7);
// Print the number 8
System.out.println(8);
// Print the number 9
System.out.println(9);
// Print the number 10
System.out.println(10);
```
The above code snippet has twenty physical SLOC and ten logical SLOC. The former is accepted as the correct way of performing this task, and the latter is widely considered a nasty piece of code. Therefore, when using SLOC as a metric to measure the productivity of software engineers, you are encouraging quantity over quality and perpetuating a copy-paste culture. This also discourages the refactoring of code to make things easier and encourages meaningless comments that serve no purpose but to increase the SLOC metric.  

In higher-level languages like Java and Python, programmers can write more useful applications using fewer lines of code than in other languages. Encouraging these programmers to increase the lines of code it should take to accomplish a task makes software systems more complex and harder to understand, making it harder to add features and fix bugs in the future. Ultimately, this leads to blockers in progress and is a waste of time and money.  

### Commit Frequency

#### What is it?
Software engineers often use version control systems when collaborating on projects. These version control systems are responsible for managing changes to files in computer programs and codebases. A commit is an individual change to a file or set of files in the repository that is managed by the version control system. Every commit is given a unique ID that provides insight into what changes were made to the source code. A commit is seen as a fundamental unit of work and is often used to measure the contribution and productivity of software engineers (Kolassa et al., 2014).  

Measuring software engineers with commit frequency is widely used to varying degrees of effectiveness. The idea is simple; the higher the number of commits a software engineer is making, the more productive they are. This assumption has been used in many companies to drive performance reviews, but there is no standard for using commit frequency when using this metric. 

<img src="https://tech.just-eat.com/wp-content/uploads/2016/01/hackathon_12.png">

#### Why doesn't it work?
Generally, programmers should make consistent commits throughout their work. The frequency and size of commits is a matter of personal preference. There is no definitive guide on what a commit should look like, and the subject is debated by all software engineers. As a result of this ambiguity, each software engineer develops their own practice when using version control systems. Some engineers prefer to make very small commits as often as possible. Some engineers prefer to make large commits seldomly. Some engineers prefer to break commits up into logical sections so that each commit deals with a different problem or part of the codebase.  

The main issue that arises when using commit frequency to measure software engineers is similar to that of SLOC; it is an easy metric to game. While it can be argued that frequent small commits are more useful than larger ones, it is not always possible to make tiny commits. More often than not, problems of greater complexity require more time to solve and can result in fewer commits, while solving many sometimes trivial issues (such as comments and formatting) result in many commits. Using commit frequency as a metric to evaluate software engineers performance discourages them from taking on large complex issues of design and problem solving and encourages them to make small refactors to pieces of code that are working fine.  

### Why don't traditional metrics work?
The metrics discussed above were initially used to measure the productivity of software engineers in the 1970s when the Waterfall Development Model (WDM) was being used to develop software. The waterfall model is a software development practice which involves the breakdown of project activities into linear sequential phases. In the WDM, each step depends on the completion of the previous one, as the features that are implemented in a stage requires the deliverables of the previous one. In the WDM, in-process metrics such as commit frequency and SLOC can be useful; higher metrics mean that more work is being done to deliver the requirements of the current stage (McCormick, 2012).  

Modern software development organisations adopted the Agile Development Method (ADM) in the early 2000s. The ADM approach discovers requirements through the development of solutions and relies on the collaboration of cross-functional teams and their customers/end-users. This differs significantly from the WDM approach. This difference in approach to developing software requires a difference in approach to measuring productivity and involves the analysis of outcome metrics rather than in-process metrics. This means that productivity is measured in accordance with business goals, and engineers are evaluated based on the quality and importance of their code.

## Modern Outcome Metrics

### Sprint Breakdown

#### What is it?
Sprint burndown is commonly used in software development methodologies like SCRUM. SCRUM is a framework in which the development process is broken into several short cycles called Sprints. The goal of a Sprint is to complete a planned amount of work, so that is ready for review. Sprints can range in length from a few days to 3-4 of weeks. Engineers work towards a Sprint goal while planning, refining, building, testing and reviewing. The goals and structure of a Sprint are decided in a Sprint planning meeting, where a set of desired features are pulled from the top of the product backlog so that they can be implemented in the coming Sprint (Schwaber, 1997).  

During a Sprint, daily SCRUM meetings are held, where team members synchronise their efforts. Daily SCRUM meetings ensure that the right things are being worked on by the right people at the right time. Each member on the team is asked three questions:  
1. What did you do yesterday to help achieve the Sprint goal?  
2. What will I do today to accomplish the Sprint goal on time?  
3. What is impeding progress toward the Sprint goal?  

The Sprint Burndown is a technique used to display the remaining work of the current Sprint. Often, a Sprint Burndown chart is used where the vertical axis represents the work remaining, and the horizontal axis represents the time remaining in the Sprint. The total amount of work left is determined in the daily SCRUM meetings, and points are plotted on the Sprint Burndown chart. Drawing a line through these points allows the development team to monitor their progress through a Sprint's work. This technique is used to measure the productivity of both software engineering teams and individual software engineers.  

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/SampleBurndownChart.svg/1200px-SampleBurndownChart.svg.png">

#### Why it works
Sprint Burndown is a useful tool that empowers software engineers to drive overall projects and individual features themselves. Instead of monitoring artificial metrics such as lines of code and number of commits, the specific contribution to features and projects is tracked, and the team collaborates to ensure that every team member is making progress. This visibility allows teams to adapt to technological challenges and provides feedback on the proposed schedule daily, thus reducing risks and alerting the team if any problems arise.  

Using Sprint Burndowns to measure productivity encourages software engineers to write quality code promptly and to communicate with their peers what work they are doing. Measuring the performance of an individual software engineer is simple, as the Sprint Burndown chart monitors the contributions of each engineer on the team. Using Sprint Breakdowns provides a software development team with a framework in which to work, gives them the capacity to grow as engineers and allows the useful measurement of groups and individuals.

-----
### Bibliography
AIHR Analytics, 2020. 21 Employee Performance Metrics | AIHR Analytics. [Online]  
Available at: https://www.analyticsinhr.com/blog/employee-performance-metrics/  
[Accessed 11 November 2020].  

Goodreads, 2020. Quote by Bill Gates: “Measuring programming progress by lines of code...”. [Online]  
Available at: https://www.goodreads.com/quotes/536587-measuring-programming-progress-by-lines-of-code-is-like-measuring  
[Accessed 12 November 2020].  

Kolassa, C., Riehle, D. & Salim, M. A., 2014. The Empirical Commit Frequency Distribution of OpenSource Projects. Friedrich-Alexander-University: arXiv.  

McCormick, M., 2012. Waterfall vs. Agile Methodology. Revised Edition 8/9/2012 ed. Washington DC: MPCS, Inc.  

Nguyen, V., Deeds-Rubin, S., Tan, T. & Boehm, B., 2007. A SLOC Counting Standard. Center for Systems and Software Engineering: University of Southern California.  

PVS-Studio, 2020. Source Lines of Code. [Online]  
Available at: https://www.viva64.com/en/t/0086/  
[Accessed 11 November 2020].  

Schwaber, K., 1997. SCRUM Development Process. Burlington, MA: Advanced Development Methods.  

TechBeacon, 2020. Why metrics don't matter in software development. [Online]  
Available at: https://techbeacon.com/app-dev-testing/why-metrics-dont-matter-software-development-unless-you-pair-them-business-goals  
[Accessed 11 November 2020].  

wibas, 2020. Sprint Burn Down. [Online]  
Available at: https://www.wibas.com/scrum/sprint-burn-down/en  
[Accessed 13 November 2020].  


 









