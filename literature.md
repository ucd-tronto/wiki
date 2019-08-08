# Project-Relevant Literature

#### Table of Contents
- [2015](#2015)
  * [VCCFinder](#vccfinder)
- [2016](#2016)
  * [SV-AF](#sv-af)
- [2017](#2017)
  * [Tags from CWE-based LDA topics](#tags-from-cwe-based-lda-topics)
  * [API-security vulnerability links](#api-security-vulnerability-links)
- [2018](#2018)
  * [Vulnerability by git history](#vulnerability-by-git-history)

## 2015

### VCCFinder
**VCCFinder: Finding potential vulnerabilities in open-source projects to assist code audits**

_Henning Perl, Sergej Dechand, Matthew Smith, Daniel Arp, Fabian Yamaguchi, Konrad Rieck, Sascha Fahl, & Yasemin Acar_
<details><summary>bib</summary>

```tex
@inproceedings{perl2015vccfinder,
  title={VCCFinder}: {F}inding potential vulnerabilities in open-source projects to assist code audits},
  author={Perl, Henning and Dechand, Sergej and Smith, Matthew and Arp, Daniel and Yamaguchi, Fabian and Rieck, Konrad and Fahl, Sascha and Acar, Yasemin},
  booktitle={{Proceedings of the 22nd ACM SIGSAC Conference on Computer and Communications Security}},
  pages={426--437},
  year={2015},
  organization={ACM}
}
```

</details>

## 2016

### SV-AF
**SV-AF – A Security Vulnerability Analysis Framework**

_Sultan S. Alqahtani, Ellis E. Eghan, & Juergen Rilling_
<details><summary>bib</summary>

```tex
@inproceedings{alqahtani2016sv,
  title={{SV-AF}---{A} Security Vulnerability Analysis Framework},
  author={Alqahtani, Sultan S and Eghan, Ellis E and Rilling, Juergen},
  booktitle={{2016 IEEE 27th International Symposium on Software Reliability Engineering (ISSRE)}},
  pages={219--229},
  year={2016},
  organization={IEEE}
}
```

</details>

What: Links existing resources, specifically the National Vulnerability Database and the Maven build repository, finding 750 releases directly affected by known vulnerabilities (less than 0.1%), and 400k affected through dependencies.

How: The general approach is to populate two ontologies corresponding to the NVD and Maven, then align the ontologies (i.e., determine whether a release in one ontology is the `sameAs` a release in the other ontology). Alignment is achieved through Probabilistic Soft Logic (PSL), scoring releases as more similar if they have similar names and version numbers, for example. Once the ontologies are aligned, OWL reasoning is straightforward to reveal projects dependent on direclty vulnerable projects.

Conclusion: The approach is sound, but the authors note internal validity problems from noise and external validity problems from their reliance on well-structured, manually annotated data.


## 2017

### Tags from CWE-based LDA topics
**An Ontology-based Approach to Automate Tagging of Software Artifacts**

_Sultan S. Alqahtani & Juergen Rilling_
<details><summary>bib</summary>

```tex
@inproceedings{alqahtani2017ontology,
  title={An ontology-based approach to automate tagging of software artifacts},
  author={Alqahtani, Sultan S and Rilling, Juergen},
  booktitle={Proceedings of the 11th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement},
  pages={169--174},
  year={2017},
  organization={IEEE Press}
}
```

</details>

What: Tag bug reports with Common Weakness Enumeration (CWE) entities based on seeded-LDA topics.

How: Tokenize existing dataset of bug reports (with sections {Title, Bug Description, Commit Messages}) and remove stopwords. Map CWE ontology to bug report concerns ontology, and use the modeled security concepts (just the names? unclear) to seed a seeded-LDA topic model. Most popular tags found are "access privilege (53%), SQL injection (40%) and authentication abuse (6.7%)." How ontology mapping is done isn't discussed, but it's probably similar to [SV-AF](#sv-af) given the authors. It's not super clear why the ontology mapping would be necessary since the dataset has its own tags.

Conclusion: Multi-labeling task implemented through LDA topic modeling. No formal evaluation or benchmarking. No large-scale confusion matrix beyond first 6 topics. Expressly preliminary.

Notes:
1. Used dataset from [10.1109/ICPC.2015.10](https://doi.org/10.1109/ICPC.2015.10)

### API-security vulnerability links
**Recovering semantic traceability links between APIs and security vulnerabilities: An ontological modeling approach**

_Sultan S. Alqahtani, Ellis E. Eghan, & Juergen Rilling_
<details><summary>bib</summary>

```tex
@inproceedings{alqahtani2017recovering,
  title={Recovering semantic traceability links between APIs and security vulnerabilities: An ontological modeling approach},
  author={Alqahtani, Sultan S and Eghan, Ellis E and Rilling, Juergen},
  booktitle={2017 IEEE International Conference on Software Testing, Verification and Validation (ICST)},
  pages={80--91},
  year={2017},
  organization={IEEE}
}
```

</details>

What: Detect API reliance on vulnerable code to avoid recommending vulnerable (versions of) APIs.

How: Align SEVONT, SBSON, and SEON ontologies using Semantic Web Rule Language (SWRL) rules and Probabilistic Soft Logic (PSL) as in [SV-AF](#sv-af). Linking takes advantage of commit messages that reference CVE IDs.

Conclusion: Limited evaluation (only 8 CVEs) makes assessment difficult. Comparison against SAP and OWASP tools does not reveal obvious advantage or disadvantage.

Notes:
 1. Intro: 88% of application code is from open source, of which 26% have vulnerabilities.
 2. See Fig. 4 for a good illustration of relevant ontology entities

## 2018

### Vulnerability by git history
**Vulnerability Detection in Source Code Based on Git History**

_Kenta Yamamoto_
<details><summary>bib</summary>

```tex
@mastersthesis{yamamoto2018,
  author={Kenta Yamamoto}, 
  title={Vulnerability by git history},
  school={Japan Advanced Institute of Science and Technology},
  year={2018},
  doi={10.13140/RG.2.2.28338.09922},
  url={https://dx.doi.org/10.13140/RG.2.2.28338.09922}
}
```

</details>

What: 

How: 

Conclusion: 
