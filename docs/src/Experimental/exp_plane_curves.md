```@meta
CurrentModule = Oscar
```

```@setup oscar
using Oscar
```

```@contents
Pages = ["exp_plane_curves.md"]
```

# Plane Curves

Affine plane curves and projective plane curves are considered in this module. An affine plane curve is defined by a polynomial in two variables, whereas a projective plane curve is defined by an homogenous polynomial belonging to a graded polynomial ring in three variables.  

## Points

Several functions involve a point on a curve. We describe in this section how to deal with points, both in the affine and projective settings.

### Point in the affine space

A point in the affine space can be defined as follows:
```@docs
Point
```
We consider also the following function for points.

```@docs
ideal_point(R::MPolyRing{S}, P::Point{S}) where S <: FieldElem
```

### Points in the projective space

In order to define a point in the projective plane, one needs first to define the projective plane as follows, where `K` is the base ring:

#### Example
```@repl oscar
K = QQ
PP = projective_space(K, 2)
```

Then, one can define a projective point as follows:

#### Example
```@repl oscar
P = Oscar.Geometry.ProjSpcElem(PP[1], [QQ(1), QQ(2), QQ(-5)])
```
## Affine and Projective Plane Curves

We consider two kinds of plane curves : affine and projective.

### Constructors

An affine plane curve is defined as the class of a two-variables polynomial ``C`` over a field ``K``, modulo the equivalence relation ``C \sim D \iff \exists \lambda \in K\backslash \{0\}, C = \lambda \cdot D``.  

#### Example

```@docs
AffinePlaneCurve
```

Similarly, a projective plane curve is defined as the class of a three-variables homogeneous polynomial ``C`` over a field ``K``, modulo the equivalence relation ``C\sim D \iff \exists \lambda \in K\backslash \{0\}, C = \lambda \cdot D``. The defining equation is supposed to belong to a graded ring.

```@docs
ProjPlaneCurve
```

A particular kind of projective curves is the case of elliptic curves, see the corresponding section for more information.


### Methods

The following methods are implemented for both affine and projective plane curves.

```@docs
in(P::Point{S}, C::AffinePlaneCurve{S}) where S <: FieldElem
```



#### Examples
```@repl oscar
S, (x,y,z) = PolynomialRing(QQ, ["x", "y", "z"])
T = grade(S)
C = Oscar.ProjPlaneCurve(T(y^2 + y*z + x^2))
PP = projective_space(QQ, 2)
P = Oscar.Geometry.ProjSpcElem(PP[1], [QQ(0), QQ(1), QQ(0)])
P in C
```

```@docs
curve_components
```

```@docs
reduction
```

```@docs
issmooth
```

```@docs
tangent
```

```@docs
common_components
```

```@docs
curve_intersect
```

```@docs
intersection_multiplicity
```

```@docs
curve_singular_locus
```

```@docs
multiplicity
```

```@docs
tangent_lines
```

```@docs
aretransverse
```

```@docs
issmooth_curve
```

```@docs
arithmetic_genus
```

```@docs
geometric_genus
```


## Divisors

In order to consider divisors on curves, we restrict our attention to smooth and irreducible curve_components.

Let ``C`` be an affine or projective plane curve defined by an equation ``F``. Then any polynomial function ``G`` which is not divisible by ``F`` will vanish on ``C`` only at finitely many points. A way to encode these points together with their intersection multiplicities is to consider a divisor. A divisor on a curve is a formal finite sum of points of the curve with integer coefficients. A natural operation of addition can be defined on the set of divisors of a curve, which turns it into an Abelian group.


### Constructors

Divisors on curves are here introduced as a dictionary associating a point on the curve to its multiplicity.

```@docs
AffineCurveDivisor
```

```@docs
ProjCurveDivisor
```

### Methods

```@docs
curve
```

```@docs
degree
```

```@docs
iseffective
```


```@docs
divisor
```

```@docs
global_sections
```

```@docs
dimension_global_sections
```

```@docs
islinearly_equivalent
```

```@docs
isprincipal
```

```@docs
principal_divisor
```


## Elliptic Curves

Elliptic Curves are a particular type of projective curves. Elliptic curves are seen in this module as geometric objects. Elliptic curves are considered from the number theory point of vue in Hecke.

### Constructors

```@docs
ProjEllipticCurve
```

```@docs
Point_EllCurve
```

### Methods

```@docs
weierstrass_form
```

```@docs
discriminant(E::ProjEllipticCurve)
```

```@docs
j_invariant(E::ProjEllipticCurve)
```

```@docs
toweierstrass
```

```@docs
rand(E::ProjEllipticCurve)
```

```@docs
istorsion_point(P::Point_EllCurve{fmpq})
```

```@docs
torsion_points_lutz_nagell(E::ProjEllipticCurve{fmpq})
```

```@docs
torsion_points_division_poly(E::ProjEllipticCurve{fmpq})
```

```@docs
list_rand(E::ProjEllipticCurve, N::Int)
```

```@docs
order(P::Point_EllCurve{fmpq})
```

```@docs
sum_Point_EllCurveZnZ
```

```@docs
IntMult_Point_EllCurveZnZ
```

## Primality Proving

Elliptic curves are involved in some primality proving tests.  

### Methods

```@docs
ECM
```

```@docs
cornacchia_algorithm
```

```@docs
Miller_Rabin_test
```

```@docs
Pollard_rho
```

```@docs
Pollard_p_1
```

```@docs
ECPP
```
