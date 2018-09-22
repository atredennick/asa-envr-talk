---
title: Spatiotemporal forecasting of plant populations and the need to partition forecast uncertainty
author: Andrew Tredennick
institute: University of Georgia
date: October 12, 2018
---

##   Collaborators

$\phantom{testtesttt}$ Peter Adler (USU) \hspace{7em} Mevin Hooten (CSU)

$\phantom{testtest}$ \roundpicture{images/peter.jpg}{} \hspace{5em} \roundpicture{images/mevin.jpg}{}

<!-- \begincols

\hspace{2em}\column{0.5\textwidth}

Peter Adler (USU)
\roundpicture{images/peter.jpg}{}

\hfill\column{0.5\textwidth}

Mevin Hooten (CSU)
\roundpicture{images/mevin.jpg}{}

\stopcols -->


##	Rapid environmental change

\includegraphics[width=\textwidth]{./figures/mora_graphic.png}

\credit{Mora et al., 2013, \emph{Nature}}

##	It's been a long time coming

\includegraphics[width=\textwidth]{./figures/clark_title.pdf}

\credit{Clark et al., 2001, \emph{Science}}

##	The time is now

\includegraphics[width=\textwidth]{./figures/dietze_title.pdf}

\credit{Dietze et al., 2018, \emph{PNAS}}

## Road map

1. Do we need demographic data?
2. Scaling up plant population forecasts
3. Partitioning forecast uncertainty -- a new agenda for ecology



#	Do we need demographic data?

##	What land managers want

\centering
\includegraphics[height=2.7in]{./figures/managers_want.pdf}

##	What land managers get

\centering
\includegraphics[height=2.8in]{./figures/managers_get.pdf}

##	Really hard work

\includegraphics[width=\textwidth]{./figures/chart_measuring.jpg}

##   Aggregate population-level data
 
\includegraphics[width=\textwidth]{./figures/missing_climate.pdf}

##   Objectives

1. Determine if population-level data contains similar climate signal as individual-level data.
2. Compare model accuracy and precision using out-of-sample validation.

##   14-year time series from Montana

\includegraphics[width=\textwidth]{./figures/mt_spp.png}

##	Two types of models

\centering
\includegraphics[height=2.7in]{./figures/mee_flow.png}

##	Integral projection model

\centering
\includegraphics[width=0.7\textwidth]{./figures/maps.pdf}

\begin{align*}
\text{survival}(t+1) &\phantom{=} \\
\text{growth}(t+1) &= f\left(\text{size}(t),\text{location},\text{crowding}(t),\text{year}(t),\text{climate}(t) \right) \\
\text{recruitment}(t+1) &\phantom{=} \\
\end{align*}

##	Qaudrat(cover)-based model

\includegraphics[width=\textwidth]{./figures/montana_quad_ts.pdf}

$$
\text{cover}(t+1) = f\left(\text{cover}(t),\text{location},\text{year}(t),\text{climate}(t) \right)
$$

##	Climate covariates

\includegraphics[width=\textwidth]{./figures/ipm_climate_effects.pdf}

##	Climate effects by vital rates

\centering
\includegraphics[height=2.5in]{./figures/mee_climate_effects.pdf}

\credit{Tredennick et al., 2017, \emph{Methods in Ecol. Evol.}}

##   Model comparison

\centering
\includegraphics[height=2.5in]{./figures/mee_forecast_accuracy_empty.pdf}

\credit{Tredennick et al., 2017, \emph{Methods in Ecol. Evol.}}

##	Model comparison

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

#	Scaling up plant population forecasts

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
\text{log}(\mu_{i,t}) &= \underbrace{\beta_{0,t} + \beta_{1}y_{i,t-1}}_\text{temporal + dens. dep} + \underbrace{\textbf{x}_{t}'\boldsymbol{\phi}}_\text{climate} + \underbrace{\eta_{i}}_\text{spatial}
\end{align*}

##	Dimension reduction for spatial effect

\includegraphics[width=\textwidth]{./figures/SAGE_Grid_wKnots_subset.png}

##	Dynamic cover model

\begin{align*}
y_{i,t} &\sim \text{Poisson}(\mu_{i,t}) \\
\text{log}(\mu_{i,t}) &= \underbrace{\beta_{0,t} + \beta_{1}y_{i,t-1}}_\text{temporal + dens. dep} + \underbrace{\textbf{x}_{t}'\boldsymbol{\phi}}_\text{climate} + \underbrace{\eta_{i}}_\text{spatial} \\
\boldsymbol{\eta} &\approx \textbf{K}\boldsymbol{\alpha}, \\
\alpha_{m} &\sim \text{Normal}(0,\sigma_{\eta}^2)
\end{align*}

##	Climate effects

\centering
\includegraphics[height=2.7in]{./figures/post_climate_covariates.pdf}

##	Model performance

\small{RMSE $\approx$ 4\%}

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

#	Partitioning forecast uncertainty

##	Forecast variance...to a first approximation

$$
y_{t+1} = f(y_t, x_t|\theta) + \epsilon_{t+1}
$$

##	Forecast variance...to a first approximation

$$
y_{t+1} = f(y_t, x_t|\theta) + \epsilon_{t+1}
$$

\small
\begin{align*}
Var[y_{t+1}] \approx \underbrace{\left(\frac{\delta f}{\delta y} \right)^2}_{\text{stability}} 
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[y_t]}_{\text{IC uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta x} \right)^2}_{\text{driver sens.}} 
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[x_t]}_{\text{driver uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta \theta} \right)^2}_{\text{param sens.}}
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[\theta]}_{\text{param. uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[\epsilon]}_{\text{process error}}
\end{align*}

\credit{Dietze, 2017, \emph{Ecological Applications}; Cariboni et al., 2007, \emph{Ecological Modeling}}

##	Forecast variance...to a first approximation

\colorlet{shadecolor}{gray!40}

$$
\textcolor{shadecolor}{y_{t+1} = f(y_t, x_t|\theta) + \epsilon_{t+1}}
$$

\small
\begin{align*}
\textcolor{shadecolor}{Var[y_{t+1}] \approx \underbrace{\left(\frac{\delta f}{\delta y} \right)^2}_{\text{stability}} 
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[y_t]}_{\text{IC uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta x} \right)^2}_{\text{driver sens.}} 
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[x_t]}_{\text{driver uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 }\left(\frac{\delta f}{\delta \theta} \right)^2}_{\text{param sens.}}
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[\theta]}_{\text{param. uncert.}} +
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[\epsilon]}_{\text{process error}}}
\end{align*}

\normalsize
$$
Var[y_{t+1}] \approx \text{Internal}+\text{External}+\text{Parameters}+\text{Process Error}
$$

\credit{Dietze, 2017, \emph{Ecological Applications}; Cariboni et al., 2007, \emph{Ecological Modeling}}


##	This is why we have weather satellites

\begincols
\column{0.68\textwidth}

\begin{align*}
Var[y_{t+1}] \approx \underbrace{\left(\frac{\delta f}{\delta y} \right)^2}_{\text{stability}} 
               \underbrace{\vphantom{ \left(\frac{\delta f}{\delta y} \right)^2 } Var[y_t]}_{\text{IC uncert.}} 
\end{align*}

$$
Var[y_{t+1}] \approx \text{Internal}
$$

\hfill\column{0.28\textwidth}

\roundpicture{figures/satellite.jpg}{}

\stopcols

## Yellowstone bison (*Bison bison*)

\includegraphics[width=\textwidth]{./figures/National-Park_Sandy-Sist.jpg}

## Yellowstone bison (*Bison bison*)

\centering
\includegraphics[height=2.7in]{./figures/bison_winter.jpg}

##	Time series of bison counts (1970 - 2017)

Response
: Bison counts

Covariate
: January precipitation

\includegraphics[width=\textwidth]{./figures/bison_data_plots.png}

##	Gompertz population growth

\begin{align*}
mu_{(t)} &= \text{log}(z_{(t-1)}) + e_{(t)} + r + b_0 \text{log}(z_{(t-1)} + e_{(t)}) + b_1 x_{(t)} \\
\text{log}(z_{(t)}) &\sim \text{Normal}\left( \mu_{(t)}, \sigma^2_\text{p} \right)
\end{align*}

\footnotesize

$z_t$
: \alert{latent} population abundance in year *t*

$e_t$
: log of harvested animals between $t-1$ and $t$

$r$
: per capita growth rate

$b_0$
: density dependence

$b_1$
: effect of January precipitation

$x_t$
: January precipitation in year *t*

$\sigma^2_\text{p}$
: process variance



## Likelihood and fully specified model
 
 Likelihood

 $$
 y_{(t)} \sim \text{NB} \left(  z_{(t)} , \kappa \right)
 $$

 Full model

\small

 $$
 \left[ \boldsymbol{\theta}_\text{p}, \kappa, z_{(t)}, z_{(t-1)} | y_{(t)}, x_{(t)} \right ] \propto \prod_{t=2}^{\textcolor{red}{48}} \underbrace{\left[ z_{(t)} | \boldsymbol{\theta}_\text{p}, z_{(t-1)}, x_{(t)} \right]}_{\text{process}} \prod_{t=1}^{\textcolor{red}{41}} \underbrace{\left[ y_{(t)} | \kappa, z_{(t)} \right]}_{\text{data}} \underbrace{\left[ \boldsymbol{\theta}_\text{p}, \kappa, z_{(t=1)}\right]}_{\text{parameters}}
 $$

 <!-- Includes a strong prior on $r$ based on Hobbs et al. 2015: $r \sim \text{Normal}(0.1, 0.02)$ -->

## Posterior distribution of climate effect

\centering
\includegraphics[height = 2.5in]{./figures/bison_post_params.pdf}

##	Model fit and forecast

\centering
\includegraphics[height=2.7in]{./figures/bison_fit.pdf}

##	Forecast partition

\centering
\includegraphics[height=2.7in]{./figures/forecast_partition.pdf}

##	Climate Projections are uncertain

\centering
\includegraphics[height=2.7in]{./figures/precip_projections.pdf}

#	Closing thoughts

##	Closing thoughts

1. We have the tools and the data streams to start forecasting.
2. The time to start is now.
3. Embrace our failures.
4. Generate \alert{meaningful} forecasts -- forecasts that someone wants.
