# Example 1: Descriptive Statistics

## Research Scenario

A fitness instructor wants to analyze body composition measurements from a group of 20 college athletes to understand the typical values and variability in their fitness levels.

## Dataset

**Variable**: Body Fat Percentage (%)

**Data** (n=20):
```
12.5, 15.2, 14.8, 13.1, 16.3, 14.5, 15.8, 13.7, 14.2, 15.5,
13.9, 14.6, 15.1, 16.0, 14.3, 13.5, 15.7, 14.9, 13.2, 14.8
```

## Statistical Analysis

### Step 1: Organize the Data

First, arrange the data in ascending order:
```
12.5, 13.1, 13.2, 13.5, 13.7, 13.9, 14.2, 14.3, 14.5, 14.6,
14.8, 14.8, 14.9, 15.1, 15.2, 15.5, 15.7, 15.8, 16.0, 16.3
```

### Step 2: Calculate Measures of Central Tendency

**Mean (Average)**
- Formula: Sum of all values / Number of values
- Calculation: (12.5 + 15.2 + ... + 14.8) / 20
- **Mean = 14.52%**

**Median (Middle Value)**
- Since n=20 (even), median is the average of the 10th and 11th values
- Values: 14.6 and 14.8
- **Median = (14.6 + 14.8) / 2 = 14.7%**

**Mode (Most Frequent Value)**
- The value 14.8 appears twice
- **Mode = 14.8%**

### Step 3: Calculate Measures of Variability

**Range**
- Formula: Maximum value - Minimum value
- **Range = 16.3 - 12.5 = 3.8%**

**Variance (s²)**
- Formula: Σ(x - mean)² / (n - 1)
- Steps:
  1. Subtract mean from each value: (12.5-14.52), (15.2-14.52), ...
  2. Square each difference: 4.08, 0.46, ...
  3. Sum all squared differences: 20.98
  4. Divide by (n-1): 20.98 / 19
- **Variance = 1.10%²**

**Standard Deviation (s)**
- Formula: √(Variance)
- **Standard Deviation = √1.10 = 1.05%**

### Step 4: Calculate Additional Descriptive Statistics

**Coefficient of Variation (CV)**
- Formula: (Standard Deviation / Mean) × 100%
- **CV = (1.05 / 14.52) × 100% = 7.23%**
- Interpretation: Low variability (CV < 15%)

**Quartiles**
- Q1 (25th percentile): 13.9%
- Q2 (50th percentile/Median): 14.7%
- Q3 (75th percentile): 15.3%

**Interquartile Range (IQR)**
- Formula: Q3 - Q1
- **IQR = 15.3 - 13.9 = 1.4%**

## Interpretation

1. **Central Tendency**: The average body fat percentage is 14.52%, with half of the athletes having values below 14.7% and half above.

2. **Variability**: The standard deviation of 1.05% indicates that most athletes' body fat percentages fall within about ±1% of the mean. This relatively low variability (CV = 7.23%) suggests the group is fairly homogeneous.

3. **Distribution**: Since the mean (14.52%) and median (14.7%) are very close, the distribution is approximately symmetric (not skewed).

4. **Range**: The data spans 3.8 percentage points, from 12.5% to 16.3%, which is a reasonable range for college athletes.

## Practical Application

These descriptive statistics help the fitness instructor to:
- Set realistic goals for athletes
- Identify outliers who may need special attention
- Track changes over time by comparing future measurements to these baseline values
- Communicate results to athletes and coaches

## Practice Problems

1. Calculate the mean and standard deviation for the following vertical jump heights (cm):
   ```
   45, 52, 48, 50, 47, 51, 49, 46, 53, 48
   ```

2. A researcher measures the 40-yard dash times (seconds) for 15 football players. The mean is 5.2 seconds with a standard deviation of 0.3 seconds. Calculate the coefficient of variation and interpret what it means.

3. Given the following reaction times (milliseconds): 
   ```
   245, 250, 248, 252, 247, 249, 251, 246, 253, 248
   ```
   Calculate: mean, median, mode, range, and standard deviation.

## Answers

**Problem 1:**
- Mean = 48.9 cm
- Standard Deviation = 2.51 cm

**Problem 2:**
- CV = (0.3 / 5.2) × 100% = 5.77%
- This low CV indicates very consistent performance times with little variability among players.

**Problem 3:**
- Mean = 248.9 ms
- Median = 248.5 ms
- Mode = 248 ms
- Range = 8 ms
- Standard Deviation = 2.47 ms
