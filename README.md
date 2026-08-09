# Stat-ML Lab — Senior DS/Applied Scientist Interview Learning Lab

A hands-on curriculum of executed Jupyter notebooks covering the topics that actually come up
in **senior data scientist / applied scientist interviews** — and in the highest-impact
real-world applications of data science: product & business analytics, experimentation,
finance, and operations.

**Who it's for.** You already know core probability, statistics, and machine learning.
These notebooks skip the basics and go straight to the applied, senior-level material:
the nuances, the pitfalls, the trade-offs, and the "how it's really done in industry."

**How it teaches.** Every notebook is a set of hands-on experiments — mostly simulations
with known ground truth, so you can *verify* that methods work (and watch them fail when
their assumptions break). Each ends with an **Interview corner** (realistic questions with
strong-answer outlines), **key takeaways**, and **exercises with solutions**.

## Setup

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Python ≥ 3.10 recommended. The two PySpark notebooks additionally need a Java runtime
(Java 17 or 21). Every notebook runs end-to-end in a few minutes on a laptop; all randomness
is seeded so a fresh run reproduces the committed outputs.

## Curriculum

### 01 · Statistical Foundations
| Notebook | What it covers |
|---|---|
| [Sampling, the CLT in Practice, and the Bootstrap](01_statistical_foundations/01_sampling_clt_bootstrap.ipynb) | Sampling distributions, real CLT convergence speed on skewed and heavy-tailed data, t-interval coverage failures, and the bootstrap (percentile/basic/BCa) with its failure modes and block/cluster fixes. |
| [Hypothesis Testing Beyond the Basics](01_statistical_foundations/02_hypothesis_testing_beyond_basics.ipynb) | Welch vs Student size distortion, exact permutation tests, what Mann-Whitney really tests, proportion tests with lift CIs, effect sizes vs p-values at huge n, and the p-value traps interviewers love to probe. |
| [Regression: the Workhorse of Applied Statistics](01_statistical_foundations/03_regression_the_workhorse.ipynb) | Inference vs prediction mindsets, coefficient interpretation across functional forms on a known-truth pricing dataset, omitted-variable-bias arithmetic, robust SEs, multicollinearity, ridge/lasso with the post-selection caveat, odds ratios vs marginal effects. |
| [Statistical Traps](01_statistical_foundations/04_statistical_traps.ipynb) | Simpson's paradox and the confounder criterion, regression to the mean, multiple-testing blowup with Bonferroni/Holm/BH, optional stopping and subgroup mining, winner's curse (Type M), survivorship and Berkson bias, Goodhart's law. |
| [When Confidence Intervals Lie](01_statistical_foundations/05_when_cis_lie.ipynb) | The epistemology of CIs and the bootstrap: what the 95% actually promises (and Fisher's relevant-subsets objection), measured coverage collapse under dependence, selection (winner's curse, best-of-K), and bias (the big-data paradox: half a million samples, 0% coverage), the bootstrap as a plug-in thought experiment with a soundness checklist, census-vs-process questions, and the overlapping-CIs fallacy. |
| [Entropy, Cross-Entropy, and KL Divergence](01_statistical_foundations/06_entropy_crossentropy_kl.ipynb) | Entropy as expected surprise and as the compression limit (Huffman coder built from scratch; cross-entropy as the cost of the wrong codebook), MLE = KL minimization, forward vs reverse KL (mass-covering vs mode-seeking, fit live), the reveal that PSI, IV, the G-test, and AIC are all KL in costume, and maximum entropy as "assume the least". |

### 02 · A/B Testing & Experimentation
| Notebook | What it covers |
|---|---|
| [An A/B Test End-to-End](02_ab_testing/01_ab_test_end_to_end.ipynb) | A checkout-flow experiment from design doc to ship decision: metric choice by variance, power and duration, hash-based assignment, SRM detection of a broken pipeline, a platform-style readout with bootstrap CIs, segment discipline, and the senior review checklist. |
| [Power, MDE, and Sample Size](02_ab_testing/02_power_mde_sample_size.ipynb) | Analytic sizing and MDE math, duration planning, triggering/dilution, a validated generic `simulate_power()` for zero-inflated revenue and arbitrary tests, unequal allocation, cluster/geo design effects, and the Type M/S consequences of underpowering. |
| [Variance Reduction: CUPED and Regression Adjustment](02_ab_testing/03_variance_reduction_cuped.ipynb) | CUPED derived and implemented (44% variance reduction), its equivalence to regression adjustment and CUPAC, post-stratification benchmarks, where it fails (new users, binary metrics), and the in-experiment-covariate bug demonstrated. |
| [Peeking, Early Stopping, and Sequential Testing](02_ab_testing/04_peeking_sequential.ipynb) | How daily peeking inflates false positives from 5% to ~27%, fixed three ways: O'Brien–Fleming alpha spending (Lan–DeMets), an always-valid mixture SPRT, and an honest look at Bayesian stopping rules. |
| [Ratio Metrics, the Delta Method, and Clustered Data](02_ab_testing/05_ratio_metrics_delta_method.ipynb) | Why naive session-level tests on CTR-style ratio metrics inflate false positives ~6x, and how the delta method, cluster bootstrap, and cluster-robust regression fix inference — plus ratio-of-means vs mean-of-ratios estimands. |
| [Interference and Advanced Designs](02_ab_testing/06_advanced_designs_interference.ipynb) | When SUTVA breaks: a two-sided marketplace simulator quantifying how naive A/B overstates effects under cannibalization, switchback design and analysis, cluster and network randomization, and interleaving. |

### 03 · Causal Inference
| Notebook | What it covers |
|---|---|
| [Potential Outcomes, DAGs, and Good vs Bad Controls](03_causal_inference/01_potential_outcomes_dags.ipynb) | The selection-bias decomposition, why randomization identifies the ATE, d-separation and the backdoor criterion, and the full good-vs-bad-controls bias arithmetic (confounders, mediators, colliders, M-bias) with each DAG drawn beside its simulation. |
| [Propensity Scores, IPW, and Doubly Robust Estimation](03_causal_inference/02_propensity_ipw_doubly_robust.ipynb) | A simulated promo campaign with known ground truth stress-tests the observational toolkit — overlap, trimming, stratification, matching, stabilized IPW, AIPW surviving single-model misspecification — and why PS-model AUC is the wrong success criterion. |
| [Difference-in-Differences, Event Studies, and Synthetic Control](03_causal_inference/03_did_synthetic_control.ipynb) | DiD from the 2x2 to clustered-SE regressions and event-study pre-trend checks, why naive TWFE breaks under staggered adoption, and synthetic control for one-city launches with placebo-based inference. |
| [Instrumental Variables and Regression Discontinuity](03_causal_inference/04_iv_rdd.ipynb) | A randomized-encouragement IV (2SLS, LATE, weak instruments, exclusion violations) and a spend-threshold sharp/fuzzy RDD with bandwidth, placebo, and density diagnostics. |
| [Uplift Modeling and Heterogeneous Treatment Effects](03_causal_inference/05_uplift_cate.ipynb) | Response vs uplift targeting with the four customer segments, S/T/X meta-learners scored against known CATEs, from-scratch Qini/AUUC, profit-optimal top-k policies with off-policy value estimation, and the noise-heterogeneity trap. |

### 04 · Machine Learning on Tabular Data
| Notebook | What it covers |
|---|---|
| [Gradient Boosting Mastery](04_ml_tabular/01_gradient_boosting_mastery.ipynb) | From a from-scratch booster to tuned XGBoost/LightGBM: the parameters that matter, early stopping, monotonic constraints for business rules, native categoricals and missing values, and a sane tuning workflow with honest diminishing returns. |
| [Data Leakage and Robust Validation Design](04_ml_tabular/02_leakage_validation.ipynb) | Five runnable leakage failure modes (post-outcome features, preprocessing contamination, temporal, group, target encoding) with quantified inflated-vs-honest gaps, the Pipeline/ColumnTransformer fix, a validation-scheme decision guide, and adversarial validation. |
| [Model Evaluation, Calibration, and Threshold Economics](04_ml_tabular/03_evaluation_calibration.ipynb) | Ranking vs calibration vs decision value: ROC vs PR at 1% prevalence, proper scoring rules, reliability diagrams with Platt/isotonic recalibration, and a retention-offer case where identical-AUC models earn +$15.6k vs −$79k at the same threshold. |
| [Imbalanced Classification: a Fraud Case Study](04_ml_tabular/04_imbalanced_fraud.ipynb) | Fraud at ~1% prevalence: PR-focused evaluation, precision@alert-budget, cost-sensitive weighting vs resampling (SMOTE skepticism, honestly evaluated), calibration repair, threshold choice under review capacity, and selective-labels reality. |
| [Feature Importance Done Right](04_ml_tabular/05_explainability_shap.ipynb) | Impurity vs permutation importance pitfalls, TreeSHAP global and local explanations, correlated-feature credit splitting, why importance ≠ causality (demonstrated), and PDP/ICE extrapolation traps. |
| [Mutual Information and Information Theory in Modern ML](04_ml_tabular/06_mutual_information_modern_ml.ipynb) | MI vs correlation on four dependence shapes, the binning-bias trap with permutation-null guards, feature screening and its synergy blind spot (mRMR included), trees as greedy MI maximizers (why XOR defeats depth-2), the data processing inequality (coarsened features, noisy-label ceilings), NMI/AMI/ARI — then the LLM era at paper scale: a character n-gram model with perplexity, temperature as an entropy dial, the RLHF reward-vs-KL frontier, and distillation with soft targets, all measured. |

### 05 · Time Series & Forecasting
| Notebook | What it covers |
|---|---|
| [Time Series Foundations](05_time_series/01_ts_foundations.ipynb) | STL decomposition and remainder reading, ADF/KPSS with the 2x2 interpretation grid, ACF/PACF identification built by simulation, spurious random-walk correlations quantified, and why autocorrelation breaks naive CIs (with Newey-West and block-bootstrap fixes). |
| [Classical Forecasting: Baselines, ETS, and (S)ARIMA](05_time_series/02_classical_forecasting.ipynb) | Baselines that set the bar, Holt-Winters/ETS, SARIMA with pragmatic order selection and residual diagnostics, fan charts with an empirical interval-coverage backtest, and rolling-origin evaluation across MAE/RMSE/MAPE/sMAPE/MASE. |
| [ML Forecasting with Gradient Boosting](05_time_series/03_ml_forecasting_backtesting.ipynb) | Forecasting as supervised learning on a multi-SKU retail panel: the off-by-one leakage trap, recursive vs direct multi-step, honest backtests against seasonal naive and ETS in both winning regimes, global vs per-SKU models, and calibrated P10/P50/P90 quantile forecasts. |
| [Time Series Anomaly Detection](05_time_series/04_anomaly_detection.ipynb) | A labeled KPI-anomaly test bed (spikes, seasonal violations, level shifts, drift) comparing STL+MAD, forecast-interval breaches, CUSUM, and IsolationForest — with detection-delay analysis, alert-budget design, and root-cause breakdowns. |

### 06 · Applied Bayesian Methods
| Notebook | What it covers |
|---|---|
| [Bayesian A/B Testing](06_bayesian_methods/01_bayesian_ab_testing.ipynb) | Beta-Binomial from priors to decisions: P(B>A) and credible intervals by Monte Carlo, the expected-loss stopping rule with its simulated frequentist operating characteristics, ROPE, two-part revenue posteriors, and an honest frequentist-vs-Bayesian comparison. |
| [The Bayesian Workflow in PyMC](06_bayesian_methods/02_pymc_workflow.ipynb) | Prior predictive checks, NUTS diagnostics, the centered-funnel divergence pathology and its non-centered fix, posterior predictive checks, a budget decision from the posterior, and side-by-sides with the frequentist GLM at large and tiny n. |
| [Hierarchical Models and Partial Pooling](06_bayesian_methods/03_hierarchical_models.ipynb) | Complete/no/partial pooling on 40 stores with unequal traffic, the classic shrinkage plot, out-of-sample proof that shrinkage wins, fair posterior-based ranking, James–Stein and MixedLM connections, and shrunken per-segment A/B effects. |
| [Multi-Armed Bandits and Thompson Sampling](06_bayesian_methods/04_bandits_thompson.ipynb) | Regret vs fixed A/B testing, a seeded race of epsilon-greedy/UCB1/Thompson sampling, batched and non-stationary variants, adaptive sampling bias with IPW fixes, and a LinUCB contextual bandit. |

### 07 · SQL & Big Data (Spark)
| Notebook | What it covers |
|---|---|
| [Advanced SQL: Window Functions and Interview Classics](07_sql_and_big_data/01_advanced_sql_duckdb.ipynb) | Window functions, ranking on ties, ROWS-vs-RANGE frames, anti-join NULL traps, gaps-and-islands, and the other SQL interview classics solved live on a simulated e-commerce warehouse in DuckDB, spot-checked against pandas. |
| [Product Analytics in SQL](07_sql_and_big_data/02_sql_product_analytics.ipynb) | DAU/WAU/MAU and rolling actives, cohort retention triangles, strictly-ordered funnels, 30-minute-gap sessionization, growth accounting with the MAU bridge, and the L28 engagement distribution — all in SQL over a simulated event log. |
| [PySpark Fundamentals: Shuffles, Joins, Skew, and Tuning](07_sql_and_big_data/03_pyspark_fundamentals.ipynb) | When Spark is actually the right tool, reading explain plans, sort-merge vs broadcast joins, diagnosing and salting skewed keys, repartition/coalesce/caching, and the measured cost of Python UDFs — with the 199/200-straggler scenario reproduced and fixed. |
| [Machine Learning at Scale with Spark ML](07_sql_and_big_data/04_sparkml_pipeline.ipynb) | A churn model end-to-end in Spark ML — Transformer/Estimator/Pipeline, the feature-vector metadata dance, CrossValidator tuning, and the honest case for training locally on a sample while scoring distributed. |

### 08 · Product & Business Analytics
| Notebook | What it covers |
|---|---|
| [Metric Design, Funnels, and Growth Accounting](08_product_analytics/01_metrics_and_growth.ipynb) | North-star metric trees, Goodhart-proof metric design, funnel and binding-constraint analysis, the classic mix-vs-rate conversion decomposition, cohort retention curves, and new/retained/resurrected/churned growth accounting. |
| [Churn: Supervised ML and Survival Analysis](08_product_analytics/02_churn_survival.ipynb) | Precise churn label design, an as-of-disciplined LightGBM model evaluated on lift and calibration against an oracle ceiling, survival analysis (KM, log-rank, Cox hazard ratios, expected remaining lifetime), and why retention targeting needs uplift, not risk. |
| [Customer Lifetime Value](08_product_analytics/03_ltv_modeling.ipynb) | Cohort LTV curves and their extrapolation traps, shifted-Beta-Geometric and BG/NBD + Gamma-Gamma implemented from scratch, and ML value prediction evaluated by decile capture and calibration instead of RMSE. |
| [Customer Segmentation](08_product_analytics/04_segmentation_clustering.ipynb) | Action-first segmentation: RFM scoring with named segments and playbooks, k-means done right (log transforms vs whales, honest elbow/silhouette), GMM soft assignments, the null-clustering trap with gap-statistic and bootstrap-ARI stability guards. |

### 09 · Finance & Operations Research
| Notebook | What it covers |
|---|---|
| [Credit Risk Scorecards](09_finance_and_operations/01_credit_scorecard.ipynb) | A full scorecard from scratch — fine/coarse classing, WOE/IV, PDO points scaling, KS/Gini/grade evaluation, PD calibration economics, a LightGBM challenger comparison, and reject inference with selection on unobservables. |
| [Financial Returns, Risk, and Backtest Overfitting](09_finance_and_operations/02_returns_risk.ipynb) | Gaussian vs fat-tailed (GARCH-t) price worlds verifying the stylized facts, a full risk stack (EWMA vol, VaR three ways, Expected Shortfall, Kupiec exception tests), and backtest overfitting exposed via 1000 zero-edge strategies with the deflated-Sharpe correction. |
| [Linear and Integer Programming](09_finance_and_operations/03_optimization_pulp.ipynb) | Translating business problems into LPs/MIPs with PuLP — budget allocation with piecewise-linearized diminishing returns, transportation, staffing MIP — plus verified shadow prices, greedy-vs-exact comparisons, and forecast-error-to-decision-regret propagation. |
| [Newsvendor, Inventory, and Queueing](09_finance_and_operations/04_inventory_simulation.ipynb) | Critical fractile verified by simulation, quantile-forecast-to-order pipelines, (s,S) policy sweeps tracing the service-vs-cost frontier, safety-stock formula failures, and M/M/c staffing with a hand-rolled discrete-event simulator validated against Erlang C. |

### 10 · ML in Production
| Notebook | What it covers |
|---|---|
| [Drift Detection and Model Monitoring](10_ml_in_production/01_drift_monitoring.ipynb) | Covariate vs concept drift vs label shift on a 30-month scoring stream: PSI from scratch with calibrated thresholds, delayed-label proxy monitoring, benign vs killer drift in code, and an honest backtest of scheduled vs triggered retraining. |
| [From Notebook to Production](10_ml_in_production/02_production_readiness.ipynb) | Refactoring a leaky workflow into a serialized sklearn Pipeline with metadata, silent training-serving skew and its schema-validation defense, retrain-and-diff reproducibility tests, pre-deploy gates, and a shadow rollout catching a bad challenger. |

## Suggested paths

- **Product DS / tech company interview:** modules 01 → 02 → 03 → 07 → 08, then 06.
- **ML-heavy applied scientist:** modules 01 → 04 → 05 → 10, then 02 → 03 and 06.
- **Finance / operations:** modules 01 → 05 → 09, then 04 → 06.

## Contributing

See [STYLE.md](STYLE.md) for the notebook structure and quality bar every notebook follows.
