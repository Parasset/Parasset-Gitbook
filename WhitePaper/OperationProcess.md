# Operation Process

---

The minter pledges the digital assets that meet the requirements to the contract, and generates parallel assets such as PBTC, PETH, and PUSD according to the selected mortgage rate. At the same time, the system generates the corresponding debt warehouse and liquidation line (Minting). Before the debt warehouse is liquidated, at any time, the mint can retrieve the mortgaged assets by returning the corresponding amount of stable coins (Redemption). Once the mortgage asset price is below the liquidation line, anyone can trigger the liquidation, and the liquidation is in accordance with the following rules: Anyone can use the parallel assets of () to liquidate, take away the mortgaged assets, the 0.9 of the liquidation goes into the insurance fund, and the parallel assets are destroyed (Clearing). The user can replenish the mortgage at any time, enter the same debt warehouse with the supplementary mortgage, and modify the liquidation line at the same time. The rule is Algorithm 1 (Supplementary Collateral). Anyone can inject insurance funds into the insurance fund pool. The requirement is the corresponding underlying asset. After the injection, the share is calculated according to the net value (Inject Insurance). The insurance funds specify the redemption date and the period is 3 months. Each share needs to be held for at least one period and redeemed according to the net value: the underlying assets will be redeemed first, and the parallel assets will be redeemed if they are insufficient (Withdraw Insurance). Users can re-mint coins in the original debt warehouse, and at the same time correct the liquidation line, according to the core algorithm (Second Minting). Users can inject 1USDT into the insurance fund pool to get 1PUSD, or inject 1PUSD in exchange for 1USDT. 2‰ handling fee is paid according to the scale, and the handling fee is measured by assets (Fast Minting and Exchange). Stability fees are calculated in blocks. Stability fees are charged for each operation of coin minting, redemption, replenishment, and liquidation. Stability fees are calculated in parallel with assets. See Core Algorithm 2 for details (Stability Fee).