# Measuring-Software-Engineering
## Introduction
Measuring employee and team performance is a practice in every industry on the planet. Managers will often schedule periodic performance reviews to evaluate if their team and individual team members are meeting a required standard that is expected by the company. Metrics are an essential part of this evaluation, often being the central point of analysis and discussion (AIHR Analytics, 2020). For most roles in traditional industries, the gathering and study of these metrics are relatively simple, as there is a clear correlation between the performance of a team or individual and the metrics that can be gathered about their work. For example, when estimating the productivity of a recruiter, it is clear that the number of interviews that they coordinate for potential hires is a useful metric when determining if they are succeeding in their role. Similarly, the number of sales that a salesperson makes is an indication of their job performance. While the above examples are not too robust, they illustrate that for some roles, there are obvious employee metrics that are useful when determining employee performance.  

In the specific case of software engineering, there are no obvious metrics that follow the logic of the examples above that are useful (TechBeacon, 2020). The transparent nature of software engineering allows managers to collect an abundance of metrics on their teams and team members. Such metrics include the number of pull requests merged in a period, the number of customer issues addressed by on-call engineers in a period and the number of tickets submitted by an engineer or engineering team in a period. While these kinds of metrics can be somewhat useful in measuring the number of things a software engineering team or individual software engineer are doing, they are not always the most unambiguous indication of performance. The goal of this report if to discuss why this traditional logic when selecting metrics does not work and provide some examples of modern measurement frameworks that empower engineers and managers to collaborate effectively to improve productivity. This report will also examine case studies of products that have been developed to measure software engineers and analyse the ethical implications of these tools.

## Traditional In-Process Metrics

### Source Lines of Code (SLOC)

#### What is it?
Source Lines of Code (SLOC or LOC) is a metric used to measure the size of a computer program. SLOC is one of the most widely used metrics to evaluate the productivity of software engineering teams and individual software engineers. SLOC is measured by counting the number of lines of code in a project's codebase (Nguyen, et al., 2007). Traditionally, SLOC is used the predict the amount of effort and time that a large project takes to build and to measure the productivity of the software engineers that are building it.  

In practice, there are two main variations of SLOC measures: physical SLOC and logical SLOC. Physical SLOC counts the number of physical lines of text in a program, while logical SLOC count the number of executable expressions (PVS-Studio, 2020). To illustrate the difference between physical and logical SLOC, have a look at the following example:
```java
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) System.out.println(i);
```
When calculating physical SLOC, we count the number of physical lines of code in the codebase. In the above code snippet, the value for physical SLOC is two: the first line is a comment, and the second line is a for loop with a print statement inside of it. When calculating logical SLOC, we count the number of executable expressions in the codebase. In the above code snippet, the value for logical SLOC is two: the first line is for the loop operator, and the second is for the print statement within the loop structure. Let us now analyse an example where the values for physical and logical SLOC are not the same:  
```java
// for loop that prints the numbers from 1 to 10
for(int i = 0; i < 10; i++) 
{
    System.out.println(i);
}
```
Using the methods outlined above, we can determine that the value for physical SLOC is five, and the value for logical SLOC is two. The above code snippet performs the same operations as the first example given but is written differently to increase physical SLOC. There is no defined standard for using SLOC and usage of physical and logical SLOC vary from company to company and person to person.  

#### Why doesn't it work?
Bill Gates once said that "measuring programming progress by lines of code is like measuring aircraft building progress by weight" (Goodreads, 2020). From the code snippets given above, it is clear that discrepancies exist in the use of physical SLOC, as two code snippets that perform the same operations can have slightly different physical SLOC values. The critical issue with SLOC is that it is an easy metric to game, and it encourages bad practices. Have a look at the following example, that performs the same task as the examples listed above:  
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
Using the methods outlined above, we can determine that the value for physical SLOC is twenty, and the value for logical SLOC is ten. Even though the above code snippet performs the same task as the other examples given, it is widely considered to be a nasty piece of code. Either of the other two samples is preferred, but when a software engineer is being measured with SLOC, they are encouraged to produce software that follows the above standard. When using SLOC as a primary metric to measure the productivity of software engineering teams, you are promoting quantity over quality and perpetuating a copy-paste culture. Not only this, but the refactoring of code to make things easier is also discouraged and the adding of meaningless comments that serve no purpose but to increase the SLOC metric is rewarded.   

Another issue with SLOC is that different programming languages require different amounts of lines of code to achieve the same functionality. For example, higher-level languages like Java and Python allow programmers to write useful applications using only a few lines of code. The same cannot be said for lower-level languages like C, where the lack of built-in memory management systems require programmers to carefully manage the allocation and deallocation of memory in their applications, therefore increasing the value of SLOC. Encouraging Java and Python programmers to increase the lines of code it takes to accomplish a task makes software systems more complex and incomprehensible, making it harder to add features and fix bugs in the future. Ultimately, this leads to blockers in progress and is a waste of time and money.  

### Commit Frequency

#### What is it?
Version control systems are vital in the development of large software systems and software engineering teams use them to collaborate during the development process. Version control systems are responsible for managing changes to files in computer programs and codebases that are made by software engineers. In this context, a commit is an individual change to a file or set of files in the repository that has been triggered by a developer with access to the codebase. To correctly manage this process, each commit is given a unique ID so that they can be tracked and reviewed at a later time. This provides insight into what changes were made to the source code and by whom. A commit is seen as a fundamental unit of work, and commit frequency is often used to measure the contribution and productivity of software engineers (Kolassa et al., 2014).    

The measurement of software engineering teams with commit frequency is used to varying degrees of effectiveness. The idea is simple; the higher the frequency of commits by an individual software engineer, the more productive they are. This idea also translates to measuring teams, where teams are compared by commit frequency and the higher the commit frequency of a team, the more productive they are. Companies and managers have used this assumption to drive performance reviews, but there is no standard for using commit frequency to measure software engineers.  

<img src="https://docs.cloudbees.com/docs/cloudbees-cd/latest/devops-insight/_images/dois/03000047.6175d30.png">

#### Why doesn't it work?
Generally, it is a good practice for programmers to make consistent commits throughout their work on a task. The frequency and size of a commit is a matter of personal preference as there is no definitive guide on how a commit should appear. In fact, the subject is hotly debated by engineers of all disciplines. As a result of this ambiguity, each software engineer develops their own practice when using version control systems that allow them to be as productive as possible. Some engineers prefer to make very small commits as often as possible so that they have as many options as possible in case a revert is required. Other engineers prefer to make larger commits more seldomly, thoroughly testing each function that they write before they make a commit. A preferred approach among many software engineers is to break commits up into logical sections so that each commit deals with a different problem or portion of the codebase.  

The critical issue that arises when using commit frequency to measure software engineers is the same as that of SLOC; it is an easy metric to game. It is sometimes argued than frequent small commits are more useful than seldom larger ones, but this is not always possible. Often, problems of greater complexity require more time to solve and require a significant amount of changes to the codebase. These scenarios result in larger, less frequent commits while solving many more straightforward, sometimes trivial issues (such as comments and formatting) result in many, smaller commits. Using commit frequency as a metric to evaluate software engineer's performance discourages them from taking on large complex issues of design and problem solving, and encourages them to make small refactors to pieces of code that are working as they should be.  

### Why don't traditional metrics work?
The metrics that have been discussed thus far began being used to measure productivity in the 1970s when the Waterfall Development Model (WDM) was used to develop software. The WDM is one of the most common software development practices, which involves the breakdown of project activities into linear sequential phases. In the WDM, each step depends on the completion of the previous one, as the features that are implemented in any stage require the deliverables of the previous one. For example, the data visualisation portion of a project would depend on the competition of the REST API from which the data will be gathered. In the WDM, in-process metrics such as commit frequency and SLOC can be useful; higher metrics mean that more work is being done to deliver the requirements of the current stage (McCormick, 2012).  

Software development has changed since the 1970s. Modern software development organisations adopted the Agile Development Method (ADM) in the early 2000s. The ADMs approach to software development discovers requirements through the development of solutions and relies on the collaboration of cross-functional teams and their customers/end-users. This differs significantly from the WDM approach. With such a difference in approach to developing software, a similar distinction is required in the course in measuring it. This difference is the use of outcome metrics rather than in-process metrics and the adoption of team-driven project measurement. This means that productivity is calculated in accordance with business goals, and engineers are evaluated based on the quality and importance of their code to the goals of the project and company.  

## Modern Outcome Metrics

### Sprint Breakdowns

#### What are they?
Sprint Burndowns are commonly used in agile software development methodologies like SCRUM. SCRUM is a framework in which the development process is broken into several short cycles called Sprints. The goal of a Sprint is to complete a planned amount of work so that it is ready for review. Sprints can range from a couple of days to 3-4 weeks. During a Sprint, software engineers work toward a pre-determined Sprint goal while planning, refining, building, testing, and reviewing. The goals and structure of a Sprint are decided in a Sprint planning meeting, where a set of desired features are pulled from the top of the product backlog so that they can be implemented in the coming Sprint (Schwaber, 1997).  

During a Sprint, daily SCRUM meetings are held, where team-members synchronise their efforts. These daily SCRUM meetings ensure that the right people are working on the right things at the right time. Each member of the team is asked three questions:
1.	What did you do yesterday to help achieve the Sprint goal?  
2.	What will I do today to accomplish the Sprint goal on time?  
3.	What is impeding progress toward the Sprint goal?  
Sprint Burndown is a technique used to display the remaining work of the current Sprint in a daily SCRUM meeting. Often, a Sprint Burndown chart is used where the vertical axis represents the work remaining, and the horizontal axis represents the time remaining in the Sprint. The total amount of work left is determined in the daily SCRUM meetings, and points are plotted on the Sprint Burndown chart. Drawing a line through these points allows the development team to monitor their progress through a Sprint's workload (wibas, 2020). This technique is used to measure the productivity of both software engineering teams and individual software engineers, as individual software engineers are asked daily about their contributions to the project.  

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/SampleBurndownChart.svg/1200px-SampleBurndownChart.svg.png">

#### Why they work
Sprint Burndown is a powerful tool that empowers software engineer to drive overall projects and individual features themselves. It also includes them as an active member of the software measurement process. Instead of monitoring artificial metrics such as lines of code and number of commits, the specific contribution to features and projects is tracked, and the team collaborates to ensure that every team member is making progress. This visibility allows teams to adapt to any technical challenges that arise and provides feedback on the proposed schedule daily, thus reducing risks and alerting the team if any problems occur.  

Using Sprint burndowns to measure productivity is a useful process that encourages software engineers to write quality code promptly and to communicate with their peers what work they are doing at all times. Measuring the performance of an individual software engineer is simple, as the Sprint Burndown chart monitors the contributions of each engineer on the team. Using Sprint Burndowns provides a software development team with a structured framework in which to work and gives them the capacity to grow as engineers. This process is much more than a measurement technique for teams and individuals; it is a system in which software engineers are encouraged to thrive.  

### Team Velocity

#### What is it?
Team velocity is a simple and extremely powerful method for measuring the rate at which software development teams using SCRUM deliver business value. In agile development, a user story is a programming task that is a part of a compartmentalised problem or feature. A story point is a metric that is used as an abstract measure of a combination of the difficulty of the user story and the effort required to implement the story. In simpler terms, a story point is a number that estimates the difficulty of a user story. Generally, team velocity is measured in story points. Much like in Sprint Burndowns, story points are decided by the software engineers on a team, taking into consideration the complexity and risk of the story, as well as the amount of time required to implement it (Visual Paradigm, 2020). Stories can range from fixing tests that are broken to extensive changes to the algorithmic approach of an application but usually should take no longer than five to ten days to implement. If a story is projected to take longer than this, it should be broken down into smaller stories that are more manageable.  

Team velocity is a measure of the number of story points completed in a given Sprint. Thus, calculating team velocity is simple; the sum of the story points completed during the successful delivering of features during a Sprint is the team velocity (Visual Paradigm, 2020). There are other algorithmic approaches to calculating team velocity, such as the below model:
```
Vi = (Number of story points completed in the Sprint)/(Duration of the Sprint)
```
The approach when using story points is similar to the approach when using Sprint Burndowns, as the story points are updated daily in a SCRUM meeting so that the team knows how many story points are left on any development tasks. Team velocity and Sprint Burndowns are often used together to measure the productivity of teams and individuals. Team velocity can also be measured in hours of work instead of story points, where team-members estimate the number of hours required to complete a task.

<img src="https://www.sealights.io/wp-content/uploads/2018/07/sprint-velocity.jpg">

#### Why it works
Team velocity is a crucial metric in measuring the productivity of software development teams and induvial software engineers in the modern software industry. Measuring team velocity helps teams:  
1.	Predict the number of stories that can be delivered by a specific date.
2.	Predict the date that a fixed number of stories can be delivered.
3.	Adapt to unforeseen challenges that were not seen during sprint planning.  

The algorithmic model described above is used to compare the productivity of teams and individuals to previous values obtained by the model for those teams and individuals. Put simply, the velocity metric obtained by every team is unique and should not be used to compare Team A to Team B or Engineer A to Engineer B. Each team has a specific estimation culture, resulting in different interpretations of story points. Therefore, team velocity is useful when comparing how a team or individual is performing relative to their previous performance, but not for comparing distinct individuals or teams.  

When a team has completed a series of Sprints, the team can use its velocity calculations to forecast release and project completion dates. Based on the velocity of the previous Sprints, the team can track how much work has been reported as complete for each Sprint and estimate how much backlog effort can be planned for if the Sprint velocity, duration and composition remain constant. Team velocity allows teams and managers to measure productivity but also provides much-needed insight into the future of the project and allows for accurate planning of future Sprints.


## Case Studies

### Case Study #1: Humanyze

#### What is it?
Ben Waber is the President and Co-Founder of Humanyze, a company that is "paving the way in leveraging Workplace Analytics to help companies make better, faster business decisions that improve both performance and the employee experience" (Humanyze, 2020). Waber calls this new field of "innovative" research "people analytics" (Business Insider, 2016). Humanyze manufacture digital badges that are worn by employees that watch and listen to their every move. These digital badges look like lanyards but have the functionality to monitor the actions and conversations of employees throughout the workday. These badges learn who employees communicate with to solve issues and can even determine employee stress levels by measuring heart rate and voice inflexion. Once a company has collected enough data from the badges, it sends this unformatted data to Humanyze, who visualise the data as a series of webs. These webs provide insight into social interactions on a second by second basis. The goal of Humanyze is to revolutionise the way that companies organise themselves.  

More than 10,000 employees wear Humanyze badges in industries across the United States. These badges thrive in companies with a smaller number of employees, that can make rapid changes to seating charts to manage and streamline communication between team members. Humanyze is backed by decades of MIT research that helps companies uncover patterns on how their employees get work done. Humanyze provides its customers with unique metrics, such as "Organization Health", which objectively quantify the health of an organisation through the analysis of employee engagement, team productivity and organisational adaptability. Humanyze endeavours to continuously measure and analyse the actions of employees to improve their performance and productivity (Humanyze, 2020).  

### Ethical Concerns
Waber has stressed that people opt into wearing Humanyze badges and that representatives from the company "go in and talk to employees about what data we collect, that we don't share it, that it's anonymous and not about recording your bathroom breaks. It's a legal contract that people choose to sign" (HR Magazine, 2020). Waber has also stated that anyone who is uncomfortable with the concept and does not opt into the monitoring service is given a fake badge so that none of the other employees know. This raises a sinister question; if this is a contract that people choose to sign, why is there a need for fake badges? These scenarios that are disguised as opt-in services end up being non-negotiable company-wide changes that employees are forced to adopt. This practice raises ethical concerns; is it appropriate for companies to force their employees to opt-in to second by second monitoring?  

The critical ethical issue with Humanyze badges is their lack of intelligence. They are not sophisticated enough to distinguish between personal and professional conversations; they are programmed to monitor employees at all times throughout the day. Thus, regardless of whether it is intentional or not, private discussions and actions are recorded and sent to Humanyze for analysis. This raises an abundance of ethical issues; is it appropriate for a company to monitor the number of americanos that an employee consumes in a day? Is it suitable for a company to analyse water-cooler conversation about weekend barbecues? It makes sense for a company to attempt to maximise the productivity of their employees, but is it ethical to do so at the cost of the employees' privacy? These practices can be likened to those of Big Brother in George Orwell's novel, "Nineteen Eighty-Four" and disrespect the civil liberties of employees, specifically concerning mass surveillance.  

-----
### Bibliography
AIHR Analytics, 2020. 21 Employee Performance Metrics | AIHR Analytics. [Online]  
Available at: https://www.analyticsinhr.com/blog/employee-performance-metrics/  
[Accessed 11 November 2020].  

Business Insider, 2016. Humanyze badges watch and listen to your every move - Business Insider. [Online]  
Available at: https://www.businessinsider.com/humanyze-badges-watch-and-listen-employees-2016-10?r=US&IR=T  
[Accessed 17 November 2020].  

Goodreads, 2020. Quote by Bill Gates: “Measuring programming progress by lines of code...”. [Online]  
Available at: https://www.goodreads.com/quotes/536587-measuring-programming-progress-by-lines-of-code-is-like-measuring  
[Accessed 12 November 2020].  

HR Magazine, 2020. The ethics of gathering employee data. [Online]  
Available at: https://www.hrmagazine.co.uk/article-details/the-ethics-of-gathering-employee-data#comment-35066  
[Accessed 17 November 2020].  

Humanyze, 2020. Humanyze - Analytics For Better Performance.. [Online]  
Available at: https://www.humanyze.com/  
[Accessed 17 November 2020].  

Kolassa, C., Riehle, D. & Salim, M. A., 2014. The Empirical Commit Frequency Distribution of OpenSource Projects. Friedrich-Alexander-University: arXiv.  

McCormick, M., 2012. Waterfall vs. Agile Methodology. Revised Edition 8/9/2012 ed. Washington DC: MPCS, Inc..  

Nguyen, V., Deeds-Rubin, S., Tan, T. & Boehm, B., 2007. A SLOC Counting Standard. Center for Systems and Software Engineering: University of Southern California.  

PVS-Studio, 2020. Source Lines of Code. [Online]  
Available at: https://www.viva64.com/en/t/0086/  
[Accessed 11 November 2020].  

Schwaber, K., 1997. SCRUM Development Process. Burlington, MA: Advanced Development Methods.  

TechBeacon, 2020. Why metrics don't matter in software development. [Online]  
Available at: https://techbeacon.com/app-dev-testing/why-metrics-dont-matter-software-development-unless-you-pair-them-business-goals  
[Accessed 11 November 2020].  

Visual Paradigm, 2020. What is Story Point in Agile? How to Estimate a User Story?. [Online]  
Available at: https://www.visual-paradigm.com/scrum/what-is-story-point-in-agile/  
[Accessed 16 November 2020].  

wibas, 2020. Sprint Burn Down. [Online]  
Available at: https://www.wibas.com/scrum/sprint-burn-down/en  
[Accessed 13 November 2020].  


 


