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
$
\begin{split}
    \begin{bmatrix}
    \dot{x}_{i,1} \\ \dot{x}_{i,2} \\ \dot{x}_{i,3}
    \end{bmatrix}
    &=
    \begin{bmatrix}
    u_{i,1}\cos(x_{i,3}) \\ u_{i,1}\sin(x_{i,3}) \\ u_{i,2}
    \end{bmatrix} = f(x_i,u_i), \\
    \begin{bmatrix}
    y_{i,1} \\ y_{i,2}
    \end{bmatrix}
    &=
    \begin{bmatrix}
    x_{i,1}+ l\cos(x_{i,3}) \\
    x_{i,2} + l\sin(x_{i,3})
    \end{bmatrix} = g(x_i), \ l \neq 0,
\end{split}\label{eqn:example_system}
$


