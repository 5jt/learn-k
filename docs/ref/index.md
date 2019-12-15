# Reference card

```txt
Verb                       Adverb                Noun            Atom List
:  Assign                  '  Each               char  " ab"       `c `C
+  Add         Flip        /  Over               name  ``a`b       `n `N
-  Subtract    Negate      \  Scan               int   Ø 0 2       `i `I
*  Multiply    First       ': Eachprior          float ø 2.3 π ∞   `f `F
%  Divideby    Inverse     /: Eachright join|sv  date 2019-06-28   `D `D   .z.d
&  Min|And     Where       \: Eachleft split|vs  time 12:34:56.789 `t `T   .z.t
|  Max|Or      Reverse
<  Less        Up          System                list (2;3.4;`c)   `l `L
>  More        Down        0: read/write line    dict {a:2;b:`c}   `a `A(table)
=  Equal       Group       1: read/write byte    step `b 0 3!2 4   `b
~  Match       Not         2: read/write data    expr :32+9*f%5    `0
!  Key         Enum        3: conn/set (.z.ms)   func {(+/x)%#x}   `1..9
,  Catenate    Enlist      4: http/get (.z.mg)
^  Except      Asc                               \l f.k  load      \h help
#  Take        Count       #[t;c;b[;a]] Select   \t[:n]x time      \l log
_  Drop        Floor       _[t;c;b[;a]] Update   \u[:n]x trace
?  Find        Unique      ?[x;i;f[;y]] Splice   \v [d]  vars
@  Index       Type        @[x;i;f[;y]] Amend    \f [d]  fns
.  Apply       Value       .[x;i;f[;y]] Dmend    \lf file \lc char \ll line
$  Cast|Pad    String      $[c;t;f]     Cond     \cd [d] get[set]  \gr x file

util: in within bin like find freq prm cmb
math: sqrt sin cos abs [n]log [n]exp [n]rand mod div
aggr: count first last min max sum avg var dev med
table: [f]asc [f]dsc [f]key [select|update|delete]A by B from T where C

datetime:YMDHRSTUV+duration:ymdhrstuv; T:.z.D+.z.t; 2019-06-28+2m; day:7 mod
`year`month`date`hour`minute`second`millisecond`microsecond`nanosecond

bool: `ascii`utf8
1way: `p`m`crc`sha`rip`bad   e.g. hash: `sha@"crypto"
2way:``j`k`csv`b64`hex`aes   e.g. json: `j?`j@{a:2;b:`c}

if[c;..];while[c;..]

K:key k:key`k1  /public private
K key k key"hi" /verify sign
"(;)"/:$`x`y`z
\\ exit
synonyms: count first last min max sum asc
```