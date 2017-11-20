# Singular

https://www.singular.uni-kl.de

For osx user, see
https://github.com/Singular/Sources/wiki/Singular-distribution-for-Mac-OS-X

Great introduction to Singular;
http://www.math.colostate.edu/~bates/courses/S09/676/singular_intro.pdf

## in and out
### Examples 
$ cat foo.sing 
// comments, probable
2+2;
LIB "poly.lib";
ring r=0, (a,b,c,d,e,f),lp;
ideal I=cyclic(6);
ideal GI=groebner(I);
GI;
$ Singular foo.sing

## some tips
### Boolean
```
> int i=5;
> i;
5
> i++;
> i;
6
> i==3;
0
> i==6;
1
```

So Singular uses 1 for TRUE and 0 for FALSE.

