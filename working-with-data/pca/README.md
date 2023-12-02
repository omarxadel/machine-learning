# Principal Component Analysis with Olivette Faces Dataset (Eigenfaces)

In this notebook, we explore Principal Component Analysis with the famous Olivetti Faces data set.

## Understanding PCA

Principal component analysis, or PCA, is a statistical procedure that allows you to summarize the information content in large data tables by means of a smaller set of “summary indices” that can be more easily visualized and analyzed.

## The Dataset

For this project, we are using the well known Olivetti Faces data set. This data set contains 64x64 pixel grayscale images of 40 individuals. There are 10 images of each indivual exhibiting different facial expressions, angles, and lighting. Here is a sample of the first 4 individuals:

![face_collage](/working-with-data/pca/face_collage.jpg)

## The Approach

We represent each image as one long flattened vector. Our data set is composed of 64x64 images, thus, each image will be represented by a 4096 dimensional vector. We pack all of these vectors into a matrix such that each row represents one of the input images.

### Pre-Processing

When applying PCA, it's usually a good practice to make some data preprocessing, specifically feature scaling and normalizing. This is reasonable, as PCA deals with the variance of different features, which may differ significantly.

### Fitting

At this point we do PCA using scikit-learn decomposition library, assigning temporarily the number of components to 24 to better understand and visualize the concepts.

In scikit-learn PCA algorithm, the $k$ vectors which minimize the projection error are the first $k$ vectors $u^{(1)}, u^{(2)}, \ldots, u^{(k)}$ of the matrix $U$ obtained from the singular value decomposition of the matrix $\Sigma = \frac{1}{m} \sum_{i=1}^n (x_i)(x_i)^T$.

Singular value decomposition is a factorization of the form $M = U \varSigma V^{\ast}$, where $M$ is the $m \times n$ real or complex matrix to be decomposed, $U$ an $m \times m$ real or complex unitary matrix, $\varSigma$ an $m \times n$ rectangular diagonal matrix with non-negative real numbers on the diagonal, and $V^{\ast}$ an $n \times n$ real or complex unitary matrix. The diagonal entries $\sigma_i$ of $\varSigma$ are known as the singular values of $X$. The columns of $U$ are called left-singular vectors, while the columns of $V^{\ast}$ are called right-singular vectors.

### Observations

1. We can observe that with just 24 components, the faces are still recognizable, but to have a more rigorous method to evaluate our model, we consider the explained variance as a metric.
1. We observe that the explained variance is pretty low, as we usually want to retain at least the 99% of the data variance. To get the desired variance explanation, we proceed manually by testing crescent values of the `n_components` parameter.

### Conclusion

In conclusion, with around 260 (of 4096) principal components the 99% of the variance in the data is retained.

In this, like in most real life scenarios, it's possible to highly compress data and still retain most of the variance. If we are not appying PCA as a preliminar step in a supervised machine learning problem, but we are in a more traditional analytical setting, the challenge at this point is in interpreting these vectors in order to get some insights on the data.

### References

1. [Principal Components Analysis on the Olivetti faces dataset](https://notebook.community/mana99/machine-playground/pca_svd-olivetti)
1. [github.com/jakeoeding/eigenfaces](https://github.com/jakeoeding/eigenfaces)

### Contact

Omar Adel - [@omarxadel](https://twitter.com/omarxadel) - omarxadel21@gmail.com
