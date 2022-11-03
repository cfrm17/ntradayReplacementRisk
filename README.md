# Intraday Replacement Risk

For any given trade, intraday replacement risk is calculated using one of the following methods:
 
1.     Mark-to-Market (MTM) + Future Potential Exposure (FPE)
2.     Formula based approach
3.     100% of the notional

Most product types, with the exception of equity derivatives, will be calculated using the MTM+FPE approach for intraday replacement risk. For deals existing as of the prior end-of-day cycle, the MTM value will be retrieved from centralized sources of this data, which in most cases is Sentry, but may be the product systems themselves if the data is not available in the prior.

For new and amended deals completed intraday, the MTM values or premiums reflecting these values, will either be retrieved directly from the product systems (assuming that appropriate pricing parameters and market data were specified at the time of input) or entered manually by the trader. The referenced FPE, calculated with risk factor based on a transaction’s product type and underlying attributes, is then added to this MTM value to come up with the replacement risk for the deal. The overall replacement risk calculation is restricted to MAX [(0, MTM)] + FPE, such that in no instances will a negative MTM be considered in the calculation.

 The formula based approach is mostly reserved for OTC equity derivatives, like Equity Forward and Equity Option, in which a diffusion model is used to determine replacement risk on a particular position. For long calls, long equity forwards and long mutual fund forwards, the 95th percentile level (1.65 sigma) of the equity price is estimated under a diffusion process with drift equal to the expected return under the CAPM formula and volatility set to the greatest of the 1, 3 and 5-year standard deviations.

The percentage replacement risk factor is determined using the ratio of the upward diffused price over the strike price. For long puts, short equity forwards and short mutual fund forwards, the current price of the equity is diffused downwards with drift equal to 0 (i.e., no directional bias) and volatility set to the greatest of the 1, 3, and 5-year standard deviations. The percentage replacement risk factor is determined using the ratio of the downward diffused price over the strike price.

Where product types that are fed into the system are unknown, or where specific transactions are denoted as non-standard, then the most conservative application would be to estimate replacement risk at 100% of the notional. Note that the risk analyst / manager who are included in the non-standard workflow will be informed of these positions, and they will then perform appropriate tasks to introduce new risk factors for the product type, assign existing product codes as proxies, or model these outside the system as is done through the non-standard transaction workflow.

Products fall into this category include Interest Rate Total Return Swap, Equity Total Return Swap, as well as other non-standard products.

FPE and MTM amounts that are used in the intraday risk calculation must be converted into USD using the spot or forward FX closing rates as at the close of the previous business day.

MTM value is also called present value or fair value or price. See https://finpricing.com/lib/FiBond.html
