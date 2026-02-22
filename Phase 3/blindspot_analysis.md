# Blind Spot Analysis (Member 3)

## Inputs
- `strategy_results.csv`: `Phase 3/outputs/strategy_results.csv`
- `min_change_summary.csv`: `Phase 3/outputs/min_change_summary.csv`
- Checkpoint: `Phase1/cifake_resnet18_final.pt`

## Grad-CAM Comparison Protocol
- For each target pair: Original, Just-before-flip, Flipped (if available).
- No true flips were present in M1/M2 outputs; the minimum-confidence stage was used as a near-success fallback for flip visualization.

## Target Selection
- Top `5` sample-strategy pairs ranked by flip flag, then max confidence drop from M1 traces.

## Attention Shift Summary
- `shifted_to_background`: **0**
- `collapsed`: **0**
- `mixed_shift`: **5**
- `stable_or_refocused`: **0**
- Mean center-focus change (flip - original): **-0.0158**
- Mean edge-focus change (flip - original): **-0.0098**

## Attack Correlation (How Attack Type Changes Attention)
- Strategy A (Spatial + Frequency): n=5, center_delta=-0.0158, edge_delta=-0.0098, shifted_bg=0, collapsed=0, mixed=5, stable=0

## Model Dependency Diagnosis
- mixed/unclear dependency: observed in **4** / 5 cases
- high-frequency artifacts: observed in **1** / 5 cases
- texture patterns: observed in **1** / 5 cases

## Case Findings
### 104 (3).jpg | FAKE | A_blur_freq
- Figure: `Phase 3/outputs/m3_gradcam/FAKE_104_3_.jpg_A_blur_freq.png`
- Original: `REAL` (0.872)
- Just-before-flip `blur0.5_freq0.15` -> `REAL` (0.846) | attention: `mixed_shift`
- Flipped stage not available in source outputs; fallback stage reused for comparison | attention: `mixed_shift`
- Dependency interpretation: `mixed/unclear dependency`

### 105 (2).jpg | FAKE | A_blur
- Figure: `Phase 3/outputs/m3_gradcam/FAKE_105_2_.jpg_A_blur.png`
- Original: `REAL` (0.841)
- Just-before-flip `blur_0.8` -> `REAL` (0.794) | attention: `mixed_shift`
- Flipped stage not available in source outputs; fallback stage reused for comparison | attention: `mixed_shift`
- Dependency interpretation: `texture patterns, high-frequency artifacts`

### 105 (3).jpg | FAKE | A_blur
- Figure: `Phase 3/outputs/m3_gradcam/FAKE_105_3_.jpg_A_blur.png`
- Original: `REAL` (0.867)
- Just-before-flip `blur_0.8` -> `REAL` (0.825) | attention: `mixed_shift`
- Flipped stage not available in source outputs; fallback stage reused for comparison | attention: `mixed_shift`
- Dependency interpretation: `mixed/unclear dependency`

### 104 (3).jpg | FAKE | A_blur
- Figure: `Phase 3/outputs/m3_gradcam/FAKE_104_3_.jpg_A_blur.png`
- Original: `REAL` (0.872)
- Just-before-flip `blur_0.8` -> `REAL` (0.829) | attention: `mixed_shift`
- Flipped stage not available in source outputs; fallback stage reused for comparison | attention: `mixed_shift`
- Dependency interpretation: `mixed/unclear dependency`

### 105.jpg | FAKE | A_blur
- Figure: `Phase 3/outputs/m3_gradcam/FAKE_105.jpg_A_blur.png`
- Original: `REAL` (0.847)
- Just-before-flip `blur_0.8` -> `REAL` (0.811) | attention: `mixed_shift`
- Flipped stage not available in source outputs; fallback stage reused for comparison | attention: `mixed_shift`
- Dependency interpretation: `mixed/unclear dependency`

## Recommendation Handoff (for Member 4)
- Texture/high-frequency dependency: add blur/frequency suppression augmentation and spectral regularization.
- Background cue dependency: add face-focused cropping/segmentation preprocessing.
- Color/contrast dependency: strengthen photometric augmentation and color jitter robustness.