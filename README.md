## Control Systems Final Project

### Introduction
Unstable systems and controls are important to simulate because some advanced control systems prove dangerous to test in real world applications. By simplifying the systems that exist in the real world, changes and behavior can be studied with little risk. The simple system known as, “balancing a ball on a beam” is an example of a small risk, simplified system. The cantilever in this project is a beam, usually anchored at one end and the other end is free to move, changing the angle of freedom of the system. The purpose of this project is to code a PID controller to balance something, either a toy car or a ball, on the beam by the use of sensors and code. The PID controller relates angle of the beam to the position of the rolling object and from this equation, the system can stabilize using feedback equations. The feedback signal, to control the beam’s angle, is derived from the ball’s current position to where the system is commanding the ball to move. This simplified system has many real-world applications, such as balancing an airplane wing in strong wind situations, although here, there is little error for adjustment and the situation is much more sensitive and dangerous. 

  There are several different variations and methods that are often experimented with on systems like the ball balancer project due to the knowledge of how the system should behave. For example, I. Petkoviç, M. Brezak, and R. Cupec built the system with an artificial vision based test [1]. Due to the preexisting results and knowledge of the system behavior, they were able to determine the rolling objects position with a camera. Similarly,  P. Dadios and R. Baylon used camera based vision systems with a study on fuzzy logic to balance the ball on the beam [2]. 
  
  This document reflects the controls systems project of a ball balancer system shown in the below figures 1 and 2, with the use of a small toy car instead of a ping pong ball (toy car not shown). The balancing system is comprised of a tall support and shorter support in which the beam is placed in between. The small support is connected to a lever which is attached to a wheel. As the wheel turns, this controls the height and angle of the beam in turn causing the toy car to roll along the beam. In theory, the end result of this project will balance the toy car in the center of the beam after a short duration of back and forth movements of the system due to the PID controller working properly. With adjustment and fine tuning the system should be able to balance the toy car in a timely manner. 

### Modeling

The physical system actually consists of an electromechanical system and a mechanical system. The first system contains a DC servo motor that take a signal from the controller and then translates that into mechanical action, or rotation displacement. The second system part is the cantilever that receives the rotation of the servo and converts it into linear displacement of the rolling ball.

Ball and Beam system model:
    A beam contains the ball where it can roll the length of the cantilever, as shown in figure 3. The free end of the beam is attached to a lever arm which connects to a servo gear. The beams angle changes as the servo gear turns. The ball will resultantly roll down the beam due to gravity and the new angle. The controllers design manipulates the balls position based on beam angle. 
    
# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ballonbeam/ballonbeam/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
