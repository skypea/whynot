# Lalonde
The Lalone simulator is based on data from [Robert LaLonde's 1986
study](https://www.jstor.org/stable/1806062) evaluating the impact of
the National Supported Work Demonstration, a labor training program, an
post-intervention income levels. Since the actual function mapping the measured
covariates to the observed outcomes is unknown, we instead simulate random
functions of varying complexity on the data to generate synthetic outputs. This
procedure allows us to generate causal inference problems with response surfaces
of varying, but known complexity.

## Simulator
In the Lalonde data, the function mapping covariates X to outcome Y is unknown,
and it is impossible to simulate ground truth. Therefore, following [Hill et
al.](https://arxiv.org/abs/1707.02641), we replace the true outcome Y with one
generated by functions f_0, f_1, corresponds to control and treatment as
followesing: 
- f_0(X) = Y(0),
- f_1(X) = Y(1),
- Y = Y(W), where W is the treatment assignment.

In our experiments, both f_0 and f_1 are random 2-layer ReLu networks with
32-dimensional hidden states. Treatment assignment is as given in the LaLonde
data.
