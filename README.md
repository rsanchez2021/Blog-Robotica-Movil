# Mobile Robotics Blog
Welcome to my personal blog of the Mobile Robotics course of the Robotics Engineering degree at Universidad Rey Juan Carlos. In this blog I will be updating the progress in the practices of the subjects as well as the final result of each of them. I hope you like it.

## Introduction
The first day we started installing the docker needed to perform the practices. While we were waiting, we were explained how to use the [Unibotics](https://unibotics.org/) platform and the interface we have.

## Practice 1 Vacuum cleaner 

### DAY 1
Today I started the practice. The goal of today was to make the basis of the practice to then be able to make the algorithm more efficient. Basically, I have made the state machine with three states: FORWARD, BACK and TURN. With that, I have managed to "clean up" what is shown in the picture. The next goal is to add a random for the spin and implement a spiral.

![Screenshot from 2023-09-25 11-22-32](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/41298f92-c23f-46d1-a17f-6d6124e18718)

### DAY 2
The goal of this day was to implement that the turn is a random time and modify parameters to make it go more smoothly. 

At the beginning I had problems with the random because it reset the parameters in each iteration and the spin time was never fulfilled. In the end I managed to get it out. Another thing that I have managed to improve was that before in the most closed room it was very difficult to enter, but thanks to the random spin time the vacuum cleaner is able to enter (you can see it in the image).


![Screenshot from 2023-09-26 09-31-20](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/7bf76171-0e51-43ed-bf88-2b44bb0e6380)

### DAY 3
The purpose of day two is to implement a fourth spiral state. At first I tried to follow the formula ***v=r⋅ω*** and keep varying the radius of the circle, but this was not the most efficient or simple thing to do. Finally, I decided that the best option was to increase the linear velocity directly without making it dependent on the radius. 

To find out the specific parameters what I did was trial and error. If I increased the speed too much the spiral would open up and leave blank holes as you can see in the picture:

![Screenshot from 2023-09-27 18-31-40](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/01bfc2d1-20ef-4e53-9ad1-17f16eee2a9f)

### Final delivery
This is the corresponding video with my final code for three minutes and a photo after leaving it for several more minutes. 

As a final conclusion, the goal was to make an algorithm based on a reactive code with a state machine, a random time for the spin and a fourth spiral state.

