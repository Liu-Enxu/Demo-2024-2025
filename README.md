![image](https://github.com/user-attachments/assets/e942e466-079f-45df-b4e0-bb45ccb46c27)![image](https://github.com/user-attachments/assets/ffb6fc83-4d6a-40de-b2e1-4778aa867bcf)# Demo-2024-2025
# 1 A Quick Deployment of Markov Decision Process in Partially-Unknown 3D Discrete Space
## 1.1 Problem Definition
Markov Decision Process works well in 2D, but 3D space? Unsafe environment w/ limited info?
Problem setup: discrete space, hidden obstacles, scanning function
Transition matrix is introduced more here

## 1.2 Methods
### 1.2.1 Value iteration
Need to determine the transition matrix
![image](https://github.com/user-attachments/assets/04af3955-7b85-4bed-975b-f7e88d6a341b)
7 actions: all directions + scan

![image](https://github.com/user-attachments/assets/db5ec620-6d86-4a33-83ed-7e4d272ac4ab)
### 1.2.2 Transition Matrix
General alignment:
![image](https://github.com/user-attachments/assets/18c0e254-b245-4107-a653-0b0e80ccedc1)
What about hidden blocks?

Naïve Simplification of the problem: a priori num of hidden obstacles (In real-world: uncharted water area)
Now we just need to know how many hidden obstacles are found and move to corresponding states.
![image](https://github.com/user-attachments/assets/e560c3b2-5689-467f-a76b-1006c8d70176)

Naïve Estimation of obstacle occurrence of an unscanned block:
![image](https://github.com/user-attachments/assets/03de46d8-0576-4c9f-8af3-fffc2d704f8d)
i.e. if too risk to move around, scan!

## 1.3 Results
### No scan
https://github.com/user-attachments/assets/1052776b-1a22-43d1-8b5d-0297be5bb258
### Scan
https://github.com/user-attachments/assets/3667fc2b-0082-4048-b058-940e3cd03e0a
### Iterations: Fine-tuned Scan
https://github.com/user-attachments/assets/441e8422-77da-4799-8c29-cb26525197e7


# 2 GNSS/INS Loose Coupling using IAEKF, IGGIII and KGP method
## 2.1 Problem Definition
GNSS & INS data suffer from dynamic measure noise; EKF cannot handle dramatic non-linearity
Develop a filtering algorithm based on model based (KF variations) & machine learning method
Problem setup: geo-data & state models from KF-GINS [1] project; combine IAEKF, IGGIII & KGP methods

## 2.2 Method
![image](https://github.com/user-attachments/assets/96b7c0ef-2360-4ae6-ab9a-c3455f1e4720)
![image](https://github.com/user-attachments/assets/34176697-2e34-4f48-ada4-4be7421f03ae)
### 2.2.1 IAEKF (Improved Adaptive Estimation-Kalman Filter (IAEKF) [2])
![image](https://github.com/user-attachments/assets/67c8b5ee-4897-477a-a2ad-c57855de4ac7)
### 2.2.2 IGGIII scheme [3]: optimizing the sliding sampling window
![image](https://github.com/user-attachments/assets/384ed96d-bd7e-4586-b192-301ec9d34edc)
### 2.2.3 KGP method [4]: compensating for the cumulative error
![image](https://github.com/user-attachments/assets/c1fe5f18-1ad1-4d5d-8c23-3c7a6cfe0bb7)

## 2.3 Results
A general performance is validated.
![image](https://github.com/user-attachments/assets/2a135272-d292-4369-8adc-f47c2388ccab)
![image](https://github.com/user-attachments/assets/b18d5c95-9ade-47d0-9467-f5ba7c6956b3)

## 2.4 References
[1] X. Niu, Q. Chen, "Notes for GNSS/INS Integrated Navigation and Principles of IMU Navigation", i2Nav Lab, GNSS Research Center, Wuhan University, 2022
[2]B. Hongwei, J. Zhihua, and T. Weifeng, “IAE-adaptive Kalman filter for INS/GPS integrated navigation system,” Journal of Systems Engineering and Electronics, vol. 17, no. 3, pp. 502–508, Sep. 2006, doi: https://doi.org/10.1016/s1004-4132(06)60086-8.
[3] “Adaptive Fading Kalman Filter Based on IGGIII Scheme - CNKI,” Cnki.net, 2020. http://kns.cnki.net/kcms/detail/11.2127.TP.20190815.1359.008.html (accessed Nov. 05, 2024).
‌[4] H. Zhang et al., “A Novel KGP Algorithm for Improving INS/GPS Integrated Navigation Positioning Accuracy,” Sensors, vol. 19, no. 7, p. 1623, Apr. 2019, doi: https://doi.org/10.3390/s19071623.


# 3 MPC crash avoidance
## 3.1 Problem Definition
The vehicle model is defined as follows:
![image](https://github.com/user-attachments/assets/b61ae373-2dea-4a1a-bc31-b0d0a9282af8)

## 3.2 Method: CVXPY & MPC & CasADi
For trajectory following:
![image](https://github.com/user-attachments/assets/f6acc106-4422-4c29-b3a7-69292389eebe)
For obstacle avoidance:
![image](https://github.com/user-attachments/assets/595da2f0-d3ec-486c-adc4-f9a7b63d87e0)

## 3.3 Result
For trajectory following:
![image](https://github.com/user-attachments/assets/d49734e5-7930-42fa-84cf-dd72f31c9536)
![image](https://github.com/user-attachments/assets/6a7bf83d-a25e-4f50-ae03-846694d4b774)
For obstacle avoidance:
![image](https://github.com/user-attachments/assets/09ccd5f3-acc5-4ead-beb6-f714eb3a8b04)
![image](https://github.com/user-attachments/assets/e7fdd52f-fd16-4178-9ddb-d87e8739d669)
![image](https://github.com/user-attachments/assets/b0cdb96c-5803-4392-8f98-15fa20c48e9c)
![image](https://github.com/user-attachments/assets/8f307f54-a07f-46a2-837b-259e67eb49b6)


# 4 Balancing Robot
## 4.1 Problem Definition
A fully model-based control robot balancing algorithm
Implemented in various phases
Problem setup: MuJoCo, inverted pendulum, controller design

## 4.2 Method
Inverted pendulum models:
![image](https://github.com/user-attachments/assets/27b50c16-a9fd-4cb9-be50-69e35c4d0c89)
![image](https://github.com/user-attachments/assets/07ee66ae-9404-483d-afc7-6fce59abac07)
Step-by-step: simulate using simplified models, then apply to the humanoid
PID,LQR,Cross-feedback etc.…

## 4.3 Result
Design the models in cube model
https://github.com/user-attachments/assets/31895acd-2482-41db-af10-7180ffec975e
https://github.com/user-attachments/assets/78c6d34a-eee2-4bc5-aa72-7966d02a2a7e
Validate in humanoid model
https://github.com/user-attachments/assets/4d749930-0843-4ae1-9515-e39a5e260ee1
https://github.com/user-attachments/assets/17bbe710-ceb3-4b58-b0d3-a0464d87aefb
https://github.com/user-attachments/assets/6416f7ae-5d1a-47c5-907a-ea21a94d1abf
Explore more (more DOF, more actuation)
https://github.com/user-attachments/assets/5dabc400-c3ed-44e0-8a97-0996fd796a8c
https://github.com/user-attachments/assets/7892e3f7-b54a-4a72-8453-c776832f7afb


# 5 DAQ/trigger system for seat actuation system
## 5.1 Problem Definition
A seat actuation system that helps to ease motion sickness, how to trigger/collect data?
Problem setup: DAQ, DAQ GUI, GPS triggering

## 5.2 Method
### 5.2.1 Wearables
2 Adjustable chest-mounted straps.
2 pairs of head straps with a mount.
Listening to previous test subjects we decided to get more adjustable and bigger chest mounts.
![image](https://github.com/user-attachments/assets/36af35a0-08bc-468e-9a1a-017ac685b68c)
![image](https://github.com/user-attachments/assets/e5351018-26a1-43ed-a619-2d13610d239b)

### 5.2.2 DAQ system
Two Raspberry Pi pico microcontrollers, one acts as DAQ one acts as switch. IMU connect to MUX, then connected to picos through I2C bus along with the GPS and the BME sensor.
![image](https://github.com/user-attachments/assets/16958ad9-611b-4674-b6aa-ef0cc9e57aa6)

### 5.3 Result
(If you wish to see more on this please arrange an online meeting)
https://github.com/user-attachments/assets/0227ccb9-be26-496d-9703-80b09ed90ce0


# 6 Quadcopter TOF/IMU data extraction
## 6.1 Problem Definition
Need to develop filtering algorithm for quadcopter, but needs data
Extract IMU, TOF (lidar)
![image](https://github.com/user-attachments/assets/bf95a124-1f6b-487e-8d55-8a9ac3256bd0)

## 6.2 Method
ESP32 has WIFI function, communicate with ESP32 through UDP comm:
  Send out data packets containing IMU & TOF data
  Receive and print out the packets with a UDP listener

## 6.3 Result
https://github.com/user-attachments/assets/1a206662-0b99-4b93-96cb-d070f77f376c
![image](https://github.com/user-attachments/assets/5ffb5e06-fa8a-4b29-a946-02c60d89c3fc)
