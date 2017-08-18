## PID Control

Below is a brief summary of the PID components of the model's PID steering system.

![](https://github.com/JLee21/PID-Control/blob/master/img/eqn2.JPG)

I realized that the integral component of the PID controller is negligible. This is because the integral term helps mitigate constant error-inducing elements in the real world. For example, if the vehicle has a bad steering alignment and is constantly shifting to the right, then a integral value would be appropriate. But within the simulator the car is assumed to have perfect alignment and no constant drifting. 

With the integral term taken care of it's time to move on to the proportional and derivative terms, Kp and Kd.

Here's a look of how the vehicle performs over time with all PID terms set to zero.

![](https://github.com/JLee21/PID-Control/blob/master/img/zero.jpg)

Clearly, the vehicle continues to accumulate cross track error (drift away from the center of the track).

If we keep the proportional and integral term at zero, let's see what a +/- 1 for the derivate term accomplishes.

![](https://github.com/JLee21/PID-Control/blob/master/img/kd.jpg)

For the derivative term, it is the rate of change of the error contributes to the steering angle. The quicker the error term grows, the larger the derivative term's contribution has on the total error of the system. This term is particularly important during turns because term is apt to changes in the track's direction.

If we keep the integral and derivative term zero, let's see what a positive and negative proportional value contributes.

![](https://github.com/JLee21/PID-Control/blob/master/img/kp.jpg)

The proportional term scales with the error of the system. If the error is large, the contribution to the total error would be a scaling factor of that error. Clearly, a negative proportional term compensates the magnitude of the error by inversing the steering command while a positive proportional term simply scales positively with the error.

Taking in account the statements above, I was able to manually tune the PID terms to produce the following results:

![](https://github.com/JLee21/PID-Control/blob/master/img/best.jpg)

The plot above shows a consistently low cross track error throughout the track.

I noticed the proportional term to be sensitive to changes while the derivative term needed to be increased to handle the change in steering as the vehicle drove through curves. If the proportional term was too high, the vehicle would induce oscillations frequently. If the derivative term was too high, the vehicle would react too violently on turns by commanding sharp steering commands.
