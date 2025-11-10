# Example 5: Linear Regression Analysis

## Research Scenario

A sports scientist wants to predict marathon finishing time (in minutes) based on weekly training mileage (in miles per week). Data is collected from 10 amateur marathon runners.

## Research Question

Can weekly training mileage predict marathon finishing time? What is the nature of this relationship?

## Dataset

*Note: The `marathon_training.csv` file in the data directory contains data from 15 runners with additional variables (age, experience, long runs, speed workouts). For this example, we use the first 10 runners and focus on weekly mileage and marathon time.*

| Runner | Weekly Training Miles (X) | Marathon Time in Minutes (Y) |
|--------|---------------------------|------------------------------|
| 1      | 30                        | 240                          |
| 2      | 35                        | 230                          |
| 3      | 40                        | 215                          |
| 4      | 25                        | 255                          |
| 5      | 45                        | 205                          |
| 6      | 50                        | 195                          |
| 7      | 38                        | 220                          |
| 8      | 42                        | 210                          |
| 9      | 32                        | 235                          |
| 10     | 48                        | 200                          |

## Statistical Analysis

### Step 1: Create Scatter Plot (Conceptual)

Plot training miles (X-axis) vs. marathon time (Y-axis). 

**Expected pattern**: Negative linear relationship (more training → faster times → lower minutes)

### Step 2: Calculate Basic Statistics

**For X (Training Miles):**
- Sum of X = 385
- Mean (x̄) = 385 / 10 = **38.5 miles**
- Sum of X² = 15,473
- Sum of (X - x̄)² = 15,473 - (385²/10) = 15,473 - 14,822.5 = **650.5**

**For Y (Marathon Time):**
- Sum of Y = 2,205
- Mean (ȳ) = 2,205 / 10 = **220.5 minutes**
- Sum of Y² = 489,725
- Sum of (Y - ȳ)² = 489,725 - (2,205²/10) = 489,725 - 486,202.5 = **3,522.5**

**For XY:**
- Sum of XY = 83,840

### Step 3: Calculate Regression Slope (b)

```
b = [Σ(XY) - (ΣX)(ΣY)/n] / [ΣX² - (ΣX)²/n]

Numerator:
Σ(XY) - (ΣX)(ΣY)/n = 83,840 - (385)(2,205)/10
                     = 83,840 - 848,925/10
                     = 83,840 - 84,892.5
                     = -1,052.5

Denominator:
ΣX² - (ΣX)²/n = 15,473 - (385)²/10
               = 15,473 - 14,822.5
               = 650.5

b = -1,052.5 / 650.5
b = -1.62 minutes per mile
```

**Interpretation**: For each additional mile of weekly training, marathon time decreases by approximately 1.62 minutes.

### Step 4: Calculate Regression Intercept (a)

```
a = ȳ - b(x̄)
a = 220.5 - (-1.62)(38.5)
a = 220.5 + 62.37
a = 282.87 minutes
```

### Step 5: Write the Regression Equation

```
Ŷ = a + bX
Ŷ = 282.87 - 1.62X
```

Where:
- Ŷ = Predicted marathon time (minutes)
- X = Weekly training miles

**Example prediction**: If a runner trains 40 miles per week:
```
Ŷ = 282.87 - 1.62(40)
Ŷ = 282.87 - 64.8
Ŷ = 218.07 minutes (approximately 3 hours 38 minutes)
```

### Step 6: Calculate Correlation Coefficient (r)

```
r = [Σ(XY) - (ΣX)(ΣY)/n] / √{[ΣX² - (ΣX)²/n][ΣY² - (ΣY)²/n]}

r = -1,052.5 / √(650.5 × 3,522.5)
r = -1,052.5 / √2,291,386.25
r = -1,052.5 / 1,513.73
r = -0.695
```

**Interpretation**: Strong negative correlation (as training increases, time decreases)

### Step 7: Calculate Coefficient of Determination (R²)

```
R² = r²
R² = (-0.695)²
R² = 0.483 or 48.3%
```

**Interpretation**: 48.3% of the variance in marathon finishing time can be explained by weekly training mileage.

### Step 8: Calculate Standard Error of Estimate (SEE)

```
SEE = √[Σ(Y - Ŷ)² / (n - 2)]

Or using: SEE = √[(1 - R²) × Σ(Y - ȳ)² / (n - 2)]

SEE = √[(1 - 0.483) × 3,522.5 / 8]
SEE = √[0.517 × 3,522.5 / 8]
SEE = √[1,821.13 / 8]
SEE = √227.64
SEE = 15.09 minutes
```

**Interpretation**: The typical prediction error is about 15 minutes.

### Step 9: Test Significance of Regression

**Hypotheses:**
- H₀: β = 0 (no linear relationship)
- H₁: β ≠ 0 (linear relationship exists)

**Test statistic:**
```
t = b / SE_b

Where SE_b = SEE / √[Σ(X - x̄)²]
SE_b = 15.09 / √650.5
SE_b = 15.09 / 25.50
SE_b = 0.592

t = -1.62 / 0.592
t = -2.74
```

**Degrees of freedom**: df = n - 2 = 10 - 2 = 8

**Critical value** (α = 0.05, two-tailed): t_critical = ±2.306

**Decision**: Since |t| = 2.74 > 2.306, we **reject H₀**.

**P-value**: p < 0.05 (statistically significant)

**Conclusion**: Weekly training mileage is a significant predictor of marathon finishing time.

### Step 10: Calculate 95% Confidence Interval for Slope

```
CI = b ± (t_critical × SE_b)
CI = -1.62 ± (2.306 × 0.592)
CI = -1.62 ± 1.37
CI = [-2.99, -0.25]
```

**Interpretation**: We are 95% confident that for each additional mile of weekly training, marathon time decreases between 0.25 and 2.99 minutes.

### Step 11: Create Residual Analysis Table

| Runner | X   | Y (Actual) | Ŷ (Predicted) | Residual (Y - Ŷ) |
|--------|-----|------------|---------------|------------------|
| 1      | 30  | 240        | 234.27        | 5.73             |
| 2      | 35  | 230        | 226.17        | 3.83             |
| 3      | 40  | 215        | 218.07        | -3.07            |
| 4      | 25  | 255        | 242.37        | 12.63            |
| 5      | 45  | 205        | 209.97        | -4.97            |
| 6      | 50  | 195        | 201.87        | -6.87            |
| 7      | 38  | 220        | 221.31        | -1.31            |
| 8      | 42  | 210        | 214.83        | -4.83            |
| 9      | 32  | 235        | 231.03        | 3.97             |
| 10     | 48  | 200        | 205.11        | -5.11            |

**Residual check**: Sum of residuals ≈ 0 ✓

## Results Summary

A simple linear regression was performed to predict marathon finishing time from weekly training mileage. The regression equation was:

**Marathon Time = 282.87 - 1.62 × (Training Miles)**

The model was statistically significant, t(8) = -2.74, p < 0.05, and explained 48.3% of the variance in marathon time (R² = 0.483). For each additional mile of weekly training, marathon finishing time decreased by 1.62 minutes (95% CI: [-2.99, -0.25]).

## Practical Implications

1. **Training Effect**: Higher training volume is associated with faster marathon times, but the relationship is moderate (R² = 0.48), suggesting other factors also play important roles.

2. **Prediction Tool**: Coaches can use this equation to set realistic time goals based on training volume:
   - 30 miles/week → ~234 minutes (3:54)
   - 40 miles/week → ~218 minutes (3:38)
   - 50 miles/week → ~202 minutes (3:22)

3. **Limitations**:
   - 52% of variance unexplained (training quality, genetics, nutrition, etc.)
   - Small sample size (n=10)
   - Limited to the range of training miles observed (25-50 miles/week)
   - Cross-sectional design (not causal)

4. **Beyond Training Volume**: Other important factors to consider:
   - Long run distance
   - Speed work intensity
   - Recovery
   - Prior running experience
   - Age and physiology

## Practice Problems

1. **Problem A**: Given the regression equation: Ŷ = 75 - 0.5X, where Y is resting heart rate and X is weekly cardio hours:
   - Interpret the slope and intercept
   - Predict resting heart rate for someone who does 10 hours of cardio per week

2. **Problem B**: A regression analysis yields:
   - b = 2.3 kg/cm
   - SE_b = 0.8
   - n = 15
   - Conduct a hypothesis test at α = 0.05 to determine if the slope is significant

3. **Problem C**: If R² = 0.64 in a regression predicting vertical jump from squat strength:
   - What percentage of variance is explained?
   - What is the correlation coefficient (assume positive relationship)?
   - What percentage of variance is unexplained?

## Answers

**Problem A:**
- Slope: For each additional hour of cardio per week, resting heart rate decreases by 0.5 beats per minute
- Intercept: Predicted resting heart rate with no cardio exercise is 75 bpm
- Prediction: Ŷ = 75 - 0.5(10) = 75 - 5 = 70 bpm

**Problem B:**
- t = 2.3 / 0.8 = 2.875
- df = 15 - 2 = 13
- Critical value (α=0.05, two-tailed) ≈ 2.160
- Since 2.875 > 2.160, the slope is statistically significant (p < 0.05)

**Problem C:**
- Explained variance: 64%
- Correlation coefficient: r = √0.64 = 0.80 (strong positive)
- Unexplained variance: 100% - 64% = 36%
