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
![image](https://github.com/user-attachments/assets/e74ccbda-cc49-453b-8ca6-1cddd60594c4)
![image](https://github.com/user-attachments/assets/e560c3b2-5689-467f-a76b-1006c8d70176)



