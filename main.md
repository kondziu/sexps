# Everything You Always Wanted to Know About SEXPs But Were Afraid to Ask



## What are SEXPs?

SEXPs are runtime objects of the GNU R runtime. They are used to represent all
objects in the R language, as well as structures internal to the R runtime. 

The term SEXP probably refers to S-expressions, or [symbolic
expressions](http://www-formal.stanford.edu/jmc/recursive/recursive.html). In
their pure form, symbolic expressions are a notation for representing complex
data structures as collections of cells. Each cell is a pair whose elements are
either values or pointers to other cells. Symbolic expressions can be used to
easily represent and operate on trees, lists, and graphs. For example, we can
use symbolic expressions to express a list as follows.

``` {ditaa}
      /-----\
      |     |
      \-+-+-/
        | |
   +----+ +----+
   v           v
/-----\     /-----\
|  1  |     |     |
\-----/     \-+-+-/
              | |
         +----+ +----+
         v           v
      /-----\     /-----\
      |  2  |     |     |
      \-----/     \-+-+-/
                    | |
               +----+ +----+
               v           v
            /-----\     /-----\
            |  3  |     | NIL |
            \-----/     \-----/
```

```lisp
(1 . (2 . (3  . NIL)))
```

SEXPs follow the outline of symbolic expressions. The cells are triples rather
than pairs, and they have a header than allows expressing a lot of extra
information, including through a list of programmer-accessible attributes, but
in essence they follow the principles of symbolic expressions. However, SEXPs
have evolved away from their classical conception by incorporating vector types
expressed as arrays, where values are contained within a contiguous memory area
associated with each SEXP, containing the contents of the vectors they
represent. 

