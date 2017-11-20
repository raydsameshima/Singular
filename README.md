# Singular

https://www.singular.uni-kl.de

For osx user, see
https://github.com/Singular/Sources/wiki/Singular-distribution-for-Mac-OS-X

Great introduction to Singular;
http://www.math.colostate.edu/~bates/courses/S09/676/singular_intro.pdf

## in and out
### Examples 
$ cat foo.sing 
``` foo.sing
// comments,
2+2;
LIB "poly.lib";
ring r=0, (a,b,c,d,e,f),lp;
ideal I=cyclic(6);
ideal GI=groebner(I);
GI;
```
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

### _ for the latest line of output
That is _ for Singular as it in Haskell, % in Maxima.

```
> 2+2;
4
> _*3;
12
```

### string

```
> string s = "Hi, how are you";s;
Hi, how are you
> s=s+" doing?";s;
Hi, how are you doing?
> s[0];

> s[1];
H
> s[2];
i
> s[20];
n
```

That is, string in Singular is a list of characters, like Haskell.

### roading proc
```gcd.sing 
// gcd 
proc MY_GCD( int a, int b)
{
  int r = a%b; // remainder?
  while (r != 0)
  {
    a = b;
    b = r;
    r = a%b;
  }
  return (b);
}
```

```
> < "gcd.sing";
// ** redefining MY_GCD (})
> MY_GCD (18,9);
9
> MY_GCD (18,72);
18
> MY_GCD (18,73);
1
```
