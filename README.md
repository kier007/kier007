# DOPAN / kier007

## AI Engineer

I build systems that reason over code, uncertainty, and real-time signals.

**Agentic systems · stochastic forecasting · computer vision**

---

## Proof / 01 — Measurable operators under constraints

Let observations and outputs inhabit complex Hilbert spaces

```math
\mathcal{H}_{X}=L^{2}(\Omega_X,\mu;\mathbb{C}^{d}),
\qquad
\mathcal{H}_{Y}=L^{2}(\Omega_Y,\nu;\mathbb{C}^{m}).
```

Write an inference system abstractly as a measurable operator

```math
T_{\theta}:(\mathcal{H}_{X},\Sigma_X)\longrightarrow(\mathcal{H}_{Y},\Sigma_Y),
```

Let the data law be a probability measure on the measurable product space

```math
\rho\in\mathcal{P}(
\mathcal{H}_{X}\times\mathcal{H}_{Y},
\Sigma_X\otimes\Sigma_Y
).
```

Engineering begins where expected risk becomes a constrained variational problem:

```math
\inf_{T\in\mathcal{A}}
\{
\int_{\mathcal{H}_{X}\times\mathcal{H}_{Y}}
\ell(Tx,y)\,d\rho(x,y)
+\lambda\,\Omega(T)
\},
\qquad
\mathcal{A}\ne\varnothing,
\quad
\lambda\ge0.
```

```math
\mathcal{A}=\{T:
\mathrm{correct}(T)\land
\mathrm{observable}(T)\land
\mathrm{deployable}(T)
\}.
```

> **Riddle 01.** I minimize expected risk over an infinite space, yet the smallest loss cannot admit me to $\mathcal{A}$. What completes the proof?

---

## Proof / 02 — Belief, memory, and action

[RepoPilot Sentinel](https://github.com/kier007/RepoPilot-Sentinel) is an autonomous GitHub maintainer agent with tool execution, structured memory, capability synthesis, and human-gated writes.

A control-theoretic view treats the repository as a partially observed state on a measurable space. From observations $o_{0:t}$, actions $a_{0:t-1}$, and memory $m_t$, the agent maintains the belief measure

```math
b_t(E)=\Pr(
s_t\in E\mid o_{0:t},a_{0:t-1},m_t
),
\qquad
E\in\Sigma_S.
```

Policies over the belief state are evaluated through

```math
V^{\star}(b_0)=\sup_{\pi}
\mathbb{E}_{\pi}[
\sum_{t=0}^{\infty}\gamma^{t}
(r_t-\beta c_t)
\mid b_0
],
\qquad 0<\gamma<1.
```

Memory and write authority evolve on separate paths:

```math
m_{t+1}=U(m_t,o_t,a_t,r_t),
\qquad
g_t=\mathbf{1}\{A_t=1\land V_t=1\}.
```

Here $A_t$ and $V_t$ are Boolean authorization and validation indicators, and $g_t$ is the write gate.

> **Riddle 02.** I am neither the hidden state, the belief, the observation, nor the reward. Remove me, and the agent can succeed once but cannot learn from having succeeded. What am I?

---

## Proof / 03 — Forecasts as stochastic processes

[Propsarim](https://github.com/kier007/Propsarim) combines SARIMA and Prophet forecasts using inverse-validation-error weights.

For the backshift operator $B$, a multiplicative seasonal ARIMA process may be written as

```math
\Phi(B)\Phi_s(B^s)(1-B)^d(1-B^s)^D y_t
=
\Theta(B)\Theta_s(B^s)\varepsilon_t,
\qquad
\{\varepsilon_t\}_{t\in\mathbb{Z}}\sim\mathrm{WN}(0,\sigma^2).
```

Given validation errors

```math
e_i=(
\frac{1}{n}\sum_{t=1}^{n}
(y_t-\widehat y_{i,t})^2
)^{1/2}>0,
```

the hybrid forecast is the barycenter

```math
w_i=\frac{e_i^{-1}}{\sum_j e_j^{-1}},
\qquad
\widehat y_{H,t}=\sum_i w_i\widehat y_{i,t},
\qquad
\boldsymbol{w}\in\Delta^{k-1}.
```

If every competing error remains bounded away from zero, then

```math
\lim_{e_k\to0^+}\boldsymbol{w}=\boldsymbol{u}_k,
\qquad
\boldsymbol{u}_k=(0,\ldots,0,1,0,\ldots,0)\in\Delta^{k-1}.
```

Here $\boldsymbol{u}_k$ is the $k$th standard basis vector.

> **Riddle 03.** As one forecast becomes exact, a probability vector collapses onto a vertex of the simplex. Which voices survive the limit?

---

## Proof / 04 — Vision across a finite channel

[See2ruMeta](https://github.com/kier007/See2ruMeta) is a Meta Quest-to-Android passthrough streaming system built around real-time vision, WebRTC, and latency-aware delivery.

Let $X$ be a visual source and $\widehat X$ its reconstruction. The rate–distortion boundary, measured in bits per source symbol, is

```math
R(D)=
\inf_{p(\widehat x\mid x):\,
\mathbb{E}[d(X,\widehat X)]\le D}
I(X;\widehat X).
```

An ideal band-limited AWGN channel with bandwidth $B$ and signal-to-noise ratio $\mathrm{SNR}$ has Shannon capacity, in bits per second,

```math
C=B\log_2(1+\mathrm{SNR}).
```

For a source-symbol rate $f_s$ in symbols per second, source–channel separation gives the dimensionally consistent feasibility condition

```math
f_sR(D)\le C.
```

A first-order additive latency budget can be written as

```math
L_{\mathrm{e2e}}
\approx L_{\mathrm{capture}}
+L_{\mathrm{encode}}
+L_{\mathrm{network}}
+L_{\mathrm{decode}}
+L_{\mathrm{display}}.
```

Stage overlap can reduce realized latency; buffering and queueing can increase it.

> **Riddle 04.** Lower distortion demands rate, rate is bounded by capacity, and every stage contributes latency. Which constraint cannot be optimized in isolation?

---

Working set: **Python · FastAPI · agent/tool orchestration · time-series modeling · WebRTC · Unity · Docker · SQLite**

The proofs remain open. The systems do not.

[Explore the repositories or collaborate on GitHub →](https://github.com/kier007?tab=repositories)
