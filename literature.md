# Project-Relevant Literature

#### Table of Contents
- [2015](#2015)
  * [VCCFinder](#vccfinder)

## 2015

### VCCFinder
*VCCFinder: Finding potential vulnerabilities in open-source projects to assist code audits*
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
*SV-AF – A Security Vulnerability Analysis Framework*
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

Links existing resources, specifically the National Vulnerability Database and the Maven build repository, showing that 750 releases are directly affected by known vulnerabilities (less than 0.1%), and 400k are affected through dependencies. The general approach is to populate two ontologies corresponding to the NVD and Maven, then align the ontologies (i.e., determine whether a release in one ontology is the `sameAs` a release in the other ontology). Alignment is achieved through Probabilistic Soft Logic (PSL), scoring releases as more similar if they have similar names and version numbers, for example. Once the ontologies are aligned, OWL reasoning is straightforward to reveal projects dependent on direclty vulnerable projects. The approach is sound, but the authors note internal validity problems from noise and external validity problems from their reliance on well-structured, manually annotated data.

## 2017

