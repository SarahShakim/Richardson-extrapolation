# Richardson-extrapolation
Taking the linear approximation of two approximations which will give us a higher order error. This higher order error will me smaller and give an overall better approximation. Thhe lower order error terms are removed to get this better approximation.

Parameters:
D(u,x,h): The function D takes a function u and two real-values, x and h, and the order of the derivative.
It approximates the center divided difference of the slope at x.

u(x): The function u is a real-valued function of a real variable. This finds the derivative using the central divided difference and considers the error term as well.

N_max: Maximum number of iterations.
eps_abs: The absolute value error.

The Richardson Extrapolation takes a function and, through repeated loops, approximates a derivative. The inputs to the function are D, u, x, h, N_max, eps_abs. First, we use checks to makes sure that all the inputs to the functions have the correct form (integer, function handle, scalar). Then we create a matrix R and set the 1,1 value to be D (u, x, h). Then we loop from i=1 to N_max and calculate D(u,x,h/2i) and then loop to calculate . If the Ri,j value is within eps_abs of the last value then the loop ends and a result returns. If the loop does not end within N_max attempts then an exception is thrown that the function did not converge.
