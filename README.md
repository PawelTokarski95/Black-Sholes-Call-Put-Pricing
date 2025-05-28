# Black-Sholes-Call-Put-Pricing

- **Language**: C++


Black-Scholes Model serves as a model to valuate Call and Put Options. In this project, I implemented it using C++, with the addition of a Wiener Process, which was important for generating future stock prices of XOM.

 ![1_82ZaRKWa3gUCCdTrZGeUlQ](https://github.com/user-attachments/assets/7ed80826-1a20-4657-9f12-1139a5090c19)

There are a few important components necessary to discuss. First of all, we need to specify the formula of the Black-Scholes model:

In the following formula we have:

N(d₁)·Sₜ – This is the component in which the price of the stock flows with normal distribution density. That implies the assumption that the prices in the market go through significant fluctuations, with “drops” and “ups.”

N(d₂)·K·e^(−r·t) – This is the second component, which implies the future strike price of our option (in this case – a call option), discounted by the factor (−r·t). The same normal distribution assumption of price movement is also applied here.

Why is the (−r·t) factor necessary? Well, it's just a simple rule of finance – there's a necessity to have a discount factor that provides us the risk-free-rate alternative investment over a specific period of time.

We also have d₁ and d₂. These serve as more precise calculations implying the “access” to a specific part of the normal distribution density (or the area beneath it, to simplify).

Then we have the Wiener Process.

![Wiener_process_with_sigma svg](https://github.com/user-attachments/assets/3d94ccc0-1804-4062-951f-412d37027899)


This is basically a mathematical representation of random noise that flows over time. It assumes that in very small time intervals, the price movement can go in any direction – up or down – with some randomness, but it follows a normal distribution. Over longer periods, this randomness accumulates, and the resulting movement is called Brownian motion.

We use it because it captures the inherent uncertainty and chaos of financial markets. In my project, it was used to simulate possible future prices of a stock, based on current market parameters like average return and volatility.

I created a Wiener process in strict relation with Markov chains. This means the future stock price depends only on the current price, not the full past history. Using this idea, I was able to generate 100 different possible future price paths for the stock (XOM).

Then, based on these price paths, I calculated call and put option prices for each scenario. Instead of just one fixed option price, I got a whole range of possible prices, which better shows the market uncertainty and risk.

This way, you can see how option prices might change under different future market conditions, rather than relying on just one number. Keep in mind, that the stock prices and option prices for the 100 observation period (100 days) is rather sensitive towards errors.

Here are the results (it can be seen that there is an inverse correlation between the call and put options which is typicall in terms of financial markets domain):

![Trajectories csv - Excel 28 05 2025 15_52_16](https://github.com/user-attachments/assets/6e859a40-41b0-4d6b-a440-633b22b1b9cd)
![Trajectories csv - Excel 28 05 2025 15_52_25](https://github.com/user-attachments/assets/5009be27-abfd-4a6a-a708-cb6c67824c0e)
