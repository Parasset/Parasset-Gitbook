# Core Algorithm

---

### Mortgage Rate

For a certain debt position, the total amount of collateral assets at time t is recorded as $$x_{t}$$, the change in collateral assets is recorded as $$x_{t}$$, then:

$$ X_{t} = X_{t-1} + x_{t}$$

The process of collateralizing assets will generate debts, which are generating parallel assets. The calculation formula is as follows:

$$ B_{t} = B_{t-1} + b_{t}$$

##### Formula notes:

1. The total debt pledged at time $$t$$
2. The amount of change in debt caused by this pledge or redemption
3. $$C_{t}$$ is the mortgage rate at time $$t$$, and its formula:$$ C_{t} = \frac{B_{t}}{P_{t} \times X_{t}}$$
> Among them $$P_{t}$$ is the price of the underlying asset $$X_{t}$$, which comes from the NEST oracle.
4. Initial collateral, then: $$\begin{cases} X_{t} = X_{0} \\ B_{0} = X_{0} \times C_{0}^{0} \times P_{0} \end{cases}$$
> Among them, $$C_{0}^{0}$$ is the initial collateral rate selected by the investor during the initial collateral.
5. Full redemption, then: $$\begin{cases} X_{N} = 0 \\ B_{N} = 0 \end{cases}$$
6. Partial redemption $$b_{t}$$, $$\begin{cases} X_{t} = X_{t-1} - \frac{X_{t-1} \times b_{t}}{B_{t}} \\ B_{t} = B_{t-1} - b_{t} \end{cases}$$
7. Second Minting $$X_{t}$$, $$\begin{cases} X_{t} = X_{t-1} + x_{t} \\ B_{t} = B_{t-1} + x_{t} \times C_{t}^{0} \times P_{t} \end{cases}$$
> $$C_{t}^{0}$$ is the initial collateral rate selected by the investor during second minting
8. Liquidation line, $$P_{t} < \frac{B_{t-1}+S_{t}}{X_{t-1}} \times k$$
> Where $$k$$ is a constant, $$k=1.2$$ or $$k=1.33$$；Total debt($$B_{t}$$) includes the stability fee for the last paragraph($$S_{t}$$); When the liquidation line is reached, anyone can use ($$X_{t} \times 0.9$$)’s parallel assets to liquidate, take away $$X_{t}$$ mortgage assets, $$0.9X_{t}$$ of the liquidation goes into the insurance fund, and destroy the parallel assets $$B_{t-1}$$: that is, the parallel asset account of the insurance fund increased by $$0.9X_{t}-B_{t-1}$$.

---

### Stability Fee

$$S_{t} = B_{t-1} \times r_{0} \times (1 + 2 \times (C_{t-1} + \frac{B_{t-1}}{X_{t-1} \times P_{t}})) \times (h_{t} - h_{t-1})$$

##### Formula notes:

1. $$S_{t}$$ is the stability fee at $$h_{t}$$
2. $$h_{t}$$ represents block height
3. $$B_{t}$$ is the total amount of debt pledged at $$h_{t}$$
4. $$C_{t-1}$$ is the mortgage rate at time $$t-1$$, its formula: $$C_{t-1} = \frac{B_{t-1}}{P_{t-1} \times X_{t-1}}$$
> Among them, $$X_{t-1}$$ is the collateralized assets, $$P_{t-1}$$ is the price of the underlying asset, which comes from the NEST oracle.
5. $$r_{0}$$ is the market base interest rate

---

### Insurance Fund

The two accounts of the insurance fund are recorded as: the underlying assets $$U_{t}$$ and parallel assets $$V_{t}$$, the sum of the two is the net assets of the insurance fund.

---

### Net Value

$$ NP_{t} = \frac{N_{t}}{F_{t}}$$

##### Formula notes:

1. Net assets $$N_{t} = U_{t} + V_{t}$$
2. $$F_{t}$$ is the insurance fund share at time $$t$$, the initial share is $$F_{0}$$, then: $$F_{t} = F_{t-1} + \Delta F_{t}$$
> $$\Delta F_{t}$$’s formula is $$\Delta F_{t} = \frac{u_{t}}{NP_{T-1}}$$, Among them, $$u_{t}$$ is the new LP asset