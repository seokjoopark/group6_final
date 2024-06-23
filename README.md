# Group6_final

## Machine Leraning and Programming - Project 6
Seokjoo Park, Gyuman Park, Hyunjun Choi, Sungmin Lee

---

### Motivation and Background 

The need of smart factory is increasing as manufacturing technology has been developed. This is made possible by developing a software for the manufacturing. 
We planned to use “rule-based algorithms which operates on a predefined set of rules or conditions to make decisions or perform task.
### Goal of the Project 

Train a rule-based algorhithms with 2 types (FCFS, MIN scheduling) and compare which records lowest tact time and also apply in DRL

### Manufacturing System 
Inspection process on LCD pallets in LCD production line. Pallets enter the test section in one line and move to the testers each pallet is assigned to. In figure 2, a pallet comes in through the fixed entrance (purple) and moves to the corresponding level where its tester is located through the vertical corridor (yellow). The pallet then arrives to the tester passing the horizontal corridor (sky blue) and enters the tester (blue) taking the first inspection. After the first inspection, the pallet exits the tester and passes along the corridors again to the second tester (green). When the second inspection is finished, the pallet finally exits the entire inspection section through the fixed exit (navy).

### Conditions 
A tester can only inspect one pallet at one time. Testers between different levels don't have any height difference, all parts are physically in the same height.

### Rule based algorithm with predetermined variables before DRL
![image](https://github.com/seokjoopark/group6_final/assets/167041720/207f4fd7-342b-454a-9f05-943b28a3a69e)
#### Priority
1. No collision between pallets
2. Maintain the flow (pallets continuously enter and exit the whole section)
3. Maximized production overtime

#### Assumption
Pallets are scheduled by the order of pallet number. Testers inspect pallets that were assigned to them first. Two-way movements are only possible in the middle corridor

#### Rules
Among the available testers on the same row, a pallet is assigned to the inside tester. Among the available schedules (for tester A, tester B), a pallet chooses the schedule with the shortest route


### Scheduling
![image](https://github.com/seokjoopark/group6_final/assets/167041720/2518c521-a39b-4ade-81b9-935a9eca1a7b)

### Rescheduling
![image](https://github.com/seokjoopark/group6_final/assets/167041720/306c1f1e-8b16-438a-b7e5-0ea522caf03a)

### Code description

floors_env.py: Executes a rule-based model for pallets as an operating environment with scheduling methods set by the autopilot_flag.
utils.arg_parser: Loads environment arguments.
map.py: Visualizes the environment and pallets.
pallet.py: Manages scheduling of pallets, testers, and other entities within the environment.





### Result of simulation
This is the result of running each flag with 200 samples each
![image24](https://github.com/seokjoopark/group6_final/assets/167041720/5789a94b-4fb7-4169-8fad-cdc24113ee99)
![image25](https://github.com/seokjoopark/group6_final/assets/167041720/7b5a235b-bb51-4ff4-9e49-a1699685ada7)

### Summary of result
We found out that FCFS scheduling simulation time takes 1,135 steps while MIN scheduling simulation time takes 1,526 steps. So for optimized Rule-based algorithms for LCD inspection, FCFS scheduling was more efficient.
Our goal was to compare these results with Reinforcement learn and overcome this issue and evaluate the whole scheduling flags and compare it with Reinforcement learning method. 
In stable_baselines/deepq/ dqn.py, we try to run the code for DQN and compare the results but issues in directing sources.


