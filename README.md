# Yield Curve Construction with PCA

Identify the small number of latent factors that explain movements in the U.S. Treasury yield curve, then reconstruct the curve using those factors.

## Problem

The U.S. Treasury yield curve contains highly correlated yields across maturities. Rather than treating nine tenors as independent variables, this project asks:

**How many underlying factors are needed to explain most of the variation in the curve?**

## Approach

1. **Data collection** - pulled daily Treasury Constant Maturity Rates for nine maturities, from 1 month to 30 years, directly from the Federal Reserve Bank of St. Louis (FRED) for January 2000 to December 2024.
2. **Data quality and EDA** - inspected missing observations, summary statistics, yield-curve movements, and cross-maturity correlations.
3. **Standardization** - standardized each tenor before PCA so differences in scale did not mechanically dominate the analysis.
4. **PCA** - extracted principal components and evaluated their individual and cumulative explained variance.
5. **Factor interpretation** - examined PCA loading profiles and interpreted the leading factors as level, slope, and curvature movements.
6. **Reconstruction** - reconstructed the original yield curve using only the first three components and compared the reconstructed yields with the original series.

## Results

The first three principal components explain **more than 99.5%** of the variation in the standardized yield curve.

The leading components have economically interpretable loading patterns associated with:

- **Level** - parallel shifts across maturities
- **Slope** - steepening and flattening movements
- **Curvature** - changes in the shape of the curve around intermediate maturities

Using only these three components produces a close reconstruction of the original yield curve while reducing the dimensionality from nine maturities to three factors.

## Tech Stack

Python · pandas · scikit-learn · PCA · StandardScaler · pandas-datareader · FRED API · matplotlib · seaborn

## Files

- `Yield_Curve_Construction.ipynb` - full data collection, PCA analysis, interpretation, and reconstruction workflow
