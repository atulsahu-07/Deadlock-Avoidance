# DEADLOCK AVOIDANCE

 ## Table Of Contents

* <a href = "#Over" > Overview </a> 

* <a href = "#Req" > Requirements </a> 

* <a href = "#Intro" > Introduction </a> 

  * <a href = "#Banker" > Banker's Algorithm </a>
  
  * <a href = "#Resource" > Resource-Request Algorithm </a>
  

* <a href = "#Refe" > References </a> 
  
## <div id = "Over"> Overview </div>

In this project we have implemented two algorithms related to deadlock.

1. Banker's Algorithm
2. Resource-Request Algorithm

## <div id = "Req"> Requirements </div>
Install JDK 11.0.9 or higher version.

## <div id = "Intro"> Introduction </div>
  This project is about avoiding the deadlock using Java programming language with the help of well-known concepts in Operating Systems. 
  
  We have taken Banker's algorithm and Resource Request algorithm here to detect deadlocks and allocation of resources to avoid deadlock.

1. ### <div id = "Banker"> Banker's Algorithm </div>
  * Banker's algorithm deals with various concepts like safe sequence. When a new process enters the system, it must declare the maximum number of instances of each resource type that it may need. This number may not exceed the total number of resources in the system. When a user requests a set of resources, the system must determine whether the allocation of these resources will leave the system in a safe state. If it will, the resources are allocated; otherwise, the process must wait until some other process releases enough resources. Several data structures must be maintained to implement the banker's algorithm. There data structures encode the state of the resource-allocation system. We need the following data structures, where **n** is the number of processes in the system and **m** is the number of resource types:

- **Available:** A vector of length m indicates the number of available resources of each type. If **Available[j]** equals k, then k instances of resource type Rj are available.
- **Max:** An n × m matrix defines the maximum demand of each process. If Max[i][j] equals k, then process Pi may request at most k instances of resource type Rj.
- **Allocation:** An n × m matrix defines the number of resources of each type currently allocated to each process. If **Allocation[i][j]** equals k, then process Pi is currently allocated k instances of resource type Rj.
- **Need:** An n × m matrix indicates the remaining resource need of each process. If Need[i][j] equals k, then process Pi may need k more instances of resource type Rj to complete its task. Note that **Need[i][j]** equals to **Max[i][j]** − **Allocation[i][j]**

2. ### <div id = "Resource"> Resource-Request Algorithm </div> 
This algorithm for determining whether requests can be safely granted. Let **Request** **i** be the request vector for process Pi. If **Request** **i** [j] == k, then process Pi wants k instances of resource type Rj. When a request for resources is made by process Pi, the following actions are taken:

1. If **Request** **i** **≤ Need** **i**, go to step 2. Otherwise, raise an error condition, since the process has exceeded its maximum claim.

2. If **Requesti** ≤ Available, go to step 3. Otherwise, Pi must wait, since the resources are not available.

3. Have the system pretend to have allocated the requested resources to process Pi by modifying the state as follows:

                                                            Available= Available-Request[i];
                                                            Allocation[i]=Allocation[i]+Request[i];
                                                            Need[i]=Need[i]-Request[i];

## <div id = "Refe"> References </div>

<div id = "Ref"> [1] It is taken from example of the book named "Abraham-Silberschatz-Operating-System-Concepts 9th edition" on page no # 332. </div>
