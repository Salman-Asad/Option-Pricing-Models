📈 Option Pricing Models
A quantitative finance project implementing and analyzing option pricing models using real market data from Apple Inc. (AAPL).

🧠 Overview
This project builds a complete option pricing framework from scratch in Python, combining the Cox-Ross-Rubinstein (CRR) binomial tree model with the Black-Scholes (BS) analytical model. The goal is to price European call and put options, verify theoretical relationships, analyze risk sensitivities, and visualize implied volatility across strikes and expiries.
All models are validated against live market data fetched via the yfinance API.

📂 Project Structure
option-pricing-models/
│
├── Option_Pricing.ipynb       # Main Jupyter Notebook
└── README.md                  # Project documentation

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
GreekFormulaMeaning:
Delta N(d1) Sensitivity of option price to stock price
Gamma N'(d1) / (S₀ σ √T) Rate of change of Delta
Vega S₀ · N'(d1) · √T Sensitivity to volatility

7. Replicating Portfolio

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
Metric                      Value  
Underlying                  AAPL 
Spot Price S₀               approx. 280
Strike K                    280
Risk-free Rate r            3%
Historical Volatility σ     approx. 32%
Delta (Call)                0.5689
Delta (Put)                 -0.4311
Gamma                       0.0065
Vega                        74.24

💡 Key Insights

CRR converges to BS as M increases — confirming the binomial model is a discrete approximation of the continuous Black-Scholes world
Put-Call Parity holds — the market is arbitrage-free for liquid AAPL options
Volatility is not constant — the heatmap clearly shows IV varies across both strikes and expiries, violating the core Black-Scholes assumption of constant sigma
The Volatility Smirk reflects the market's asymmetric fear of downside crashes vs upside moves — a phenomenon that appeared permanently in equity markets after Black Monday (1987)


🛠️ Tech Stack
Library          Purpose
Python 3.12      Core language
NumPy            Numerical computations
Pandas           Data manipulation
Matplotlib       Plotting
Seaborn          Heatmap visualization
SciPy            Normal distribution functions
yfinance         Live market data

🚀 How to Run
1. Clone the repository:
bashgit clone https://github.com/Salman-Asad/Option-Pricing-Models.git
cd Option-Pricing-Models
2. Install dependencies:
bashpip install numpy pandas matplotlib seaborn scipy yfinance jupyter
3. Open the notebook:
bashjupyter notebook Option_Pricing.ipynb
4. Run all cells from top to bottom

⚠️ Note: Market data is fetched live via yfinance — prices and IV values will differ from the results shown here depending on when you run the notebook.


📚 References

Cox, J., Ross, S., Rubinstein, M. (1979). Option Pricing: A Simplified Approach. Journal of Financial Economics.
Black, F., Scholes, M. (1973). The Pricing of Options and Corporate Liabilities. Journal of Political Economy.


👤 Author
Salman Asad

"Built as part of a quantitative finance self-study project."
