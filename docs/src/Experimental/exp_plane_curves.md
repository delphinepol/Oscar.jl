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

## Affine and Projective Plane Curves

### Constructors
Affine Plane Curve, Projective Plane Curve, Point, ProjSpcElem


### Methods

The following methods are implemented for both affine and projective plane curves.

```@docs
in(P::Point{S}, C::AffinePlaneCurve{S}) where S <: FieldElem
```

```@docs
issmooth(C::AffinePlaneCurve{S}, P::Point{S}) where S <: FieldElem
```

```@docs
tangent(C::AffinePlaneCurve{S}, P::Point{S}) where S <: FieldElem
```

```@docs
common_components(C::AffinePlaneCurve{S}, D::AffinePlaneCurve{S}) where S <: FieldElem
```

```@docs
curve_intersect(C::AffinePlaneCurve{S}, D::AffinePlaneCurve{S}) where S <: FieldElem
```

```@docs
singular_locus(C::AffinePlaneCurve)
```


## Divisors

Divisors on curves are introduced as a dictionary associating a point on the curve to its multiplicity.

### Constructors

### Methods

## Elliptic Curves

Elliptic Curves are a particular type of projective curves. Elliptic curves are seen in this module as geometric objects. Elliptic curves are considered from the number theory point of vue in Hecke.

### Constructors

### Methods

```@docs
discriminant(E::ProjEllipticCurve)
```

```@docs
j_invariant(E::ProjEllipticCurve)
```

```@docs
curve(P::Point_EllCurve{S}) where S <: FieldElem
```

```@docs
toweierstrass(C::ProjPlaneCurve{S}, P::Oscar.Geometry.ProjSpcElem{S}) where S <: FieldElem
```

```@docs
weierstrass_form(E::ProjEllipticCurve{S}) where {S <: FieldElem}
```
## Primality Proving

Elliptic curves are involved in some primality proving tests.  

### Methods
