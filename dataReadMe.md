This document provides a comprehensive overview of the data structure implemented in the paper folding simulation code. The simulation models a complex process involving various entities such as papers, dispensers, robots, operators, jigs, workstations, and waste stations.

Classes
1. Paper
Represents a piece of paper in the simulation.
Attributes:
env (Simulation environment): The environment in which the paper exists.
is_defective (Boolean): Indicates whether the paper is defective.
2. PaperDispenser
Manages the availability of paper in the simulation.
Attributes:
env (Simulation environment): The environment in which the dispenser operates.
papers (SimPy Dispenser): A dispenser object managing the availability of papers.
Methods:
check_availability_paperdispenser(operator): Checks if there is enough paper in the dispenser.
pick_paper(operator, workstation1, Robot): Picks up paper from the dispenser.
restock_paperdispenser(): Restocks the paper dispenser.
3. Robot
Represents a robot in the simulation.
Attributes:
env (Simulation environment): The environment in which the robot operates.
workstation1 (Reference): Reference to the associated Workstation1.
robot (SimPy Resource): Represents the robot as a resource with a capacity of 1.
Methods:
actuate(workstation1): Simulates the robot's actuation process.
load_paper(paper, paperdispenser): Simulates loading paper onto the robot.
push_paper_to_jig1(paper): Simulates pushing paper to Jig1.
insert_paper_to_jig2(jig2): Simulates inserting paper into Jig2.
extract_paper_from_jig2(jig2): Simulates extracting paper from Jig2.
return_to_start(): Simulates the robot returning to the start position.
hand_over_paper(workstation2): Simulates handing over paper to Workstation2.
4. Operator
Represents an operator in the simulation.
Attributes:
env (Simulation environment): The environment in which the operator works.
workstation1 (Reference): Reference to the associated Workstation1.
folded_papers (Unused attribute): A placeholder attribute, currently unused.
Methods:
quality_check_fold1(paper): Simulates quality check after folding in Jig1.
place_paper_on_robot1(robot, paper): Simulates placing paper on Robot1.
quality_check_fold2(paper): Simulates quality check after folding in Jig2.
place_paper_on_robot2(robot, paper): Simulates placing paper on Robot2.
5. Jig1
Represents Jig1 in the simulation.
Attributes:
env (Simulation environment): The environment in which Jig1 operates.
Methods:
fold1(): Simulates the folding process in Jig1.
6. Jig2
Represents Jig2 in the simulation.
Attributes:
env (Simulation environment): The environment in which Jig2 operates.
Methods:
fold2(): Simulates the folding process in Jig2.
7. Workstation2
Represents Workstation2 in the simulation.
Attributes:
env (Simulation environment): The environment in which Workstation2 operates.
8. WasteStation1
Represents a waste station for defective papers in Jig1.
Attributes:
env (Simulation environment): The environment in which WasteStation1 operates.
Methods:
dispose(paper): Simulates the waste disposal process for defective papers.
9. WasteStation2
Represents a waste station for defective papers in Jig2.
Attributes:
env (Simulation environment): The environment in which WasteStation2 operates.
Methods:
dispose(paper): Simulates the waste disposal process for defective papers.
10. WorkStation1
Represents Workstation1 in the simulation.
Attributes:
env (Simulation environment): The environment in which Workstation1 operates.
robot (Reference): Reference to the Robot.
workstation2 (Reference): Reference to Workstation2.
waste_station1 (Reference): Reference to WasteStation1.
waste_station2 (Reference): Reference to WasteStation2.
folded_papers (Counter): Tracks the number of folded papers.
total_operation_time (Accumulator): Accumulates the total production time.
Methods:
workstation1_process(operator, paper, jig1, jig2): Simulates the entire process at Workstation1.
Simulation Environment
SimPy environment object (env) is used to manage the simulation.
Paper instances are generated and processed in the paper_generator function.