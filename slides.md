---
title: Spatiotemporal forecasting of plant populations and a proposal to partition forecast uncertainty
author: Andrew Tredennick
institute: University of Georgia
date: October 12, 2018
---

##   Collaborators

$\phantom{testtesttt}$ Peter Adler (USU) \hspace{7em} Mevin Hooten (CSU)

$\phantom{testtest}$ \roundpicture{images/peter.jpg}{} \hspace{5em} \roundpicture{images/mevin.jpg}{}

## Road map

1. Plant population forecasts over large spatial extents
2. A plea (and a proposal) to partitioning forecast uncertainty 


#   Plant population forecasts

##   What land managers want

\centering
\includegraphics[height=2.7in]{./figures/managers_want.pdf}

##   What land managers get

\centering
\includegraphics[height=2.8in]{./figures/managers_get.pdf}

##   Really hard work

\includegraphics[width=\textwidth]{./figures/chart_measuring.jpg}


##   Do we need demographic data?

\centering
\includegraphics[height=2.5in]{./figures/mee_forecast_accuracy_empty.pdf}

\credit{Tredennick et al., 2017, \emph{Methods in Ecol. Evol.}}

##	Free from the tyranny of demographic data!

\centering
\includegraphics[height=2.5in]{./figures/mee_forecast_accuracy.pdf}

\credit{Tredennick et al., 2017, \emph{Methods in Ecol. Evol.}}

##	Forecast horizons

\centering
\includegraphics[height=2.5in]{./figures/mee_horizons.pdf}

\credit{Tredennick et al., 2017, \emph{Methods in Ecol. Evol.}}

##	Do we need demographic data?

\centering
Maybe not.

##   Let's use satellites

\centering
\includegraphics[height=2.7in]{./figures/landsat8.jpg}

##	Sagebrush sea in Wyoming

\centering
\includegraphics[height=2.5in]{./figures/sage_pic.pdf}

##	Study area

\centering
\includegraphics[height=2.8in]{./figures/studyarea_map.png}

##	Landsat time series

\includegraphics[height=2.8in]{./figures/all_years_percCover.pdf}

##	Dynamic cover model

\begin{align*}
y_{i,t} &\sim \text{Poisson}(\mu_{i,t}) \\
\text{log}(\mu_{i,t}) &= \underbrace{\beta_{0,t} + \beta_{1}y_{i,t-1}}_\text{temporal + dens. dep} + \underbrace{\textbf{x}_{t}'\boldsymbol{\gamma}}_\text{climate} + \underbrace{\eta_{i}}_\text{spatial}
\end{align*}

##	Dimension reduction for spatial effect

\includegraphics[width=\textwidth]{./figures/SAGE_Grid_wKnots_subset.png}

##	Dynamic cover model

\small

\begin{align*}
y_{i,t} &\sim \text{Poisson}(\mu_{i,t}) \\
\text{log}(\mu_{i,t}) &= \underbrace{\beta_{0,t} + \beta_{1}y_{i,t-1}}_\text{temporal + dens. dep} + \underbrace{\textbf{x}_{t}'\boldsymbol{\gamma}}_\text{climate} + \underbrace{\eta_{i}}_\text{spatial} \\
\boldsymbol{\eta} &\approx \textbf{K}\boldsymbol{\alpha}, \\
\textbf{K} &= \mathbf{w}_{s,m} / \sum_{s=1}^S \mathbf{w}_{s,m} \\
\mathbf{w}_{s,m} &= \text{exp}\left(-d_{s,m} / \sigma \right) \\
\alpha_{m} &\sim \text{Normal}(0,\sigma_{\eta}^2)
\end{align*}


##	Climate effects

\centering
\includegraphics[height=2.7in]{./figures/post_climate_covariates.pdf}

##	Model performance

\small{In-sample RMSE $\approx$ 4\%}

\includegraphics[width=\textwidth]{./figures/obs_predict_spatial_pres.pdf}

\credit{Tredennick et al., 2016, \emph{Ecosphere}}

##   Forecasts under climate change: spatial

\includegraphics[width=\textwidth]{./figures/clim_change_mean_spatial_empty.pdf}

\credit{Tredennick et al., 2016, \emph{Ecosphere}}

##	Forecasts under climate change: spatial

\includegraphics[width=\textwidth]{./figures/clim_change_mean_spatial.pdf}

\credit{Tredennick et al., 2016, \emph{Ecosphere}}

##	Forecasts under climate change: temporal

\centering
\includegraphics[height=2in]{./figures/temporal_forecasts_presentation.pdf}

\credit{Tredennick et al., 2016, \emph{Ecosphere}}


# Partitioning forecast uncertainty

## Forecast uncertainty, to a first approximation

Forecast of state $z$ at $t+1$ from function $q$: $q = f(z_t, x_t, \theta, \varepsilon_{t+1})$

\small

\begin{align*}
Var[y_{t+1}] \approx \underbrace{\left(\frac{\delta q}{\delta y} \right)^2}_{\text{stability}} 
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 } Var[y_t]}_{\text{IC uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta x} \right)^2}_{\text{driver sens.}} 
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 } Var[x_t]}_{\text{driver uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta \theta} \right)^2}_{\text{param sens.}}
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 } Var[\theta]}_{\text{param. uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta q}{\delta y} \right)^2 } Var[\varepsilon_{t+1}]}_{\text{process error}}
\end{align*}

\credit{Dietze, 2017, \emph{Ecological Applications}}

## An \emph{inverse} error propagation problem

For some function $q$: $q = f(x_1,x_2,\dots,x_n)$

\begin{align*}
\sigma^2_q &= \left( \frac{\delta q}{\delta x_1} \sigma_{x_1} \right)^2 + \left( \frac{\delta q}{\delta x_2} \sigma_{x_2} \right)^2 + \cdots + \left( \frac{\delta q}{\delta x_n} \sigma_{x_n} \right)^2 \\
&= \sum^n_{i=1}\left( \frac{\delta q}{\delta x_i} \sigma_{x_i} \right)^2
\end{align*}

\credit{Ku, 1966, \emph{J. Res. National Bureau of Standards - C}}

## An \emph{inverse} error propagation problem

\begin{align*}
\sigma^2_q &= \underbrace{\sum^n_{i=1}\left( \frac{\delta q}{\delta x_i} \sigma_{x_i} \right)^2}_{\text{variances}} + \alert{\underbrace{\sum^n_{i=1} \sum^n_{j(j \ne i)} 2 \sigma_{ij}\left( \frac{\delta q}{\delta x_i} \right)\left( \frac{\delta q}{\delta x_j} \right)}_{\text{covariances}}}
\end{align*}

\credit{Ku, 1966, \emph{J. Res. National Bureau of Standards - C}}


##   Interaction (covariances) cannot be ignored

\begin{align*}
z_{t+1} &= z_{t} \beta_0 + x_t \beta_1 + \varepsilon_{t+1}, \\
z_{t=1} &\sim \text{Normal}(z_0, \sigma^2_{\text{init.}}), \qquad \scriptstyle\text{initial conditions uncertainty} \\
\mathbf{\beta} &\sim \text{MVN}(0, \sigma^2_{\text{param.}} \mathbf{I}), \qquad \scriptstyle\text{parameter uncertainty} \\
\varepsilon_t &\sim \text{Normal}(0, \sigma^2_{\text{proc.}}) \qquad \scriptstyle\text{process uncertainty}
\end{align*}

##   Interaction (covariances) cannot be ignored

\centering
\includegraphics[width=\textwidth]{./figures/forecast_uncertainty_example.pdf}

##	Hierarchical Bayesian models propagate uncertainty for us

\begin{equation*}
\begin{aligned}[b]
\textbf{Data Model:} \quad y_t &\sim \left[y_t \;|\; z_t, \sigma^2_{\text{o}}\right], &t = 1,\dots,T, \\ 
\textbf{Process Models:} \quad z_t &\sim \left[z_t \;|\; \mu_t, \sigma^2_{\text{p}}\right],  \\ 
\mu_t &= g \left(z_{t-1},\textbf{x}'_t, \boldmath{\theta} \right), &t = 2,\dots,T, \\ 
\textbf{Parameter Models:} \quad \boldmath{\phi} &\sim \left[\boldmath{\theta},\sigma^2_{\text{p}},\sigma^2_{\text{o}},z_{t=1} \right]
\end{aligned}
\end{equation*}

\credit{Berliner, 1996, \emph{in} Maximum entropy and bayesian methods}

##	The Forecast distribution

\begin{equation*}
\begin{gathered}
\left[z_{T+1} | y_1,\dots,y_T \right] = \int \int \dots \int \left[z_{T+1} | z_T, \textbf{x}_T, \theta, \sigma^2_{\text{p}} \right] \\ \times \left[z_1,\dots,z_{T+1},\theta, \sigma^2_{\text{p}} | y_1,\dots,y_T \right] d \theta d \sigma^2_{\text{p}} d z_1 \dots d z_T
\end{gathered}
\end{equation*}

\credit{Hobbs and Hooten, 2015, Bayesian Models: A Statistical Primer for Ecologists}

##  The Forecast Distribution, via MCMC

We have:

\begin{itemize}
 \item $k = 1,\dots,K$ MCMC iterations
 \item $j = 1,\dots,J$ realizations of the covariate, resampled to match $K$
 \item Forecasts at times $T+q,\dots,T+Q$
\end{itemize}

\begin{equation*}
z_{T+q}^{(k)} \sim \left[z_{T+q} | g(z_{T+q-1}^{(k)}, \textbf{x}_{T+q}^{(j(k))},\boldmath{\theta}^{(k)}), \sigma^{2(k)}_{\text{p}} \right]
\end{equation*}

##	\emph{Post hoc} partitioning from MCMC samples

\bf{Ignore initial conditions uncertainty}

\begin{equation*}
\alert{z_{T}^{(\ast)}} = E(z_{T} | y_1,\dots,y_T) \approx \frac{\sum^K_{k=1} z_{T}^{(k)}}{K}
\end{equation*}

\begin{equation*}
    z_{T+q} \sim 
\begin{cases}
    \left[z_{T+q} | g(z_{T+q-1}^{(k)}, \textbf{x}_T^{(j(k))}, \boldmath{\theta}^{(k)}), \sigma^{2(k)}_{\text{p}} \right], &q>1 \\
    \left[z_{T+q} | g(\alert{z_{T}^{(\ast)}}, \textbf{x}_T^{(j(k))}, \boldmath{\theta}^{(k)}), \sigma^{2(k)}_{\text{p}} \right], &q=1.
\end{cases}
\end{equation*}


##	\emph{Post hoc} partitioning from MCMC samples

| \emph{k} | $z_T$          | $\theta_1$       | $\cdots$  |
|:--------:|:--------------:|:----------------:|:---------:|
| 1        | $z_{T}^{(\ast)}$ | $\theta_1^{(1)}$ | $\cdots$  |
| 2        | $z_{T}^{(\ast)}$ | $\theta_1^{(2)}$ | $\cdots$  |
| 3        | $z_{T}^{(\ast)}$ | $\theta_1^{(3)}$ | $\cdots$  |
| 4        | $z_{T}^{(\ast)}$ | $\theta_1^{(4)}$ | $\cdots$  |
| 5        | $z_{T}^{(\ast)}$ | $\theta_1^{(5)}$ | $\cdots$  |
| $\vdots$ | $\vdots$       | $\vdots$         | $\vdots$  |
| K        | $z_{T}^{(\ast)}$ | $\theta_1^{(K)}$ | $\cdots$  |


##	\emph{Post hoc} partitioning from MCMC samples

\begin{align*}
\textbf{Z}^{(I)} &= \textbf{Z}^{(I,\overline{PA},\overline{D},\overline{PS})} \\
\textbf{Z}^{(I)} &\approx \left[z_{T+q} \; | \; g(z_{T+q-1}^{(k)}, \textbf{x}^{(\ast)}_T, \boldmath{\theta}^{(\ast)}), 0 \right] \\
\end{align*}

##	\emph{Post hoc} partitioning from MCMC samples

\begin{align*}
\textbf{Z}^{(I)} &= \textbf{Z}^{(I,\overline{PA},\overline{D},\overline{PS})} \\
\textbf{Z}^{(I)} &\approx \left[z_{T+q} \; | \; g(z_{T+q-1}^{(k)}, \alert{\textbf{x}^{(\ast)}_T, \boldmath{\theta}^{(\ast)}}), \alert{0} \right]
\end{align*}

##	\emph{Post hoc} partitioning from MCMC samples

\begin{align*}
\textbf{Z}^{(I)} &= \textbf{Z}^{(I,\overline{PA},\overline{D},\overline{PS})} \\
\textbf{Z}^{(I)} &\approx \left[z_{T+q} \; | \; g(z_{T+q-1}^{(k)}, \alert{\textbf{x}^{(\ast)}_T, \boldmath{\theta}^{(\ast)}}), \alert{0} \right] \\
V^{(I)} &= \text{var}(\textbf{Z}^{(I)})
\end{align*}

##	\emph{Post hoc} partitioning from MCMC samples

| Source of Uncertainty | Notation           |
| :-------------------- | :----------------- |
| Initial conditions    | $V^{(I) \ } = V^{(I,\overline{PA},\overline{D},\overline{PS})}$ | 
| Parameter uncertainty | $V^{(PA)} = V^{(\overline{I},PA,\overline{D},\overline{PS})}$ |
| Driver uncertainty    | $V^{(D) \ } = V^{(\overline{I},\overline{PA},D,\overline{PS})}$ |
| Process uncertainty   | $V^{(PS)}=V^{(\overline{I},\overline{PA},\overline{D},PS)}$ |

##	Partition Forecast Uncertainty: ANOVA

\begin{equation*}
\begin{aligned}[b]
V_{T+q}^{(F)} = \ &V_{T+q}^{(I)} + V_{T+q}^{(PA)} + V_{T+q}^{(D)} + V_{T+q}^{(PS)}
\end{aligned}
\end{equation*}

##	Partition Forecast Uncertainty: ANOVA

\begin{equation*}
\begin{aligned}[b]
V_{T+q}^{(F)} = \ &V_{T+q}^{(I)} + V_{T+q}^{(PA)} + V_{T+q}^{(D)} + V_{T+q}^{(PS)} \\
&+ \varepsilon_{T+q}^{(I,PA)} + \varepsilon_{T+q}^{(I,D)} + \varepsilon_{T+q}^{(I,PS)} + \varepsilon_{T+q}^{(PA,PS)} + \varepsilon_{T+q}^{(PA,D)} + \varepsilon_{T+q}^{(D,PS)} \\
&+ \varepsilon_{T+q}^{(I,PA,D)} + \varepsilon_{T+q}^{(I,PA,PS)} + \varepsilon_{T+q}^{(I,D,PS)} + \varepsilon_{T+q}^{(PA,D,PS)} \\
&+ \varepsilon_{T+q}^{(I,PA,D,PS)}
\end{aligned}
\end{equation*}

##	Partition Forecast Uncertainty: ANOVA

Example where forecast is influenced by initial conditions ($I$) and parameter uncertainty ($PA$):

\begin{equation*}
V^{(F)}_{T+q} = V^{(I)}_{T+q} + V^{(PA)}_{T+q} + \alert{\varepsilon_{T+q}^{(I,PA)}}
\end{equation*}

so,

\begin{equation*}
\alert{\varepsilon_{T+q}^{(I,PA)}} = V^{(F)}_{T+q} - \left[ V^{(I)}_{T+q} + V^{(PA)}_{T+q} \right]
\end{equation*}

##	Return to example of AR(1) process

\centering
\includegraphics[height=2.5in]{./figures/example_interaction_effect.pdf}

#	Concluding thoughts

##	Conclusions

1. Partition uncertainty to advance ecological forecasting -- how do we get better?
2. Partition uncertainty to advance scientific progress -- what don't we know?
3. Hierarchical Bayesian models ideally suited for partitioning uncertainty because they allow us to fully specify the inclusion of uncertainty.

