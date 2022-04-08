<!-- toc -->

April 07, 2022

# DESCRIPTION

```
Package: AUCST
Title: What the Package Does (One Line, Title Case)
Version: 0.0.0.9000
Authors@R: 
    person("First", "Last", , "first.last@example.com", role = c("aut", "cre"),
           comment = c(ORCID = "YOUR-ORCID-ID"))
Description: What the package does (one paragraph).
License: `use_mit_license()`, `use_gpl3_license()` or friends to pick a
    license
Encoding: UTF-8
Roxygen: list(markdown = TRUE)
RoxygenNote: 7.1.2
LazyData: true```


# `fp.func3`

Polynomial


## Description

Polynomial


## Usage

```r
fp.func3(sk, t, theta)
```


## Value




# `logL`

calculate the log-likelihood


## Description

calculate the log-likelihood


## Usage

```r
logL(theta, sk, d.times, n1.h.mat, n2.h.mat, eta.sk.mat, sk.le.dh, Ewt.die)
```


## Value




# `main1.sub.func`

Calculate Two-dimensional area under curve (AUC)


## Description

Calculate the two-dimensional incident dynamic AUC(s,t) to evaluate the prediction performance of longitudinal biomarkers for a time-to-event outcome. Returns a matirx contains the estimated AUC(s,t), a vector of estimated parameters of the polynomial function, a matrix containing model-based standard error estimates and a convergence indicator.


## Usage

```r
main1.sub.func(
  da,
  da.long,
  sk,
  par0 = c(0.5, 0, 0, 0, 0, 0, 0, 0, 0, 0),
  tseq.eval,
  resample = 0,
  nsap = 1,
  seed = 12345
)
```


## Arguments

Argument      |Description
------------- |----------------
`da`     |      a dataset includes subject id obs_id,  observed event time Y, and status delta. 
`da.long`     |      a longitudinal dataset includes subject id obs_id,  measurement time vtime, and biomaker value Zt. 
`sk`     |      a vector containing the biomarker measurement time under the regular visit scenario. 
`par0`     |      a vector containing the initial value for theta, used in optimization. 
`tseq.eval`     |      a vector containing the time points for calculating the AUC. 
`resample`     |      an indictacor of resampling. (resample=1: conduct perturbed-resampling, resample=0: do not contudct the perturbed-resampling.) 
`nsap`     |      number of perturbation. To obtain SE, set resample to 1 and nsap to a large number (e.g., 250). 
`seed`     |      seed used for resampling. 


## Value

A list containing:
  

*  
  

*  
  

*  
  

*


## Seealso

[`fp.func3`](#fp.func3) , [`logL`](#logl)


## References

Jing Zhang, Jing Ning, Xuelin Huang, Ruosha Li. On the time-varying predictive performance of longitudinal biomarkers: measure and estimation. Statistics in Medicine. 40(23): 5065-5077, 2021.


## Examples

```r
da.sim.short <- AUCst::da.sim.short
da.sim.long <- AUCst::da.sim.long
sort(unique(da.sim.long$vtime))
obj.i=AUCst::main1.sub.func(da=da.sim.short,
da.long=da.sim.long,
sk=c(0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1, 1.1, 1.2),
tseq.eval=c(0.4,1.11,1.50,1.90), resample =1, nsap=3)
obj.i$AUC
obj.i$theta
obj.i$SE
obj.i$conv
```


