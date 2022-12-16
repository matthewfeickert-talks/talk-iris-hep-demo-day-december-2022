class: middle, center, title-slide
count: false

# Software Citation Tools, Technologies,<br> and Best Practices

.huge.blue[Matthew Feickert]<br>
.large[(University of Wisconsin-Madison)]
<br>
[matthew.feickert@cern.ch](mailto:matthew.feickert@cern.ch)

[Software Citation and Recognition in HEP Workshop 2022](https://indico.cern.ch/event/1211229/contributions/5120858/)
<br>
November 23rd, 2022

.middle-logo[]

---
# Introduction and Overview

.kol-1-2.large[
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
]

---
# Make clear how to cite in documentation

.kol-1-2.large[
- The easiest, but least robust way: If you have a particular citation that you want people to use, put it .bold[everywhere]
   - Version control repository README
   - Online software documentation (landing page, how to cite page)
   - Package distribution websites (e.g. PyPI)
- Having single source of truth for citations: version control repository that all other sources derive from.
- Make your citation preferences clear to the world and SEO. Do not rely on people emailing to ask (they shouldn't have to).
]
.kol-1-2[
.center.width-100[[![pyhf-citation-request](figures/pyhf-citation-request.png)](https://pyhf.readthedocs.io/en/stable/citations.html)]
.center[[pyhf's "Use and Citations" page in documentation](https://pyhf.readthedocs.io/en/stable/citations.html)]
]

---
# CITATION.cff

.kol-3-5.large[
- Adopt the [Citation File Format](https://citation-file-format.github.io/) as a common standard and add a `CITATION.cff` to project repository
   - Human- and machine-readable file format in YAML
   - Has well defined, versioned schema
   - Convertible to other citation formats (BibTeX, CodeMeta, EndNote, RIS, schema.org, Zenodo, APA)
- Supported by [GitHub](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files), [Zenodo](https://twitter.com/ZENODO_ORG/status/1420357001490706442), and [Zotero](https://twitter.com/zotero/status/1420515377390530560)!
- [Web tool initializer](https://citation-file-format.github.io/cff-initializer-javascript/) for easily creating first `CITATION.cff`
- [Tooling for validation](https://github.com/citation-file-format/cff-converter-python)
.tiny[
```console
$ python -m pip install cffconvert
$ cffconvert --validate
Citation metadata are valid according to schema version 1.2.0.
```
]
]
.kol-2-5[
.tiny[
```
cff-version: 1.2.0
message: "If you use this software, please cite it as below."
authors:
  - family-names: Druskat
    given-names: Stephan
    orcid: https://orcid.org/0000-0003-4925-7248
title: "My Research Software"
version: 2.0.4
doi: 10.5281/zenodo.1234
date-released: 2021-08-11
```
]

.center[Example of minimal `CITATION.cff`]

.center.width-100[[![citation-link](figures/citation-link.png)](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files)]
]

---
# CITATION.cff: How to keep up to date?

.large[
- As plain text, very easy to update version information when cutting a release
- Can use tool control of version update to make it easier
   - Example: [`tbump`](https://github.com/your-tools/tbump)
   - `$ tbump <version target>`
- Also possible to have [automated version bump workflows](https://github.com/scikit-hep/pyhf/blob/d9355e23ffd4aceb24041c51c697a55fa40a3d94/.github/workflows/bump-version.yml) using continuous integration
- (Jumping ahead a slide) What about the Zenodo DOI?
   - For simplicity, use the project level DOI and not the version level DOI
]

.smaller[
```yaml
cff-version: 1.2.0
message: "Please cite the following works when using this software."
type: software
...
title: "mylibrary: v1.2.3"
version: 1.2.3
doi: 10.5281/zenodo.1123456
repository-code: "https://github.com/myorg/mylibrary/releases/tag/v1.2.3"
url: "https://mylibrary.readthedocs.io/en/v1.2.3/"
```
]

---
# Zenodo

.kol-1-2[
.center.width-100[[![zenodo-landing-page](figures/zenodo-landing-page.png)](https://zenodo.org/)]

- Open source (but your files can be closed access)
- Versioned archival of everything: code, documents, data products, data sets
]
.kol-1-2[
.center.width-75[[![why_use_zenodo](figures/why_use_zenodo.png)](https://zenodo.org/)]
]

---
# Zenodo: DOI minting made easy

- Everything on Zenodo has a DOI
   - Provides both a .bold[project] DOI (resolves to latest) and .bold[version specific] DOI
- Enable it to [automatically preserve work from GitHub](https://guides.github.com/activities/citable-code/) (can also directly upload, but lose out on automation)
   - Benefit from having a DOI for .bold[every version] regardless of software paper landscape state
- Once you have a DOI, put it .bold[everywhere] (again)
   - Recommend sharing the project DOI and letting users select a specific version if they want it

.center[
.width-80[[![Zenodo_DOI_guide](figures/Zenodo_DOI_guide.png)](https://zenodo.org/account/settings/github/)]
]

---
# Zenodo + CITATION.cff

.center.large[CITATION.cff used by Zenodo importer to fully define Zenodo archive metadata]

.kol-1-2[
.center.width-85[[![pyhf-citation-cff](figures/pyhf-citation-cff.png)](https://github.com/scikit-hep/pyhf/blob/d9355e23ffd4aceb24041c51c697a55fa40a3d94/CITATION.cff)]
]
.kol-1-2[
.center.width-110[[![pyhf-zenodo-page](figures/pyhf-zenodo-page.png)](https://zenodo.org/record/7110486)]
]

---
# Zenodo: Communities allow archival collections

.kol-1-2[
.center.width-100[[![Zenodo_communities_PyHEP](figures/Zenodo_communities_PyHEP.png)](https://zenodo.org/communities/?p=PyHEP)]
]
.kol-1-2[
<br>
.center.width-100[[![Zenodo_communities_ATLAS](figures/Zenodo_communities_ATLAS.png)](https://zenodo.org/communities/atlas_experiment/)]
]

---
# Proving a citation information from APIs

.kol-2-3.large[
- In addition to providing standard formats, providing users a language API or CLI API to get the citation information for the version of the tool is helpful
   - User doesn't have to check if the information they find online matches their version.
- Historically, this was done by printing a banner with citation or copyright information when the library is used
   - This should .bold[not] be done now. This creates noise for users and if multiple tools did this your terminal would get filled.
   - Most libraries that used to do this have now abandoned this approach.
- Opinion: There are tools in broader scientific ecosystem that provide citation information for their dependencies as well. While very conscientious, I think this is .bold[unnecessary] and can be confusing to users.
]
.kol-1-3[
<br><br>
```console
# CLI API
$ mytool --citation
$ mytool --cite
```
```python
# Python API
import mytool
mytool.utils.citation()
```
.center.large[Example APIs]
]

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
# Does any of this actually work?

As mentioned, these opinions have been formed from developing pyhf, and the citation count for the [JOSS paper](https://doi.org/10.21105/joss.02823) has increased each year.

.center.width-100[[![pyhf-inspire-citations-count](figures/pyhf-inspire-citations-count.png)](https://inspirehep.net/literature?sort=mostrecent&size=25&page=1&q=refersto%3Arecid%3A1845084&ui-citation-summary=true)]

---

class: end-slide, center
count: false

The end.
