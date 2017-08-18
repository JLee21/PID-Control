## PID Control

Student describes the effect of the P, I, D component of the PID algorithm in their implementation. Is it what you expected?
Visual aids are encouraged, i.e. record of a small video of the car in the simulator and describe what each component is set to.

I realized that the integral component of the PID controller is negligible. This is because the integral term helps mitigate constant error inducing elements in the real world. For example, if the vehicle had a bad steering alignment and was constantly shifting to the right, then a integral value of zero would be appropriate. But within the simulator the car is assumed to have perfect aligment and no constant drifting. 

With the integral term taken care of it was time to move on to the proportional and derivative terms, Kp and Kd.

Here's a look of how the vehicle performs over time with all PID terms set to zero.

![]()

Clearly, the vehicle continues to accumulate cross track error (drift away from the center of the track).

If we keep the proportional and integral at zero, let's see what a +/- 1 for the derivate term accomplishes.

![]()

For the derivative term, it is the rate of change of the error contributes to the steering angle.

If we keep the integral and derivative term zero, let's see what a positive and negative proportional value contributes.

![]()

The proportional term scales with the error of the system. If the error is large, the contributuion to the total error would be a scaling factor of that error. Clearly, a negative proportional term compensates the magnitude of the error by inversing the steering commmand while a postive proportional term simply scales positively witht the error.

Student discusses how they chose the final hyperparameters (P, I, D coefficients). 
This could be have been done through manual tuning, twiddle, SGD, or something else, or a combination!
