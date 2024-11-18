# Demo-2024-2025
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
