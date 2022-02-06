# Implementation and Deployment

# **Implementation Introduction**

Implementation is the step where we actually begin coding our project. We have detailed what objectives the system should meet, have come up with a good design, and are now ready to begin coding.

This process is going to be very specialized on what the system calls for. A website, iPhone app, server OS, desktop app, and eCommerce store will all be entirely different projects. Because of this, in this section I want to focus more on the theory about implementation and deployment. If you want to learn more about the technology that will solve your problem specifically, I might suggest looking up a specific course here on Udemy. There are many great options out there for just about anything.

# **Implementation Overview**

**Programmer Care**

The number one thing to understand when building software is to take care of your engineers/programmers. When a programmer starts to get tired, their code quality decreases. This decrease in quality can attribute to poor architecture, design, and overall code. This introduces the idea of "technical debt".

Technical debt is a corner cut now, that will cost up to 10x the effort later on. So a 1 hour corner cut now, could cost 10 hours of work down the road. We want to prevent this as much as possible. Imagine if we gained 10 hours of technical debt every week over the course of a 26 week build. That would total to 260 hours of bad work. This means we could be looking at 2600 hours, or 325 WORKDAYS of effort to fix those problems.

We have to remember that 35 hours a week of programming can be just as productive as 70 hours when we factor in technical debt.

**Coding Principals**

- Use a style guide, so all the code looks generally the same.
- Code is written for people, not computers.
- Make modules easy to learn and understand.
- Go into everything with a plan. (You can experiment, but clean up after)
- Shorter code does not equal better code! MAKE IT READABLE.
- Break up actions into methods.

More Information: [https://www.makeuseof.com/tag/basic-programming-principles/](https://www.makeuseof.com/tag/basic-programming-principles/)

**Buy Vs. Build**

Good design allows us to see our entire project before it is built. With this, we can decide which areas we want to build, and which areas we want to purchase. The great thing about purchasing code is that it is almost always cheaper.

Imagine a company which develops a subsystem to sell. They spend 3000 man hours building it. At a rate of $40 an hour, they would have spent $12,000 developing the software. If we wanted to build the same thing, we could expect the same outcome in cost.

However, this company wouldn't sell it at $12,000. They have the benefit of being able to sell it over and over and over again. Because of this, they might sell it at say $500. They only need 24 sales to break even, and we save $11,500 through purchasing it.

It's almost always a win-win situation to purchase instead of build. Coding however is usually very specific. This makes it rare to find software that perfectly fits the problem. However, do some research before you begin building, you can save a lot of money.

More Information: [https://www.scalyr.com/blog/build-vs-buy/](https://www.scalyr.com/blog/build-vs-buy/)

# **Deployment Notes**

# **Deployment Overview**

Deployment is the time when we take our program, and deploy it to it's final location. So if it's a website, this is the point we make it public to all. Deployment is an interesting part of the software development process. It comes after testing, but must be planned out, typically before implementation. To get it correct, we must also typically program it a certain way, meaning it also fits into the implementation section.

The level of planning here directly relates to how large the scope of the deployment is. If we are deploying the system for the first time, a lot of planning needs to take place. If we are applying a really small bug patch, then we don't need as much planning.

Deployment should always be designed with the idea of retreat. If something goes wrong, how can we revert. During the initial deployment, this plan might be to take the product back offline. If however we are running a website like Amazon, we will have to do a bit more planning. If we accidentally break the website, we need the fastest plan possible to return the site to it's previous version.

# **Deployment Rollback**

This process of retreat is officially known as "rollback".  We look for the point of no return. This is the single point where it takes longer to go back, than it does to just continue with the deployment.

Knowing this point of no return helps us make the decision to rollback, or continue forward. When planning our rollback, we should have key points during the process. At each of these points, we will need to make the decision of whether we rollback, or continue forward.

If a fatal error comes up at any point, even right before completion, we need a plan to get back to the previous version. Maybe this plan entails switching to a backup server, or undoing changes, or having a hybrid version of the two updates running together. Whatever it is, we need to have it planned out beforehand.