# Caesar-Cipher-1.0
## Simple Caesar Cipher w/ additional shift function

This is an R-programmed Caesar Cihper which shifts the alphabet back or forth and replaces letters with letters in the shifted positions. More info https://en.wikipedia.org/wiki/Caesar_cipher.

The functions main part is based upon modular arithmetic, more specifically the fomula 
<img src="https://render.githubusercontent.com/render/math?math=E_{n}(x) = (x %2B n) \ mod \ 26,">
which is the part that shifts the alphabet. The function also includes a "string cleaning" function
and if TRUE, a separate alphabetic shift function outputs only the switched letters, if one desires.
Note, the %+=% operator stems from Python code that have the property <img src="https://render.githubusercontent.com/render/math?math=x+=C \equiv x=x%2BC, \implies x_{new} - x_{old} = C,"> and does NOT exist for R.

Limitations: For the separate shift function, the shift value must uphold <img src="https://render.githubusercontent.com/render/math?math=\forall%20\x%20\in [-25,25],"> 
and the main function must have <img src="https://render.githubusercontent.com/render/math?math=x%20\in \Z.">
The other "somewhat" limitation is that as of right now, punctuation, commas and signs etc is not well handled. Adding multiple signs
will only end the output string with multiple NA, the rest of the string is correct and intact. 
