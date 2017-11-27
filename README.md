# Singular

https://www.singular.uni-kl.de

For osx user, see
https://github.com/Singular/Sources/wiki/Singular-distribution-for-Mac-OS-X

Great introduction to Singular;
http://www.math.colostate.edu/~bates/courses/S09/676/singular_intro.pdf

To find out some command,
```
> help syz;
// ** Displaying help in browser 'mac'.
// ** Use 'system("--browser", <browser>);' to change browser,
// ** where <browser> can be: "mac", "mac-net", "safari", "xinfo", "info", "mac-www", "safari-www-idx", "safari-www", "builtin", "dummy", "emacs".
running `open /usr/local/bin/../Cellar/singular/4.1.0p3_1/bin/../share/singular/html/sing_351.htm &`
```

## to do list
AG note with Singular codes.

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
.sing is a standard extension.

```gcd.sing
// gcd.sing
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

or use read (say, on the fly);
```
> read("gcd.sing");
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

### first of all, ring
```
> ring R=0,(x,y,z),lp;
// ** redefining R (ring R=0,(x,y,z),lp;)
> R;
// coefficients: QQ
// number of vars : 3
//        block   1 : ordering lp
//                  : names    x y z
//        block   2 : ordering C
> poly f=2x2+y3;f;
2x2+y3
```

Here we define a polynomial ring R of (x,y,z), the base field is infinity field, and lex order (lp).

### groebner basis
```
> ring R=0,(x,y),lp;
// ** redefining R (ring R=0,(x,y),lp;)
> poly f =x^3-2xy;
> poly g =x^2*y -2y^2 + x;
> ideal I = f,g;
> I;
I[1]=x3-2xy
I[2]=x2y+x-4y2
> groebner (I);
_[1]=2y6-y3
_[2]=x+4y5-4y2
> reduce (f,G);
0
> reduce (g,G);
0
```

We define a polynomial ring of x,y on an infinite field with lex order.
Define two polynomial f and g, and compute the ideal generated by f and g.
The evaluate the groebner basis for this ideal.


