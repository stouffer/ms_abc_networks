---
title: How ecological networks evolve
short: Network macro-evolution
bibliography: default.json
csl: nature.csl
author:
  - family: Poisot
    given: Timothée
    affiliation: 1, 2, 3
    email: tim@poisotlab.io
    id: tp
    orcid: 0000-0002-0735-5184
  - family: Stouffer
    given: Daniel B.
    affiliation: 1
    id: dbs
affiliation:
  - id: 1
    text: Centre for Integrative Ecology, School of Biological Sciences, University of Canterbury, Christchurch, New Zealand
  - id: 2
    text: Université de Montréal, Département de Sciences Biologiques, 90 Avenue Vincent d'Indy, Montréal, QC, CAN, H2V3S9
  - id: 3
    text: Québec Centre for Biodiversity Sciences, 1205 Dr. Penfield Avenue, Montréal, QC, CAN, H3A1B1
keyword:
  - k: ecological networks
  - k: Approximate Bayesian Computation
  - k: bipartite networks
  - k: macroevolution
date: Work in progress.
abstract: Here be science yo.
---

# Introduction

The extant structure and distribution of biodiversity is the outcome of
macro-evolutionnary processes, and the modelling of these processes stimulated a
large variety of approaches @REF. At their core, these approaches are
birth-death processes, in that they model the rate of speciation and extinction
to generate a prediction about both the temporal dynamics of species richness,
and its predicted current state. Yet these models often consider species as
being isolated entities, in that even though they share ancestry, they are not
involved in inter-specific interactions. This is problematic, as from an
ecological [@gravel_tti] and evolutionary @eklofs standpoint, interactions serve as a
*scaffold* to build up increasingly diverse communities: plant require
pollinators to persist, predators require preys, etc.

The addition of species interactions to models of macro-evolution is well
motivated by two key observations. First, the structure of extant networks is
non-random, and displays a strong evolutionary signal @stouffer. Second, there
is a dynamics of the structure of ecological networks over evolutionary
timescales @dunne @roopnarine, suggesting the ongoing action of
macro-evolutionary processes. Models of macro-evolution with explicit
consideration of species interactions are needed to develop a theoretical
understanding of how networks evolve, and how much of their extant structure
originated through evolutionary processes.

Despite the relative lack of well-resolved time series of the macroevolution of
species interactions (ruling out modelling approches comparing temporal
dynamics), the question of how networks evolve can still be adressed by
confronting extent data with the outcome of network diversification scenarios.
And although comparing two networks is a difficult task, comparing their
structure, as represented by the distance between key summary statistics, is
feasible. In this paper, we first present a stochastic model of network
macro-evolution based on a speciation-extinction process. We then simulate this
model under the complete range of meaningful parameter space, and compare its
output to a large dataset of extent ecological interactions (mutualistic and
antagonistic). Using Approximate Bayesian Computation (ABC), we show that (i)
the structure of extent networks is adequately described by our model; (ii)
networks of different interaction types have different parameter values; (iii)
networks of antagonistic interactions are, on average, more difficult to predict
than networks of positive or mutualistic interactions.

# Results and discussions

## Model output

1. Model output

## Posterior distribution of parameters

2. Parameters distributions for different types of networks

## Accuracy of predictions

3. Z-scores

4. Use the method to *generate* realistic networks by sampling the relevant posteriors

# Methods

## Data selection

We used empirical data from mutualistic interactions (XX networks),
plant-herbivore interactions (XX networks), phage-bacteria networks (XX
interactions), plant-dispersers interactions (XX networks), and host-parasite
interactions (XX networks). Mutualistic and dispersers interactions were taken
from the *WebOfLife* database. Phage-bacteria data are from @flores.
Host-parasite data are from @stank. Plant-herbivore data are from @theb. Each
network was cleaned in the following way. First, species with no interactions
(if any) were removed. Second, interactions strengths (if present) were removed.
This yields adjancency matrices in which all species have at least one
interaction.

## Stochastic model

We model the diversification of bipartite networks. Bipartite networks are a
useful way of representing several types of ecological interactions in which a
group of species (*blue*) interacts with a second group of species (*red*;
examples include pollination, frugivory, seed dispersal, parasitism, ...). The
starting point of every simulation is the simplest possible network: one blue
and one red species, with a single interaction between them.

Our model is structurally close to speciation/extinction models -- at each time
step, there is a probability $p$ that one of the blue species (taken at random)
will undergo a speciation event (and conversely, a probability $1-p$ that a red
species will speciate). Upon speciation, the incipient species starts with *all*
interactions of its ancestor; each of these interactions is lost with
probability $\epsilon$,

\begin{equation}
\epsilon = \epsilon_0 \times \text{whatever}
\end{equation}

, where <!-- TODO: description of the parameters -->.

- parameters ranges (from preliminary simulations)

## Simulations

We conducted the following two numerical experiments. First, we conducted a
systematic exploration of the model's behavior using evenly spaced parameter
values. Each combination of parameters was simulated 1000 times. Second, we
sampled the parameter space uniformly, by drawing $10^5$ parameters sets at
random from within the aforementioned bounds. These outputs were used in the
parameter selection experiment described below.

## Network measures

We measure th

- connectance
- nestedness
- motifs (explain the correction)

The raw number of motifs was corrected to account for the number of species in
each layer of the bipartite network. The maximum number of a motif with (e.g.) 2
species at the top and 2 species at the bottom is the product of the number of
combinations of 2 species in the top layer, and of 2 species in the bottom layer
(evaluated by their binomial coefficients). This gives a total number of sets of
species that *could* be involved in a 2x2 motif; the raw number of this motif is
divided by this maximum number. This yields values in the 0-1 range,
representing the proportion of sets of species that *do* form a given motif out of
the sets of species that *could*.

- modularity

## Parameter selection

We used ABC (Approximate Bayesian Computation) to select the parameter values
that yielded realistic networks, by assessing how closely each replicate of the
second numerical experiment resembles empirical communities. For each empirical
network, its array of ranged summary statistics was compared to each output of
the stochastic model. The inverse of the Euclidean distance between the two
arrays was recorded as the score of the parameter set. As every empirical
network had different absolute values of scores, fixing a common threshold was
not feasible. We selected the posterior distribution as the 500 parameters sets
that gave the best scores (i.e. above the 95th percentile).

# References

<!-- #figure:
#  - id: figure1
#    caption: This is a figure.
#    short: Example figure.
#    file: figure1.png
#  - id: figure2
#    caption: This is a second figure. It is taking the two columns in preprint mode.
#    short: Example figure.
#    file: figure1.png
#    wide: true -->