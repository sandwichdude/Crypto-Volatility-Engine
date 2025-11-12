# Crypto Volatility Prediction Engine (SVCJ Model)

This is a cryptocurrency volatility prediction project based on implementing the **Stochastic Volatility with Co-Jumps (SVCJ)** framework. The model is designed to capture the unique characteristics of cryptocurrency markets, such as sudden price jumps and volatility clustering, primarily inspired by the research paper by **Huang, et al. (2022)**.

The project uses a **Particle Filter** algorithm for model calibration and **Monte Carlo simulations** to forecast volatility.

## 📊 Project Structure & Features

This repository is divided into two main components:

1.  **`Summary_Statistics.ipynb`**:

      * Performs exploratory data analysis (EDA) on historical data for the top 100 cryptocurrencies.
      * Cleans and processes raw data, including converting financial short-forms (e.g., '2B', '1.5M') into numeric values.
      * Calculates key summary statistics: mean log-return, standard deviation, skewness, and kurtosis.
      * Generates visualizations for market cap distribution and correlation heatmaps for 7-day and 30-day returns.

2.  **`Vol_Pred_Engine.ipynb`**:

      * Implements the core **SVCJ (Stochastic Volatility with Co-Jumps)** model to forecast volatility.
      * Uses a Bayesian resample-move **Particle Filter** algorithm to calibrate the model and estimate its complex parameters (`&mu;`, `&kappa;`, `&theta;`, `&lambda;j`, etc.).
      * Runs **Monte Carlo simulations** based on the estimated parameters to generate a full predictive distribution for the next day's volatility.
      * Visualizes the evolution of parameter estimates over time and the final predicted volatility histogram.

## ⚙️ Core Methodology

### Stochastic Volatility with Co-Jumps (SVCJ)

The model is an extension of standard stochastic volatility models, which incorporates simultaneous jumps in both asset returns and volatility. This is particularly suitable for cryptocurrencies, where sudden shocks are common. The mathematical formulation follows the dynamics described by Duffie et al. (2000) and Eraker et al. (2003).

### Parameter Estimation

A **Particle Filter** algorithm is used for sequential learning and parameter estimation. This approach is based on iterated batch importance sampling (Chopin, 2002) and employs a Bayesian resample-move algorithm (Andrieu et al., 2010). Prior distributions for the parameters are informed by financial literature from Kim et al. (1998), Chib et al. (2002), and Eraker et al. (2003).

## 💿 Installation & Usage

1.  Clone the repository:

    ```bash
    git clone https://github.com/sandwichdude/crypto-volatility-engine.git
    cd crypto-volatility-engine
    ```

2.  Install the required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Notebooks:**

      * Start with `Summary_Statistics.ipynb` for data exploration.
      * Run `Vol_Pred_Engine.ipynb` to calibrate the model and generate volatility forecasts. *Note: The particle filter is computationally intensive and may take time to run.*

## 🔑 Key Dependencies

  * `pandas`
  * `numpy`
  * `matplotlib`
  * `seaborn`
  * `scipy`
  * `tqdm`
  * `numba`

(Full list in `requirements.txt`)

## 📚 References

  * Andrieu, C., Doucet, A., & Holenstein, R. (2010). Particle Markov chain Monte Carlo methods. *Journal of the Royal Statistical Society: Series B (Statistical Methodology), 72*(3), 269-342.
  * Chib, S., Nardari, F., & Shephard, N. (2002). Markov chain Monte Carlo methods for stochastic volatility models. *Journal of econometrics, 108*(2), 281-316.
  * Chopin, N. (2002). A sequential particle filter method for static models. *Biometrika, 89*(3), 539-551.
  * Duffie, D., Pan, J., & Singleton, K. (2000). Transform analysis and asset pricing for affine jump-diffusions. *Econometrica, 68*(6), 1343-1376.
  * Eraker, B., Johannes, M., & Polson, N. (2003). The impact of jumps in volatility and returns. *The Journal of Finance, 58*(3), 1269-1300.
  * Huang, J.-Z., Ni, J., & Xu, L. (2022). Leverage effect in cryptocurrency markets. *Pacific-Basin Finance Journal, 73*, 101773.
  * Kim, S., Shephard, N., & Chib, S. (1998). Stochastic volatility: Likelihood inference and comparison with ARCH models. *The Review of Economic Studies, 65*(3), 361-393.
