# SynchronizedPathFollowing
This GitHub repo contains the work I did during my internship at the University of Waterloo on Synchronized Path following and an extension to nonminimum phase systems. The research was done under supervision of Prof. Christopher Nielsen.

# Repo structure
This GitHub repo contains Matlab scripts for the following:
1. Defining geometric paths:
  - Elliptical paths
  - 2d-spline paths
  - Iterative solution to find the closest point on the path in the form of Newton Raphson's method
2. Synchronized path following for a minimum phase system:
  - Path following for a multi agent system for circular paths
  - The extended version to non-circular paths
3. Path following for nonminimum phase systems
4. Controlling of nonminimum phase system in the path following normal form
5. Current challenges

The paper in file "X" contains an elaborate discussion of the underlying theory, the main purpose of this repo is to facilitate future research on synchronized path following for nonminimum phase systems.

The code uses two different dynamical systems to test the algorithms: A differential drive robot and a two box system.

The differential drive robot is represented by the following kinematic equation:
$$ \begin{bmatrix}
\dot{x}_{i,1} \\ 
\dot{x}_{i,2} \\ 
\dot{x}_{i,3}
\end{bmatrix}
=
\begin{bmatrix}
u_{i,1}\cos(x_{i,3}) \\ 
u_{i,1}\sin(x_{i,3}) \\ 
u_{i,2}
\end{bmatrix} = f(x_i,u_i), $$

$$ \begin{bmatrix}
y_{i,1} \\ 
y_{i,2}
\end{bmatrix}
=
\begin{bmatrix}
x_{i,1}+ l\cos(x_{i,3}) \\
x_{i,2} + l\sin(x_{i,3})
\end{bmatrix} = g(x_i), \ l \neq 0, $$

with the visual representation given by:
![differential_drive_robot](../images/differential_drive_robot.png)

The two box system is represented by:
$$ M\Ddot{y} &= D(\dot{y} - \dot{z}) + u, \\
m\Ddot{z} &= D(\dot{z} - \dot{y}) + G(z - y), $$

And is converted to a state space model, using the state: $x = [z_1,\dot{z}_1,z_2,\dot{z}_2,y_1,\dot{y}_1,y_2,\dot{y}_2]$, which gives the following matrices:
$$ A_p &=  \begin{bmatrix}
        0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
        \frac{g_1}{m} & -\frac{d_1}{m} & 0 & 0 & -\frac{g_1}{m} & \frac{d_1}{m} & 0 & 0 \\
        0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
        0 & 0 & \frac{g_2}{m} & -\frac{d_2}{m} & 0 & 0 & -\frac{g_2}{m} & \frac{d_2}{m} \\
        0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
        0 & \frac{d_1}{M} & 0 & 0 & 0 & -\frac{d_1}{M} & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
        0 & 0 & 0 & \frac{d_2}{M} & 0 & 0 & 0 & -\frac{d_2}{M} \\
        \end{bmatrix}, $$
$$ B_p &= \begin{bmatrix}
        0 & 0 \\ 0 & 0 \\ 0 & 0 \\ 0 & 0 \\ 0 & 0 \\ \frac{1}{M} & 0 \\ 0 & 0 \\ 0 & \frac{1}{M}
        \end{bmatrix}, $$
$$ C_p &= \begin{bmatrix}
        0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 & 0 & 1 & 0
        \end{bmatrix} $$

A visual representation of the two box system is given by:
![two_box_system](../images/two_box_system.png)

