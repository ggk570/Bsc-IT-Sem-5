#### <span style="color:blue;">1. Describe the nature of resources and their scheduling.</span>
1. A resource refers to any person, equipment, material or asset that is necessary for the execution of project activities and achievement of project objectives. Resources are essential components that contribute to the successful completion of project.
2. They can be categorized into several types:
	1. **Human Resources:** This includes the personnel involved in the project, such as project managers, developers, designers, and support staff. Human resources are crucial because they bring skills and expertise to the project.
	2. **Physical Resources:** These are tangible assets needed for project execution, including equipment, materials, and facilities. Examples include computers, machinery, office space, and raw materials.
	3. **Financial Resources:** This refers to the budget and funds allocated for the project. Proper financial resources ensure that all project activities can be completed without financial constraints.
	4. **Time Resources:** Time is a critical resource in any project. It refers to the schedule or timeline within which the project must be completed. Effective time management is essential to ensure timely project delivery.
	5. **Information Resources:** These include data and information that are vital for decision-making throughout the project lifecycle. This can involve research, analysis, and documentation.
3. **Scheduling of Resources:**
	1. Resource scheduling is the process of allocating and managing resources effectively throughout the project lifecycle. It involves planning when and how resources will be used to meet project goals. Here are key components and steps in resource scheduling:
		- **Resource Allocation:** This involves determining which resources are needed for specific tasks and ensuring they are available when required.
		- **Priority Setting:** Tasks may need to be prioritized based on deadlines, importance, or resource availability, influencing the order in which resources are scheduled.
		- **Utilization Monitoring:** It’s important to track how resources are being used to avoid overallocation or underutilization, which can affect project performance.
		- **Adjustment and Flexibility:** As projects progress, adjustments may be necessary due to unforeseen changes, requiring re-scheduling and re-allocation of resources.
		- **Tools and Techniques:**
		    - **Gantt Charts:** Visual tools to plan and schedule tasks over time.
		    - **Critical Path Method (CPM):** Identifies the longest stretch of dependent tasks and helps prioritize resource allocation.
		    - **Resource Leveling:** A technique to resolve conflicts and ensure a balanced workload.

#### <span style="color:blue;">2. List and describe Bohem's top ten software project risks and the different strategies for reducing it.</span>
Boehm's top ten software project risks are key factors that can significantly impact the success of software projects. Understanding these risks allows project managers to take proactive measures to mitigate them. Here’s a detailed explanation of each risk and corresponding strategies for reduction:
1. **Personnel Shortfalls:** This risk occurs when there aren’t enough qualified team members available to complete the project. It may result from unforeseen absences, turnover, or insufficient staffing during project planning.
	- **Reduction Strategies:**
		- **Cross-Training:** Train team members in multiple roles to increase flexibility.
		- **Hiring Plans:** Develop a recruitment strategy ahead of time to ensure sufficient staffing.
		- **Backup Resources:** Maintain a list of freelancers or consultants who can be called in when needed.
2. **Unrealistic Schedules and Budgets:** Setting overly ambitious timelines or budgets without adequate analysis of the project scope and resources can create unrealistic expectations.
	- **Reduction Strategies:**
		- **Historical Data:** Use data from previous projects to create more accurate estimates.
		- **Buffer Time:** Include contingency time in schedules for unexpected delays.
		- **Incremental Planning:** Break the project into smaller phases with realistic milestones.
3. **Developing the Wrong Software Functions:** This occurs when the software being developed does not align with user needs or business objectives, often due to inadequate requirements gathering or stakeholder engagement.
	- **Reduction Strategies:**
		- **Stakeholder Engagement:** Involve users and stakeholders early in the requirements gathering process.
		- **Prototyping:** Use prototypes or mockups to validate ideas before full development.
		- **Regular Feedback Loops:** Incorporate iterative feedback throughout the project to ensure alignment with needs.
4. **Developing the Wrong User Interface:** If the user interface (UI) does not meet user expectations or usability standards, it can hinder user adoption and satisfaction.
	- **Reduction Strategies:**
		- **User Testing:** Conduct usability testing with actual users to gather feedback on UI designs.
		- **Design Standards:** Follow established UI/UX design principles and guidelines.
		- **Iterative Design:** Use an iterative design process that incorporates user feedback at multiple stages.
5. **Gold Plating:** This refers to adding unnecessary features or enhancements that were not part of the original project scope, often driven by a desire to exceed expectations.
	- **Reduction Strategies:**
		- **Strict Scope Management:** Clearly define project scope and stick to it; avoid adding features without proper evaluation.
		- **Change Control Process:** Implement a formal process for evaluating and approving changes.
		- **Focus on Requirements:** Prioritize essential functions based on user needs and business goals.
6. **Continuing Stream of Requirement Changes:** Frequent changes to requirements throughout the project can disrupt workflow and lead to scope creep, where the project expands beyond its original goals.
	- **Reduction Strategies:**
		- **Change Management:** Establish a formal change management process to assess the impact of changes.
		- **Stakeholder Commitment:** Secure commitment from stakeholders to minimize changes once the project is underway.
		- **Regular Reviews:** Schedule regular review meetings to discuss and prioritize any new requirements.
7. **Shortfalls in Externally Furnished Components:** Reliance on third-party components (like libraries or frameworks) can introduce risks if those components fail to meet quality or performance standards.
	- **Reduction Strategies:**
		- **Component Evaluation:** Thoroughly evaluate third-party components for compatibility and performance.
		- **Backup Solutions:** Identify alternative components or solutions in case of failure.
		- **Testing Early:** Integrate and test external components early in the development cycle to identify issues promptly.
8. **Shortfalls in Externally Performed Tasks:** This risk arises when tasks that are outsourced or handled by external teams do not meet expectations in terms of quality, timeline, or communication.
	- **Reduction Strategies:**
		- **Vendor Assessment:** Choose reputable vendors based on past performance and references.
		- **Clear Contracts:** Establish clear expectations and deliverables in contracts.
		- **Regular Communication:** Maintain regular communication with external teams to monitor progress and address issues quickly.
9. **Real-Time Performance Shortfalls:** Software that requires real-time processing may encounter performance issues if it cannot handle the necessary speed or efficiency, often due to inadequate testing or design flaws.
	- **Reduction Strategies:**
		- **Performance Testing:** Conduct rigorous performance testing under realistic conditions.
		- **Scalable Architecture:** Design software with scalability in mind to handle increasing loads.
		- **Early Identification:** Identify performance bottlenecks early in the development process.
10. **Straining Computer-Science Capabilities:** This risk involves pushing the limits of current technology or the team’s skill set, which can occur with overly complex projects or cutting-edge technologies.
	- **Reduction Strategies:**
		- **Feasibility Analysis:** Conduct a feasibility study to assess the capabilities required versus available skills.
		- **Training and Development:** Invest in training for the team to build the necessary skills for complex tasks.
		- **Incremental Complexity:** Gradually introduce complex features rather than implementing them all at once.

#### <span style="color:blue;">3. Explain the concept of forward pass, backward pass and critical path.</span>
1. The concepts of **forward pass**, **backward pass**, and **critical path** are fundamental in project management, particularly in techniques like the Critical Path Method (CPM).
2. They help in scheduling project activities and determining the overall project timeline.
3. **Forward Pass:** Forward Pass is a technique used in project management to calculate the earliest possible start and finish dates for each activity in a project. It is also known as the Early Start (ES) or Early Finish (EF) method. The forward pass is used to determine the critical path of a project, which is the sequence of activities that must be completed on time in order for the entire project to be finished on schedule.
	**Steps to calculate Forward Pass:**
	1. **Start with zero:** Set the early start (ES) of the first activity to zero. 
	2. **Calculate early finish:** Add the duration to the early start to calculate the early finish 
	    - **Formula**: EF = ES + Duration 
	3. **Calculate early start for next activity:** Use the early finish of the previous activity to calculate the early start of the next activity: 
	    - **Formula**: ES = (highest) previous EF
	4. **Continue:** Repeat steps 2 and 3 until you've calculated the early start and finish times for all activities.
4. **Backward Pass:** A backward pass in project management is a technique used to move through a project network diagram. The backward pass identifies your late start and late finish values, so that you can understand the project’s duration and eventually find the critical path.
	**Steps to calculate Backward Pass:**
	- **Start with the last activity:** Set its latest finish time to the project's end date (or the deadline).
	- **Calculate LS:** For each activity, the latest start time is determined by subtracting the duration of the activity from its latest finish time.
		- **Formula**: LS = LF - Duration
	- **Move to preceding activities:** For activities that come before others, the latest finish time is determined by the latest start time of the subsequent activity.
		- **Formula**: LF = Minimum( LS subsequent activity )
5. **Critical Path:** The critical path is the longest sequence of dependent activities in a project that determines the shortest possible project duration. It includes activities that have zero float or slack, meaning any delay in these activities directly affects the overall project timeline.
	1. Float represents how much each individual activity can be delayed without delaying successor activities or project completion date.
		- **Formula**: Total Float = LS – ES or LF – EF
	2. Free Float represents the amount of time that an activity can be delayed before any successor’s activity will be delayed. A zero free float represents that there is no space to delay the activity without delaying the entire project.
		- **Formula**: Free Float = Lowest ES of successors - EF
	3. Any activity with zero total float is considered critical and is part of the critical path.
	4. Understanding the critical path helps project managers prioritize tasks that are crucial for timely project completion, enabling them to focus resources and attention where they are most needed.

#### <span style="color:blue;">4. Distinguish between PERT and CPM.</span>
1. Project Evaluation and Review Technique (PERT) and Critical Path Method (CPM) are both project management tools used for planning and controlling projects. However, they have distinct characteristics and applications. Here’s a comparison

| Aspect                | PERT                                                                                                                                               | CPM                                                                                                                                          |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | A statistical tool used for analyzing the tasks involved in completing a project, especially in research and development.                          | A project management technique used to determine the longest stretch of dependent activities and measure the time required to complete them. |
| **Focus**             | Primarily focuses on time estimation and uncertainty in project scheduling.                                                                        | Focuses on the trade-off between project duration and cost, emphasizing cost management.                                                     |
| **Activity Duration** | Uses three time estimates (optimistic, pessimistic, and most likely) to calculate the expected time for each activity, accounting for uncertainty. | Uses a single time estimate for each activity, assuming that the duration is known and fixed.                                                |
| **Network Diagram**   | The network diagram is more complex and emphasizes the sequence of activities, often using event-oriented diagrams.                                | The network diagram is straightforward and activity-oriented, showing the tasks and their dependencies.                                      |
| **Application**       | Most commonly used in projects where time is crucial and activities have uncertain durations, such as research and development projects.           | Used for projects where time and costs are predictable, such as construction projects.                                                       |
| **Critical Path**     | Does not specifically focus on the critical path but identifies the sequence of activities that directly impact project completion time.           | Explicitly identifies the critical path, which is the longest path through the project, determining the minimum completion time.             |
#### <span style="color:blue;">5. Suppose four risks namely R1, R2, R3 and R4 have been identified and assigned the probabilities of occurences 0.1, 0.2, 0.3, 0.4 respectively. The likely damages due to four risks are Rs 60000, Rs 100000, Rs 70000, Rs 80000 respectively. Calculate the risk exposure of all the risks.</span>
1. **Risk exposure** is a financial metric used to assess the potential loss that an organization might face due to identified risks. It quantifies the impact of risks based on their likelihood of occurrence and the potential damage or loss they could cause.
2. To calculate the risk exposure for each risk, we use the formula:
	Risk Exposure = Probability of Occurrence × Potential Damage
3. Given Data:
	- **Risk R1:** Probability = 0.1, Damage = Rs 60,000
	- **Risk R2:** Probability = 0.2, Damage = Rs 100,000
	- **Risk R3:** Probability = 0.3, Damage = Rs 70,000
	- **Risk R4:** Probability = 0.4, Damage = Rs 80,000
4. Calculations:
	1. **Risk R1:**
	    Risk Exposure = 0.1 × 60000 = 6000
	2. **Risk R2:**
	    Risk Exposure = 0.2 × 100000 = 20000
	3. **Risk R3:**
	    Risk Exposure = 0.3 × 70000 = 21000
	4. **Risk R4:**
	    Risk Exposure = 0.4 × 80000 = 32000
5. Summary of Risk Exposures:
	- **Risk R1:** Rs 6,000
	- **Risk R2:** Rs 20,000
	- **Risk R3:** Rs 21,000
	- **Risk R4:** Rs 32,000
6. Total Risk Exposure:
	To find the total risk exposure, sum up the individual risk exposures:
	Total Risk Exposure = 6000 + 20000 + 21000 + 32000 = 80000
7. Final Results:
	- **Risk Exposure of R1:** Rs 6,000
	- **Risk Exposure of R2:** Rs 20,000
	- **Risk Exposure of R3:** Rs 21,000
	- **Risk Exposure of R4:** Rs 32,000
	- **Total Risk Exposure:** Rs 80,000

#### <span style="color:blue;">6. Create a precedence activity network using the following details: Calculate earliest and latest start and end dates and the float associated with each activity. From this identify the critical path.</span>

| Activity | Depends On | Duration (days) |
| -------- | ---------- | --------------- |
| A        |            | 5               |
| B        | A          | 7               |
| C        | B          | 6               |
| D        | A          | 5               |
| E        | D          | 10              |
| F        | B          | 15              |
| G        | B          | 8               |
| H        | G          | 8               |
| I        | C          | 4               |
| J        | G          | 4               |
| K        | E, F       | 7               |
| L        | I, H       | 5               |
**Solution**

| Activity        | Depends On | Duration (days) | ES  | EF  | LS  | LF  | Float |
| --------------- | ---------- | --------------- | --- | --- | --- | --- | ----- |
| A               |            | 5               | 0   | 5   | 0   | 5   | 0     |
| B               | A          | 7               | 5   | 12  | 5   | 12  | 0     |
| C               | B          | 6               | 12  | 18  | 19  | 25  | 7     |
| D               | A          | 5               | 5   | 10  | 12  | 17  | 7     |
| E               | D          | 10              | 10  | 20  | 17  | 27  | 7     |
| F               | B          | 15              | 12  | 27  | 12  | 27  | 0     |
| G               | B          | 8               | 12  | 20  | 13  | 21  | 1     |
| H               | G          | 8               | 20  | 28  | 21  | 29  | 1     |
| I               | C          | 4               | 18  | 22  | 25  | 29  | 7     |
| J               | G          | 4               | 20  | 24  | 30  | 34  | 10    |
| K               | E, F       | 7               | 27  | 34  | 27  | 34  | 0     |
| L               | I, H       | 5               | 28  | 33  | 29  | 34  | 1     |
| **Project End** |            | 0               | 34  | 34  | 34  | 34  | 0     |
Critical Path is A-->B-->F-->K

#### <span style="color:blue;">7. Briefly explain objectives of Activity Planning.</span>
The objectives of activity planning include:
1. **Feasibility assessment:** Is the project possible withing required timescales and constraints? It is not until we have constructed a detailed plan that we can forecast a completion date with any reasonable knowledge of its achievability.
2. **Resource allocation:** What are the most effective ways of allocating resources to the project and when should they be available? The project plan allows us to investigate the relationship between timescales and resource availability and the efficiency of additional spending on resource procurement.
3. **Detailed costing:** How much will the project cost and when is that expenditure likely to take place? After producing an activity plan and allocating specific resources, we can obtained more detailed estimates of costs and their timing.
4. **Motivation:** Providing targets and being seen to monitor achievement against targets is an effective way of motivating staff, particularly where they have been involved in setting those targets in the first place.
5. **Co-ordination:** When do the staff in different departments need to be available to work on a particular project and when do staff need to be transferred between projects? The project plan, particularly with large projects involving more than a single project team, provides an effective vehicle for communication and co-ordination among teams.

#### <span style="color:blue;">8. Explain with a neat diagram the components in Lyytinen-Mathiassen-Ropponen risk framework.</span>
![[Lyytinen-Mathiassen-Ropponen.png]]
1. The Lyytinen-Mathiassen-Ropponen risk framework is a comprehensive approach to understanding and managing risks in software projects.
2. It emphasizes the dynamic nature of risks and their interrelations. Here’s an explanation of its key components along with a simple diagram to illustrate the framework.
	- **Actors:** Refers to all stakeholders involved in the project, including project managers, developers, clients, and users. Their roles, motivations, and interactions can significantly influence project success and risk levels.
	- **Technology:** Encompasses the tools, platforms, and technologies used in the project. Risks can arise from the choice of technology, its maturity, compatibility, and the team's familiarity with it.
	- **Structure:** Involves the organizational structure and processes that support the project. This includes how teams are organized, communication channels, and the project governance framework.
	- **Tasks:** Refers to the specific activities and work packages that make up the project. The complexity, dependencies, and requirements of these tasks can introduce various risks.

#### <span style="color:blue;">9.Briefly explain Monte Carlo simulation approach.</span>
1. Monte Carlo Analysis is a risk management technique used to conduct a quantitative analysis of risks.
2. Monte Carlo gives you a range of possible outcomes and probabilities to allow you to consider the likelihood of different scenarios.
3. The Monte Carlo simulation is a statistical technique used to model and analyze the impact of uncertainty and variability in complex systems or processes. It leverages random sampling and repeated simulations to provide insights into potential outcomes and risks.
4. Key Features of Monte Carlo Simulation
	1. **Random Sampling:** The simulation utilizes random inputs to represent uncertainty in variables. By generating a wide range of possible outcomes through numerous simulations with varying random values, it effectively captures the inherent variability of the system being analyzed.
	2. **Probability Distributions:** Monte Carlo employs various probability distributions (such as normal, triangular, or uniform) to model uncertain variables. This approach allows for a more realistic representation of input variability, moving beyond fixed values to better reflect real-world conditions.
	3. **Iterative Process:** The simulation runs thousands or even millions of iterations, with each iteration calculating a result based on randomly selected input values. This iterative nature facilitates a comprehensive analysis of potential outcomes, helping to identify trends and patterns across a broad range of scenarios.
	4. **Output Analysis:** Once the simulations are complete, the results are analyzed to understand the probability of different outcomes. This statistical analysis supports informed decision-making by providing insights into the risks and uncertainties involved, enabling stakeholders to make choices based on a thorough understanding of potential results.

#### <span style="color:blue;">10. How is successful project scheduling achievable?</span>
1. Successful project scheduling is essential for the timely delivery of projects and involves several key practices and strategies.
2. Successful project scheduling can be achieved using various existing methods or frameworks. Two of the most used methods are:
	1. **CPM (Critical Path Method)**
	2. **PERT (Program Evaluation Review Technique)**
3. Both PERT and CPM utilize network diagrams to represent project activities and their dependencies. Activities are depicted as nodes or arrows, showing the sequence and relationships among tasks.
4. PERT uses three time estimates (optimistic, pessimistic, and most likely) for each activity, allowing project managers to account for uncertainty in task durations. This helps in creating a more flexible schedule.
5. CPM focuses on identifying the longest sequence of dependent activities (the critical path) to determine the shortest possible project duration, ensuring that deadlines are met.
6. Depending on the requirements we can choose our own method for scheduling.

#### <span style="color:blue;">11. Define risk management. Explain different categories of it.</span>
1. Risk management is the process of identifying, assessing, and prioritizing risks followed by coordinated efforts to minimize, monitor, and control the probability or impact of unforeseen events. It aims to protect an organization’s assets, including its reputation, and ensure the achievement of objectives.
2. **Categories of Risk based on source:**
	- **Actors:** Refers to all stakeholders involved in the project, including project managers, developers, clients, and users. Their roles, motivations, and interactions can significantly influence project success and risk levels.
	- **Technology:** Encompasses the tools, platforms, and technologies used in the project. Risks can arise from the choice of technology, its maturity, compatibility, and the team's familiarity with it.
	- **Structure:** Involves the organizational structure and processes that support the project. This includes how teams are organized, communication channels, and the project governance framework.
	- **Tasks:** Refers to the specific activities and work packages that make up the project. The complexity, dependencies, and requirements of these tasks can introduce various risks

#### <span style="color:blue;">12. State and explain Burman's priority list in project management.</span>
1. For a project, when scheduling of all activities is done, resource allocation needs to be done to distribute resources over each tasks in project activities.
2. Since a project needs to be completed with limited resources to achieve profitability, there are chances of resource clashes.
3. Resource clashes occurs when the same resource is needed in more than one place at the same time.
4. It can be resolved by delaying one activity and taking advantage of the float time, or if that is not possible, push back project completion. Could also be resolved by taking resources from a non-critical activity, or by bringing in additional resources - increases cost.
5. When prioritizing between two competing activities, there are two ways of doing this:
	1. **Total float priority:** Those with the smallest float have the highest priority.
	2. **Ordered list priority:** This uses a priority list of activities to allocate resources. Here Burman's priority list can be used. It takes duration of activity and float into account.
6. Burman's priority list includes below activities:
	1. **Shortest critical activities:** These are tasks that must be completed on time to ensure the project stays on schedule. They have zero float (slack), meaning any delay will directly impact the project deadline. Hence they are given first priority for resource allocation.
	2. **Other critical activities:** These are additional critical tasks that are essential to project success but may not be the shortest in duration. They also have zero float. While they may take longer than the shortest critical activities, these tasks are equally important for maintaining the project timeline and should be monitored to prevent any potential delays. Hence second priority is given to them.
	3. **Shortest non critical activities:** These tasks do not directly impact the project's critical path and have some float, meaning they can be delayed without affecting the overall project timeline.
	4. **Non critical activities with least float:** Among non-critical tasks, those with the least amount of float are the ones that are most at risk of becoming critical if delays occur. These have more constraints on their start and finish times than other non-critical tasks.
	5. **Non critical activities:** As soon as the prior tasks are completed the resources freed can be utilize for non critical activities. These are given least priority because they have sufficient float which means delay occuring in such tasks don't impact overall project schedule and deadline.

#### <span style="color:blue;">13. Explain network planning model.</span>
1. In project management, a network planning model is used to represent the sequence of activities required to complete a project. This model helps in visualizing the project's tasks and their dependencies
2. Network planning model is used with project scheduling techniques like PERT and CPM.
3. In the network, time flows from left to right
4. Network models can be drawn using **activity on arrow approach** to visuale the project as a network where activities are drawn as arrows joining circles, or nodes, which represent the possible start and/or completion of an activity or set of activities.
5. Another approach for this is **Precedence network diagram**. This used activity on node approach.
6. Here activities are represented as nodes and the links between nodes represent precedence (or sequencing) requirements. This latter approach avoids some of the problems inherent in the activity-on-arrow representation and provides more scope for easily representing certain situations. It is this method that is adopted in the majority of computer applications currently available.

#### <span style="color:blue;">14. Explain the term nature of resources and their scheduling.</span>
1. A resource is any equipment, material, asset or any person required for the execution of the project activities and achievement of project objectives.
2. Resources are essential components that contribute to the successfull completion of project.
3. Resource categories includes:
	1. **Human Resource:** This includes the personnel involved in the project, such as project managers, developers, designers, and support staff. Human resources are crucial because they bring skills and expertise to the project
	2. **Physical Resources:** These are tangible assets needed for project execution, including equipment, materials, and facilities. Examples include computers, machinery, office space, and raw materials.
	3. **Financial Resources:** This refers to the budget and funds allocated for the project. Proper financial resources ensure that all project activities can be completed without financial constraints.
	4. **Time Resources:** Time is a critical resource in any project. It refers to the schedule or timeline within which the project must be completed. Effective time management is essential to ensure timely project delivery.
	5. **Information Resources:** These include data and information that are vital for decision-making throughout the project lifecycle. This can involve research, analysis, and documentation.
4. **Scheduling Resources:**
	1. Resource scheduling is the process of allocating and managing resources effectively throughout the project lifecycle. It involves planning when and how resources will be used to meet project goals.
	2. There are some project planning tools to automatically allocate resources, they generally display information using histogram graph. However they don't consider all factors that could be used by project manager.
	3. In practice, resources must be allocated to a project on an activity-byactivity basis and finding the "best" allocation can be time consuming and difficult. As soon as a member of the project team is allocated to an activity, that activity acquires a scheduled start and finish date, and the team member becomes unavailable for other activities for that period. Thus, allocating a resource to one activity limits the flexibility for resource allocation and scheduling of other activities.
	4. Therefore helpful to prioritize activities so that resources can be allocated to competing activities in some rational order
	5. When prioritizing between two competing activities, there are two ways of doing this:
		1. **Total float priority:** Those with the smallest float have the highest priority.
		2. **Ordered list priority:** This uses a priority list of activities to allocate resources. Here Burman's priority list can be used. It takes duration of activity and float into account.
	6. Burman's priority list includes below activities:
		1. **Shortest critical activities** 
		2. **Other critical activities**
		3. **Shortest non critical activities**
		4. **Non critical activities with least float**
		5. **Non critical activities**

#### <span style="color:blue;">15. What are the factors considered while allocating tasks to the individuals?</span>
When allocating tasks to individuals in a project, several factors must be considered to ensure effective resource utilization and successful outcomes. Here are some key factors to keep in mind:
1. **Skills and Expertise**: Aligning an individual’s specific skills, knowledge, and experience with the task requirements is essential. Properly matching skills to tasks enhances both efficiency and quality.
2. **Workload Balance**: Distributing tasks evenly among team members is crucial to avoid burnout and prevent any one individual from becoming overloaded. Monitoring existing workloads aids in making fair allocations.
3. **Availability**: Consider the current availability of team members, including their commitments to other projects. Assigning tasks to those who are available ensures timely completion.
4. **Interest and Motivation**: Assigning tasks based on individual interests can lead to higher motivation and improved performance. Engaged team members are more likely to invest the effort needed for success.
5. **Team Dynamics**: Understanding how team members interact is vital. Pairing individuals who collaborate well can enhance communication and productivity.
6. **Task Complexity**: The complexity of the task should match the individual’s capabilities. More challenging tasks may require team members with greater experience.
7. **Learning Opportunities**: Allocating tasks that provide opportunities for skill development benefits both individuals and the overall skill set of the team.
8. **Deadlines**: Timelines and deadlines are critical for effective resource allocation. Urgent tasks should be assigned to individuals who can work swiftly without compromising quality.
9. **Previous Performance**: Historical performance data can guide decisions on task allocation. Individuals who have proven reliability and competence in the past can be trusted with critical assignments.
10. **Resource Constraints**: Budgetary and resource limitations may impact the availability of individuals for certain tasks. These constraints should be taken into account during the allocation process.

#### <span style="color:blue;">16. Define activity. Discuss three approaches to identify the activities.</span>
1. In project management, an **activity** refers to a specific task or set of tasks that are performed to achieve a project objective. Activities are the building blocks of a project, representing the work that needs to be completed, and are typically defined in terms of time, resources, and deliverables.
2. There are 3 most common approaches or methods for the identification of activities in any software project:
	1. **Activity based approach:** 
		- It consists of creating a list of all the activities that the project is supposed to involve in its life cycle. 
		- It can be done by using a brainstorming process which includes the complete project team and analysis of the past projects. 
		- Work Breakdown Structure (WBS) is created for the same purpose. It involves dividing a complex and big scale project into simpler, manageable, independent and smaller tasks which can be completed in approximately few weeks by a single development team working on the project.
	    - The root of the project tree is labelled by the project name itself. Each node (activity) is recursively decomposed and divided into smaller sub-activities, until at the leaf level, the activities require approximately two weeks to develop and can be given to a single development team. It follows top-down approach.
	2. **Product based approach:**  
	    - The PFD indicates, for each product, which other products are required as inputs.
	    - The PFD can therefore be easily transformed into an ordered list of activities by identifying the transformations that turn some products into others.
	    - Proponents of this approach claim that it is less likely that a product will be left out of a PBS than that an activity might be omitted from an unstructured activity list.
	3. **Hybrid approach:**  
	    In this approach, an alternative work breakdown structure is constructed based on:
	    - A simple list of final deliverable.
	    - For each deliverable, a set of activities required to produce that product.

#### <span style="color:blue;">17. Write a short note on Project Evaluation and Review Technique.</span>
1. **Project Evaluation and Review Technique (PERT)** is a procedure through which activities of a project are represented in its appropriate sequence and timing.
2. It is a scheduling technique used to schedule, organize and integrate tasks within a project.
3. It is a technique of project management which is used to manage uncertain (i.e., time is not known) activities of any project.
4. It uses three time estimates (optimistic, pessimistic, and most likely) to calculate the expected time for each activity, accounting for uncertainty.
5. PERT is basically a mechanism for management planning and control which provides blueprint for a particular project.
6. It majorly focuses on time as meeting time target or estimation of percent completion is more important.
7. It is appropriate for high precision time estimation.
8. In this technique, a PERT Chart is made which represent a schedule for all the specified tasks in the project.

#### <span style="color:blue;">18. Define the following term: I) Critical Path II) Float III) Free Float IV) Interfering Float V) Hammock Activity</span>
1. **Critical Path:** The **Critical Path** is the longest sequence of dependent tasks in a project that determines the shortest possible completion time. Any delay in the activities on the critical path directly impacts the overall project duration. Identifying the critical path helps project managers prioritize tasks and allocate resources effectively.
2. **Float:** It is also known as slack, is the amount of time that a task can be delayed without affecting the project’s overall completion date. It indicates the flexibility available in scheduling tasks. There are two main types of float: total float and free float.
3. **Free Float:** It is the amount of time that a task can be delayed without affecting the start date of any subsequent tasks. It measures the flexibility of a specific task without impacting the overall project timeline. Free float is important for understanding how delays in one task may or may not affect others.
4. **Interfering Float:** It is a type of float that occurs when a task has some slack but delaying it would cause a subsequent task to be delayed. It indicates a situation where the float available is not entirely free because it interferes with the timing of dependent tasks.
5. **Hammock Activity:** A **Hammock Activity** is a type of project management activity that spans multiple tasks or phases. It is used to summarize or aggregate the duration of several related tasks, often representing a higher-level view of project progress. Hammock activities are useful for tracking and reporting on groups of activities, and they are typically scheduled at the end of the related tasks to reflect their total duration.