# Example 4: One-Way ANOVA (Analysis of Variance)

## Research Scenario

A researcher wants to compare the effectiveness of three different exercise programs on improving flexibility (measured by sit-and-reach test in cm). Fifteen participants are randomly assigned to one of three groups: yoga (n=5), static stretching (n=5), or dynamic stretching (n=5). After 6 weeks, flexibility is measured.

## Research Question

Is there a significant difference in flexibility improvements among the three exercise programs?

## Dataset

*Note: The `exercise_programs.csv` file in the data directory contains data from 20 participants including a Control group. For this example, we use the first 5 participants from each of the three treatment groups (yoga, static stretching, and dynamic stretching).*

**Yoga Group (cm):**
```
35, 38, 36, 37, 39
```

**Static Stretching Group (cm):**
```
32, 30, 33, 31, 34
```

**Dynamic Stretching Group (cm):**
```
28, 30, 29, 27, 31
```

## Statistical Analysis

### Step 1: State Hypotheses

- **H₀** (Null Hypothesis): μ₁ = μ₂ = μ₃ (All group means are equal)
- **H₁** (Alternative Hypothesis): At least one group mean is different
- **Significance level**: α = 0.05

### Step 2: Calculate Descriptive Statistics

**Yoga Group:**
- n₁ = 5
- Sum = 185
- Mean (x̄₁) = 185 / 5 = **37.0 cm**
- Squared deviations: 4, 1, 1, 0, 4
- SS₁ = 10

**Static Stretching Group:**
- n₂ = 5
- Sum = 160
- Mean (x̄₂) = 160 / 5 = **32.0 cm**
- Squared deviations: 0, 4, 1, 1, 4
- SS₂ = 10

**Dynamic Stretching Group:**
- n₃ = 5
- Sum = 145
- Mean (x̄₃) = 145 / 5 = **29.0 cm**
- Squared deviations: 1, 1, 0, 4, 4
- SS₃ = 10

**Grand Mean:**
```
x̄_grand = (185 + 160 + 145) / 15
x̄_grand = 490 / 15 = 32.67 cm
```

### Step 3: Calculate Sum of Squares

**Total Sum of Squares (SS_total):**

Method 1 - Direct calculation from grand mean:
- For each value, calculate (x - x̄_grand)²
- Yoga: (35-32.67)² + (38-32.67)² + (36-32.67)² + (37-32.67)² + (39-32.67)²
       = 5.43 + 28.41 + 11.09 + 18.75 + 40.15 = 103.83
- Static: (32-32.67)² + (30-32.67)² + (33-32.67)² + (31-32.67)² + (34-32.67)²
        = 0.45 + 7.13 + 0.11 + 2.79 + 1.77 = 12.25
- Dynamic: (28-32.67)² + (30-32.67)² + (29-32.67)² + (27-32.67)² + (31-32.67)²
         = 21.81 + 7.13 + 13.45 + 32.13 + 2.79 = 77.31

**SS_total = 103.83 + 12.25 + 77.31 = 193.39**

Or using the formula: SS_total = SS_within + SS_between

**Between Groups Sum of Squares (SS_between):**
```
SS_between = Σ[nᵢ(x̄ᵢ - x̄_grand)²]
SS_between = 5(37.0 - 32.67)² + 5(32.0 - 32.67)² + 5(29.0 - 32.67)²
SS_between = 5(4.33)² + 5(-0.67)² + 5(-3.67)²
SS_between = 5(18.75) + 5(0.45) + 5(13.47)
SS_between = 93.75 + 2.25 + 67.35
SS_between = 163.35
```

**Within Groups Sum of Squares (SS_within):**
```
SS_within = SS₁ + SS₂ + SS₃
SS_within = 10 + 10 + 10
SS_within = 30
```

**Verification:**
```
SS_total = SS_between + SS_within
193.39 ≈ 163.35 + 30 = 193.35 ✓
```
(Small difference due to rounding)

### Step 4: Calculate Degrees of Freedom

- **df_between** = k - 1 = 3 - 1 = **2** (k = number of groups)
- **df_within** = N - k = 15 - 3 = **12** (N = total sample size)
- **df_total** = N - 1 = 15 - 1 = **14**

### Step 5: Calculate Mean Squares

```
MS_between = SS_between / df_between
MS_between = 163.35 / 2 = 81.68

MS_within = SS_within / df_within
MS_within = 30 / 12 = 2.5
```

### Step 6: Calculate F-Statistic

```
F = MS_between / MS_within
F = 81.68 / 2.5
F = 32.67
```

### Step 7: Determine Critical Value and Make Decision

- **Critical F-value** (α = 0.05, df₁ = 2, df₂ = 12): F_critical = 3.89
- **Calculated F-statistic**: F = 32.67

**Decision**: Since F = 32.67 > 3.89, we **reject the null hypothesis**.

**P-value**: p < 0.001 (highly significant)

### Step 8: ANOVA Summary Table

| Source of Variation | SS      | df  | MS    | F     | P-value |
|---------------------|---------|-----|-------|-------|---------|
| Between Groups      | 163.35  | 2   | 81.68 | 32.67 | <0.001  |
| Within Groups       | 30.00   | 12  | 2.50  |       |         |
| Total              | 193.35  | 14  |       |       |         |

### Step 9: Effect Size (Eta Squared, η²)

```
η² = SS_between / SS_total
η² = 163.35 / 193.35
η² = 0.845 or 84.5%
```

**Interpretation**: 84.5% of the variance in flexibility is explained by the exercise program type. This is a **very large effect**.

Effect size guidelines for η²:
- Small: 0.01
- Medium: 0.06
- Large: 0.14

## Post-Hoc Tests (Tukey HSD)

Since the ANOVA is significant, we need to determine which specific groups differ.

### Tukey HSD Formula:

```
HSD = q × √(MS_within / n)
```

Where q is the studentized range statistic (α = 0.05, k = 3, df = 12): q = 3.77

```
HSD = 3.77 × √(2.5 / 5)
HSD = 3.77 × √0.5
HSD = 3.77 × 0.707
HSD = 2.67 cm
```

### Pairwise Comparisons:

| Comparison                  | Mean Difference | Significant? |
|-----------------------------|-----------------|--------------|
| Yoga vs. Static            | 37.0 - 32.0 = 5.0 | Yes (5.0 > 2.67) |
| Yoga vs. Dynamic           | 37.0 - 29.0 = 8.0 | Yes (8.0 > 2.67) |
| Static vs. Dynamic         | 32.0 - 29.0 = 3.0 | Yes (3.0 > 2.67) |

**Conclusion**: All three groups are significantly different from each other.

**Ranking** (from highest to lowest flexibility):
1. Yoga (M = 37.0 cm)
2. Static Stretching (M = 32.0 cm)
3. Dynamic Stretching (M = 29.0 cm)

## Results Summary

A one-way ANOVA was conducted to compare the effects of three exercise programs (yoga, static stretching, dynamic stretching) on flexibility. The analysis revealed a significant difference among the groups, F(2, 12) = 32.67, p < 0.001, η² = 0.845. 

Tukey HSD post-hoc tests indicated that all three programs produced significantly different results:
- Yoga (M = 37.0, SD = 1.58) resulted in greater flexibility than static stretching (M = 32.0, SD = 1.58)
- Static stretching resulted in greater flexibility than dynamic stretching (M = 29.0, SD = 1.58)
- Yoga resulted in greater flexibility than dynamic stretching

## Practical Implications

1. **Most Effective Program**: Yoga was the most effective for improving flexibility in this study.

2. **All Programs Differ**: Each program produced distinct results, suggesting they work through different mechanisms.

3. **Recommendations**: For maximum flexibility gains, yoga appears to be the optimal choice, followed by static stretching, with dynamic stretching being least effective for this outcome.

4. **Considerations**:
   - Dynamic stretching may have other benefits (e.g., power, preparation for activity)
   - Sample size is relatively small
   - Individual responses may vary

## Practice Problems

1. **Problem A**: Calculate the F-statistic for the following data on heart rate recovery (beats):
   - Group 1 (n=4): 25, 28, 26, 27 (Mean = 26.5)
   - Group 2 (n=4): 22, 24, 23, 21 (Mean = 22.5)
   - Group 3 (n=4): 18, 20, 19, 19 (Mean = 19.0)

2. **Problem B**: If SS_between = 120, SS_within = 180, with 4 groups and 20 total participants, calculate F and determine if it is significant at α = 0.05.

3. **Problem C**: An ANOVA yields F(3, 36) = 4.25. Using α = 0.05, is this result significant? What does this tell you?

## Answers

**Problem A:**
- SS_between = 4(26.5-22.67)² + 4(22.5-22.67)² + 4(19.0-22.67)² = 112.67
- SS_within = 6 + 10 + 2 = 18
- MS_between = 112.67/2 = 56.34
- MS_within = 18/9 = 2.0
- F = 56.34/2.0 = 28.17
- Critical F(2,9) ≈ 4.26; Result: Highly significant

**Problem B:**
- MS_between = 120/3 = 40
- MS_within = 180/16 = 11.25
- F = 40/11.25 = 3.56
- Critical F(3,16) ≈ 3.24
- Result: Significant (reject H₀)

**Problem C:**
- Critical F(3,36) ≈ 2.87
- Since 4.25 > 2.87, result is significant
- Conclusion: At least one group mean differs from the others; conduct post-hoc tests to determine which specific groups differ
