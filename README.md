### Assignment Description

http://github.com/rdpeng/ProgrammingAssignment2

### My Source


```r
  makeCacheMatrix <- function(x = matrix()) {
  
      m <- NULL
      set <- function(y) {
        x <<- y
        m <<- NULL
      }
    
    get <- function() x
    setinverse <- function(solve) m <<- solve
    getinverse <- function() m
  
    list(set = set, get = get,
         setinverse = setinverse,
         getinverse = getinverse)
  }
    
  cacheSolve <- function(x, ...) {
    m <- x$getinverse()
    
    if(!is.null(m)) {
      message("getting cached data")
      return(m)
    }
    
    data <- x$get()
    
    m <- solve(data, ...)
    x$setinverse(m)
    
    m
  }
```

## Result

```r
> source("cachematrix.R")
> m1 <- matrix(0:3, 2, 2)
> r1 <- makeCacheMatrix(m1)
> cacheSolve(r1)
     [,1] [,2]
[1,] -1.5    1
[2,]  0.5    0
> cacheSolve(r1)
getting cached data
     [,1] [,2]
[1,] -1.5    1
[2,]  0.5    0
```

