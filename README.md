# Mobile Robotics Blog
Welcome to my personal blog of the Mobile Robotics course of the Robotics Engineering degree at Universidad Rey Juan Carlos. In this blog I will be updating the progress in the practices of the subjects as well as the final result of each of them. I hope you like it.

## Introduction
The first day we started installing the docker needed to perform the practices. While we were waiting, we were explained how to use the [Unibotics](https://unibotics.org/) platform and the interface we have.

## Practice 2 Follow line

### Day 1
Today's goal is to create a color filter to visualize the red line and obtain the centroid. I must take into account that the Formula 1 camera is not centered, so the centroid will be slightly offset.

![Captura desde 2023-10-09 09-42-19](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/8055f22c-5db2-4982-890b-4a19ccc66309)

Once the color filter is applied and the centroid is obtained, the vision looks like this:

![image](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/93374e9f-a3d8-49d8-b424-95c94e135d14)

### Day 2
The objective for today was to complete a lap and fine-tune the PID control as much as possible. After several attempts, the fastest lap was completed in 3 minutes and 16 seconds. The goal for the next day will be to distinguish between curves and straight sections in order to set different speeds and save time.

### Day 3
Once the distinction between curves and straight sections based on the error is established, the lap time is 160 seconds. If you want to see the video click [here](https://raw.githubusercontent.com/rsanchez2021/Blog-Robotica-Movil/main/p2_160.webm)

The next step I need to take is to fine-tune the parameters gradually to reduce times. I considered adding a PID controller to the linear velocity when the error is very high (in curves), and although it worked very well, it was moving quite slowly:

![Screencast from 10-14-2023 07 17 05 PM (online-video-cutter com)(1)](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/cba9ea29-75d9-4e07-b88c-b144317996de)


### Subsequent Days
On the following days, I focused on refining the parameters to further reduce lap times. After several attempts, I achieved the fastest lap in **111 seconds**. However, that code, on other circuits, ended up with the car crashing. Therefore, the code I sent works for all circuits (with specific changes for each one), but the following [code](https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/p2_line_v3.py) is for the fast lap on the simple circuit.

Finally, this is my fastest lap on the simple circuit. The video is playing at 2x speed; if you want to watch it at normal speed, click [here](https://raw.githubusercontent.com/rsanchez2021/Blog-Robotica-Movil/main/p2_fast.webm).



[screencast-from-10-15-2023-02-34-23-pm-ipjma1fx_sGqsBapt.webm](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/f9ba6406-0699-4763-bbd8-439076174d83)




## Practice 1 Vacuum cleaner 

### DAY 1
Today I started the practice. The goal of today was to make the basics of the practice to then be able to make the algorithm more efficient. Basically, I have made the state machine with three states: FORWARD, BACK and TURN. With that, I have managed to "clean up" what is shown in the picture. The next goal is to add a random for the spin and implement a spiral.

![Screenshot from 2023-09-25 11-22-32](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/41298f92-c23f-46d1-a17f-6d6124e18718)


### DAY 2
The goal of this day was to implement a random variable associated with the turn time and modify parameters to make it go smoother.

At the beginning I had problems with the random variable because it reset the parameters in each iteration and the spin time was never fulfilled. In the end I managed to get it out. Another thing that I have managed to improve was that before it was very difficult to enter in the most closed room, but thanks to the random spin time the vacuum cleaner is able to enter (you can see it in the image).


![Screenshot from 2023-09-26 09-31-20](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/7bf76171-0e51-43ed-bf88-2b44bb0e6380)

### DAY 3
The purpose of day three was to implement a fourth spiral state. At first I tried to follow the formula ***v=r⋅ω*** and keep varying the radius of the circle, but this was not the most efficient or simple way to do it. Finally, I decided that the best option was to increase the linear velocity directly without making it dependent on the radius. 

To find out the specific parameters what I did was trial and error. If I increased the speed too much the spiral would open up and leave blank holes as you can see in the picture:

![Screenshot from 2023-09-27 18-31-40](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/01bfc2d1-20ef-4e53-9ad1-17f16eee2a9f)

### Final delivery
This is the corresponding video with my final code for three minutes and a photo after leaving it for several more minutes. 

![Screencast from 09-28-2023 03 20 54 PM(1)](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/ff13c290-3915-4f54-8e2a-6bdde5745542)


![Screenshot from 2023-09-28 17-56-28](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/3dde564e-6654-45eb-87c5-b37482a35cf6)




As a final conclusion, the goal was to make an algorithm based on a reactive code with a state machine, a random time for the spin and a fourth spiral state.

