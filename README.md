# Quarterly Projection Model (QPM)

**Created by:** Arturo López Pérez  
**Contact:** [alopezperez.2605@gmail.com](mailto:alopezperez.2605@gmail.com)

# Overview

This repository implements a Quarterly Projection Model (QPM) for monetary policy analysis and forecasting in a small open economy.

The model follows a semi-structural QPM framework of core New Keynesian relationships, following the standard architecture used by the International Monetary Fund and some central banks. 

It is built around four core blocks:

1. **IS curve (aggregate demand)**
2. **Phillips curve (inflation dynamics)**
3. **Monetary policy rule (a forward looking Taylor rule type)**
4. **Modified Uncovered Interest Parity (UIP) condition**

An exogenous foreign block closes the small open economy framework.

The specification is consistent with log-linearization equations around the steady state from a structural Small Open Economy NK-DSGE.

---

# Model Structure

## Non-Policy Block: IS Curve (Aggregate Demand)

The output gap dynamics are given by:

$$
\hat{y}_t
=
b_1 \hat{y}_{t-1}
-
b_2 \, mci_t
+
b_3 \hat{y}_t^{\ast}
+
\varepsilon_t^{y}
$$

where the **monetary conditions index (MCI)** is defined as:

$$
mci_t
=
b_4 \hat{r}_t
+
(1 - b_4)(-\hat{z}_t)
$$

which represents the two main transmission channels for monetary policy in a small open economy.
---

## Non-Policy Block: Phillips Curve (Inflation Dynamics)

Inflation follows a hybrid New Keynesian Phillips Curve:

$$
\pi_t
=
a_1 \pi_{t-1}
+
(1 - a_1) \mathbb{E}_t[\pi_{t+1}]
+
a_2 \, rmc_t
+
\varepsilon_t^{\pi}
$$

The real marginal cost index is defined as:

$$
rmc_t
=
a_3 \hat{y}_t
+
(1 - a_3)\hat{z}_t
$$

which represents the two main real marginal costs factors in a small open economy.


Expected inflation assumes **rational expectations**:

$$
\pi_{t+1}^e = \mathbb{E}_t[\pi_{t+1}]
$$

---

## Monetary Policy Rule (Modified Taylor Rule)

The nominal policy interest rate follows a smoothed Taylor-type rule:

$$
i_t
=
g_1 i_{t-1}
+
(1 - g_1)
\left(
i_t^{neutral}
+
g_2 \left(
\mathbb{E}_t[\pi_{t+4}^4]
-
\mathbb{E}_t[\pi_{t+4}^{TAR}]
\right)
+
g_3 \hat{y}_t
\right)
+
\varepsilon_t^{i}
$$

The neutral nominal interest rate is defined as:

$$
i_t^{neutral}
=
\bar{r}_t
+
\mathbb{E}_t[\pi_{t+1}^4]
$$

---

## UIP Condition (Exchange Rate Dynamics)

The nominal exchange rate follows a modified UIP condition:

$$
s_t
=
(1 - e_1)\mathbb{E}_t[s_{t+1}]
+
e_1
\left(
s_{t-1}
+
\frac{2}{4}
\left(
\pi_t^{TAR}
-
\bar{\pi}_t^{\ast}
+
\Delta \bar{z}_t
\right)
\right)
+
\frac{-i_t + i_t^{\ast} + prem_t}{4}
+
\varepsilon_t^{s}
$$

---

## Foreign Block

All foreign variables follow simple autoregressive processes.

### Foreign Output Gap

$$
\hat{y}_t^{\ast}
=
\rho_{y^{\ast}} \hat{y}_{t-1}^{\ast}
+
\varepsilon_t^{y^{\ast}}
$$

### Foreign Nominal Interest Rate

$$
i_t^{\ast}
=
\rho_{i^{\ast}} i_{t-1}^{\ast}
+
(1 - \rho_{i^{\ast}})(\bar{r}_t^{\ast} + \pi_t^{\ast})
+
\varepsilon_t^{i^{\ast}}
$$

### Foreign Real Interest Rate

$$
r_t^{\ast} = i_t^{\ast} - \pi_t^{\ast}
$$

### Foreign Natural (Trend) Real Interest Rate

$$
\bar{r}_t^{\ast}
=
\rho_{r^{\ast}} \bar{r}_{t-1}^{\ast}
+
(1 - \rho_{r^{\ast}})\bar{r}^{\ast SS}
+
\varepsilon_t^{\bar{r}^{\ast}}
$$

### Foreign Real Interest Rate Gap

$$
\hat{r}_t^{\ast} = r_t^{\ast} - \bar{r}_t^{\ast}
$$

### Foreign Inflation

$$
\pi_t^{\ast}
=
\rho_{\pi^{\ast}} \pi_{t-1}^{\ast}
+
(1 - \rho_{\pi^{\ast}})\pi^{\ast SS}
+
\varepsilon_t^{\pi^{\ast}}
$$

---

## Long-Run UIP Condition

In the long run, the UIP condition implies a consistency of trends condition:

$$
\Delta \bar{z}_{t+1}
=
\bar{r}_t
-
\bar{r}_t^{\ast}
-
prem_t
$$

which implicitly determines the risk premium, while the remaining trend variables follow exogenous autoregressive processes.
---

## Purpose of the Repository

This repository is intended for:

- Monetary policy analysis
- Forecasting and scenario simulations
- Impulse response analysis
- Replication of QPM frameworks

---

## License

This project is currently shared for academic and research purposes.
