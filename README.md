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
; The constructor of 2D points
(define geometry:point2d (import "geometry:point2d"))
(geometry:point2d 1 2)

; The constructor of 3D points
(define geometry:point3d (import "geometry:point3d"))
(geometry:point3d 1 2 3)

; The constructor of 2D vectors
(define geometry:vector2d (import "geometry:vector2d"))
(geometry:vector2d 1 2)

; The constructor of 3D vectors
(define geometry:vector3d (import "geometry:vector3d"))
(geometry:vector3d 1 2 3)

; An interface for adding/substracting multiple two-dimensional elements
; The type will be coerced to match the first argument
(define geometry:2d+ (import "geometry:2d+"))
(define geometry:2d- (import "geometry:2d-"))
(geometry:2d+ (geometry:vector2d 1 2) (geometry:point2d 1 2)) ; will return a vector
(geometry:2d- (geometry:point2d 1 2) (geometry:vector2d 1 2)) ; will return a point

; Of course we can do the same to three-dimensional elements
(define geometry:3d+ (import "geometry:3d+"))
(define geometry:3d- (import "geometry:3d-"))
(geometry:3d+ (geometry:vector3d 1 2 3) (geometry:point3d 1 2 3)) ; will return a vector
(geometry:3d- (geometry:point3d 1 2 3) (geometry:vector3d 1 2 3)) ; will return a point

; We can switch between those types, either generically or typesafely
(define geometry:vector2d->point2d (import "geometry:vector2d->point2d"))
(define geometry:vector3d->point3d (import "geometry:vector3d->point3d"))
(define geometry:vector->point (import "geometry:vector->point"))

; The origin could be handy sometimes;
; it is just a meaningful definition for a point with all coordinates set to 0
(define geometry:ORIGIN2D (import "geometry:ORIGIN2D"))
(define geometry:ORIGIN3D (import "geometry:ORIGIN3D"))

; dot- and crossproduct exist also
(define geometry:dot (import "geometry:dot"))
(geometry:dot (geometry:vector3d 1 3 -5) (geometry:vector3d 4 -2 -1)) ; => 3

(define geometry:cross (import "geometry:cross"))
(geometry:dot (geometry:vector3d 1 2 3) (geometry:vector3d 4 5 6)) ; => vector with contents (-3 6 -3)
```

<hr/>

Have fun!
