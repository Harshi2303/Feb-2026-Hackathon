# Final Recommendation (Member 4)

## Inputs Used
- M1 baseline attacks: `Phase 3/outputs/strategy_results.csv`
- M2 minimal-change summary: `Phase 3/outputs/min_change_summary.csv`
- M3 blindspot report: `Phase 3/outputs/blindspot_analysis.md`
- M3 attack correlation: `Phase 3/outputs/m3_attack_correlation.csv`

## Chosen Defense Strategy
- Primary vulnerability from M3: `Strategy A (Spatial + Frequency)`
- Implemented defense: `strategy_a_robust_aug`
- Applied robust transform with Gaussian blur + random grayscale + mild color jitter to reduce texture/high-frequency over-reliance.

## Prototype Training
- Checkpoint loaded: `Phase1/cifake_resnet18_final.pt`
- Fine-tune epochs: `3` (prototype setting)
- Train samples used: `4000`
- Val samples used: `1000`
- Robust model saved: `Phase 3/outputs/robust_model_prototype.pt`

## Stress-Test Comparison (Same Attack Families)
- Flip_Rate_Strategy_A: before=0.045000, after=0.155000, delta=+0.110000
- Flip_Rate_Strategy_B: before=0.090000, after=0.075000, delta=-0.015000
- Flip_Rate_Overall: before=0.067500, after=0.115000, delta=+0.047500
- Mean_Confidence_Drop_A: before=-0.029532, after=-0.010307, delta=+0.019225
- Mean_Confidence_Drop_B: before=0.029154, after=-0.009184, delta=-0.038338
- MeanAbsDelta_p_fake_All_Attacks: before=0.046534, after=0.072111, delta=+0.025577

## Deliverables
- `robust_model_prototype.pt`: `Phase 3/outputs/robust_model_prototype.pt`
- `robustness_comparison.csv`: `Phase 3/outputs/robustness_comparison.csv`
- `final_recommendation.md`: `Phase 3/outputs/final_recommendation.md`