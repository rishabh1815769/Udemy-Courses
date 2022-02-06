# Design: Modularity

# **Design Introduction**

Once we have the architecture of the system set up, we can begin working on the design. The design is where we really plan out our system. We can go as detailed as possible in this step.

The main focus here is to break up the project into subsystems, and modules.

**Subsystem** - Independent system which holds independent value.

**Module** - Component of a subsystem which cannot function as a standalone.

For example, let's say in our architecture phase we separated the main project into 4 different areas. We would look into each of these 4 areas and come up with the subsystems that would be needed. We would then go into each of those subsystems and see if it can be broken into more subsystems. Eventually we will reach a level where we then come up with some modules that work together to accomplish the task of the subsystem.

Figuring out where to separate the program is one of the most difficult parts of software development. It's very easy to stick with the attempt. This however is just as bad as skipping design entirely, and doing as you program. This step should be iterative. We should slowly refine and reorganize the systems and sub-modules until they make the most sense. Having multiple engineers with multiple viewpoints working on this will help the process immensely.

# **Information Hiding and Data Encapsulation**

**Information Hiding** - Hiding the complexity of the program inside of a "black box".

**Data Encapsulation** - Hiding the implementation details from the user, providing only an interface.

Both of these work to hide the implementation details, and protect the integrity of the data. We want to control the flow of data, and provide the user with an easy to use experience.

Imagine on Facebook if you needed to know how to code to submit a new status update. No one would use it. So what we do is we encapsulate that function. We provide the user with an area to enter in a status message. Once the user hits the submit button, all of the code activates to make that status update permanent. All the user needs to do is enter text into the box and click a button.

With these ideas, we can take the most complex of code, and make it accessible to anyone. Doing this at each step in the design process also helps make the code easier to maintain.

With it implemented properly, we don't need to know the entire codebase to make a change. We only need to know the part of the program we are working on. The encapsulation of all the other levels of the program, make things easy to test and change.

More Information: [https://techdifferences.com/difference-between-data-hiding-and-encapsulation.html](https://techdifferences.com/difference-between-data-hiding-and-encapsulation.html)

# **Coupling Notes**

# **Coupling Introduction**

Coupling is one of the major things to look at when designing the modularity of the system. It details how dependent each module is on every other module. A set of modules with tight coupling is bad design. It creates hard to maintain code.

Think about designing a program, and just creating a random set of files to detail that system. There are let's say 1,000 files that make the system work. Each file uses information and calls from 10 other files. Let's say we want to take out a file and replace it with a new one.

At a minimum we will have to update 10 files to make this change. What if one of those calls goes one layer deeper. We have a possibility of 10 * 10, or 100 files that might need to be changed.

This will make the program very inflexible. After it's created, it will only be able to serve one purpose. Any changes will require a ton of effort and money. Overtime the program will quickly become outdated due to this cost.

Our enemy with all of this is dependence. We don't want our modules to be dependent on one another. We want to be able to swap one module out with another, and only have to update code in the swapped module. The more dependent our program is, the more and more modules we will have to rewrite for every change.

# **Tight Coupling**

This is the worst form of coupling. Tight coupling means there is a strong dependence between modules. Changes will be very hard to make and bugs will be difficult to track down.

**Content Coupling -** This details when one module modifies or relies on the inner workings of another module. If we have module A and module B, tight coupling would be A calling B.data. A in this situation is directly calling the data from B. This means if B were to change, be replaced, or even just be renamed, then A would fail. If a bunch of files all called the information directly from B, and B were renamed, there would be failures in each of these files.

**Common Coupling -** This is when a bunch of modules have access to manipulate the same global data. If 10 files directly read and write to this global data, we can quickly run into issues. Let's say one of the modules is built wrong. It pushes up an incorrect value to the global data. The other 9 files pull this data down, and instantly corrupt. We now have errors in 10 different places in our program. The only way to track an issue like this down, is to check all 10 files. It becomes a nightmare to debug.

Also, if that variable in the global data is renamed, we have to update all files which touch it as well. Same if we want to split up, or rework the global data. We end up running into a problem where a simple rename project could take weeks.

**External Coupling -** This coupling is when several modules have direct access to the same external Input/Output. A common example of this is with an API. Let's say we have a program with 800 different files all making API calls to Google.

The issue here is we don't have control over Google. They are free to change their API whenever they want. One day Google does just that. They decide to rename a call we use. We now have to update 800 different files to mitigate this change. More importantly, our active code will be errored out until we can make those changes. If we are running an online store, that can be a very large amount of money lost.

# **Medium Coupling**

Here the coupling is getting better, but we still have room for improvement.

**Control Coupling -** This is when data is passed that influences the internal logic of another module. A common example of this is through the use of a flag system. Let's say you have a module X which calculates a value depending on the country you are in. So module X must take in the data, and then a country flag to work.

Any module which accesses X will have direct control over it. If we go into module X and change one of the values, we have the possibility of breaking every single direct call.

A better way to do this would be to enter in a latitude and longitude as variables. This way, module X is free to process that data how it wants. It can select the country from within, and make the applicable changes. It can switch out it's code format, and nothing will break.

**Data Structure Coupling -** This is when multiple modules share the same data-structure. We are starting to get into the area where we might be able to justify this action. Here the major problem is if we switch out the data structure.

If we have multiple modules updating the same Array, there will be a problem if we decide to change it to a linked-list. We will have to update every module. These modules all become dependent on the data-structure. If we find out a new data structure will improve our program, we will have to spend a lot of time in the change.

# **Loose Coupling**

**Data Coupling -** This is when two modules share the same data. This is a good form of coupling. At the end of the day, our program's modules have to communicate with one another. With this form of coupling, the only thing we are passing back and forth is data. Our modules are processing the data, and making their decisions independently. Due to this, our dependency overall is extremely low.

We have the ability to swap our modules easily, with little code that must be updated. Our program becomes more flexible, and easier to maintain.

**Message Coupling -** This coupling is when messages or commands are passed between modules. This is when we send a message to another module that tells it to start/stop, or run a function. We aren't controlling how these operations are being implemented. We are just giving the modules messages, which it then interprets and executes through it's own logic.

**No Coupling -** No communication between modules whatsoever. This is undesirables and unrealistic. Our modules need to communicate to have a purpose. No communication is purely a theory level. Our goal is to get as close to data and message coupling as possible.

# **Cohesion Notes**

# **Cohesion Introduction**

Cohesion is the other area to focus on when we are talking about modularity. Cohesion is the measurement of how focused our module is on a single task. The more focused the module, the higher the cohesion.

With cohesion, higher is better. We want modules which only do one thing and one thing only. The reason for this is with maintainability. Imagine if the entirety of Facebook was on a single file. This would be extremely hard to maintain. There would be millions of lines of code read through to fix a single bug.

Not only this, but we couldn't reuse that code anywhere. If however we have a module which "swaps two values in a database", then we can reuse that in other projects. If we are smart and build a set of really cohesive modules, we can use those modules as building blocks for our next project.

Our goal with modularity is to balance both coupling, and cohesion. A single file is not very cohesive, but it's perfect coupling. 1000 tiny 1 line modules which are linked to other modules are highly cohesive, but very tightly coupled. What we want to find is the point where we can maximize the effects of both. We want to create loose coupling, and high cohesion.

# **Weak Cohesion**

**Coincidental Cohesion -** The tasks within the module are only linked because they are in the same module. This is the weakest form of cohesion. Here, the modules are completely random. There is nothing linking the tasks within a module, except the fact that they were simply put into the same file.

A single file project would be an example of this. The only reason everything is in the same file, is because no additional files were created. Essentially there is no organization.

**Temporal Cohesion -** The tasks within the module are only linked because events happen around the same time. Example a module which does:

- Brush Teeth
- Take Shower
- Eat Breakfast
- Wake Up

Here the tasks are only linked together because they happen in the morning. Past that, anything goes. An example in the computer world would be "do shutdown activities". In this command we could be doing server calls, shutting off physical machines, sending emails, updating the front end, etc. The list could include really anything. For this reason, it is weakly cohesive.

**Logical Cohesion -** The tasks within the module are linked due to being in the same general category. With this level, we have begun to organize the modules a bit more. We have made general categories, and broken up the modules into these categories. Example:

- Drive to Dallas
- Fly to Dallas
- Take Train to Dallas
- Take Boat to Dallas

In the above example, the category here is "getting to Dallas". Flying and driving are completely and totally different however. Their implementations would involve entirely different sets of code.

If our module for example was "backup manager", then it still has a lot of wiggle room. In this controller we could be backing up user data, financial data, cache, cookies, and so on. Additionally we could be running commands that might have to do with backing up. Overall, this is still a weak form of cohesion.

# **Medium Cohesion**

**Procedural Cohesion -** The order of execution passes from one command to the next. Here we have a relationship of time. This is different from temporal because the tasks are both linked, and essential for one another. There is an order by which these must be executed to work properly.

- Spray car with Water
- Fill out form
- Scrub Car and Rinse
- Dry off Car

You can see that drying off the car before we washed it wouldn't make too much sense. However, there isn't a direct link to task focus in this category. "Fill out form" is apart of the business process. It's true that it happens at this point in the procedure, but it's not as focused as we would like.

**Communicational Cohesion -** When all tasks support the same input and output data. Here we start to organize by an important factor, data. We are now beginning to organize based on computer science related areas, instead of just "logical" areas. Example module:

- Find author of article
- Find date of article
- Find length of article
- Set content of article

Here we are accepting an article as input, and returning a value about that article as output. This module is very specified, dealing with only articles and their content.

**Sequential Cohesion -** A combination of the previous two. When all tasks work in which the output data for one, is the input data for the next. With this, we have a procedure of tasks, and these tasks all share the same data. Example module:

- Sand car body
- Apply primer to car
- Spray main coat to car
- Spray clear coat to car

With this example, we take a car object and pass it into the first. After this task is complete, it takes the modified car and sends it to second. Then the car goes to the third, and finally to the last. In this process, the tasks are not only linked through a time requirement, they are also linked through a data requirement. The level of organization within the module has increased quite a bit from the start. However, we can still do better.

# **Strong Cohesion**

**Functional Cohesion -** This is when all tasks within a module support activities needed for one, and only one problem-related task. In essence the module only does a single action. Examples (each are separate modules):

- Determine monthly payment
- Compute intercept of graphs
- Backup user table

In these situations, the module is more like a large function. Just from looking at the name, you know exactly what the module is doing.

**Object Cohesion -** This can either be lumped in with functional cohesion, or by itself. Object cohesion is when all activities modify a single object.

This only works in object-oriented languages. An example might be a module which only modifies a user object. All tasks within this module update the user module in some way.

# **Cohesion Conclusion**

Cohesion is really important to make code which is easy to understand and maintain. The more focused the modules, the easier the code will be to debug.

Remember however, that this must be a balance with coupling. A group of extremely cohesive modules might also be tightly coupled together. We are looking for the balance between the two. If you remember one thing from these sections, it's that we want "loose coupling, and strong cohesion".