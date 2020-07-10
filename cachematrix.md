


#################################Coursera - R Programming########################################
#########################Programming Assignment 2: Lexical Scoping###############################
# This code was made by Leonardo Moreno Naranjo

## Description
This first function (makeCacheMatrix) allows to create a"special" matrix that save the inverse matrix into cache.
If the results was stored previously in cache,  the second function (cacheSolve) retrieve the solution from the cache memory or compute the inverse matrix


### *First Function:* store the inverse matrix in the cache memory
```r

makeCacheMatrix <- function(x = matrix()) {
  
  in1<- NULL
  set<- function(y){
        x<<-y
        in1<<-NULL
  }
  get<- function()x
  setinv<-function(result)in1<<-result
  getinv<-function()in1
  list(set=set,get=get,
       setinv=setinv,
       getinv=getinv)
}

```

### *Function 2:* calculate the inverse matrix, if the results were stored in cache previously, returns the values from this memory, else, compute the inverse matrix

```r

cacheSolve <- function(x, ...) {
      in1<-x$getinv()
      if(!is.null(in1)){
        message("Retrieving from cache data:This function Works! :)")
        return(in1)
      }
      v<-x$get()
      in1<-solve(v,...)
      x$setinv(in1)
      in1
}
```
### Test the functions
#### 1 option
```r
F<-matrix(1:4,2,2)
u<-makeCacheMatrix(F)
cacheSolve(u)
```

```
##      [,1] [,2]
## [1,]   -2  1.5
## [2,]    1 -0.5
```


####2 option
```r
k<-c(1,0,5,2,1,6,3,4,0)
J<-matrix(k,3,3)
s<-makeCacheMatrix(J)
cacheSolve(s) #run this function twice and see what happens
```

```
##      [,1] [,2] [,3]
## [1,]  -24   18    5
## [2,]   20  -15   -4
## [3,]   -5    4    1
```


## *Thanks for review me!*
```

