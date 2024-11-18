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
