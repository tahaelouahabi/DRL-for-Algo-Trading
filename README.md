# Deep Reinforcement Learning for Algo-Trading | RL & Quant Finance
Authors: [Taha-Abderrahman EL OUAHABI](taha.abderrahman.el.ouahabi@ensae.fr) | ENSAE Paris & [Anass Essounaini](essounaini97@gmail.com) | M2MO - Université de Paris VII
## Table of contents
* [About](#about)
* [Learning](#learning)
* [Results](#results)
* [References](#References)
* 

## About

In this project, we explore the possibility of applying Deep Reinforcement Learning -DRL- Strategies in an Algortihmic Trading environnment. DRL has gained significant traction due to its state-of-the-art performance in many applications such as NLP, speech recognition and our objective here was to explore the possibility of such performance in an Algorithmic Trading -an environnement characterized with a high level of randomness- setting.

## Learning 

In this experiment, the algorithmic trading problem is equivalent to managing a single stock portfolio. Hence, the value of the trading portfolio can be decomposed as follows: <img src="http://latex.codecogs.com/svg.latex?v_{t}&space;\quad=\quad&space;v_{t}^{c}&space;\quad&plus;\quad&space;v_{t}^{s}" title="http://latex.codecogs.com/svg.latex?v_{t} \quad=\quad v_{t}^{c} \quad+\quad v_{t}^{s}" />

**The Observation Space:** In our Experiment, we used a reduced version of the truly obsevable states. It is reduced to OHLCV + Position Data. We mean by OHLCV Data the Open, High, Low, Close, and Volume Data for each given stock.

**The Action Space:** Here the action space is modeled with the quantity of the asset that will be held. i.e 
<img src="http://latex.codecogs.com/svg.latex?a_{t}&space;=&space;Q_{t}&space;\in&space;\mathbb{Z}" title="http://latex.codecogs.com/svg.latex?a_{t} = Q_{t} \in \mathbb{Z}" />. We supposed the action to take discrete values to simplify the model.

Key Assumptions:

* Trading actions occur at market closure with execution price
* We accounted for the transaction costs that are mainly due to costs and taxes and to slippage costs.

The learning was carried out with the Deep Q Learning algorith. Check report for more details.
## Results

We train the model for data between 2012-1-26 and 2018-1-25, and used multiple assets exhibitng a positive trend, negative trend, no trend at all. The Backtest period spans 1 year, from 2018-1-26 up to 2018-12-26. We acknoaldge that the backtest period is rather short and might not reflect the performance of the agent perfectly.
We compared the DRL agent with vanilla strategies, such as the classical buy and hold. We found out that the perfromance of the DRL agent significantly outperformed that of the these vanilla strategies on the backtested period. 

| Metric                |  B&H  |  S&H  | RSI | BBANDS |  MACD |  SMA  | TQDN (DRL Agent) |
|-----------------------|:-----:|:-----:|:---:|:------:|:-----:|:-----:|:----------------:|
| Sharpe Ratio          |  0.21 |  0.07 | NaN |   1.3  |  0.17 |  0.81 |       0.79       |
| Sortino Ratio         |  0.29 |  0.11 | NaN |  2.01  |  0.23 |  1.17 |        1.2       |
| Max Drawdown          | -0.18 | -0.27 |  0  |  -0.09 | -0.12 | -0.12 |       -0.15      |
| Profit Ratio          |  0.71 |  1.39 | NaN |  0.03  |  0.07 |  0.55 |       0.57       |
| Annualized Returns    |   6%  |   %   |  0% |   27%  |   3%  |  22%  |        20%       |
| Annualized Volatility |  28%  |   %   |  0% |   21%  |  15%  |  27%  |        26%       |

Performance assessment for all strategies

## References
[1] Théate, T., Ernst, D. (2021). - An application of deep reinforcement learning to algorithmic trading (Expert Systems with Applications, 173, 114632).
[2] Kaufmann,E. (INRIA Lille) , Valko,M. (INRIA Lille & Deepmind) - Lecture notes on reinforcement learning (Ecole Centrale de Lille).
[3] MichelFliess(LIX,INRIASaclay-IledeFrance),CédricJoin(INRIASaclay-Ile de France, CRAN) - A mathematical proof of the existence of trends in financial time series ( arXiv:0901.1945 ).
