# EEG Pre-Aura Detection — Preliminary Signal Characterization Study
## Overview
Migraine aura often precedes severe migraine episodes, but patients often have little to no actionable advance warning. Its downstream clinical problem is well defined, but it remains unclear whether non-invasive EEG contains any detectable pre-event signal at all that could plausibly support advance warning. This is a foundational feasibility study. I am not attempting to build a clinical system or make medical claims. Rather, I am asking a simple and fundamental question: do interpretable EEG features exhibit statistically detectable changes in the period preceding a labeled neurological event, relative to baseline? The goal is to establish whether a signal exists under minimal assumptions before pursuing more complex models, datasets or clinical integrations.

## Problem Framing 
EEG-based prediction of neurological events is challenging due to low signal to noise ratios, high inter-subject variability and imprecise and unreliable event labeling. In migraine specifically, aura onset is subjective and can be difficult to timestamp precisely. As opposed to assuming predictive capability, this work starts one level upstream and probes the hypothesis that pre-event neural instability or spectral shifts may be weakly observable in time-frequency representations prior to the debut of an event window. 
This intentionally focuses on:
1. Signal existence, not performance
2. Interpretable features, not black-box models
3. Falsifiable results, including null findings
   
## Data 
Current implementation uses open EEG datasets to validate the end-to-end analysis pipeline. "Pre-event" windows are defined as fixed intervals preceding a labeled neurological event, with baseline windows sampled from non-event periods within the same recording. This setup serves as a proxy task rather than a migraine-specific dataset. 
Key limitations of the data:
1. Events are not migraine aura-specific
2. Labeling precision varies across datasets
3. Recordings are not longitudinal per patient

Despite this, the proxy task preserves several properties relevant to migraine aura detection:
1. Temporal proximity to a neurological transition
2. Gradual pre-event dynamics as opposed to abrupt onset
3. Non-stationary relative to baseline

## Methods
This pipeline focuses on basic, interpretable EEG features, including:
1. Band-limited power across standard frequency ranges
2. Time-frequency representations
3. Simple statistical comparisons between baseline and pre-event windows
The emphasis is on detecting consistent directional shifts or variance changes, not on optimizing classification accuracy. All analysis is intentionally conservative and avoids leakage across subjects or time.

## Results (Exploratory)

Preliminary results suggest that:
1. Any detectable pre-event signal is weak and highly variable
2. Group-level trends occasionally emerge in specific frequency bands
3. Effects are unstable under strict subject-wise validation

These findings are consistent with prior literature on EEG event prediction and reinforce the difficulty of the problem. Importantly, they do not rule out the existence of a usable signal under better data conditions, but they do set realistic expectations about effect size and noise. Plots and intermediate outputs are available in the results/ directory.

## Limitations

This study has several fundamental limitations:
1. Proxy datasets are not migraine-specific
2. Aura onset timing is not represented
3. EEG signal quality varies significantly
4. Inter-subject variability dominates weak effects
5. No personalization or longitudinal adaptation is applied

As such, these results should not be interpreted as predictive performance or clinical evidence.

## Next Steps

With access to improved data or collaborators, the next technical steps would include:
1. Migraine-specific EEG or ambulatory EEG collection
2. Patient-reported aura timestamps for finer temporal alignment
3. Longitudinal, within-subject modeling to reduce variability
4. Personalized baselines rather than population-level aggregation
5. Exploration of stability metrics (entropy, synchrony) as opposed to raw power alone

The long-term objective is to determine whether personalized, continuous neural monitoring could provide meaningful early warning for migraine sufferers, starting from a rigorously validated signal foundation.

## Status

This repository represents an early technical probe intended to test feasibility, surface constraints, and inform whether further investment—technical or clinical—is justified.
