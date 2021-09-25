# Concept Explanation

---

### Collateral Assets

Decentralized on-chain native assets, such as ETH and NToken, are used to generate parallel assets.

### Underlying Assets

The digital asset of the target in the parallel universe.

### Parallel Assets

The intrinsic value of the underlying asset is anchored year-on-year, and it is mortgaged by agreement.

### Collateral Rate

When the initial coin is minted, users enter mortgage assets to generate parallel assets. The mortgage rate is the ratio of unit mortgage assets to the price of mortgage assets, and the mortgage rate is less than 1.

### Liquidation Line

When the price of mortgaged assets drops, the liquidation line and the mortgage rate conform to a certain relationship, and the liquidation line is generally 10%-20% higher than the mortgage rate.

### Debt Position

After the mint user enters the mortgage assets into the contract, a debt warehouse for keeping the mortgage assets is generated. When the user redeems the mortgage assets in the debt warehouse, the debt warehouse ends. If the mortgage assets are increased or mortgaged again, the same debt warehouse is shared.

### Insurance Capital Pool

Used to ensure that the exchange relationship always maintains a 1:1 ratio when liquidation occurs, and the insurance fund pool needs to be entered into USDT. Anyone can use a digital asset to enter the insurance fund pool to generate a parallel asset, or return a parallel asset to the pool in exchange for a digital asset.

### Oracle

Call NEST Protocol to provide on-chain price information for mortgage assets.

### Stability Fee

Based on the stability fee designed by the mortgage rate, each debt warehouse must pay the stability fee according to the difference between the settlement line and the current price and the time period when adding mortgage, minting new coins, redeeming and liquidating.

### Minter

A user who mortgages for parallel assets.

### Insurer

The liquidity provider of the insurance fund.

### Insurance Net Value

See core algorithm four for details.

