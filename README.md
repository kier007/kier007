# DOPAN / kier007

## AI Engineer

I build systems that reason over code, uncertainty, and real-time signals.

**Agentic systems · statistical forecasting · computer vision**

---

## Proof / 01 — The algebra of a useful system

Let the problem space be

$$
\mathcal{X} = \mathcal{X}_{\text{code}} \cup \mathcal{X}_{\text{time}} \cup \mathcal{X}_{\text{vision}},
\qquad
\mathcal{Y} = \mathcal{Y}_{\text{decisions}} \cup \mathcal{Y}_{\text{forecasts}} \cup \mathcal{Y}_{\text{streams}}.
$$

I work on functions

$$
f_{\theta}: \mathcal{X} \rightarrow \mathcal{Y}
$$

subject to one practical condition:

$$
\operatorname{useful}(f_{\theta})
= \operatorname{correct}(f_{\theta})
\land \operatorname{observable}(f_{\theta})
\land \operatorname{deployable}(f_{\theta}).
$$

> **Riddle 01.** I translate ambiguity into a measurable decision. A model can describe me, but only a working system can prove me. What am I?

---

## Proof / 02 — A function over projects

Define the project set and its engineering domains:

$$
\mathcal{P} = \{R,F,V\},
\qquad
\mathcal{D} = \{\text{agents},\text{forecasting},\text{real-time vision}\},
\qquad
g: \mathcal{P} \rightarrow \mathcal{D}.
$$

| Element | Project | Domain | Evidence |
|:--:|---|---|---|
| $R$ | [RepoPilot Sentinel](https://github.com/kier007/RepoPilot-Sentinel) | Autonomous agents | GitHub tool execution, structured memory, safe capability synthesis, and human-gated writes |
| $F$ | [Propsarim](https://github.com/kier007/Propsarim) | Statistical forecasting | SARIMA and Prophet combined through validation-weighted ensembling |
| $V$ | [See2ruMeta](https://github.com/kier007/See2ruMeta) | Real-time vision | Meta Quest-to-Android passthrough streaming over a latency-aware WebRTC pipeline |

> **Riddle 02.** A repository, a time series, and a stereoscopic stream enter the same function. Its form changes for every input; its purpose does not. What remains invariant?

---

## Proof / 03 — Fractions, limits, and constraints

For forecasting models with validation errors $e_i = \operatorname{RMSE}_i > 0$, Propsarim assigns

$$
w_i = \frac{e_i^{-1}}{\sum_j e_j^{-1}},
\qquad
\widehat{y}_{\text{hybrid}} = \sum_i w_i\widehat{y}_i,
\qquad
\sum_i w_i = 1.
$$

If every competing error remains positive, then

$$
\lim_{e_i \to 0^+} w_i = 1.
$$

For a real-time media path such as See2ruMeta, latency is additive:

$$
L_{\text{end-to-end}}
= L_{\text{capture}}
+ L_{\text{encode}}
+ L_{\text{network}}
+ L_{\text{decode}}
+ L_{\text{display}}.
$$

> **Riddle 03.** Two forecasters share a vote in inverse proportion to error; five stages share a delay by addition. When one term dominates, which system fails first?

---

## Proof / 04 — Probability in a small space

| System | Reason | Predict | Perceive |
|---|:---:|:---:|:---:|
| RepoPilot Sentinel | $1$ | $0$ | $0$ |
| Propsarim | $0$ | $1$ | $0$ |
| See2ruMeta | $0$ | $0$ | $1$ |
| Dopan / kier007 | $?$ | $?$ | $?$ |

Working set: **Python · FastAPI · agent/tool orchestration · time-series modeling · WebRTC · Unity · Docker · SQLite**

$$
\Pr(\text{ship} \mid \text{model},\text{system},\text{evidence})
\;?\;
\Pr(\text{ship} \mid \text{model}).
$$

> **Riddle 04.** Complete the inequality. Then complete the final row of the matrix.

---

The remaining proof is in the work.

[Explore the repositories or collaborate on GitHub →](https://github.com/kier007?tab=repositories)
