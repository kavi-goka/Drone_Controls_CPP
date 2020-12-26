# Implementing Controller 

The main goal of this project is to develop a cascaded PID controller for a virtual drone which could perform as expected in certain scenarios. 

**Scenario 1 : Intro** 

Initially, when the C++ sim is run, the drone will not hover and will move towards the ground. The drone can be made to hover, by adjusting the Mass parameter to 0.5 in the QuadControlParams.txt. 


**Scenario 2 : Body rate and Roll/Pitch Controller**

Under the function GenerateMotorCommand, the following equations should solved. 


Here F1 to F4 are the thrust of each motors, tau(x,y,z) are the respect moments, kappa is the drag to thrust ratio and l is the length of arm. Next is to implement a P controller for the Body rate using Inertia. Tune the Kp(pqr) to prohibit the drone from flipping. Once that is complete, the Roll/Pitch controller needs to be implemented. For this, the Rotation Matrix R needs to be used along with the following equation. 



After implementation is complete, the Kp_bank value needs to be tuned along with Kp_pqr. 


**Scenario 3 : Position Control - Lateral and Altitude Controller**

The Altitude controller is a PD Controller and will have the following equations implemented in the function.


The Lateral control is a PID controller to control the lateral acceleration and the Yaw control is a P controller between -pi and pi. 
The next step is to tune the following parameters kpYaw,kpPosXY, kpVelXY, kpPosZ and kpVelZ. 


**Scenario 4 : Non-idealities**

In this scenario, there are 3 quads moving a meter forward. The mass of the quads are shifted a bit and therefore each will act a little different from each other. Therefore, the PD controller for Altitude control was modified to a PID Controller. Tuning the parameters will eventually enable a proper motion of all 3 drones and to pass this section. 


**Scenario 5 : Tracking trajectories**

For this scenario, everything is already set ready. There will be 2 drones flying 2 trajectories. If everything was done right, the drones will follow the trajectories close enough. 








