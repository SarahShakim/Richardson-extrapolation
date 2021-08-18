% richardson22
% Taking a linear approximation of two approximations which give us a
% higher order error. This higher order error will be smaller and give an
% overall better aprroximation. To do this, we remove the lower order error
% terms
%
% Parameters
% ==========
%    D :It approximates the center divided difference of the slope at x
%    u: This finds the derivative using the central divided difference and
%    considers the error term as well.
%
%    x: The point we are using for our approximation. Value where we are
%    trying to approximate our derivative
%    h: A small value to give us a value close to x
%
%    N_max: maximum number of iterations 
%    eps_abs: The absolute value error
%
% Return Value
% ============
%    du: Best approximation of the derivative at a point x
 
function [du] =  richardson21( D, u, x, h, N_max, eps_abs )
if ~isscalar( h ) 
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument h is not a scalar' ) );
end
if ~isscalar( x ) 
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument x is not a scalar' ) );
end  
if ~isscalar( N_max ) || (N_max ~= round( N_max )||( N_max <=0))  
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument N_max is not a positive integer' ) );
end
if ~isa( u, 'function_handle' )
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument u is not a function handle' ) );
end
if ~isa( D, 'function_handle' )
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument D is not a function handle' ) ); 
end  
if ~isscalar( eps_abs ) || (eps_abs <= 0) 
        throw( MException( 'MATLAB:invalid_argument', ...
        'the argument eps_abs is not a positive scalar' ) );
end
    
    
R(1, 1) = D(u, x, h);
 
for i=1:N_max
   h = h/2;
 
   
    R(i + 1, 1) = D(u, x, h);
   
   for j=1:i
      R(i + 1, j + 1) = (4^j*R(i + 1, j) - R(i, j))/(4^j - 1);
   end
 
   if ( abs( R(i + 1, i + 1) - R(i, i) ) < eps_abs )
      du = R(i + 1, i + 1);
      du
      break;
   elseif ( i == N_max )
      error( 'Richardson extrapolation failed to converge' );
   end
end    


