# Example 3: Independent Samples T-Test

## Research Scenario

A strength and conditioning coach wants to compare two different training methods for improving vertical jump performance. Twenty athletes are randomly assigned to either a plyometric training group (n=10) or a traditional weight training group (n=10). After 8 weeks, vertical jump height (in cm) is measured.

## Research Question

Is there a significant difference in vertical jump height between athletes who completed plyometric training versus traditional weight training?

## Dataset

**Plyometric Training Group (cm):**
```
52, 55, 53, 57, 54, 56, 55, 58, 54, 56
```

**Traditional Weight Training Group (cm):**
```
48, 50, 49, 51, 47, 52, 49, 50, 48, 51
```

## Statistical Analysis

### Step 1: State Hypotheses

- **H₀** (Null Hypothesis): μ₁ = μ₂ (No difference in mean vertical jump height between groups)
- **H₁** (Alternative Hypothesis): μ₁ ≠ μ₂ (There is a difference in mean vertical jump height)
- **Significance level**: α = 0.05 (two-tailed test)

### Step 2: Calculate Descriptive Statistics

**Plyometric Training Group:**
- n₁ = 10
- Sum = 550 cm
- Mean (x̄₁) = 550 / 10 = **55.0 cm**
- Variance calculation:
  - Squared deviations: 9, 0, 4, 4, 1, 1, 0, 9, 1, 1
  - Sum of squared deviations = 30
  - s₁² = 30 / 9 = 3.33
- Standard deviation (s₁) = √3.33 = **1.83 cm**

**Traditional Weight Training Group:**
- n₂ = 10
- Sum = 495 cm
- Mean (x̄₂) = 495 / 10 = **49.5 cm**
- Variance calculation:
  - Squared deviations: 2.25, 0.25, 0.25, 2.25, 6.25, 6.25, 0.25, 0.25, 2.25, 2.25
  - Sum of squared deviations = 22.5
  - s₂² = 22.5 / 9 = 2.5
- Standard deviation (s₂) = √2.5 = **1.58 cm**

### Step 3: Check Assumptions

1. **Independence**: Groups are independent (different athletes in each group) ✓
2. **Normality**: With n=10 per group, we assume approximate normality (in practice, would check with plots) ✓
3. **Homogeneity of Variance**: Test using F-test
   - F = s₁² / s₂² = 3.33 / 2.5 = 1.33
   - Critical F (df₁=9, df₂=9, α=0.05) = 3.18
   - Since 1.33 < 3.18, variances are not significantly different ✓

**Conclusion**: Use pooled variance t-test

### Step 4: Calculate Pooled Variance

```
s²ₚ = [(n₁-1)s₁² + (n₂-1)s₂²] / (n₁ + n₂ - 2)
s²ₚ = [(10-1)(3.33) + (10-1)(2.5)] / (10 + 10 - 2)
s²ₚ = [29.97 + 22.5] / 18
s²ₚ = 52.47 / 18
s²ₚ = 2.915
```

Pooled standard deviation: sₚ = √2.915 = 1.71 cm

### Step 5: Calculate Standard Error

```
SE = sₚ × √(1/n₁ + 1/n₂)
SE = 1.71 × √(1/10 + 1/10)
SE = 1.71 × √0.2
SE = 1.71 × 0.447
SE = 0.765 cm
```

### Step 6: Calculate T-Statistic

```
t = (x̄₁ - x̄₂) / SE
t = (55.0 - 49.5) / 0.765
t = 5.5 / 0.765
t = 7.19
```

### Step 7: Determine Critical Value and Make Decision

- **Degrees of freedom**: df = n₁ + n₂ - 2 = 10 + 10 - 2 = 18
- **Critical value** (α = 0.05, two-tailed): t_critical = ±2.101
- **Calculated t-statistic**: t = 7.19

**Decision**: Since |t| = 7.19 > 2.101, we **reject the null hypothesis**.

**P-value**: p < 0.001 (highly significant)

### Step 8: Calculate Effect Size (Cohen's d)

```
d = (x̄₁ - x̄₂) / sₚ
d = (55.0 - 49.5) / 1.71
d = 5.5 / 1.71
d = 3.22
```

**Interpretation of effect size:**
- Small effect: d = 0.2
- Medium effect: d = 0.5
- Large effect: d = 0.8
- **Very large effect**: d = 3.22

### Step 9: Calculate 95% Confidence Interval

```
CI = (x̄₁ - x̄₂) ± (t_critical × SE)
CI = 5.5 ± (2.101 × 0.765)
CI = 5.5 ± 1.61
CI = [3.89, 7.11]
```

**Interpretation**: We are 95% confident that the true difference in mean vertical jump height between the plyometric and traditional training groups is between 3.89 cm and 7.11 cm.

## Results Summary

**Statistical Results:**
- Plyometric Training: M = 55.0 cm, SD = 1.83 cm
- Traditional Weight Training: M = 49.5 cm, SD = 1.58 cm
- Independent t-test: t(18) = 7.19, p < 0.001, d = 3.22
- 95% CI: [3.89, 7.11]

**Conclusion**: The plyometric training group demonstrated significantly higher vertical jump heights compared to the traditional weight training group, with a very large effect size. The difference of 5.5 cm is both statistically significant and practically meaningful for athletic performance.

## Practical Implications

1. **Training Recommendations**: Plyometric training appears to be more effective than traditional weight training for improving vertical jump performance in this population.

2. **Effect Size**: The very large effect size (d = 3.22) indicates not just statistical significance, but substantial practical significance.

3. **Application**: Coaches working with athletes who need to improve vertical jump (basketball, volleyball) should consider incorporating plyometric training.

4. **Limitations**: 
   - Sample size is modest (n=10 per group)
   - Study duration is 8 weeks; long-term effects unknown
   - Participant characteristics not specified (age, training history)

## Practice Problems

1. **Problem A**: Two groups of runners complete different training programs. Group A (n=12) has mean finishing times of 45.5 minutes (SD=3.2) for a 10K race. Group B (n=14) has mean finishing times of 42.8 minutes (SD=2.9). Conduct an independent t-test at α=0.05.

2. **Problem B**: Calculate Cohen's d for the following data:
   - Group 1: M=75 kg, SD=8 kg
   - Group 2: M=68 kg, SD=7 kg
   - Pooled SD=7.5 kg

3. **Problem C**: A researcher obtains t(24)=2.35 for an independent samples t-test. Using α=0.05 (two-tailed), is this result significant? What is the approximate p-value?

## Answers

**Problem A:**
- Pooled variance = 9.51
- SE = 1.22
- t = 2.21
- Critical value (df=24) = 2.064
- Result: Significant (reject H₀); Group B is significantly faster

**Problem B:**
- Cohen's d = (75-68)/7.5 = 0.93
- Interpretation: Large effect size

**Problem C:**
- Critical value (df=24, α=0.05, two-tailed) = 2.064
- Since 2.35 > 2.064, result is significant
- Approximate p-value: 0.02 < p < 0.05
