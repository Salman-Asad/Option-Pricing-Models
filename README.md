📈 Option Pricing Models
A quantitative finance project implementing and analyzing option pricing models using real market data from Apple Inc. (AAPL).

🧠 Overview
This project builds a complete option pricing framework from scratch in Python, combining the Cox-Ross-Rubinstein (CRR) binomial tree model with the Black-Scholes (BS) analytical model. The goal is to price European call and put options, verify theoretical relationships, analyze risk sensitivities, and visualize implied volatility across strikes and expiries.
All models are validated against live market data fetched via the yfinance API.

📂 Project Structure
option-pricing-models/
│
├── Option_Pricing.ipynb       # Main Jupyter Notebook
├── README.md                  # Project documentation

📌 Features
1. CRR Binomial Tree Model

Implemented the Cox-Ross-Rubinstein (1979) binomial tree for pricing European call and put options
Standard parametrization: u = exp(σ√Δt), d = exp(-σ√Δt)
Risk-neutral probability q derived from no-arbitrage condition

2. Black-Scholes Model

Analytical pricing formula for European call and put options
Implemented d1, d2 directly for reuse across Greeks calculations

3. CRR Convergence to Black-Scholes

Demonstrated that CRR price converges to BS price as number of steps M → ∞
Plotted convergence curve across M = [2, 5, 10, 20, 50, 100, 200, 500]

4. Put-Call Parity Verification

Verified the no-arbitrage relationship: C - P = S₀ - Ke^(-rT)
Confirmed parity holds for both CRR and BS models

5. Greeks (Risk Sensitivities)
GreekFormulaMeaningDeltaN(d1)Sensitivity of option price to stock priceGammaN'(d1) / (S₀σ√T)Rate of change of DeltaVegaS₀ · N'(d1) · √TSensitivity to volatility
6. Replicating Portfolio

Constructed a portfolio of Δ shares + B bond that exactly replicates the option payoff
Verified: Δ · S₀ + B = Option Price for both call and put

7. Volatility Smile

Calculated implied volatility (IV) across strikes for a single expiry
Observed the classic Volatility Smirk — higher IV for low strikes reflecting crash risk

8. Volatility Surface (Heatmap)

Extended the smile across 6 expiries: May-26 to Mar-27
Visualized as a 2D heatmap showing both:

Strike dimension → Volatility Smirk
Time dimension → Term Structure of Volatility


📊 Key Results
MetricValueUnderlyingAAPLSpot Price S₀~280Strike K280Risk-free Rate r3%Historical Volatility σ~32%Delta (Call)0.5689Delta (Put)-0.4311Gamma0.0065Vega74.24

💡 Key Insights

CRR converges to BS as M increases — confirming the binomial model is a discrete approximation of the continuous Black-Scholes world
Put-Call Parity holds — the market is arbitrage-free for liquid AAPL options
Volatility is not constant — the heatmap clearly shows IV varies across both strikes and expiries, violating the core Black-Scholes assumption of constant sigma
The Volatility Smirk reflects the market's asymmetric fear of downside crashes vs upside moves — a phenomenon that appeared permanently in equity markets after Black Monday (1987)


🛠️ Tech Stack

Python 3.12
NumPy — numerical computations
Pandas — data manipulation
Matplotlib — plotting
Seaborn — heatmap visualization
SciPy — normal distribution functions
yfinance — live market data

🚀 How to Run

Clone the repository:

bashgit clone https://github.com/Salman-Asad/option-pricing-models.git
cd option-pricing-models

Install dependencies:

bashpip install numpy pandas matplotlib seaborn scipy yfinance jupyter

Open the notebook:

bashjupyter notebook Option_Pricing.ipynb

Run all cells from top to bottom


⚠️ Note: Market data is fetched live via yfinance — prices and IV values will differ from the results shown here depending on when you run the notebook.


📚 References

Cox, J., Ross, S., Rubinstein, M. (1979). Option Pricing: A Simplified Approach. Journal of Financial Economics.
Black, F., Scholes, M. (1973). The Pricing of Options and Corporate Liabilities. Journal of Political Economy.


👤 Author
Salman Asad
Show Image

Built as part of a quantitative finance self-study project.
