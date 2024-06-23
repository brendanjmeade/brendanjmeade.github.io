---
layout: page
permalink: /software/
title: software
description: 
nav: true
---




#### celeri - [github](https://github.com/brendanjmeade/celeri)
- Next generation python based imaging of earthquake cycle, fault and plate kinematics
- Easy to use python foundation
- Convenient automated block closure
- Memory efficient H-matrix compression 
- Standardized file formats
- Fast C/Fortran elastic calculations 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/software/celeri.jpeg" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>
<br>


#### skies - [github](https://github.com/brendanjmeade/skies)
- A python-based package designed to generate three-dimensional earthquake sequences in time across geometrically complex fault systems using kinematically constrained loading and emperical statistical models.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/software/skies.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>
<br>


#### bem2d.jl - [github](https://github.com/brendanjmeade/bem2d.jl)
- Two-dimensional elastic boundary elements with quadratic shape functions
- Written in Julia
- Quadratic shape functions for more accurate near-field stress calculations
- Supported element interactions
  -  displacement &#8594; displacement
  -  displacement &#8594; traction (use with caution)
  -  traction &#8594; displacement (use with caution)
  -  traction &#8594; traction (use with caution)
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/software/bem2d.jpeg" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>
<br>


#### Triangular dislocation elements - [github](https://github.com/brendanjmeade/tde)
- A Matlab implementation of the analytic solutions for the displacements, strains, and stresses caused by spatially uniform slip on a triangular dislocation element in a homogeneous elastic half space
- [Richard Styron](https://rocksandwater.net/) has [a great python port](https://github.com/cossatot/tri_dislocations_python)
- Superceded by the [Nikhoo and Walters (2015)](https://academic.oup.com/gji/article/201/2/1119/572006) singularity reducing improvements with [Ben Thompson's](https://tbenthompson.com/) [amazing CUDA implementation (100 million TDEs per second)](https://github.com/tbenthompson/cutde)
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/software/tdes.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>
<br>


#### Machine learning aftershock locations - [github](https://github.com/phoebemrdevries/Learning-aftershock-location-patterns)
- A Python pipeline for learning (using [Keras](https://keras.io/)) the relationships between mainshock (from the [SRCMOD catalog](http://equake-rc.info/srcmod/)) static elastic stress changes and aftershock locations.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/software/nn_aftershocks.jpeg" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<br>
<br>
