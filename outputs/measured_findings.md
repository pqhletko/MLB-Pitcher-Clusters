# Measured analysis findings

**Supported argument:** Arsenal and results define substantially different pitcher partitions across the tested cluster counts and targeted sensitivities. Exact memberships, especially combined and GMM partitions, depend on analytical choices; these results support representation-dependent descriptions rather than a unique taxonomy.

Frozen build: regular-season-coverage95-2026-11-22; n=1305.
All results below use real data; no simulated controls were run.

- arsenal/kmeans: diagnostic silhouette selects k=8, minimum hard cluster n=10; range-boundary selection=False.
- arsenal/gmm: diagnostic bic selects k=9, minimum hard cluster n=11; range-boundary selection=False.
- results/kmeans: diagnostic silhouette selects k=2, minimum hard cluster n=616; range-boundary selection=True.
- results/gmm: diagnostic bic selects k=2, minimum hard cluster n=376; range-boundary selection=False.
- combined/kmeans: diagnostic silhouette selects k=6, minimum hard cluster n=10; range-boundary selection=False.
- combined/gmm: diagnostic bic selects k=6, minimum hard cluster n=37; range-boundary selection=False.

## Matched-count agreement
- kmeans, arsenal vs results: ARI 0.037 at k=4; range 0.000–0.037 over k=2–12.
- gmm, arsenal vs results: ARI 0.001 at k=4; range -0.005–0.010 over k=2–12.
- arsenal, k-means vs GMM at k=4: ARI 0.078.
- results, k-means vs GMM at k=4: ARI 0.233.
- combined, k-means vs GMM at k=4: ARI 0.042.
- Mean within-representation method ARI exceeds mean arsenal/results ARI at 11/11 tested matched counts; the gap ranges 0.023–0.240. This is a descriptive contrast.

## Perturbation stability at k=4
- arsenal/gmm: mean ARI 0.740; empirical 10th–90th percentiles 0.583–0.957 (not a confidence interval).
- arsenal/kmeans: mean ARI 0.607; empirical 10th–90th percentiles 0.414–0.812 (not a confidence interval).
- combined/gmm: mean ARI 0.693; empirical 10th–90th percentiles 0.538–0.838 (not a confidence interval).
- combined/kmeans: mean ARI 0.691; empirical 10th–90th percentiles 0.567–0.851 (not a confidence interval).
- results/gmm: mean ARI 0.482; empirical 10th–90th percentiles 0.283–0.726 (not a confidence interval).
- results/kmeans: mean ARI 0.518; empirical 10th–90th percentiles 0.356–0.844 (not a confidence interval).

## Targeted sensitivity at k=4
- strict_100: kmeans arsenal/results ARI=0.036, gmm arsenal/results ARI=0.007.
- no_PCA: kmeans arsenal/results ARI=0.032, gmm arsenal/results ARI=0.010.
- observed_PA_500: kmeans arsenal/results ARI=0.050, gmm arsenal/results ARI=0.012.
- sqrt_shares: kmeans arsenal/results ARI=0.028, gmm arsenal/results ARI=-0.000.
- Equal-block combined/kmeans: ARI to baseline combined=0.281.
- Equal-block combined/gmm: ARI to baseline combined=0.631.

## Concrete profiles and analytical qualifications
- Arsenal k-means cluster 0 (n=574; representative DL Hall): FF share 33.5%, SI share 12.8%, other share 0.1%, velocity 88.0 mph. These are pitcher means; labels carry no rank.
- Arsenal k-means cluster 1 (n=452; representative Jon Gray): FF share 49.6%, SI share 4.7%, other share 0.0%, velocity 90.3 mph. These are pitcher means; labels carry no rank.
- Arsenal k-means cluster 2 (n=269; representative Dario Agrazal): FF share 11.9%, SI share 43.8%, other share 0.0%, velocity 89.3 mph. These are pitcher means; labels carry no rank.
- Arsenal k-means cluster 3 (n=10; representative Mitch Bratt): FF share 38.0%, SI share 12.9%, other share 22.7%, velocity 88.6 mph. These are pitcher means; labels carry no rank.
- A small group dominated by the aggregated other-pitch category is a metric-sensitive result, not a single coherent pitch family. Inspect the share-transform sensitivity before naming it an archetype.
- At k=4, descriptive mean results-block variance accounted for by arsenal clusters is kmeans: 5.3%, gmm: 1.0%. This cross-block description is not an out-of-sample estimate.
- Initialization sensitivity uses the full baseline optimization budgets; see initialization_summary.csv and objective differences in initialization_replicates.csv. Successful convergence does not guarantee a global optimum.

## Interpretation guardrails
- These partitions describe different similarity metrics; no unique natural cluster count is established.
- Stability is algorithmic reproducibility on this sample, not proof of discrete biological types.
- Profiles are circular descriptions; cross-block variance accounting is descriptive, not prediction.
- Sensitivity and method counterexamples must accompany any headline claim.
