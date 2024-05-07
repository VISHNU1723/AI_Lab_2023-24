# Ex.No: 11  Planning –  Monkey Banana Problem
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 
### Program:
```
(define (domain monkey)	       
  (:requirements :strips)
   (:constants monkey box knife bananas glass waterfountain)
   (:predicates (location ?x)
	       (on-floor)
	       (at ?m ?x)
	       (hasknife)
	       (onbox ?x)
	       (hasbananas)
	       (hasglass)
	       (haswater))
   ;; movement and climbing
  (:action GO-TO
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
	     :effect (and (at monkey ?x) (not (at monkey ?y))))
   (:action CLIMB
	     :parameters (?x)
	     :precondition (and (location ?x) (at box ?x) (at monkey ?x))
	     :effect (and (onbox ?x) (not (on-floor))))
   (:action PUSH-BOX
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) 
				 (on-floor))
	     :effect (and (at monkey ?x) (not (at monkey ?y))
			   (at box ?x)    (not (at box ?y))))
  ;; getting bananas
  (:action GET-KNIFE
	     :parameters (?y)
	     :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
	     :effect (and (hasknife) (not (at knife ?y))))
  (:action GRAB-BANANAS
	     :parameters (?y)
	     :precondition (and (location ?y) (hasknife) 
                                 (at bananas ?y) (onbox ?y))
	     :effect (hasbananas))
  ;; getting water
  (:action PICKGLASS
	     :parameters (?y)
	     :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
	     :effect (and (hasglass) (not (at glass ?y))))
  (:action GETWATER
	     :parameters (?y)
	     :precondition (and (location ?y) (hasglass)
				 (at waterfountain ?y)
				 (at monkey ?y)
				 (onbox ?y))
	     :effect (haswater)))
```
### Input 
```

(define (problem pb1)
    	(:domain monkey)
  	(:objects p1 p2 p3 p4 bananas monkey box knife)
  	(:init (location p1)
		(location p2)
		(location p3)
		(location p4)
	 	(at monkey p1)
		(on-floor)
		(at box p2)
		(at bananas p3)
	 	(at knife p4)
	)
  	(:goal (and (hasbananas)))
)
```

### Output/Plan:
![Screenshot 2024-05-07 195903](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/9396a5dc-52ed-4c6b-b14e-c90a0ead1bf2)

![Screenshot 2024-05-07 195916](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/622c848a-c709-4069-9f5d-765c844a96b0)

![Screenshot 2024-05-07 195932](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/ff6a0461-94d2-4bad-b3a3-c3213234a41c)

![Screenshot 2024-05-07 195951](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/76c64178-2ca9-4296-b75b-876a13c60ea7)

![Screenshot 2024-05-07 200007](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/56c53809-91e5-4b39-86a8-66ba51d4fa03)

![Screenshot 2024-05-07 200019](https://github.com/VISHNU1723/AI_Lab_2023-24/assets/160720840/f5484834-20d4-437e-b51d-209ff3982791)

### Result:
Thus the plan was found for the initial and goal state of given problem.
