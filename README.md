# Alternatives_EASE


## EASE_R Model

The **EASE_R** model is a variation of the EASE (Embarrassingly Shallow Autoencoder) algorithm for recommendation systems. It applies a regularization term to the right-side Gram matrix.

### Implementation Details
- Computes the right Gram matrix: \( G_R = X X^T \)
- Applies a regularization parameter \( \lambda \)
- Computes the inverse of \( G_R \)
- Generates item recommendations using:  
  \[
  B_R = P / (-\text{diag}(P))
  \]
  where \( P = G_R^{-1} \).
- Final rating predictions are obtained as:
  \[
  \text{rating} = B_R \cdot X
  \]

### Parameters
- `lambda_`: Regularization parameter.

### Code Reference
Implemented in the `EASE` class under the mode `"ease_R"`.

---

## both_RT Model

The **both_RT** model extends **EASE** by applying regularization to both left and right Gram matrices and performing additional transformations.

### Implementation Details
- Computes both Gram matrices:
  - Left Gram matrix: \( G_L = X^T X \)
  - Right Gram matrix: \( G_R = X X^T \)
- Applies different regularization parameters \( \lambda_L \) and \( \lambda_R \).
- Computes their inverses.
- Generates predictions using matrix multiplications:
  \[
  B_L = G_L^{-1} \cdot X^T
  \]
  \[
  B_R = G_R^{-1} \cdot X
  \]
  \[
  \text{rating} = B_R \cdot X \cdot B_L
  \]

### Parameters
- `lambda_L`: Regularization parameter for left Gram matrix.
- `lambda_R`: Regularization parameter for right Gram matrix.

### Code Reference
Implemented in the `EASE` class under the mode `"both_RT"`.

---

For more details, please refer to the source code in the repository.


See the following repository to get an well-structured implementation:

https://github.com/seoyoungh/svd-ae.git
