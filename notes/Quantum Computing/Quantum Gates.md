Quantum Gates

## NOT
<svg width="160" height="30">
   <line x1="5" y1="15" x2="70" y2="15" stroke="black" stroke-width="2" />
   <rect x="70" y="5" width="20" height="20"  stroke="black" fill="none" stroke-width="2" />
   <text x="75" y="20" fill="black" font-style="italic">X</text>
   <line x1="90" y1="15" x2="150" y2="15" stroke="black" stroke-width="2" />
   Sorry, your browser does not support inline SVG.
</svg>

The Pauli X matrix:
$$
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
\alpha \\
\beta
\end{bmatrix}
=
\begin{bmatrix}
\beta \\
\alpha
\end{bmatrix}
$$
$$
X( \alpha \vert 0 \rangle  + \beta \vert {1} \rangle ) = \beta \vert 0 \rangle + \alpha \vert 1 \rangle 
$$

## CNOT
<svg width="160" height="100">
   <line x1="5" y1="10" x2="150" y2="10" stroke="black" stroke-width="1" />
   <circle cx="80" cy="10" r="5" stroke="black" stroke-width="1" fill="black" />
   <line x1="80" y1="10" x2="80" y2="90" stroke="black" stroke-width="2" />
   <line x1="5" y1="80" x2="150" y2="80" stroke="black" stroke-width="2" />
   <circle cx="80" cy="80" r="10" stroke="black" stroke-width="2" fill="none" />
   Sorry, your browser does not support inline SVG.
</svg>

$$
CNOT = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
$$
| Input | Output |
|:------|:-------|
| $\vert 0 0 \rangle$ | $\vert 0 0 \rangle$ |
| $\vert 0 1 \rangle$ | $\vert 0 1 \rangle$ |
| $\vert 1 0 \rangle$ | $\vert 1 1 \rangle$ |
| $\vert 1 1 \rangle$ | $\vert 1 0 \rangle$ |

## Hadamard
<svg width="160" height="30">
   <line x1="5" y1="15" x2="70" y2="15" stroke="black" stroke-width="2" />
   <rect x="70" y="5" width="20" height="20"  stroke="black" fill="none" stroke-width="2" />
   <text x="75" y="20" fill="black" font-style="italic">H</text>
   <line x1="90" y1="15" x2="150" y2="15" stroke="black" stroke-width="2" />
   Sorry, your browser does not support inline SVG.
</svg>

$$
\frac{1}{\sqrt 2}\begin{bmatrix}
1 & 1 \\
1 & -1
\end{bmatrix}
\begin{bmatrix}
\alpha \\
\beta
\end{bmatrix}
=
\begin{bmatrix}
\frac{\alpha + \beta}{\sqrt 2} \\
\frac{\alpha - \beta}{\sqrt 2} \\
\end{bmatrix}
$$
## Toffoli
<svg width="160" height="175">
   <line x1="5" y1="10" x2="150" y2="10" stroke="black" stroke-width="1" />
   <circle cx="80" cy="10" r="5" stroke="black" stroke-width="1" fill="black" />
   <line x1="80" y1="10" x2="80" y2="165" stroke="black" stroke-width="2" />
   <circle cx="80" cy="80" r="5" stroke="black" stroke-width="1" fill="black" />
   <line x1="5" y1="80" x2="150" y2="80" stroke="black" stroke-width="2" />
   <line x1="5" y1="155" x2="150" y2="155" stroke="black" stroke-width="2" />
   <circle cx="80" cy="155" r="10" stroke="black" stroke-width="2" fill="none" />
   Sorry, your browser does not support inline SVG.
</svg>

$$
Toffoli = \begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\
\end{bmatrix}
$$

| Input | Output |
|:------|:-------|
| $\vert 0 0 0 \rangle$ | $\vert 0 0 0 \rangle$ |
| $\vert 0 0 1 \rangle$ | $\vert 0 0 1 \rangle$ |
| $\vert 0 1 0 \rangle$ | $\vert 0 1 0 \rangle$ |
| $\vert 0 1 1 \rangle$ | $\vert 0 1 1 \rangle$ |
| $\vert 1 0 0 \rangle$ | $\vert 1 0 0 \rangle$ |
| $\vert 1 0 1 \rangle$ | $\vert 1 0 1 \rangle$ |
| $\vert 1 1 0 \rangle$ | $\vert 1 1 1 \rangle$ |
| $\vert 1 1 1 \rangle$ | $\vert 1 1 0 \rangle$ |
