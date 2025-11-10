# Example 2: Correlation Analysis

## Research Scenario

A sports scientist wants to determine if there is a relationship between upper body strength (measured by bench press 1RM in kg) and throwing velocity (measured in m/s) in baseball players.

## Research Question

Is there a significant correlation between bench press strength and throwing velocity?

## Dataset

Data from 12 collegiate baseball players:

| Player | Bench Press (kg) | Throwing Velocity (m/s) |
|--------|------------------|-------------------------|
| 1      | 80               | 35                      |
| 2      | 85               | 37                      |
| 3      | 75               | 33                      |
| 4      | 90               | 39                      |
| 5      | 95               | 40                      |
| 6      | 70               | 32                      |
| 7      | 88               | 38                      |
| 8      | 82               | 36                      |
| 9      | 92               | 39                      |
| 10     | 78               | 34                      |
| 11     | 86               | 37                      |
| 12     | 84               | 36                      |

## Statistical Analysis

### Step 1: Create a Scatter Plot (Conceptual)

Plot bench press (X-axis) vs. throwing velocity (Y-axis) to visualize the relationship.

**Observation**: The points should show an upward trend, suggesting a positive relationship.

### Step 2: Calculate the Pearson Correlation Coefficient (r)

**Formula:**
```
r = Σ[(x - x̄)(y - ȳ)] / √[Σ(x - x̄)² × Σ(y - ȳ)²]
```

**Calculations:**

1. **Calculate means:**
   - x̄ (mean bench press) = 1005 / 12 = 83.75 kg
   - ȳ (mean throwing velocity) = 436 / 12 = 36.33 m/s

2. **Calculate deviations and products:**

| Player | x    | y  | (x - x̄) | (y - ȳ) | (x - x̄)(y - ȳ) | (x - x̄)² | (y - ȳ)² |
|--------|------|----|---------|---------|--------------|---------|---------| 
| 1      | 80   | 35 | -3.75   | -1.33   | 4.99         | 14.06   | 1.77    |
| 2      | 85   | 37 | 1.25    | 0.67    | 0.84         | 1.56    | 0.45    |
| 3      | 75   | 33 | -8.75   | -3.33   | 29.14        | 76.56   | 11.09   |
| 4      | 90   | 39 | 6.25    | 2.67    | 16.69        | 39.06   | 7.13    |
| 5      | 95   | 40 | 11.25   | 3.67    | 41.29        | 126.56  | 13.47   |
| 6      | 70   | 32 | -13.75  | -4.33   | 59.54        | 189.06  | 18.75   |
| 7      | 88   | 38 | 4.25    | 1.67    | 7.10         | 18.06   | 2.79    |
| 8      | 82   | 36 | -1.75   | -0.33   | 0.58         | 3.06    | 0.11    |
| 9      | 92   | 39 | 8.25    | 2.67    | 22.03        | 68.06   | 7.13    |
| 10     | 78   | 34 | -5.75   | -2.33   | 13.40        | 33.06   | 5.43    |
| 11     | 86   | 37 | 2.25    | 0.67    | 1.51         | 5.06    | 0.45    |
| 12     | 84   | 36 | 0.25    | -0.33   | -0.08        | 0.06    | 0.11    |
| **Sum**|      |    |         |         | **197.03**   | **574.22**| **68.68** |

3. **Calculate r:**
```
r = 197.03 / √(574.22 × 68.68)
r = 197.03 / √39,430.07
r = 197.03 / 198.57
r = 0.992
```

**Pearson Correlation Coefficient: r = 0.99**

### Step 3: Interpret the Correlation

**Strength of Correlation:**
- |r| = 0.99 indicates a **very strong positive correlation**

**Direction:**
- Positive r means that as bench press strength increases, throwing velocity tends to increase

**Classification of correlation strength:**
- 0.00 to 0.29: Weak
- 0.30 to 0.49: Moderate
- 0.50 to 0.69: Strong
- 0.70 to 1.00: Very Strong

### Step 4: Calculate Coefficient of Determination (r²)

```
r² = (0.99)² = 0.98
```

**Interpretation**: 98% of the variance in throwing velocity can be explained by bench press strength.

### Step 5: Test for Significance

**Hypotheses:**
- H₀: ρ = 0 (no correlation in the population)
- H₁: ρ ≠ 0 (correlation exists in the population)

**Test statistic:**
```
t = r√(n-2) / √(1-r²)
t = 0.99√(12-2) / √(1-0.98)
t = 0.99 × 3.16 / √0.02
t = 3.13 / 0.14
t = 22.36
```

**Degrees of freedom:** df = n - 2 = 10

**Critical value** (α = 0.05, two-tailed, df = 10): t_critical = ±2.228

**Decision**: Since |t| = 22.36 > 2.228, we reject H₀.

**Conclusion**: There is a statistically significant positive correlation between bench press strength and throwing velocity (r = 0.99, p < 0.001).

## Interpretation for Practitioners

1. **Strong Relationship**: The extremely high correlation (r = 0.99) suggests that upper body strength is strongly associated with throwing velocity in these baseball players.

2. **Practical Implications**: 
   - Strength training, particularly exercises that increase bench press performance, may help improve throwing velocity
   - Players with lower bench press numbers might benefit from strength training programs
   - This could be used for talent identification and development

3. **Caution**: 
   - Correlation does not imply causation
   - Other factors (technique, biomechanics, genetics) also influence throwing velocity
   - The sample size is relatively small (n=12)

## Practice Problems

1. **Problem A**: Calculate the correlation coefficient for these data on leg strength (kg) and sprint time (seconds):
   ```
   Leg Strength: 150, 160, 145, 170, 155, 165, 142, 168, 158, 162
   Sprint Time:  12.5, 12.0, 13.0, 11.5, 12.3, 11.8, 13.2, 11.6, 12.1, 11.9
   ```

2. **Problem B**: If the correlation between hours of practice and free throw percentage is r = 0.65, what percentage of the variance in free throw percentage is explained by practice time?

3. **Problem C**: A researcher finds r = 0.45 between body mass index (BMI) and vertical jump height in a sample of 25 athletes. Calculate the t-statistic and determine if this correlation is significant at α = 0.05.

## Answers

**Problem A:**
- Expected: Negative correlation (as leg strength increases, sprint time decreases)
- r ≈ -0.92 (very strong negative correlation)

**Problem B:**
- r² = (0.65)² = 0.42 or 42%
- 42% of the variance in free throw percentage is explained by practice time

**Problem C:**
- t = 0.45√(25-2) / √(1-0.45²) = 0.45 × 4.80 / 0.893 = 2.42
- Critical value (df=23, α=0.05, two-tailed) ≈ 2.069
- Since 2.42 > 2.069, the correlation is statistically significant
