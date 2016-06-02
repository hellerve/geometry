# geometry

A minimal geometry library for and in zepto.
Supports 2D and 3D points and vectors.

## Installation
```
zeps install hellerve/geometry
```

## Usage

The module includes an admittedly small but tested
interface to the datatypes `point2d`, `point3d`, `vector2d`
and `vector2d`. They all implement the stringify and
collec protocols to interface nicely with existing
collections.

```clojure
(load "geometry/geometry")
(import-all "geometry")
; The constructor of 2D points
(geometry:point2d 1 2)

; The constructor of 3D points
(geometry:point3d 1 2 3)

; The constructor of 2D vectors
(geometry:vector2d 1 2)

; The constructor of 3D vectors
(geometry:vector3d 1 2 3)

; An interface for adding/substracting multiple two-dimensional elements
; The type will be coerced to match the first argument
(geometry:2d+ (geometry:vector2d 1 2) (geometry:point2d 1 2)) ; will return a vector
(geometry:2d- (geometry:point2d 1 2) (geometry:vector2d 1 2)) ; will return a point

; Of course we can do the same to three-dimensional elements
(geometry:3d+ (geometry:vector3d 1 2 3) (geometry:point3d 1 2 3)) ; will return a vector
(geometry:3d- (geometry:point3d 1 2 3) (geometry:vector3d 1 2 3)) ; will return a point

; We can switch between those types, either generically or typesafely
(define geometry:vector2d->point2d (import "geometry:vector2d->point2d"))
(define geometry:vector3d->point3d (import "geometry:vector3d->point3d"))
(define geometry:vector->point (import "geometry:vector->point"))

; The origin could be handy sometimes;
; it is just a meaningful definition for a point with all coordinates set to 0
geometry:ORIGIN2D
geometry:ORIGIN3D

; dot- and crossproduct exist also
(geometry:dot (geometry:vector3d 1 3 -5) (geometry:vector3d 4 -2 -1)) ; => 3

(geometry:dot (geometry:vector3d 1 2 3) (geometry:vector3d 4 5 6)) ; => vector with contents (-3 6 -3)
```

<hr/>

Have fun!
