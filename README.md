**PCA Integrative Project: Ellipses and Higher Dimensions**

Youlin Huang and Christopher Soliman

**360-SNP-VA**

Instructor: Evgenjski Kritchevski

**Introduction**

Let us consider an ellipsoid or a cylindrical paraboloid. These high dimensional geometries may seem difficult to grasp, but mathematical analysis may help us better understand their properties.

Suppose we could only perceive in 2 dimensions with axes x and y, it would be incredibly difficult for us to visualize a 3-dimensional geometry. We can, however, dissect said geometry into slices, a technique in mathematics called cross-sectioning. A cross-section of a geometry is essentially a slice of the geometry along its 3rd dimension, supposing the variable associated with that dimension to be constant.

The shape of a cross-section can effectively tell us the shape of the geometry it is taken from.
To analyze the shape of a 2-dimensional elliptical equation – the shape of the cross-section we are going to take – we must use the determinant . We will now prove in this paper that the determinant may help us understand the shape of the elliptical equation.

We can apply this knowledge to the analysis of high-dimensional elliptical equations as well. In this paper, we prove that high-dimensional analysis of elliptical equations is possible by studying their 3-dimensional variants with 2-dimensional cross sections, which in our case would simply be a 2-dimensional elliptical equation.

1. **Background: Ellipses and Conic Sections**

Ellipses are a widely known curve that is found in several disciplines, such as geometry, physics and linear algebra and can be represented in this standard form:

![](data:image/png;base64...)

Ellipses are also known as a conic section because they are the result of the intersection of a single nappe of a right circular cone. In other words, an ellipse is an intersection on only one of the two cones that compose a double cone divided by a single vertex. This was formally documented by Apollonius of Perga in Book I (Proposition I.13) and modern proofs by Germinal Pierre Dandelin that show why the intersection curve of a plane and a cone at an angle where α < β < 90o has a constant sum of distance to foci (i.e the definition of an ellipse) using Dandelin spheres.

![](data:image/jpeg;base64...)

This provides a geometric understanding of ellipses. However, if the ellipse’s axes are not aligned with the x and y axis it is not possible to directly use the standard form which makes the curve harder to interpret because the formula is now the following:

This formula is true for ellipses, hyperbolas, and parabolas. The extra term makes the curve non-degenerate which indicates that the ellipse is rotated and implies that the foci do not lie on the x or y axes which makes it more difficult to find their coordinates.

The main problem with a tilted ellipse is that its equation is a general quadratic equation. This equation is shared by many other geometric shapes, such as ellipsoids, cylindrical parabolas, hyperboloids(pringles), and parabolic cylinders in 3 dimensions.

To address this complexity, we claim that it is possible to reduce the complexity of the equation and thereby increase its discernibility by reconsidering our coordinates system.

1. **The Problem: Rotated Ellipses**

To reduce complexity, it is possible to rotate the x and y axis to be parallel with the axis of the ellipse. This can be done by converting a set of coordinates to new rotated coordinates:

To find the angle of rotation required to be parallel with the ellipse’s axes:

These formulas remove the term and form a degenerate curve where the ellipse is aligned. However, these operations are tedious and are not efficient to use in real world applications such as representing or altering images, shapes and models in computers. Computers instead use transformation matrices, eigenvalues, and eigenvectors because they are simpler and easier to use.

Furthermore, these equations rely on a much more graphical, geometric intuition of the ellipse. To truly understand why we must apply the formulas above to transform our coordinates into the desired space, we must dive deeper into linear algebra and matrices.

An ellipse is a conic section, which in algebraic form, looks like this:

Where:

The monomials and represent the shifting of the conic section. In our study, we do not need to take such things into consideration, therefore we can assume D and E to be 0.

The F constant can be moved to the right side of the equation to serve as the constant sum of the equation, and later, the z axis value of the equation.

Thus, by reorganizing the equation of a conic section, we end up with an ellipse’s equation:

1. **Core Concepts: Eigenvalues, Eigenvectors, and Diagonalization**

**3.1 Eigenvalues and Eigenvectors**

If A is an n x n matrix, a number λ is called an eigenvalue of A if

for some column

Diagonalization transforms one set of coordinates from the standard basis into an eigen basis, a basis which is made up of only eigenvectors. Inside said eigenbasis, it’s possible to linearly combine its component eigenvectors to produce any vector residing inside it. A basis can be understood as a subspace where only the most essential axes are kept.

We are actively trying to rotate the axes of our subspace to align with the ellipse into a new space where relative to this new space, the ellipse is perfectly aligned with the axes, exactly what diagonalization achieves.

* 1. **Change of Basis**

To mathematically express our coordinates into our desired space, we need to transform the standard basis.

A basis of a subspace, where a subspace is the collection of all points in (in our case, in ) is a set of vectors such that it can uniquely represent any vector in . The standard basis is simply:

The standard basis forms the Euclidean plane which is a 2D infinite plane where Euclidean geometry applies such as, points, lines and angles where they are described geometrically. In the case of coordinates, the Cartesian plane is a specific example of a Euclidean plane where instead of defining geometrically, it assigns coordinates by using an x and y-axes using the standard basis. Now suppose we have the matrix P that is composed of a basis in a different space, we can multiply it with our supposed new basis coordinates to transform them back into standard basis coordinates:

This is also reversable:

This works because we suppose an aligned eigenbasis can be transformed back into the standard basis where our equation resides.

* 1. **Diagonalization**

Diagonalization is the process of representing a matrix as a diagonal matrix (i.e. a matrix with only entries on its diagonal). The reason for this is that a matrix is much easier to deal with in its diagonal form than any other.

If we understand a matrix as an array of vectors, a diagonal matrix, having only entries on its diagonal, would be an array of axes. Which is to say that a non-diagonal matrix is a matrix that represents a transformation relative to another space, while a diagonal matrix represents a transformation relative to itself. This diagonal matrix representing a transformation relative to itself is exactly what we are searching for with our rotation of the axes.

Diagonalization goes through a similar multiplication process as that which occurred to our matrix above.

where:

The diagonal matrix is the diagonalized result, the new space we require, the given matrix is the non-diagonal matrix we are given (in our case, the original coefficient matrix), and the change-of-basis matrix is the matrix that transforms the old coordinate system into the new coordinate system.

To show that D is diagonal, let’s consider its action on the standard basis vectors.

λ1v1, we get:

Similarly, applying D to e2 gives:

Therefore, D scales each standard basis independently, which means it must be diagonal:

1. **Quadratic Forms and Matrix Representation**The quadratic equation of 2 variables can actually be rewritten in matrix form:

Where:

This is because we can view any quadratic equation as

Where the A matrix is the coefficient matrix for the linear equation:

To reinterpret this equation as a matrix multiplication:

Where and are the x and y coordinates of whatever basis we choose to adopt, and suppose matrix A to be the coefficient matrix in the center:

This matrix form equation makes things a little clearer. The X matrix is the point that we are currently evaluating, and by multiplying together with its own transposition and the coefficients matrix, we obtain the k constant.

Since this coefficients matrix does not send our coordinates into any new space, it is what we call an endomorphism, where coefficient matrix :

Maps our points from space V to V, albeit modified, in this case, .

For an endomorphism matrix, to change its basis, we must first change the coordinates into the correct basis, apply the mapping, then back to the original basis:

Where P is the change of basis matrix.

We now view the equation from the perspective of the aligned eigenbasis. The change-of-basis matrix P will change our eigenbasis coordinates into standard basis coordinates to multiply with the coefficients matrix A in standard space, while the matrix will change the basis of the result back into the aligned eigenbasis, to multiply with the transposed eigenbasis coordinates vector.

This essentially converts our equation into:

In doing so, we now have the term , which we can then replace as a new, simpler diagonal coefficient matrix D by applying the diagonalization we mentioned previously.

Let v1 and v2 be eigenvectors of the matrix A with the corresponding values λ1 and λ2. This means:

With the matrix P = [v1, v2], whose columns are the eigenvectors we can define:

This represents the matrix A expressed in the eigen basis.

This essentially creates another quadratic form:

As stated above, the D matrix is a diagonalization result of the term , meaning that its contents are:

The diagonalization results in the diagonal matrix D, which can assume the role of a coefficients matrix for an equivalent elliptical equation in the aligned eigenbasis. This effectively reduces the xy coefficient to 0, making the equation rely solely on and . This diagonalization rotates the perspective that we view the equation from, but observe that fundamentally the equation remains of the same form. This diagonalization also requires our original quadratic form to partition the coefficients in A symmetrically:

Although the variables andcan be any partitions of B that add up to exactly 1 B, we partition them symmetrically according to standard convention since a diagonalization will be performed on A, and as Charles-Francois Sturm and Cauchy noted: “real symmetric matrices have real eigenvalues”.

Since the matrix A is symmetric, the eigenvectors of A must also be orthogonal to each other. This fits with our narrative of rotating the perspective, as a rotation should preserve the perpendicular property between the axes x and y, otherwise we would be fundamentally changing the shape of the ellipse.

This is due to the Hermitian properties of a symmetric matrix.

A symmetric matrix with only real entries is believed to be Hermitian by definition, and can be defined as a matrix that satisfies the condition:

Where and are arbitrary vectors, and is the inner product operation – which in our case where all numbers are real, is simply a dot product of the 2 components.
This suggests that a matrix is only Hermitian if:

And since dot product is commutative, using the identity that :

Meaning a matrix is Hermitian, if it is real-symmetric, just like the A matrix we obtained above by diagonalization.

This further allows us to understand why both eigenvectors of the matrix must be orthogonal to each other, since:

And:

Then:

Where:

And since the inner product operation for real matrices is simply the dot product of the vectors:

Obtaining:

Given that matrix A is a Hermitian or a real symmetric, let *λ1* and *λ2* be two distinct eigenvalues of matrix A. Suppose that is an eigenvector of A which corresponds to *λ1,* and is an eigenvector of A which corresponds to *λ2:*

If we take the transpose of the first equation, we get:

Given then:

Now multiply on the right

By associativity of matrix multiplication

Now substitute the second equation,

Simplify,

Bring all the terms on one side,

Since then , which means the only way for the above equation to be equal to zero is if:

And when the dot product of two vectors equals zero, it means that they are orthogonal.

This diagonalization where the standard coordinates are changed into rotated coordinates, and transformed by the A matrix, then transformed back into standard coordinates gives us this final equation:

As Jacobi proved, there is an orthogonal change of variables for every real quadratic form matrix that puts the matrix in diagonal form, which further proves that diagonalization via change-of-basis is applicable and necessary to “purify” our equation.

1. **Change of Basis and Rotation Angle**Now that we have proven that the eigenvectors of a symmetric matrix are orthogonal, we can construct an orthogonal basis from the eigenvectors. Let v and w be two orthogonal eigenvectors of A, normalized to a unit length:

If we form the matrix , the columns are orthonormal, which means that their vector length is 1 and every pair of different vectors is orthogonal. Because they are orthonormal, it means:

This is because the entry of PTP is the dot product of the column and column of . Since when and when , we get the identity matrix. This also means

This is the property of the rotation matrix, which means P represents a rotation of coordinates. This implies that our entire realignment of the ellipse via change-of-basis can be interpreted as a rotation of the axes of the coordinate system to match that of the ellipse.

If we multiply the left-hand side of P by matrix A we get:

Now let D be the diagonal matrix of eigenvalues and multiply the left-hand side by matrix P

Now notice that,

Therefore,

Multiply both sides on the left by PT

Therefore,

As established above, to rotate the axes, we must rotate every point in the eigenbasis to align with the standard basis, perform the linear transformation to achieve the elliptical curve in standard basis, then rotate each point from the standard basis back to the eigenbasis. To do this, we can simply turn the vector, into a rotated vector, by simply multiplying it with the rotation matrix:

Therefore, the full equation becomes:

Upon expanding the transposed product, we obtain the equation:

This exposes an interesting particularity. If we multiply and combine the 3 matrices in the center, namely the transposed rotation matrix , the coefficient matrix , and the rotation matrix , into 1 big matrix, we obtain the same formula as before, but slightly different:

where

This brings us to another interesting prospect. We know that in this newly transformed equation, we wish to preserve the ellipse’s shape, therefore the algebraic form of our matrix equation must also be that of an ellipse. This means that our transformed matrix equation must also be a matrix form representation of a quadratic equation with 2 variables. The newly transformed matrix equation must be in quadratic form.

If we were to rewrite this in algebraic form, then it would look like this:

As mentioned previously, the xy term makes the equation confusing and difficult to analyze. What if we can just remove it entirely? The solution is simpler than would be expected.

If we manage to make , then the term would be removed from the equation entirely.

We have previously defined the matrix P as a matrix multiplication product: . With this in mind, we can write down a sub-equation:

Fully multiplying this equation can give us a clearer view of what’s going on:

We can observe that this actually gives us 3 distinct equations, each similar to the equations we’ve obtained geometrically above.

This massive matrix of equations eventually simplifies down to:

The 12 and 21 slots of the matrix have identical equations, and both are equal to 0.

So we’ve obtained:

Using trigonometry identities, we know that:

Therefore:

This proves that the we can, in fact, consider the newly transformed equation as an equation that uses the product of for its coefficient matrix.

Interestingly enough, is also the inverse of . This is a special property of the rotation matrix, which we will make use of later.

1. **Diagonalization Applied: Full Proof**

Since we define the equation:

we can write the equation in matrix form:

As seen before, we can also obtain a “straightened” version of the equation by applying a change-of-basis on the A matrix.

where the P matrix is the rotation matrix as we previously stated.

So, since we consider , we can also rewrite the change-of-basis equation above as:

And since the transpose of a rotation matrix is the same as its inverse.

This gives us a special condition:

This gives us another method of diagonalizing the coefficients matrix A:

This means that we can look at our A matrix as such:

Therefore,

Making A out to be a symmetrical matrix, meaning that as previously proven, the eigenvectors of A must be orthogonal to each other.

We have diagonalized the symmetric matrix A using an orthogonal matrix P. The resulting diagonal matrix D contains the eigenvalues of A along its diagonal. We then apply this result to simplify the quadratic form.

where are the original coordinates

Let’s introduce a change of variables by using which is defined by the rotation

This means that we are rotating the coordinate axes to align with orthonormal column vectors of P, u1 and u2. Let’s substitute in the original equation

Distribute the transpose,

Using the diagonalization result from before *,* we substitute:

Expand the product,

Computing *D****x****′,*

Simplifying,

As we can see, the original quadratic form was *k*=*Ax*2+*Bxy*+*Cy*2 which contained a cross term Bxy. After rotating the coordinate system using the orthonormal eigenvectors of matrix A, the quadratic form simplifies to a diagonal form with only squared terms. The coefficients are the eigenvalues and . This is the fundamental simplification that allows the identification and classification of the curve.

1. **Analyzing the shape of an elliptical equation**To be able to apply these previously proven concepts on an elliptical equation, we must satisfy that:

   Is:
   We can use this to analyze the shape of the elliptical equation.
   An equation of an ellipse is written in the form:
   An equation of a hyperbola is written in the form:

or

This allows us to read the form of the aligned equation by supposing:

For the equation to render an ellipse, and must be of the

same sign, therefore, . This can simplify to the

common determinant we are all familiar with:

For the equation to draw a hyperbola instead, and would have to be of opposing

signs, therefore, . This too, will simplify to the

determinant we’ve stated above:

An interesting phenomenon to note is that as approaches 0, the eigenvalues become larger and larger, and as they eventually reach infinity, at , the curvature of the elliptical curve becomes trivial, and they become virtually straight. This will result in the curve plotting out two parallel lines.

1. **Higher Dimensions**Now that we have the basic understanding as to how to align a cross section of an elliptical equation by diagonalization and by trigonometry, we can reapply these principles to higher dimensions elliptical constructs.

   Suppose an elliptical equation plotted in 3 dimensions, we could understand it as a stack of 2-dimensional elliptical cross-sections, where instead of the equation being different for each cross-section, we simply make the result of the equation a variable:
   We replace the constant k with the variable , denoting the variable along the 3rd axis in . This allows us to use one set of coefficients to consider the entirety of a 3-dimensional by only changing the variable .

   If the 2-dimensional cross section is the shape of an ellipse, then as z varies, it forms a cylindrical paraboloid.
   If the 2-dimensional cross section were in the shape of a hyperbola, then as z varies, it will form a hyperboloid.
   Finally, if the 2-dimensional cross section were in the shape of 2 parallel straight lines, it will form a parabolic cylinder as z changes.

# References

Rotation by Shearing — <https://www.ocf.berkeley.edu/~fricke/projects/israel/paeth/rotation_by_shearing.html>

A Fast Algorithm for General Raster Rotation (DocsLib) — <https://docslib.org/doc/2182789/a-fast-algorithm-for-general-raster-rotation>

Diagonalization of a Matrix (GeeksforGeeks) — <https://www.geeksforgeeks.org/maths/diagonalization-of-a-matrix/>

Affine transformation (Wikipedia) — <https://en.wikipedia.org/wiki/Affine_transformation>

Eigenvectors for shear matrix and diagonalizing (Math Stack Exchange) — <https://math.stackexchange.com/questions/960912/eigenvectors-for-shear-matrix-and-diagonalizing>

Eigenvalues and eigenvectors (Wikipedia) — <https://en.wikipedia.org/wiki/Eigenvalues_and_eigenvectors>

Euclidean Plane (Wolfram MathWorld) — <https://mathworld.wolfram.com/EuclideanPlane.html>

Cartesian Plane (Wolfram MathWorld) — <https://mathworld.wolfram.com/CartesianPlane.html>

Cartesian Plane — Definition, Meaning, Quadrants, Examples — <https://www.cuemath.com/geometry/cartesian-plane/>

Standard basis (Wikipedia) — <https://en.wikipedia.org/wiki/Standard_basis>

2.7: Basis and Dimension (LibreTexts) — [https://math.libretexts.org/Bookshelves/Linear\_Algebra/Interactive\_Linear\_Algebra\_(Margalit\_and\_Rabinoff)/02%3A\_Systems\_of\_Linear\_Equations-\_Geometry/2.07%3A\_Basis\_and\_Dimension](https://math.libretexts.org/Bookshelves/Linear_Algebra/Interactive_Linear_Algebra_%28Margalit_and_Rabinoff%29/02%3A_Systems_of_Linear_Equations-_Geometry/2.07%3A_Basis_and_Dimension)

Euclidean plane (Wikipedia) — <https://en.wikipedia.org/wiki/Euclidean_plane>

Cartesian Plane vs Euclidean Plane (M-Power Sitedocs) — <https://baseonballs.github.io/mpower-sitedocs/mathematics/a2/resources/cartesian-vs-euclidean-plane/>

2.6: Subspaces (LibreTexts) — [https://math.libretexts.org/Bookshelves/Linear\_Algebra/Interactive\_Linear\_Algebra\_(Margalit\_and\_Rabinoff)/02%3A\_Systems\_of\_Linear\_Equations-\_Geometry/2.06%3A\_Subspaces](https://math.libretexts.org/Bookshelves/Linear_Algebra/Interactive_Linear_Algebra_%28Margalit_and_Rabinoff%29/02%3A_Systems_of_Linear_Equations-_Geometry/2.06%3A_Subspaces)

Bases and coordinate systems — [https://understandinglinearalgebra.org/sec- bases.html](https://understandinglinearalgebra.org/sec-%20bases.html)

Symmetric Matrices (CUHK) — <https://www.cse.cuhk.edu.hk/~taoyf/course/1410/19-spr/notes/matrix-sym.pdf>

Section 8-2 (Emory) — <https://math.emory.edu/~lchen41/teaching/2020_Fall/Section_8-2.pdf>

8.2: Orthogonal Diagonalization (LibreTexts) — [https://math.libretexts.org/Bookshelves/Linear\_Algebra/Linear\_Algebra\_with\_Applications\_(Nicholson)/08%3a\_Orthogonality/8.02%3a\_Orthogonal\_Diagonalization](https://math.libretexts.org/Bookshelves/Linear_Algebra/Linear_Algebra_with_Applications_%28Nicholson%29/08%3a_Orthogonality/8.02%3a_Orthogonal_Diagonalization)

DLA Theory (University of Alberta) — <https://sites.ualberta.ca/~jsylvest/books/DLA/section-quadratic-forms-theory.html>

Real Eigenvalues in Real Symmetric matrices — <https://en.wikipedia.org/wiki/Eigenvalues_and_eigenvectors>