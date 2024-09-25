# Entropic_Vectors_via_NNs

## Introduction
This is the numerical data of the paper [1, Section IV].


## Description
The files come in three formats in total: `.txt`, `.npy` and `.ext`.

Files with formats `.txt` and `.npy` are suggested to be loaded by `numpy` in `python`.

The file with the format `.ext` is specially processed by polyhedron computation methods including `lrs` [2,3], `qhull` [4,5] and `cdd` [6,7] (or `pycddlib` [8] in `Python`).

Please note that the elements of the entropic vector in data are placed according to [1, Eq. (4)].

The data of joint PMFs have the `numpy` shape of:
```
(1,4,4,4,4)
```
To compute the marginal PMFs from the given joint PMF data, the following code is suggested:
```
#  'probs' is the joint PMF data with numpy shape (1,4,4,4,4)
p1 = np.sum(probs, axis=(-2, -3, -4))
p2 = np.sum(probs, axis=(-1, -3, -4))
p3 = np.sum(probs, axis=(-1, -2, -4))
p4 = np.sum(probs, axis=(-1, -2, -3))

p12 = np.sum(probs, axis=(-3, -4))
p13 = np.sum(probs, axis=(-2, -4))
p14 = np.sum(probs, axis=(-2, -3))
p23 = np.sum(probs, axis=(-1, -4))
p24 = np.sum(probs, axis=(-1, -3))
p34 = np.sum(probs, axis=(-1, -2))

p123 = np.sum(probs, axis=(-4))
p124 = np.sum(probs, axis=(-3))
p134 = np.sum(probs, axis=(-2))
p234 = np.sum(probs, axis=(-1))
```


## Directory `Section_IV_A`
The files in this directory correspond to [1, Section IV.A], more specifically, Figure 1.

For example, in directory `Figure_1_Target_1`, `curve.npy` contains the data of convergence curve, `dnorm.txt` contains the normalized distance result, `h.txt` contains the entropic vector yileding this normalized distance result, and `p.npy` contains the PMF realizing this entropic vector.

### Directory `Figure_1_Target_1`
The files here correspond to the result of `Target 1` in [1, Figure 1].

### Directory `Figure_1_Target_2`
The files here correspond to the result of `Target 2` in [1, Figure 1].

### Directory `Figure_1_Target_3`
The files here correspond to the result of `Target 3` in [1, Figure 1].


## Directory `Section_IV_A`
The files in this directory correspond to [1, Section IV.B], more specifically, Table I.

For example, in directory `Table_I_-0.0893733002`, `result.txt` contains the score/index result, `h.txt` contains the entropic vector yileding this socre/index result, and `p.txt` contains the PMF realizing this entropic vector.

Please note that the instance of Ingleton inequality used here is [1, Eq. (13)].

### Directory `Table_I_-0.0893733002`
The files here correspond to the result in the first row of [1, Table I].

### Directory `Table_I_-0.0925001031`
The files here correspond to the result in the second row of [1, Table I].

### Directory `Table_I_0.0281316527`
The files here correspond to the result in the third row of [1, Table I].

### Directory `Table_I_0.0288304141`
The files here correspond to the result in the fourth row of [1, Table I].


## Directory `Section_IV_A`
The file in this directory corresponds to [1, Section IV.C], more specifically, Table II.

The only file `Table_II_72.0437.ext` in this directory contains **2585** vertices which yields the result `72.0437%` in [1, Tabel II].

To compute the volume of this polytope, one is highly suggested to use `lrs` with the `Estimation` feature.
Thus, the end description of the file `Table_II_72.0437.ext` constains the following configuration:
```
maxdepth 13
estimates 13
volume
```
Quaoting [3], this configuration means that *this will cause lrs to perform 13 random probes from each node of the tree at depth 13*.

The above `Estimation` procedure may take several weeks.
For more discusstions of this result, please see [9], which is the extended version of [1].


## Reference
[1] S. Zhang, N. Liu, W. Kang, H. Permuter, “On Verifying Entropic Vectors with Distributions Generated by Neural Networks,” in Proc. IEEE Inf. Theory Workshop (ITW), Nov. 2024 (Paper Accepted).

[2] Avis, D. A revised implementation of the reverse search vertex enumeration algorithm. In Proceedings of the Polytopes—combinatorics and computation. Springer, 2000, pp. 177–198.

[3] Avis, D. lrs. [Online]. Available: http://cgm.cs.mcgill.ca/~avis/C/lrs.html. Accessed: May 18, 2024.

[4] Barber, C.B.; Dobkin, D.P.; Huhdanpaa, H. The quickhull algorithm for convex hulls. ACM Transactions on Mathematical Software (TOMS) 1996, 22, 469–483.

[5] Barber, C.B.; Dobkin, D.P.; Huhdanpaa, H. Qhull. [Online]. Available: http://www.qhull.org. Accessed: May 18, 2024.

[6] Fukuda, K.; Prodon, A. Double description method revisited. In Proceedings of the Franco-Japanese and Franco-Chinese conference on combinatorics and computer science. Springer, 1995, pp. 91–111.

[7] Fukuda, K. cdd, cddplus and cddlib. [Online]. Available: https://people.inf.ethz.ch/fukudak/cdd_home/. Accessed: May 18, 2024.

[8] Troffaes, M. pycddlib. [Online]. Available: https://github.com/mcmtroffaes/pycddlib. Accessed: May 18, 2024. 

[9] S. Zhang, N. Liu, W. Kang, H. Permuter, “Optimizing Distributions for Associated Entropic Vectors via Generative Convolutional Neural Networks,” Entropy, vol. 26, no. 8, p. 711, Aug. 2024.
