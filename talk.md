class: middle, center, title-slide
count: false

# Integrating AGC pipeline at BNL facility

.huge.blue[Matthew Feickert]<br>
.large[(University of Wisconsin-Madison)]
<br>
[matthew.feickert@cern.ch](mailto:matthew.feickert@cern.ch)

[IRIS-HEP / AGC Demo Day December 2022](https://indico.cern.ch/event/1211229/contributions/5120858/)
<br>
November 23rd, 2022

.middle-logo[]

---
# Introduction and Overview

<!-- .kol-1-2.large[
- In Tuesday's session, Daniel Katz already gave very nice high level overview of software citation .bold[principles] and .bold[tools]
- This is an .red[opinionated] summary of the tooling landscape and examples of workflows
   - Full disclosure: Opinions formed from pyhf development and from Scikit-HEP community discussions (c.f. [Eduardo's talk](https://indico.cern.ch/event/1211229/contributions/5150204/)).
- Meant to be recommendations to software developers on making your work as .bold[easy to cite as possible]
   - These recommendations can transfer to experiment software as well
]
.kol-1-2[
<br><br>
.center.width-100[[![dan-katz-intro](figures/dan-katz-intro.png)](https://indico.cern.ch/event/1211229/contributions/5120849/)]
.center[[Daniel Katz's talk](https://indico.cern.ch/event/1211229/contributions/5120849/)]
] -->

---
# BNL SDCC Jupyter Launcher --- custom images!

.center.width-100[[![BNL-launcher-page](figures/BNL-launcher-page.png)](https://atlas-jupyter-test.sdcc.bnl.gov/)]


---
# Summary
.kol-2-3.huge[
- Build community practices on top of .bold[established standards]
   <!-- - There are professional communities at work building tools, so we should join them, not rebuild a wheel -->
- If citation of your software is important to you, .bold[make it easy] for a user to find your citation information
- Modern standards like `CITATION.cff` allow for .bold[single source of citation information] that can be exported as needed
- Long term archives + [FAIR practices](https://indico.cern.ch/event/1211229/contributions/5120857/)
   - Zenodo provides automatically release information each release
]
.kol-1-3[
.center.width-80[[![CFF-logo](figures/CFF-logo.png)](https://citation-file-format.github.io/)]

.center.width-100[[![zenodo-logo](figures/zenodo-logo.svg)](https://zenodo.org/)]
]

---
class: end-slide, center

.huge[Backup]

---

class: end-slide, center
count: false

The end.
