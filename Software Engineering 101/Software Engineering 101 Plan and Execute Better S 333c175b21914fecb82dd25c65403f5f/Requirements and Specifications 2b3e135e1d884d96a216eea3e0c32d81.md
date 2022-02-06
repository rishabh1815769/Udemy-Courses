# Requirements and Specifications

# **Requirements Definition**

⇒ Requirements define the problem at hand. In this step we are trying to find out the "what". We are NOT trying to find out the "how". This means we want to come up with a set of goals the system should be able to do, but not try to figure out how to accomplish these goals.

⇒ For example, let's say we have the problem of needing a form to track financial transactions. In the requirements we might look to define what exactly this form should track. Maybe we need a name, date, amount, and bank account field. From there, it needs to be stored into a database. These would all be requirements. We don't however need to figure out the best way to do any of that. Those questions are for the design phase.

⇒ So to reiterate, requirements are just to define the problem. It's the phase where we come up with a common set of goals that we are working towards. The requirements will constantly be looked at through production to make sure the product being built is actually solving the original problem.

# **Requirements vs Specifications**

⇒ Within the requirements phase, we also look at something called specifications. Specifications are in essence "technical requirements". They are used to define the problem in terms of the technical constraints.

⇒ By constraints, I mean limitations, or implementations that must happen. For example, if a client only uses MySQL databases, then we have to use a MySQL database as well. This isn't a design choice, it's something that must happen, therefore it goes into requirements.

**Requirements** - A non-technical definition of something that is required from the system.

**Specifications** - A technical definition of what is required from the system.

With requirements, we are trying to keep it simple. We don't want to use any technical jargon. It should be understood by just about anyone. Something very simple like "*Should record bank account information*" is good.

With specifications, we can be a little more exact, and use some technical jargon. We still want to keep it as simple as possible though. "*Encrypt the bank account information with at-least a AES 256 standard*".  Again, we are NOT trying to design it here. We aren't going into the specifics, just saying the technical standard by which we need to meet. We will come up with how to do this, which encryption to actually use, etc. in the design phase.

# **Non-Functional vs Functional**

There is one final area of organization we can add onto our requirements. This is the idea between functional, and non-functional requirements.

**Functional** - Functional requirements are requirements which pertain to the function of the system.

**Non-Functional** - Non-Functional requirements are requirements which cover areas that don't directly effect the function of the program.

Functional requirements are pretty straightforward and easy to create. All we have to ask is "what should the program do?". Any answers to this question are functional requirements.

For example: the system should collect user information, the system should provide a cart system for collecting items, the system should provide a way to rate and review different products. These are all functional requirements. They detail the way the program should function.

Non-functional however are a little bit trickier. They are typically constraints. These constraints might be implemented by the government (safety regulations), the company (quality regulations), or the client. They are things we have to follow, but don't directly pertain to the function of the program.

An example of a non-functional requirement would be that the program must be coded in Java. This requirement might come from the client, so it's easy to maintain by their engineers who only know Java. This doesn't describe the functional of the program at all. It will still do exactly the same thing in any programming language. This makes it a non-functional requirement.

There are different categories of non-functional requirements to make it a little bit easier. These categories are product, organizational, and external.

**Product** - Must have behaviors of the product (referring to the code, servers, etc). Example: Product must be coded in Java. Product must use Microsoft based servers.

**Organizational -** Company policies, standards, styles, rules, etc. Example: The project will be developed using scrum. Every function must be documented.

**External** - External laws, regulations, trends, etc. Product must use SSL due to European law XYZ. Product should use new technique of XYZ to collect data.

# **WRSPM Model**

**World** - The world assumptions which are used to develop the system. (Will there be internet? Electricity? What is the speed of the internet? )

**Requirements** - Defining the problem at hand and how a solution to that problem should operate.

**Specifications** - Defining the technical requirements of the system. Here we are linking together the idea of the solution, to the system itself.

**Program** - The program and code itself.

**Machine** - The physical hardware needed for the software. Servers, RAM, CPU, etc.

![https://img-b.udemycdn.com/redactor/raw/2019-03-14_13-00-39-4e837355ddcc46b176880488ecf502f6.PNG?secure=Nt-AjxEshkJYARjRsoAzNQ%3D%3D%2C1644048269](https://img-b.udemycdn.com/redactor/raw/2019-03-14_13-00-39-4e837355ddcc46b176880488ecf502f6.PNG?secure=Nt-AjxEshkJYARjRsoAzNQ%3D%3D%2C1644048269)

The WRSPM model helps define the problem better. Not only do we take into account the program we are building, we also consider things like the environment, and the actual hardware. Taking into account things like the environment can make very important distinctions to how the program is developed.

For example, lets say we are developing a software which handles user financial transactions. We as programmers assume that the system will always be connected to power. However, maybe this particular software is being developed for a place which has random blackouts. So at any time the power can be cut.

We now need to develop a software solution which has fail-safe features for if the power is suddenly cut off. Maybe this takes place at the terminal, or the server itself. However it's designed, it's important to know this constraint beforehand. The WRSPM model helps us answer these questions.

There are additional areas of classification we can use as well.

**Eh** - Environment hidden. These are pieces of data within the environment, which are just concepts or ideas. For example, the password you have memorized for an account. This piece of information exists only within your mind. Therefore it's a variable, but hidden.

**Ev -** Environment Visible. These are pieces of data within the environment which are now visible. Entering that password into a computer terminal manifests it. It is now represented in the physical world, and in a way which the system can now use.

**Sv** - System Visible. This is the part of the system which is visible to the user. This includes the program and the machine. So the keyboard, monitor, mouse etc. It also covers the screens and part of the program which you can interact with.

**Sh** - System Hidden. This is the part of the system which is hidden from the user. This includes the part of the software that the user doesn't touch, and the components within the machine itself. An example of this would be with a calculator. The user enters in the two numbers to be added. The hidden part is how the machine adds the numbers together before showing the result to the user.