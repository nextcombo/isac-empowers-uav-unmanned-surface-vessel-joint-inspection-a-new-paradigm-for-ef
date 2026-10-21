# ISAC Empowers UAV-Unmanned Surface Vessel Joint Inspection: A New Paradigm for Efficiency Optimization in Drone-Unmanned Surface Vessel Collaborative Systems [with MATLAB Code]

ISAC Empowered Air-Sea Collaborative System: A New Paradigm for Efficiency Optimization in UAV-USV Joint Inspection
As the low-altitude economy rapidly develops, unmanned aerial vehicles (UAVs) have become widely used in maritime inspection scenarios due to their high maneuverability and high-resolution perception capabilities. However, limited by onboard battery capacity and data storage capabilities, the long endurance and wide range of operations of UAVs have always been bottlenecks in the industry. Conversely, surface unmanned ships (USVs) with their enduring endurance and ability to carry edge computing and charging equipment, however, suffer from slow mobility and limited sensing vision.
When integrated sensor and communication (ISAC) technology meets air-sea heterogeneous unmanned platforms, can it break through the boundaries of each other's capabilities, achieve dual sharing of hardware and spectrum for perception and communication, and release system energy efficiency potential through collaborative planning? The latest paper published by the team from Harbin Engineering University titled "ISAC Empowered Air-Sea Collaborative System: A UAV-USV Joint Inspection Framework" provides a complete solution.

The core challenges of air-sea collaboration are traditionally addressed using a leader-follower architecture: the UAV takes the lead in planning paths for perception, while the USV follows the route. However, in the ISAC empowered collaborative system, the UAV needs to maintain stable communication with the USV throughout the entire process, completing target perception tasks simultaneously. This introduces two new technical challenges:
1. Coupling between trajectories: The UAV needs to approach the target to ensure the quality of perception, while the USV must maintain a specific distance from the UAV to keep the communication link stable. The movement trajectories of both become interdependent, deeply binding according to the needs of the task.
2. Heterogeneous trajectories: The UAV flies at high speed in three-dimensional free space, while the USV moves slowly on the water surface, directly affected by currents and obstacles. The differences in speed and environmental constraints significantly affect overall system energy efficiency, making traditional single-platform trajectory planning methods no longer applicable.
In addition, the coupling of variables such as transduction beam design, target scheduling, and time allocation significantly increases the complexity of the joint optimization problem.

The research team in system framework and problem modeling adopts a multi-stage flying - homing mode: during the flying phase, the drone maintains communication with the unmanned boat, and upon reaching the homing point, it performs both perception and communication tasks simultaneously. This mode not only avoids the Doppler effect on perception performance during flight but also allows for the complex trajectory optimization problem to be broken down into stages for processing.

The entire task cycle is divided into several equal-length time slots, each containing multiple scanning rounds. In the homing mode, the drone uses the same set of antennas and spectrum resources to simultaneously transmit perception beams and communication beams, achieving hardware and spectrum sharing and reuse.

Communication link: Using an air-sea channel model, including large-scale path fading and small-scale fading, and based on uniform linear array construction of array response.
Perception link: Using a two-way radar channel model, combined with target radar cross section, deriving the corresponding relationship between perception signal-to-noise ratio and distance.
Energy consumption and optimization objective The total energy consumption of the system consists of the energy consumption of the drone and the unmanned boat:
Drone energy consumption: Includes rotorcraft flight profile power, induced power, drag power, and radio frequency power consumed by beam emission, modeled separately for homing and flying modes.
Unmanned boat energy consumption: Adopts a drag power model proportional to the square of relative water flow speed, fully considering the propulsion or obstruction effect of water flow on navigation.
The research team focuses on minimizing system total energy consumption as the core objective, constructing a joint optimization problem with multiple constraints, covering communication minimum rate, target cumulative perception signal-to-noise ratio, maximum transmission power, obstacle avoidance, and platform maximum speed.
Due to the highly coupled variables and discrete target scheduling variables, direct solution is extremely difficult. The team decomposes the original problem into subproblems of homing point selection and trajectory - beam joint optimization, solving them step by step through hierarchical progression.
III. Core Solution: Hierarchical Iterative Optimization Framework Subproblems
Step 1: Virtual Base Station Coverage and Clustering
Step 2: Bi-TSPN visit order planning The traditional Traveling Salesman Problem (TSP) only considers a single entity, whereas here two "travelers" - drones and unmanned boats - need to cooperate in their movement. The team has constructed a mixed cost index that integrates dual-platform energy consumption, taking into account distance, speed, and water flow impacts. The problem is transformed into a bi-TSPN with neighborhoods, and then the optimal visiting sequence is solved using the classical open-loop TSP algorithm.
Step 3: Fine-tuning of the hover point and time allocation. Based on a determined access order, introducing auxiliary variables such as flight duration, hover duration, and average speed, linearize non-convex energy consumption and motion constraints through the Continuously-Convex Approximation (SCA) method, iteratively optimize the precise position of the hover point and the allocation of time across different stages.
Sub-question 2: After determining the homing point with trajectory and beam optimization, conduct refined trajectory and beam design for each flight/hover phase separately.
Optimizes the flight mode to eliminate unnoticed interference during the flight phase, with the optimal beamforming being maximum ratio transmission (MRT). At this point, the optimization variable is simplified to dual-platform trajectory and communication power allocation. This problem is a convex optimization problem, which can be solved directly by convex optimization tools.
Hover mode optimization: The position of the drone during the hover phase is fixed, requiring simultaneous optimization of the unmanned boat trajectory and the transducer beamforming. The team adopted an alternating optimization algorithm:
When fixing the trajectory of unmanned boats, the problem of synthesizing the sensing and transmission beamforming is solved by semidefinite relaxation (SDR) method to minimize the transmitting power.
During fixed beamforming, the non-convex communication constraints are convexified through the SCA method to optimize the unmanned boat's navigation trajectory and minimize the energy consumption. The two methods alternately iterate until convergence, achieving the joint optimality of trajectory and beam.
IV. Simulation Verification and Core Conclusions The research team conducted extensive numerical simulations to validate the performance of the proposed scheme, comparing it with two classic baseline strategies: a sequential access strategy (where drones are suspended above the target one by one), and a leader-follower strategy (first optimizes the drone trajectory individually, then the unmanned boat's tracking trajectory).
Simulation results show that under typical scenarios of 15 targets, the total energy consumption of the proposed scheme is only 40.91 kJ, which is about 30% lower than the sequential access strategy and about 20% lower than the leader-following strategy. The core reason lies in the significant reduction of drone flight paths by cluster hovering, and the dual platform collaborative planning avoids the unnecessary energy consumption of unmanned boats.
In addition, the paper also reveals several key engineering rules:
1  
The more dispersed the target distribution, the faster the system energy consumption increases; the energy-saving advantage of clustering suspension is more obvious in dense target scenarios.
2  
The higher the perception signal-to-noise ratio, the more hover points needed, and the longer the dwell time, significantly increasing energy consumption, reflecting the trade-off between perception performance and system energy efficiency.
3  
The requirement for increased communication speed will force the two platforms to be closer, which in turn will change the entire trajectory planning and increase the total energy consumption of the system.
4  
The direction of the water flow significantly affects energy consumption. The energy consumption in reverse flow is much higher than that in forward flow, and the joint optimization framework automatically adjusts the route to take advantage of the water flow.
V. Summary and Outlook
In the future, the research team will further integrate scenarios such as edge computing unloading and drone docking charging within this framework, promoting the evolution of air-sea collaborative unmanned systems towards longer endurance and stronger intelligence.

## Images

![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](01.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](02.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](03.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](04.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](05.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](06.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](07.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](08.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](09.jpg)
![ISAC empowers the KH-UAV collaborative system: a new paradigm for energy efficiency optimization in joint drone-unmanned boat inspection. [Included is MATLAB code]](10.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
