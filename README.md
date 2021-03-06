# FrequentDirections
Matlab code for matrix sketching using Frequent Directions (FD) variants. Implements the original and fast FD algorithms (Liberty, 2013), a parameterization that varies smoothly between iterative SVD and FD (Desai et al, 2016), as well as a randomized variant suited for sparse inputs (Teng & Chu, 2017).

## Installation
Add the single file [`FrequentDirections.m`](https://github.com/brian-lau/FrequentDirections/blob/master/FrequentDirections.m) to your Matlab path. Adding the directory `Examples` to the path is useful for running the examples. Unit tests can be run from the `Testing` directory.

## Examples
To sketch an in-memory matrix:
```
k = 16;                            % sketch size
sketcher = FrequentDirections(k);  % Initialize object
d = 64;                            % data dimensionality
data = randn(1000,d);
sketcher(data);                    % process samples
get(sketcher)                      % return sketch
sketcher.coverr(data)              % covariance error
sketcher.projerr(data)             % projection error
```

To sketch streaming data:
```
d = 512;                           % different data dimensionality
sketcher = FrequentDirections(32); % Initialize object
count = 0;
while count < 1000
   data = randn(1,d);              % random sample
   sketcher(data);                 % consume sample
   count = count + 1;
end
get(sketcher)                      % return sketch
```

The script [`exampleDesai.m`](https://github.com/brian-lau/FrequentDirections/blob/master/Examples/exampleDesai.m) reproduces a figure from Desai et al. 2016 illustrating the performance and runtime of different FD variants:
<img src="https://raw.githubusercontent.com/brian-lau/FrequentDirections/master/Examples/exampleDesai.png?token=AE8LTL05MRJUFS425NSfXQ1tioSTmhjxks5Zeu0QwA%3D%3D" alt="Drawing" style="width: 700px;" />

## References
* Desai, A., Ghashami, M., & Phillips, J. M. (2016). [Improved practical matrix sketching with guarantees](http://ieeexplore.ieee.org/abstract/document/7429755/). IEEE Transactions on Knowledge and Data Engineering, 28(7), 1678-1690.
* Ghashami, M., Liberty, E., Phillips, J. M., & Woodruff, D. P. (2016). [Frequent directions: Simple and deterministic matrix sketching](http://epubs.siam.org/doi/abs/10.1137/15M1009718?journalCode=smjcat). SIAM Journal on Computing, 45(5), 1762-1792.
* Liberty, E. (2013). [Simple and deterministic matrix sketching](http://www.cs.yale.edu/homes/el327/papers/simpleMatrixSketching.pdf). In Proceedings of the 19th ACM SIGKDD international conference on Knowledge discovery and data mining (pp. 581-588).
* Teng, D. & Chu, D. (2017). [Low-Rank approximation via sparse frequent directions. arXiv preprint arXiv:1705.07140.](https://arxiv.org/abs/1705.07140)

Contributions
--------------------------------
Copyright (c) 2017 Brian Lau [brian.lau@upmc.fr](mailto:brian.lau@upmc.fr), see [LICENSE](https://github.com/brian-lau/FrequentDirections/blob/master/LICENSE)

Please feel free to [fork](https://github.com/brian-lau/FrequentDirections/fork) and contribute!
