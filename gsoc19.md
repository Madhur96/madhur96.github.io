---
layout: page
title: Google Summer of Code 2019
subtitle: Infinite scrolling using MAM and General Improvement.
use-site-title: true
---

#### *About Project*

This project intends to improve the overall functionality of Poezio by implementing “Infinite scrolling using Message Archive Management (MAM)” and adding important features linked with it for general improvement.

Some of the features planned for this project along with infinite scrolling of messages are:
- Implementation of scrollback command
- Work on lastlog plugin
- A tab to display important messages
- Attaching a message with a past linked message

My proposal can be viewed [here](https://docs.google.com/document/d/1jqBL_IHtQ3HnBJTF2EDyugrxHQRRzJr-FE5lz-eNp28/edit?usp=sharing)

#### *Bonding period*

* ##### *1st week*  
I have created [4 Pull Requests](https://github.com/GeomScale/volume_approximation/pulls) in github repository of `volesti` package, to add the implementations of my preliminary work for the GSoC proposal:  
1. [Check if the requested error is positive](https://github.com/GeomScale/volume_approximation/pull/14).
2. [Dikin walk implementation](https://github.com/GeomScale/volume_approximation/pull/16).
3. [Boundary sampling](https://github.com/GeomScale/volume_approximation/pull/15) with Hit-and-Run.
4. [Volume computation and sampling for low dimensional convex polytopes](https://github.com/GeomScale/volume_approximation/pull/17).

* ##### *2nd - 3rd week*
I have read some papers that are retated to the coding project. In particular, we discussed methods given in:  
1. [Algorithmic Theory of ODEs and Sampling from Well-conditioned Logconcave Densities](https://arxiv.org/abs/1812.06243), Yin Tat Lee, Zhao Song, Santosh S. Vempala.  
2. [Optimal Convergence Rate of Hamiltonian Monte Carlo for Strongly Logconcave Distributions](https://arxiv.org/abs/1905.02313), Zongchen Chen, Santosh S. Vempala.  
3. [The Dynamics of Lagrange and Hamilton](https://nisheethvishnoi.files.wordpress.com/2018/09/lagrangehamiltonian.pdf), Nisheeth K. Vishnoi.  
4. [Nonconvex sampling with the Metropolis-adjusted Langevin algorithm](https://arxiv.org/abs/1902.08452), Oren Mangoubi, Nisheeth K. Vishnoi.  
5. [Efficient Convex Optimization with Membership Oracles](https://arxiv.org/abs/1706.07357), Yin Tat Lee, Aaron Sidford, Santosh S. Vempala.  
6. [Riemann Manifold Langevin and Hamiltonian Monte Carlo](https://pdfs.semanticscholar.org/16c5/06c5bb253f7528ddcc80c72673fabf584f32.pdf), Mark Girolami, Ben Calderhead, Siu A. Chin.  
   
#### *Coding period*  

* ##### *1st week*  
I have created a [new branch](https://github.com/TolisChal/volume_approximation/tree/HMC_sampling) in my repo at github to implement Remannian Hamiltonian Monte Carlo. I have started coding.

