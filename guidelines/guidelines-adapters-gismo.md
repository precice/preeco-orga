---
title: G+Smo adapter guideline
permalink: community-guidelines-adapters-gismo.html
keywords: contribute, develop, adapters, standardization, preECO, G+Smo
summary: A review of the G+Smo adapter using the contributing guidelines.
toc: true
---

The G+Smo adapter conforms to most of the preCICE best practices and fulfills many of the additional criteria.

Metadata:

- M.1: G+Smo
- M.2: https://precice.org/adapter-gismo.html
- M.3: MPL-2.0
- M.4: Jingya Li `<j.li-9@tudelft.nl>`, Hugo Verhelst `<hugomaarten.verhelst@unipv.it>`
- M.5: https://arxiv.org/abs/2505.19346
- M.6: library

Required best practices:

- [x] R.1: Tutorial is available for G+Smo adapter. See, https://precice.org/tutorials-perpendicular-flap-stress.html.
- [x] R.2: [`README.md`](https://github.com/precice/precice.github.io/blob/master/pages/docs/adapters/adapter-gismo.md)
- [x] R.3: [`LICENSE`](https://github.com/gismo/gsPreCICE/blob/main/LICENSE)
- [x] R.4: [GitHub project](https://github.com/gismo/gsPreCICE) (public)
- [ ] R.5: [versioning scheme](https://github.com/gismo/gsPreCICE/releases/tag/v25.07.0) → Still need to add explaination in documentation page.
- [x] R.6: [`CHANGELOG`](https://github.com/gismo/gsPreCICE/releases/tag/v25.07.0) 
- [x] R.7: [issue tracker on GitHub](https://github.com/gismo/gsPreCICE/issues)
- [x] R.8: [Formatting Guidelines](https://github.com/gismo/gismo/wiki/Contributing#code-style-and-formatting)
- [x] R.9: See, for example, https://github.com/gismo/gsPreCICE/blob/main/gsPreCICE.h
- [ ] R.10: Still requires porting of single fields, e.g. `preciceConfig` → `preciceConfigFileName`.
- [x] R.11: See call to `addMesh` in https://github.com/gismo/gsPreCICE/blob/main/gsPreCICE.h

Additional criteria:

- [x] A.1: MPL-2.0
- [x] A.2: [repository](https://github.com/gismo/gsPreCICE) is publicly accessible
- [x] A.3: on precice.org, see, https://precice.org/adapter-gismo.html
- [x] A.4: yes, but only at compile-time
- [x] A.5: [preprint](https://arxiv.org/abs/2505.19346)
- [ ] A.6: There are no guideline for contribution.
- [x] A.7: ['PULL_REQUEST_TEMPLATE.md'](https://github.com/gismo/gsPreCICE/blob/main/.github/PULL_REQUEST_TEMPLATE.md).
- [ ] A.8: There are no software architecture documentation.
- [ ] A.9: There are no unit tests
- [ ] A.10: Have not integrated into the system tests
- [ ] A.11: The adapter is currently not packaged in either the solver community repositories or on Spack.
