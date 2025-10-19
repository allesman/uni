References for MathJax usage in Markdown sintax

[Mathjax plugin](https://github.com/sommerregen/grav-plugin-mathjax/blob/master/README.md) for math formula insertion has an extensive [documentation](http://docs.mathjax.org/en/latest/).

In [Mathjax quick sintax reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) tutorial and reference are available.

Inline formulas enclose \ ( ... \ )

Displayed formulas \ [ ... \ ]

Curly braces {} to group pieces of formulas

Superscripts ( ^ ) and subscripts ( _ ) : x1e

Fractions:

ab \frac {a} {b}

xy {x} \over {y} }

Unscaled parentheses

|Symbol|Code|
|---|---|
|(...)|(...)|
|[...]|[...]|
|{...}|{ ... }|
|\|...\||\vert ... \vert|
|‖...‖|\Vert ... \Vert|
|⟨...⟩|\langle ... \rangle|
|⌈...⌉|\lceil ... \rceil|
|⌊...⌋|\lfloor ... \rfloor|

Scaled parentheses

|Symbol|Code|
|---|---|
|(...)|\left( ... \right)|
|[...]|\left[ ... \right]|
|{...}|\left{ ... \right}|
|\|...\||\left\vert ... \right\vert|
|‖...‖|\left\Vert ... \right\Vert|
|⟨...⟩|\left\langle ... \right\rangle|
|⌈...⌉|\left\lceil ... \right\rceil|
|⌊...⌋|\left\lfloor ... \right\rfloor|

Hidden parentheses

|Symbol|Code|
|---|---|
|{...|\left{ ... \right.|
|...]|\left. ... \right]|

- manual adjustment: (((((x))))) \Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr)

|Symbol|Code|
|---|---|
|<|\lt|
|>|\gt|
|≤|\le|
|≤|\leq|
|≦|\leqq|
|⩽|\leqslant|
|≥|\ge|
|≥|\geq|
|≧|\geqq|
|⩾|\geqslant|
|≠|\neq|
|∧|\land|
|∨|\lor|
|¬|\lnot|
|∀|\forall|
|∃|\exists|
|∄|\nexists|
|⊤|\top|
|⊥|\bot|
|⊢|\vdash|
|⊨|\vDash|
|≈|\approx|
|∼|\sim|
|≃|\simeq|
|≅|\cong|
|≡|\equiv|
|≺|\prec|
|⊲|\lhd|
|∴|\therefore|

|Symbol|Code|
|---|---|
|×|\times|
|÷|\div|
|±|\pm|
|∓|\mp|
|⋅|\cdot|
|⋆|\star|
|∗|\ast|
|⊕|\oplus|
|∘|\circ|
|∙|\bullet|

|Symbol|Code|
|---|---|
|∪|\cup|
|∩|\cap|
|∖|\setminus|
|⊂|\subset|
|⊆|\subseteq|
|⊊|\subsetneq|
|⊃|\supset|
|∈|\in|
|∉|\notin|
|∅|\emptyset|
|∅|\varnothing|

|Symbol|Code|
|---|---|
|→|\to|
|→|\rightarrow|
|←|\leftarrow|
|⇒|\Rightarrow|
|⇐|\Leftarrow|
|⇔|\Leftrightarrow|
|↦|\mapsto|

|Symbol|Code|
|---|---|
|∞|\infty|
|∇|\nabla|
|∂|\partial|
|ℑ|\Im|
|ℜ|\Re|
|…|\ldots|
|⋯|\cdots|
|ℓ|\ell|

|Symbol|Code|
|---|---|
|sin⁡x|\sin x|
|cos⁡x|\cos x|
|tan⁡x|\tan x|
|cot⁡x|\cot x|
|sec⁡x|\sec x|
|csc⁡x|\csc x|
|arcsin⁡x|\arcsin x|
|arccos⁡x|\arccos x|
|arctan⁡x|\arctan x|

|Symbol|Code|
|---|---|
|x3|\sqrt{x^3}|
|xy3|\sqrt[3]{\frac xy}|
|ln⁡(x)|\ln(x)|
|log2⁡(x)|\log_{2}(x)|
|∑n=1Nn|\sum_{n=1} ^{N} n|
|∏n=1Nn|\prod_{n=1} ^{N} n|
|∫0∞xdx|\int_{0} ^{\infty} x dx|
|∬0∞xdx|\iint_{0} ^{\infty} x dx|
|∭0∞xdx|\iiint_{0} ^{\infty} x dx|
|limx→∞1x|\lim_{x \to \infty} {1 \over x }|
|max(1,2,3)|\max(1,2,3)|
|min(3,4,5)|\min(3,4,5)|
|(n+12k)|{n+1 \choose 2k}|
|(n+12k)(n+12k)|\binom{n+1}{2k} (n+12k)|

|Symbol|Code|
|---|---|
|α|\alpha|
|β|\beta|
|γ|\gamma|
|δ|\delta|
|ϵ|\epsilon|
|ε|\varepsilon|
|ζ|\zeta|
|η|\eta|
|θ|\theta|
|ϑ|\vartheta|
|ι|\iota|
|κ|\kappa|
|λ|\lambda|
|μ|\mu|
|ν|\nu|
|ξ|\xi|
|ο|\omicron|
|π|\pi|
|ϖ|\varpi|
|ρ|\rho|
|ϱ|\varrho|
|σ|\sigma|
|ς|\varsigma|
|τ|\tau|
|υ|\upsilon|
|ϕ|\phi|
|φ|\varphi|
|χ|\chi|
|ψ|\psi|
|ω|\omega|

|Symbol|Code|
|---|---|
|Γ|\Gamma|
|Δ|\Delta|
|Θ|\Theta|
|Λ|\Lambda|
|Ξ|\Xi|
|Π|\Pi|
|Σ|\Sigma|
|Υ|\Upsilon|
|Ψ|\Psi|
|Ω|\Omega|

Note: other greek uppercase lettere are the same as Roman letter.

|Symbol|Code|
|---|---|
|N|\mathbb{N}|
|Z|\mathbb{Z}|
|Q|\mathbb{Q}|
|I|\mathbb{I}|
|R|\mathbb{R}|
|C|\mathbb{C}|
|is an even number|\text{ is an even number}|
|blackboardbold|\Bbb{blackboard bold}|
|boldface|\mathbf{boldface}|
|italics|\mathit{italics}|
|boldfaceditalicsboldfaceditalics|\pmb{boldfaced italics}|
|fortypewriter|\mathtt{ for typewriter}|
|romanfont|\mathrm{roman font}|
|sans−seriffont|\mathsf{sans-serif font}|
|calligraphicletters|\mathcal{calligraphic letters}|
|scriptletters|\mathscr{script letters}|
|Fraktur(oldGermanstyle)letters|\mathfrak{Fraktur (old German style) letters}|

|Symbol|Code|
|---|---|
|Thin space|Thin \ space|
|Normalspace|Normal \; space|
|Bigspace|Big \quad space|
|Biggerspace|Bigger \qquad space|

|Symbol|Code|
|---|---|
|x^|\hat{x}|
|xyz¯|\overline{xyz}|
|x→|\vec{x}|
|xy^|\widehat{xy}|
|x¯|\bar{x}|
|xy→|\overrightarrow{xy}|
|xy↔|\overleftrightarrow{xy}|
|x˙|\dot{x}|
|x¨|\ddot{x}|

Plain text: {x∈N∣x is an even number}

The Einstein field equations (EFE) may be written in the form:

Rμν−12gμνR+gμνΛ=8πGc4Tμν