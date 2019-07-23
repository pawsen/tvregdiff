# tvregdiff

Python version of Rick Chartrand's algorithm for numerical differentiation of
noisy data.

Requires Numpy, Scipy and sksparse.cholmod installed. The latter is only used
for cholesky factorization and for shorter data samples, numpy's version can
easily be used. Just comment out line 286.
Matplotlib optional for plotting.

Usage: 

```python
u = TVRegDiff( data, iter, alph, u0, scale, ep, dx, plotflag, diagflag );
```

Test:

```bash
python tvregdiff.py
```

Algorithm adapted from the Matlab version found [here](https://sites.google.com/site/dnartrahckcir/home/tvdiff-code).

Comment from authors homepage
> In versions before R2009b, the tilde output argument is not supported. In the 'else' branch of the 'if diagflag' (one for each of the small and large cases), the pcg command can have the tilde output argument replaced with a dummy variable name. (Having an argument suppresses the printing of pcg diagnostics.)

> The 'large' case is missing a factor of dx in the definition of both A and AT. I am not changing it for now, so that the demo results will more closely match those of the paper. In any event, using a value of dx that is larger than that dictated by your problem can make things better conditioned, so it's best to simply rescale the results.

Note. In this implementation u is scaled with dx afterwards(as suggested above). So all is good.

> The function cholinc is not available anymore starting in Matlab version R2013a. For recent versions, line 225 in TVRegDiff.m should be changed to:
> R = ichol( B, struct( 'type', 'ict', 'droptol', droptol ) );

Rick Chartrand (rickc@lanl.gov), Apr. 10, 2011
Please cite Rick Chartrand, "Numerical differentiation of noisy, nonsmooth data," *ISRN Applied Mathematics*, Vol. 2011, Article ID 164564, 2011.
