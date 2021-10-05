# Implementing Kalman Filters into Neural Hardware
## With Robert Wilson, Summer 2020. [Poster Presentation](Kalman_Pres.pdf)
<hr>
Do humans and other animals' brains naturally implement an algorithm commonly used in radar? There seems to be some evidence from recent psychology research that they do! The Kalman Filter is a bayesian inference based estimator that fuses together past information with new information to create informed estimates on the current state of an object. One of its first uses was on the apollo missions, predicting the location of the spaceships from their onboard computer. Since then, they have been used in a very large number of areas including missiles, biometric sensors, and radar.  

The framework of bayesian inference is a theory of probability that allows for the existance of beliefs about the parameters of probability distributions and is concerned with how to change those beliefs in optimal ways as more data is collected. The Kalman Filter gives the optimal way to update beliefs about an object when both the prior belief on the location of the object is a normal distribution as well as all the observations, and the object is moving linearly in space.

If we are able to observe animals behaving in a way that fits into a bayesian framework, the next question is how would their brains actually implement them? One mathematical model for how animals keep track of their position in space and time is through network attractor dynamics. In this model, neurons work collectively to maintain steady state activity 'bumps' on a coordinate system that translates to their position in real life. These bumps serve as an internal position model and can move over time as the animal senses themselves moving. We can then see what would happen if new information on the animals position was aquired, and another bump were added to the network. If we treat the height of the createures position bump as proportional to the variance of their internal model, and choose an activation function with divisive inhibition, we can use the dynamics of the network to approximate a Kalman Filter. This model was previously worked out by Wilson and Finkel in *A Neural Implementation of the Kalman Filter*.

<img src = "./images/bump_move.gif" alt="responsive" style="border:solid #292b2c;width:65vw;height:auto"/>

However, this model has a limitation in that it only works for a single dimensional Kalman Filter. In this summer project, I worked to extend it to approximate any arbitrary dimensional Kalman Filter. One major difficulty I had to overcome in building this is that the typical Kalman Filter equations involve a matrix inversion, which isn't a type of computation possible in the neural hardware unless there is no correlation between the variables. However if we rewrite the Kalman Filter equations as (assuming all variables are observed):

<p style="text-align:center">
  μ<sub>t−</sub> = Aμ<sub>(t−1)+</sub> + b
  <br>
  Σ<sub>t−</sub><sup>−1</sup> = A<sup>−1</sup>Σ<sub>(t−1)+</sub><sup>−1</sup>A<sup>−T</sup>
  <br>
  Σ<sub>t+</sub><sup>−1</sup> = Σ<sub>t−</sub><sup>−1</sup> + S<sub>t</sub><sup>−1</sup>
  <br>
  μ<sub>t+</sub> = Σ<sub>t+</sub>Σ<sub>t−</sub><sup>−1</sup>μ<sub>t−</sub> + S<sub>t</sub><sup>−1</sup>X<sub>t</sub>
</p>

We never have to uninvert any matrix, except in solving the fourth equation. However, we can approximately solve equation 4 without any inversion by performing gradient descent on the equation:

<p style = "text-align:center">
  Σ<sub>t+</sub><sup>−1</sup>μ<sub>t+</sub> = Σ<sub>t−</sub><sup>−1</sup>μ<sub>t−</sub> + S<sub>t</sub><sup>−1</sup>X<sub>t</sub>
</p>

It turns out that this type of operation can be performed by the network through adding dynamic terms to the weights. Then by making a network of n<sup>2</sup> bumps for a covariance matrix of size n by n, with scaled bumps equal to the magnitude of each covariance matrix entry, spatial locations equal to the coordinate model mean corresponding to that entry's covariance column, and several other architecture configurations, we can approximately solve the Kalman Filter equations using neural attractor dynamics in any dimension. 
