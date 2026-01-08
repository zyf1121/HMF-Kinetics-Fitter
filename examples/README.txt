# HMF Kinetics Fitting Tool - Example Datasets

## File Naming Convention

The example files follow a systematic naming convention:

### Version Numbers
- **v2** = Model WITHOUT surface adsorption (single-phase model)
  - Considers only bulk phase reactions
  - Faster computation, simpler model

- **v3** = Model WITH surface adsorption (two-phase model)
  - Considers both surface and bulk phase reactions
  - More accurate but computationally intensive
  - Includes adsorption/desorption rate constants

### Temperature Indicators
- **60** = WITH side products (humins formation)
  - Higher temperature experiments (60°C)
  - Includes humins as a product species
  - Additional rate constant: k_sidereaction (or kfe/kby)

- **10, 20, 40** = WITHOUT side products (no humins formation)
  - Lower temperature experiments (10°C, 20°C, 40°C)
  - Does not include humins in the reaction network

## Available Examples

| Folder | Model Type | Side Reaction | Temperature | Species Count | Rate Constants |
|--------|-----------|---------------|-------------|---------------|----------------|
| v2_10 | No adsorption | No | 10°C | 6 species | 13 parameters |
| v2_20 | No adsorption | No | 20°C | 6 species | 13 parameters |
| v2_40 | No adsorption | No | 40°C | 6 species | 13 parameters |
| v2_60 | No adsorption | Yes | 60°C | 7 species | 14 parameters |
| v3_10 | With adsorption | No | 10°C | 12 species | 25 parameters |
| v3_20 | With adsorption | No | 20°C | 12 species | 25 parameters |
| v3_40 | With adsorption | No | 40°C | 12 species | 25 parameters |
| v3_60 | With adsorption | Yes | 60°C | 13 species | 26 parameters |

## File Structure

Each example folder contains three files:

1. **vX_XX_INPUT.txt** - Configuration file
   - Model parameters (epochs, learning rate, regularization)
   - File paths for experimental data and initial rate constants

2. **exp_data_vX_XX.csv** - Experimental concentration data
   - Time series of concentration measurements
   - Columns: Time, HMF, HMFCA, DFF, FFCA, FDCA, DHMF [, Humins]

3. **initial_k_vX_XX.txt** - Initial rate constants
   - Starting values for optimization
   - All rate constant parameters (k1c, k2c, k3c, k1e, k2e, k0e, etc.)

## Which Example to Use?

### Choose based on your experimental data:

**Does your data include humins concentration?**
- YES → Use **60** version (v2_60 or v3_60)
- NO → Use **10** version (v2_10 or v3_10)

**Is surface adsorption significant in your system?**
- YES → Use **v3** version (v3_10 or v3_60)
- NO → Use **v2** version (v2_10 or v2_60)

### Quick Reference

```
v2_10  → 10°C, no adsorption, no side products
v2_20  → 20°C, no adsorption, no side products
v2_40  → 40°C, no adsorption, no side products
v2_60  → 60°C, no adsorption, with side products (humins)
v3_10  → 10°C, with adsorption, no side products
v3_20  → 20°C, with adsorption, no side products
v3_40  → 40°C, with adsorption, no side products
v3_60  → 60°C, with adsorption, with side products (humins)
```

## Notes

- The "10", "20", "40", and "60" in filenames refer to experimental temperatures (10°C, 20°C, 40°C, 60°C)
- You can use these examples as templates for your own data
- Adjust initial rate constants in the *_k*.txt files as needed
- The model will automatically adjust based on your experimental time range
- **Only 60°C datasets include side products (humins formation)**
- 10°C, 20°C, and 40°C datasets do NOT include humins

---

For more information, see the main README_EN.md file.
