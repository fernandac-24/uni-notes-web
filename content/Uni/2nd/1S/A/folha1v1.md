---
title: Versão do Claude
---
# Álgebra (LCC) — Grupos · Resumo completo

**Convenções:** produto $ab$; identidade $1$ (ou $e$); em $S_n$: $(f\circ g)(x)=f(g(x))$ (da **direita** para a esquerda).
**Prioridades:** [Essencial] · [Útil] · [Se sobrar espaço]

---

[[Folhav1Algebra.pdf| Folha em formato LateX]]

---

## 1. Grupos: definição e propriedades

**[Essencial] Definição.** $(G,\cdot)$ é grupo se: (i) $(ab)c=a(bc)$; (ii) $\exists\,1:\ 1a=a1=a$; (iii) $\forall a\ \exists a^{-1}:\ aa^{-1}=a^{-1}a=1$. Abeliano: $ab=ba$. Neutro e inverso são **únicos**. Ordem do grupo: $|G|$.

**[Útil] Hierarquia.** grupoide (op. binária) ⊃ semigrupo (+associativa) ⊃ monóide (+identidade) ⊃ grupo (+inversos).

**[Essencial] Propriedades.**
- $(ab)^{-1}=b^{-1}a^{-1}$; $(a^{-1})^{-1}=a$; $(a^n)^{-1}=(a^{-1})^n$; $a^m a^n=a^{m+n}$.
- **Lei do corte** (em qualquer grupo): $ac=ad\Rightarrow c=d$ e $ca=da\Rightarrow c=d$.
- $ax=b\iff x=a^{-1}b$ e $ya=b\iff y=ba^{-1}$ (solução única).
- Num grupo abeliano: $(ab)^n=a^nb^n$ para todo $n\in\mathbb Z$.

**[Essencial] Como provar que $G$ é abeliano:**
- Se $x^2=1\ \forall x$: $a^2=1\iff a=a^{-1}$, logo $ab=(ab)^{-1}=b^{-1}a^{-1}=ba$.
- Se $(xy)^2=x^2y^2\ \forall x,y$: $xyxy=xxyy\Rightarrow yx=xy$ (corte).
- Equivalente: $(xy)^{-1}=x^{-1}y^{-1}\ \forall x,y$.
- Todo o grupo cíclico é abeliano.

**[Essencial] Completar tabela de Cayley:**
- Linha e coluna do neutro são cópias dos cabeçalhos.
- Cada elemento aparece **exatamente uma vez** por linha e por coluna (solução única de $ax=b$).
- Comutativo $\iff$ tabela simétrica.
- Se houver ambiguidade, usar associatividade/potências (ex.: se $s^2=t$ então $s^3=st$).
- Ordem prima $\Rightarrow$ cíclico. Ordem 4: $\mathbb Z_4$ ou $\mathbb Z_2\times\mathbb Z_2$ (Klein: todo $x\neq e$ tem ordem 2; **não** é cíclico).

---

## 2. Grupos de referência

- **[Essencial]** $\mathbb Z_n=\{[0],\dots,[n-1]\}$, $[a]+[b]=[a+b]$: abeliano, ordem $n$, $=\langle[1]\rangle$. $[m]$ gera $\iff \operatorname{mdc}(m,n)=1$.
- **[Essencial]** $S_n$: $|S_n|=n!$; não abeliano se $n\ge 3$. $A_n$ (permutações pares) $\le S_n$, $|A_n|=n!/2$.
- **[Útil]** $D_n\le S_n$ (simetrias do $n$-ágono), $|D_n|=2n$, $D_3=S_3$.
- **[Útil]** $S_3=\{\mathrm{id},(123),(132),(12),(13),(23)\}$. Subgrupos próprios não triviais: $\langle(123)\rangle$ e os três $\{\mathrm{id},(ij)\}$. Não é cíclico.
- **[Essencial] Produto direto** $G_1\times G_2$: $(g_1,g_2)(h_1,h_2)=(g_1h_1,g_2h_2)$; identidade $(1,1)$; inverso componente a componente; $|G_1\times G_2|=|G_1||G_2|$; abeliano $\iff$ ambos abelianos.
  - $o(g,h)=\operatorname{mmc}(o(g),o(h))$ (porque $(g,h)^k=(g^k,h^k)$).
  - $\mathbb Z_m\times\mathbb Z_n$ cíclico $\iff \operatorname{mdc}(m,n)=1 \iff \mathbb Z_m\times\mathbb Z_n\cong\mathbb Z_{mn}$.
  - Cuidado: $\mathbb Z_2$ é cíclico mas $\mathbb Z_2\times\mathbb Z_2$ não é (contraexemplo para V/F).

---

## 3. Subgrupos

**[Essencial] Critério.** $H\le G \iff$
(i) $1\in H$; (ii) $a,b\in H\Rightarrow ab\in H$; (iii) $a\in H\Rightarrow a^{-1}\in H$.
**Critério II:** (i) $1\in H$ e (ii') $a,b\in H\Rightarrow ab^{-1}\in H$.

**[Essencial] Dicas.**
- Sempre existem $\{1\}$ (trivial) e $G$ (impróprio).
- $\bigcap_i H_i\le G$. $H_1\cup H_2\le G\iff H_1\subseteq H_2$ ou $H_2\subseteq H_1$ (ex.: $2\mathbb Z\cup 3\mathbb Z\not\le\mathbb Z$).
- Em $G$ **abeliano**, são subgrupos: $\{x: x^k=1\}$ [porque $(xy)^k=x^ky^k$ e $(x^{-1})^k=(x^k)^{-1}$] e $\{x^k: x\in G\}$ [porque $x^ky^k=(xy)^k$ e $(x^k)^{-1}=(x^{-1})^k$].
- **[Útil]** Em $G$ abeliano, $T_G=\{a: o(a)<\infty\}$ é subgrupo: $a^m=b^n=1\Rightarrow(ab)^{mn}=1$.
- **Listar subgrupos:** só ordens $d\mid |G|$ (Lagrange); calcular $\langle x\rangle$ para cada $x$; se $|G|$ é primo só há $\{1\}$ e $G$.
- **[Útil]** Subgrupos de $(\mathbb Z,+)$: exatamente os $n\mathbb Z$; $\langle m,n\rangle=\operatorname{mdc}(m,n)\mathbb Z$.

**[Essencial] Centro** $Z(G)=\{x: ax=xa\ \forall a\}$ e **centralizador** $C_a=\{x: ax=xa\}$ são subgrupos. $G$ abeliano $\iff Z(G)=G$.
*Prova de $Z(G)\trianglelefteq G$* (anotado "sai no teste"):
- $1\in Z(G)$.
- Fecho: $(ab)y=a(yb)=(ay)b=(ya)b=y(ab)$.
- Inversos: $ay=ya\Rightarrow a^{-1}y=ya^{-1}$ (multiplicar por $a^{-1}$ dos dois lados).
- Normal: $xax^{-1}=axx^{-1}=a$.

---

## 4. Subgrupo gerado, ordem de um elemento, grupos cíclicos

**[Essencial] Definições.** $\langle A\rangle$ = menor subgrupo contendo $A$. $\langle a\rangle=\{a^n:n\in\mathbb Z\}$ (aditivo: $\{na\}$). $G$ cíclico se $G=\langle a\rangle$. $o(a)=|\langle a\rangle|$.
$a$ tem ordem finita $\iff\exists k\in\mathbb N: a^k=1$; $o(a)$ = menor tal $k$.

**[Essencial] Com $k=o(a)$:**
$$\langle a\rangle=\{1,a,\dots,a^{k-1}\},\quad a^n=1\iff k\mid n,\quad a^m=a^n\iff k\mid m-n,\quad a^n=a^{\,n\bmod k},\quad o(a^{-1})=o(a)$$
$$o(a^m)=\frac{k}{\operatorname{mdc}(m,k)},\qquad a^m \text{ gera }\langle a\rangle\iff\operatorname{mdc}(m,k)=1$$

**[Essencial] Truque:** $a^p=a^q\ (p>q)\Rightarrow o(a)\mid p-q$. Ex.: $a^{15}=a^6\Rightarrow o(a)\mid 9$.

**[Essencial] $G=\langle a\rangle$ cíclico de ordem $n$:**
- Todo subgrupo é cíclico: $H=\langle a^k\rangle$ com $k$ o menor natural tal que $a^k\in H$, e $n=k\,|H|$.
- Para cada $d\mid n$ existe **um único** subgrupo de ordem $d$: $\langle a^{n/d}\rangle$.
- Com $g=\operatorname{mdc}(m,n)$: $\langle a^m\rangle=\langle a^g\rangle$, $|\langle a^m\rangle|=n/g$, $(G:\langle a^m\rangle)=g$, e $a^j\in\langle a^m\rangle\iff g\mid j$.
- Cíclico infinito $\cong\mathbb Z$; cíclico de ordem $n\cong\mathbb Z_n$ (via $a^m\mapsto[m]$); dois cíclicos da mesma ordem são isomorfos.

**[Essencial] Conjugação:** $(aba^{-1})^n=ab^na^{-1}$, logo $o(aba^{-1})=o(b)$.
**[Útil]** $o(ab)=o(ba)$. Em abeliano: $o(ab)\mid\operatorname{mmc}(o(a),o(b))$.

**Exemplo (opcional):** $a=15\in\mathbb Z_{50}$: $\langle15\rangle=\langle5\rangle$, $|H|=50/5=10$, $(\mathbb Z_{50}:H)=5$.

---

## 5. Permutações

**[Essencial] Notação.** Ciclo $(i_1\,i_2\cdots i_k)$: $i_1\to i_2\to\cdots\to i_k\to i_1$. Inverso: $(i_k\cdots i_1)$. Inversa em duas linhas: trocar as linhas.

**[Essencial] Ciclos disjuntos.** Partir de 1, seguir as imagens até fechar; repetir com o menor elemento não visitado; omitir pontos fixos. Ciclos disjuntos comutam. Para um produto de ciclos **não** disjuntos: calcular a imagem de cada $x$ da direita para a esquerda e só depois decompor.

**[Essencial] Ordem e potências.**
- $o(\sigma)=\operatorname{mmc}$ dos comprimentos dos ciclos disjuntos.
- $\sigma^n=\prod c_i^{\,n}$ e, para um ciclo de comprimento $\ell$, $c^n=c^{\,n\bmod \ell}$. Reduzir $n$ módulo $o(\sigma)$ (se $n<0$, usar $n\bmod o(\sigma)$).
- $o(\sigma^m)=o(\sigma)/\operatorname{mdc}(m,o(\sigma))$.

**[Essencial] Paridade.** Um ciclo de comprimento $k$ é produto de $k-1$ transposições: $(i_1\cdots i_k)=(i_1i_2)(i_2i_3)\cdots(i_{k-1}i_k)$.
- $\sigma$ é par $\iff$ o nº de ciclos de comprimento **par** é par.
- par·par = ímpar·ímpar = par; par·ímpar = ímpar.
- $\sigma^{-1}$ tem a paridade de $\sigma$; $\alpha^{\pm2}$ é sempre par; uma transposição é ímpar.

**[Essencial] $H=\langle\sigma^k\rangle$.** Calcular $\sigma^k$ e as suas potências até $\mathrm{id}$. $|H|=o(\sigma)/\operatorname{mdc}(k,o(\sigma))$. $\langle\sigma^{-k}\rangle=\langle\sigma^{k}\rangle$.

**[Essencial] Equações.** Não é comutativo: multiplicar pelos inversos do lado certo.
Ex.: $\alpha^{-3}\sigma\beta^{22}=\alpha\Rightarrow\sigma=\alpha^{4}\beta^{-22}$.
Se só aparecem potências do mesmo $\sigma$, comutam e somam-se expoentes: $\sigma^{-2}\alpha\sigma^{8}=\sigma\Rightarrow\alpha=\sigma^{-5}$.

**[Útil] Elemento de ordem $m$ em $S_n$.** Escolher ciclos disjuntos com soma dos comprimentos $\le n$ e mmc $=m$ (ex.: ordem 20 em $S_9$: ciclos de comprimento $4$ e $5$). Em $S_8$ as ordens possíveis são $\{1,\dots,8,10,12,15\}$. Para V/F do tipo "existe $\alpha$ par/ímpar de ordem $m$": construir o exemplo e contar ciclos de comprimento par.

**Exemplo (opcional, dos apontamentos):**
$(2\,6\,3)(4\,3\,8\,1\,2)(3\,4)(2\,3\,7\,8)=(1\,6\,3\,7)(4\,8)$, logo $o=\operatorname{mmc}(4,2)=4$ e há 2 ciclos de comprimento par, portanto é par.

---

## 6. Homomorfismos

**[Essencial] Definição.** $\varphi:G\to G'$ com $\varphi(xy)=\varphi(x)\varphi(y)$.
- mono = injetivo; epi = sobrejetivo; iso = bijetivo ($G\cong G'$; $\cong$ é relação de equivalência).
- endomorfismo/automorfismo: $G\to G$.

**[Essencial] Propriedades.**
- $\varphi(1)=1'$; $\varphi(a^{-1})=\varphi(a)^{-1}$; $\varphi(a^m)=\varphi(a)^m$.
- $o(\varphi(a))\mid o(a)$, com igualdade se $\varphi$ for mono.
- A imagem de um subgrupo e a imagem recíproca de um subgrupo são subgrupos.
- $\operatorname{Im}\varphi=\varphi(G)\le G'$; $\operatorname{Nuc}\varphi=\{x:\varphi(x)=1'\}\le G$.
- **mono $\iff\operatorname{Nuc}\varphi=\{1\}$; epi $\iff\operatorname{Im}\varphi=G'$.**

**[Essencial] Provar / refutar.**
- Provar hom: verificar $\varphi(xy)=\varphi(x)\varphi(y)$.
- Não é hom se $\varphi(1)\neq1'$, ou se $o(\varphi(a))\nmid o(a)$, ou por contraexemplo.
- Exemplos: $x\mapsto x+n$ só é hom se $n=0$; $x\mapsto nx$ em $(\mathbb Z,+)$ é sempre hom (mono se $n\ne0$); $x\mapsto[x]_m$ é epi; $x\mapsto e^x$, $(\mathbb R,+)\to(\mathbb R^+,\cdot)$ é iso.

**[Essencial] A partir de um grupo cíclico.** Se $G=\langle a\rangle$, $\varphi$ fica determinado por $\varphi(a)$ e $\operatorname{Im}\varphi=\langle\varphi(a)\rangle$.
Para $\mathbb Z_n$: $\varphi(\bar x)=\varphi(\bar 1)^x$ define um hom $\iff\varphi(\bar1)^n=1'$ (isto é, $o(\varphi(\bar1))\mid n$). Então $\operatorname{Nuc}\varphi=\{\bar x:\ o(\varphi(\bar 1))\mid x\}$.

**[Útil] $\mathbb Z_m\to\mathbb Z_n$:** existe epi $\iff n\mid m$; existe mono $\iff m\mid n$.
(Epi: $\varphi(\bar1)$ tem de ter ordem $n$ e dividir $m$. Mono: $\varphi(\bar1)$ tem de ter ordem $m$ e dividir $n$, por Lagrange.)

**[Essencial] Isomorfismos.**
- Para mostrar $G\cong\mathbb Z_n$: achar $g$ com $o(g)=|G|=n$ e definir $\varphi(g^k)=[k]$.
- Para mostrar que **não** são isomorfos: ordens diferentes, nº de elementos de cada ordem diferente, só um é cíclico ou abeliano.

**[Essencial] Prova com epimorfismo.** Se $\varphi:G_1\to G_2$ é epi, então $\varphi(Z(G_1))\subseteq Z(G_2)$. Dado $y'\in G_2$, escreve $y'=\varphi(y)$ (sobrejetivo); então $\varphi(x)y'=\varphi(xy)=\varphi(yx)=y'\varphi(x)$.

**Exemplos (opcionais):**
- $G=\mathbb Z_3\times\mathbb Z_2$: $(a,b)$ tem ordem 6, logo gera $G\cong\mathbb Z_6$, com $\varphi((a,b)^k)=[k]$. Há subgrupos de ordem $1,2,3,6$ e nenhum de ordem $4$ ou $5$.
- $\varphi:\mathbb Z_6\to S_3$ com $\varphi(\bar1)=(1\,3\,2)$ (ordem $3\mid 6$, logo existe): $\varphi(\bar x)=(1\,3\,2)^x$; $\operatorname{Im}=\langle(1\,3\,2)\rangle$ (3 elementos); $\operatorname{Nuc}=\{\bar0,\bar3\}$; nem mono nem epi, logo não é iso.

---

## 7. Teorema de Lagrange

**[Essencial]** $G$ finito, $H\le G$: $|G|=(G:H)\cdot|H|$. Consequências:
- $|H|\mid|G|$ e $o(a)\mid|G|$, logo $a^{|G|}=1$.
- Se existe subgrupo de ordem $d$, então $d\mid|G|$ (a recíproca só a garanto em cíclicos).
- $|G|=p$ primo $\Rightarrow G$ cíclico, gerado por qualquer $a\ne1$; só tem $\{1\}$ e $G$.

**[Útil]**
- $\operatorname{mdc}(|H|,|K|)=1\Rightarrow H\cap K=\{1\}$ (porque $|H\cap K|$ divide ambos).
- $K\le H\le G$: $(G:K)=(G:H)(H:K)$.

---

## 8. Parte final: normais, quociente, TFH (compacto; decide tu o que entra)

**[Útil] Classes laterais.** $a\,\rho\,b\iff a^{-1}b\in H$; $aH=\{ah:h\in H\}$; $G/H=\{aH\}$; $(G:H)=|G/H|$; $|aH|=|H|$.

**[Útil] Subgrupo normal** $H\trianglelefteq G$: $aH=Ha\ \forall a$.
- **Critério:** $H\le G$ e $xhx^{-1}\in H$ para todo $x\in G$, $h\in H$.
- Sempre normais: $\{1\}$, $G$; qualquer subgrupo se $G$ é abeliano; $(G:H)=2$; $Z(G)$; $\operatorname{Nuc}\varphi$.

**[Útil] Quociente** ($H\trianglelefteq G$): $(aH)(bH)=(ab)H$; identidade $H$; $(aH)^{-1}=a^{-1}H$; $|G/H|=|G|/|H|$. O epimorfismo canónico é $\pi:a\mapsto aH$.

**[Útil] Teorema Fundamental do Homomorfismo.** Se $\varphi:G\to G'$ é hom com núcleo $K$, então $G/K\cong\operatorname{Im}\varphi$. Em particular $|\operatorname{Im}\varphi|=|G|/|\operatorname{Nuc}\varphi|$.
**Método:** calcular $\operatorname{Nuc}$ e $\operatorname{Im}$ e concluir.

**[Se sobrar espaço] Tipo do Teste 2022-Q6.** Se $G'$ é abeliano e $\operatorname{Nuc}\varphi\subseteq H\le G$, então $H\trianglelefteq G$:
$\varphi(xhx^{-1}h^{-1})=1'$ (abeliano) $\Rightarrow xhx^{-1}h^{-1}\in\operatorname{Nuc}\varphi\subseteq H\Rightarrow xhx^{-1}\in H$.

