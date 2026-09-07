---
layout: page
title: Thesis Part 1
description: Galaxy Properties via MCMC
img: assets/img/cornerplot.jpg
importance: 1
category: work
related_publications: true
---

Galaxies emit light across a huge range of wavelengths, and the exact mix of brightness at each wavelength (its "spectral energy distribution," or SED) encodes clues about what the galaxy is made of and how it got that way. Some of the most important galaxy properties that can be extracted are:

    - How many stars it has: Stellar Mass 
    - How old those stars are: Star Formation History
    - And how much interstellar dust is dimming the light: Dust Amount (A_v)

However, you can't measure those properties directly. When you take an image of a galaxy, all you can measure is a brightness that is associated with a range of wavelengths. One solution is to take multiple images of the same galaxy with different wavelength filters (a.k.a. bands). From the relative brightnesses of the galaxy in different bands, one can infer the properties that produce those ratios. Doing this is complicated, and requires a special tool that models the galaxy, complete with knobs to turn for stellar mass, age, dust content, and other variables, and simulate what its light would look like from a modern telescope. I performed this procedure with a tool called Prospector, and the fitting was applied to six extremely distant, gravitationally lensed galaxies. Essentially, a gravitationally lensed galaxy is one whose light is bent and magnified by a massive galaxy cluster sitting in front of them. That process acts similarly to a magnifying glass or fun-house wiggly mirror. I measured the brightnesses of these six galaxies in several wavelength bands from the Hubble Space Telescope (HST) and the Spitzer Space Telescope. Those brightness measurements were the input data to the Prospector algorithm.

Rather than searching for a single "best guess" set of properties, my analysis used a Bayesian approach paired with a technique called Markov Chain Monte Carlo (MCMC) sampling. Instead of asking "what is *the* age of this galaxy," MCMC asks "given the data and its uncertainties, what is the full range of ages consistent with what we observed, and how likely is each one?" It does this by generating thousands of candidate model galaxies, nudging their properties around, and keeping track of which combinations plausibly reproduce the observed brightnesses — gradually building up a probability distribution for each property rather than a single number. This matters because real measurements are noisy and some properties (like stellar mass) turn out to be much better constrained by the data than others (like dust content), so reporting a full range of plausible values is critical to understanding what the data can and can't tell you. My thesis also used a flexible non-parametric approach to modeling star-formation history. This allows the rate of star formation to vary freely over several time bins in the galaxy's past, rather than assuming a simple, one-size-fits-all shape. Past research has shown this method recovers a galaxy's true history with less bias than older, simpler models.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/galaxies.jpg" title="6feild" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/SED_explainer.jpg" title="1343SED" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/SFH_explainer.jpg" title="1343SFH" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Left:</strong> The six galaxies captured with the Hubble Space Telescope. Each galaxy is identified by yellow bars (note that some have multiple images of the same galaxy -- a consequence of gravitaional lensing). <strong>Middle:</strong> A SED plot for one of the six galaxies. The smaller images contain the image of that galaxy in multiple wavelength bands, and point to the dot on the spectral diagram that represents them. <strong>Right:</strong> A simulated star-formation history for one of the galaxies. 
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cornerplot.jpg" title="cornerplot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A sample prospector output. Along the diagonal (from top left to bottom right) the probability distributions of parameters are shown. In the rest of the diagram, parameter correlations are shown.
</div>

Finally, after extensively testing all 6 galaxies, here are the results formatted neatly in a table!

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/prospectoroutput.jpg" title="prospectortable" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

We were able to constrain the stellar mass, statistical measures on the age of the stellar population, and two different types of dust amounts. And equally as important as the values, we were able to rigorously constrain error bars on our measurements.