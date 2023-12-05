# Mobile Robotics Blog
Welcome to my personal blog of the Mobile Robotics course of the Robotics Engineering degree at Universidad Rey Juan Carlos. In this blog I will be updating the progress in the practices of the subjects as well as the final result of each of them. I hope you like it.

* [Index][Ind]
* [Introduction][intro]
* [Practice 1][p1]
* [Practice 2][p2]
* [Practice 3][p3]

[Ind]: https://github.com/rsanchez2021/Blog-Robotica-Movil/main/README
[intro]: https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/README.md#introduction
[p1]: https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/README.md#practice-1-vacuum-cleaner
[p2]: https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/README.md#practice-2-follow-line
[p3]: https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/README.md#practice-3-obstacle-avoid


## Introduction
The first day we started installing the docker needed to perform the practices. While we were waiting, we were explained how to use the [Unibotics](https://unibotics.org/) platform and the interface we have.

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


## Practice 3 Obstacle Avoid
The objective of this practice is to make the vehicle successfully complete a full lap of the circuit without encountering any obstacles, such as walls or other vehicles. To achieve this, it is equipped with a laser system, and it accomplishes the task by calculating both repulsive forces (resulting from obstacles) and attractive forces (related to waypoints).

### Day 1
On the first day, we were provided with a detailed explanation of the practical procedure and how to calculate the forces and potential errors that may arise. They emphasized that the waypoint should not be precise; rather, it should be represented in area, as a precise waypoint could result in the vehicle overturning. Additionally,  we must be careful with the forces, as they can become trapped in a local minimum. This means that both forces cancel each other out, causing the vehicle to remain stationary. To address this, one option is to wait for a certain period, and if the situation persists, execute a turn and continue, repeating this process until escaping the local minimum is achieved.

Today, I have experimented with the provided functions and made an initial outline of the practical exercise.

### Day 2
Today, we were informed about potential errors we might encounter. One of them pertains to the laser data reading function. In the event that the laser data arrives empty, if we utilize a while loop or a for loop and assume a range of 10, it does not function correctly. To address this issue, several solutions were provided, such as using enumerate(laser_data.values) or for dist in laser_data.values. For this practice, I have decided that the best option is as follows:

```python3
def parse_laser_data(laser_data):
    laser = []
    for i in range(len(laser_data.values)):
        dist = laser_data.values[i]/1000.0
        angle = math.radians(i)
        laser += [(dist, angle)]
    return laser
```

Another thing that was explained to us was the function for creating the repulsive force. As can be seen in the code, specific weights need to be assigned based on the distance to ensure that the repulsive force is accurate.

```python
x = 1 / distance * math.cos(angle - math.pi / 2) * -1
y = 1 / distance * math.sin(angle - math.pi / 2) * -1

```

### Day 3

Today, after implementing the majority of the functions, I focused on fine-tuning the weighting of the forces to optimize the resultant vector. Increasing the weight of the repulsive force caused the car to veer off the track and move backward. On the other hand, a significant increase in the weight of the attractive force led to the car colliding with the walls.These have been the weights that I have given to each force

```python
ALPHA = 3.5
BETA = 0.00005
resultant_force = ALPHA * atractive_force + BETA * repulsive_fource
```


Moreover, when I achieved a relatively balanced set of weights to make it work, there was an issue with certain cars getting stuck in a local minimum. I attempted to implement a function that, in the event of such a situation, would wait for a period and, if the issue persisted, proceed in a straight path. However, I was unable to find a solution that allowed the function to address this challenge while keeping the code responsive.


[minimo-local_lDbwaWyZ.webm](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/71cac2a0-6eb7-4e30-a8c1-5b9755e0f86a)



### Rest of days

During the remaining days, my tasks mainly involved addressing minor errors, such as variable names, and debugging the code. When I attempted to enhance the code, I encountered issues, as the car was veering off the track, as depicted in the image. This problem arose because I had not defined the target area as sufficiently large for the car to reach and make a successful turnaround.


[screencast-from-11-06-2023-060634-pm_c2x59bm5.webm](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/c79cbd49-cf85-453a-a222-454a2d2cb94b)


### Final video
This is the final video accelerated x2, if you want to see it at normal speed [click](https://github.com/rsanchez2021/Blog-Robotica-Movil/blob/main/p3_final.webm) here.

[p3-final_PdR7TvHw.webm](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/1614c418-c97c-4ab0-af90-899c5d7fb1d2)

## Practice 4 Global Navigation

El objetivo de la práctica es implementar un código enel que se calcule un mapa por gradiente de una ciudad donde hay obstáculos, calcular la ruta a un punto y posteriormente navegar con el taxi hasta el punto.

El primer paso es realizar el mapa de costes con una cola de prioridad. Para ello, he implementado la función binarize_map en la que toma las paredes detectadas y crea un matriz binaria, asignando valores de 255 a las ubicaciones ocupadas y 0 a laslibres. Selecciono las coordenadas de las parede y, mediante un algoritmo, expando la marca hacia las áreas adyacentes a las paredes para asegurar un margen de seguridad alrededor de ellas. Para generar el gradiente y rellenarlo, uso la función fill_gradient que calcula el mapa de costes desde la posición inicial hasta la final. Realiza un procesamiento en cola, expandiendo gradualmente el área de gradiente y fnalmente devuelve las posiciones de los obstáculos detectados durante el llenado. Parahacer esta parte del código, mehe guiado con la función que ya implementamos en la asignatura de Inteligencia Artificial que puedes ver en este [repo](https://gitlab.etsit.urjc.es/rebeca1/inteligencia_artificial/-/tree/main/P1_Search?ref_type=heads).

Aquí hay varios vídeos de como he ido haciendo mapa a lo largo del tiempo

Costes de los obstáculos muy altos, obstáculos muy inflados:

https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/c4f1ce61-a102-4b55-96dc-75887dfc526b

Costes delos obstáculos muy bajos, el coche se come las esquinas

https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/e1e21b89-4f14-4653-9fdc-1ff85bc2b413

Una vez se ha creado el mapa de gradiente, se calcula la trayectoria óptima. Dentro del bucle principal, se está constantemente ajustando la velocidad y la dirección del taxi para seguir la trayectoria, además de comprobar si ha llegado a su destino. Algunas rutas calculadas:

![Screenshot from 2023-12-05 21-40-09](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/eb72b380-a862-44d5-be19-07caa480d3bc)

![Screenshot from 2023-12-05 21-41-18](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/ae2bd770-be1b-4df6-a5fc-7db3862dc310)

![Screenshot from 2023-12-05 21-44-44](https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/c33d73ac-b29e-4ebc-b0c6-fbcd7f451e17)



https://github.com/rsanchez2021/Blog-Robotica-Movil/assets/113595025/426b1dc3-8786-4d7d-82c3-7714cc067078

