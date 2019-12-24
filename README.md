# MECA 482 Control Systems Final Project

## Team Members
Thomas Allen: Mechanical Engineer<br/>Aaron Fisher: Mechatronic Engineer<br/>Kate Gordon: Mechanical Engineer<br/>Stuart Matthews: Mechatronic Engineer


### Introduction
Unstable systems and controls are important to simulate because some advanced control systems prove dangerous to test in real world applications. By simplifying the systems that exist in the real world, changes and behavior can be studied with little risk. The simple system known as, “balancing a ball on a beam” is an example of a small risk, simplified system. The cantilever in this project is a beam, usually anchored at one end and the other end is free to move, changing the angle of freedom of the system. The purpose of this project is to code a PID controller to balance something, either a toy car or a ball, on the beam by the use of sensors and code. The PID controller relates angle of the beam to the position of the rolling object and from this equation, the system can stabilize using feedback equations. The feedback signal, to control the beam’s angle, is derived from the ball’s current position to where the system is commanding the ball to move. This simplified system has many real-world applications, such as balancing an airplane wing in strong wind situations, although here, there is little error for adjustment and the situation is much more sensitive and dangerous. 

  There are several different variations and methods that are often experimented with on systems like the ball balancer project due to the knowledge of how the system should behave. For example, I. Petkoviç, M. Brezak, and R. Cupec built the system with an artificial vision based test [1]. Due to the preexisting results and knowledge of the system behavior, they were able to determine the rolling objects position with a camera. Similarly,  P. Dadios and R. Baylon used camera based vision systems with a study on fuzzy logic to balance the ball on the beam [2]. 
  
  This document reflects the controls systems project of a ball balancer system shown in the below figures 1 and 2, with the use of a small toy car instead of a ping pong ball (toy car not shown). The balancing system is comprised of a tall support and shorter support in which the beam is placed in between. The small support is connected to a lever which is attached to a wheel. As the wheel turns, this controls the height and angle of the beam in turn causing the toy car to roll along the beam. In theory, the end result of this project will balance the toy car in the center of the beam after a short duration of back and forth movements of the system due to the PID controller working properly. With adjustment and fine tuning the system should be able to balance the toy car in a timely manner. 
  
![Fig 1](https://user-images.githubusercontent.com/58873673/70845111-a3313b00-1dff-11ea-9be5-96872db1c250.PNG)   
![Fig 2](https://user-images.githubusercontent.com/58873673/70845144-e9869a00-1dff-11ea-95a0-d161ff75e9c1.PNG)


### Modeling
The physical system actually consists of an electromechanical system and a mechanical system. The first system contains a DC servo motor that take a signal from the controller and then translates that into mechanical action, or rotation displacement. The second system part is the cantilever that receives the rotation of the servo and converts it into linear displacement of the rolling ball.

Ball and Beam system model:
    A beam contains the ball where it can roll the length of the cantilever, as shown in figure 3. The free end of the beam is attached to a lever arm which connects to a servo gear. The beams angle changes as the servo gear turns. The ball will resultantly roll down the beam due to gravity and the new angle. The controllers design manipulates the balls position based on beam angle. 
    
  ![Fig 3](https://user-images.githubusercontent.com/58873673/70845179-42eec900-1e00-11ea-9cde-5472b456f19a.PNG)
    
From this model the transfer function relating the distance of the rolling ball to the angle of the servo rotation is shown in Equation (1). 

![Eqns 1](https://user-images.githubusercontent.com/58873673/70845168-294d8180-1e00-11ea-9206-ac4d8ba283f6.PNG)

    
### Electromechanical Model
  The DC motor is a common actuator in controls as it can easily be coupled and provides either rotary or translational motion. Either wheels, drums or cables are easily attached to motors for a variety of system modeling. The electric armature and equivalent circuit of the motor can be found in figure 4.

![Fig 4](https://user-images.githubusercontent.com/58873673/70845200-8a755500-1e00-11ea-9db0-526295916009.PNG)

The transfer function for this circuit shows the relationship between the rotation angle and voltage of the circuit, and can be found in equation (2).

![Eqns 2](https://user-images.githubusercontent.com/58873673/70845208-a4af3300-1e00-11ea-8e59-68bdabe86181.PNG)


### Controller Design
  The design of the controller for the overall systems proved to be difficult. To simplify the system as a whole, it was divided into different feedback loops which can be seen in figure 5. The first is the inner loop, which controls the gear angle position so the angle tracks the reference signal. The second loop, or the outer loop, controls the car’s position based on the feedback of the inner loop.

![Fig 5](https://user-images.githubusercontent.com/58873673/70845233-dfb16680-1e00-11ea-9c5a-8c3ec7f2eae4.PNG)


### Inner Loop Design
  The inner loop utilizes a PD controller to correctly determine the position of the servo gear. This control feedback system can be seen in figure 6. In order to meet the performance desired, the proportional and velocity constants, or “gains”, had to be determined. This can be seen in equation (3).  
  
  ![Fig 6](https://user-images.githubusercontent.com/58873673/70845250-08396080-1e01-11ea-8bab-1174e4bdbbf2.PNG)
  ![Eqns 3](https://user-images.githubusercontent.com/58873673/70845252-11c2c880-1e01-11ea-81bd-ee691a17f85d.PNG)
  
  The proportional controller is used from above and if the system proves to be unstable a derivative or integral term will be added.


### Outer Loop Design
  The outer loop contains a compensator term in the control design. This is due to the knowledge of a zero in the forward path increasing the bandwidth of the closed loop feedback system. On the contrary, adding a pole increases overshoot and rise time making the overall design less stable. In the practical sense, the overshoot must be minimized and bandwidth maximized. In figure 7, the inner loop is replaced with a single block G(s). 
  
  ![Fig 7](https://user-images.githubusercontent.com/58873673/70845305-ebe9f380-1e01-11ea-92ef-dba11c242908.PNG)
  
  
### Simulations
  To start the design of simulation, the proportional gain term was set to one hundred. The systems response was then recorded by using a step input of .25 m. The systems response curve can be seen below in figure 8.
  
  ![Fig 8](https://user-images.githubusercontent.com/58873673/70845327-1a67ce80-1e02-11ea-8e22-fe73ccb7c4cc.PNG)
  
  The system response remains unstable no matter the value of the proportional constant. The derivative term was then added and the response was plotted as seen in figure 9.
  
  ![Fig 9](https://user-images.githubusercontent.com/58873673/70845337-3b302400-1e02-11ea-8d49-9a274f69fb2f.PNG)
  
  After introducing the derivative term to the system the response shows stability. However, the overshoot was much too large and the settling time must drop. From simple PID controller characteristics, tuning the derivative term to a larger value the overshoot was lowered and the settling time was reduced. Then by increasing the proportional gain slightly the settling time came down to achieve the desired response. The system’s step response can be seen in figure 10.
  
  ![Fig 10](https://user-images.githubusercontent.com/58873673/70845343-51d67b00-1e02-11ea-875c-ea97f791060c.PNG)
  
  
### Resources
[1] Ali, A. T., Ahmed, A. M., Almahdi, H. A., Taha, O. A., & Naseraldeen, A. (2017). Design
    and implementation of ball and beam system using pid controller. MAYFEB Journal of
    Electrical and Computer Engineering, 1.
    
[2] Dadios, E. P., Baylon, R., De Guzman, R., Florentino, A., Lee, R. M., & Zulueta, Z. (2000,
    October). Vision guided ball-beam balancing system using fuzzy logic. In 2000 26th
    Annual Conference of the IEEE Industrial Electronics Society. IECON 2000. 2000 IEEE
    International Conference on Industrial Electronics, Control and Instrumentation. 21st
    Century Technologies (Vol. 3, pp. 1973-1978). IEEE. 

