# Project-Relevant Literature

#### Table of Contents
- [2006](#2006)
  * [Large-Scale Vulnerability Analysis](#large-scale-vulnerability-analysis)
- [2013](#2013)
  * [PACE](#pace)
- [2015](#2015)
  * [VCCFinder](#vccfinder)
- [2016](#2016)
  * [SV-AF](#sv-af)
- [2017](#2017)
  * [Tags from CWE-based LDA topics](#tags-from-cwe-based-lda-topics)
  * [API-security vulnerability links](#api-security-vulnerability-links)
- [2018](#2018)
  * [Vulnerability by git history](#vulnerability-by-git-history)
## 2006

### Large-Scale Vulnerability Analysis
**Large-Scale Vulnerability Analysis**

_Stefan Frei, Martin May, Ulrich Fiedler, Bernhard Plattner_
<details><summary>bib</summary>

```tex
```

</details>

What: 1. Quantify relations between cybersecurity vulnerability discovery, disclosure, and patching. 2. Assess how responsive the industry is to vulnerabilities. See Figure 2 for good summary of their model of vulnerability lifecycle (cf. Arbaugh et al., 2000). Generally discouraging conclusions: "We find that the number of zero-day exploits is increasing dramatically"; "we observe that the availability of exploits is faster than the availability of patches".

How: Authors used National Vulnerability Database (NVD) and Open Source Vulnerability Database (OSVDB) to get the vulnerabilities but also had to normalize 80k entries (about 14k vulnerabilities) from security information providers refereenced in these databases to get info on disclosure and patching. After consideration, they prefer NVD and SIPs SecurityFocus and ISS X-Force.

Commentary: Strong overview of the vulnerability cycle. Possibly outdated (13 years old). Worthwhile to look at citing papers for updates. Would be interesting to see updated version of Fig. 1, i.e. security disclosures per day and cumulative security disclosures.

Notes: 
1. mention but don't use the common vulnerability scoring system http://www.first.org/cvss/

## 2013

### PACE
**PACE: Pattern Accurate Computationally Efficient Bootstrapping for Timely Discovery of Cyber-Security Concepts**

_Oak Ridge et al._
<details><summary>bib</summary>

```tex
```

</details>

What: Bootstrapping for vulnerability-related entities. Key addition is keeping contextual info along with entity names, specifically a 5-token left context and a 5-token right context. Labeled entity types {Exploit, Exploit Symbol, Vulnerability, Vulnerability Potential Effects, Vulnerable Software, Vulnerability Category, Date} (mutually exclusive).

How: Hand-annotated 10 docs (both NE and context). Stemmed words using NLTK and removed a subset of usual stopwords including punctuation. Phrase chunking, probably through NLTK, is used for entity nomination. The system works on token patterns that are a subset of the context, e.g. "allow attacker to `_`". Proposed patterns must have one of: a. shares at least the rightmost token of an existing left context; b. shares at least the rightmost word of an existing entity; c. shares at least the leftmost token in an existing right context. Bias is toward longer entity phrases. Patterns are specific to entity classes. As a cost-saving measure, patterns are only proposed from contexts with known entities. Patterns are scored using Basilisk scoring, and the top-scoring 50% of entities and 25% of patterns (% not tuned) are kept for the next round of n rounds.

Commentary: Makes an excellent case for our own project, e.g. "Information usually appears in unstructured sources earlier than in structured sources." and this information is spread across multiple sources rather than centralized. This includes large- and small-scale providers like Twitter, Reddit, and individual blogs, recalling previous research on (e.g. flu) outbreak tracking. Weak/generous evaluation on limited dataset, but some useful learning did occur. 23/25 new entity names were correct. Approach inherently limited by lack of syntax. Could work on huge dataset with wider context, but couldn't we get similar things from word2vec or similar? Overall, a promising start.

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

Commentary: The approach is sound, but the authors note internal validity problems from noise and external validity problems from their reliance on well-structured, manually annotated data.


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

Commentary: Multi-labeling task implemented through LDA topic modeling. No formal evaluation or benchmarking. No large-scale confusion matrix beyond first 6 topics. Expressly preliminary.

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

Commentary: Limited evaluation (only 8 CVEs) makes assessment difficult. Comparison against SAP and OWASP tools does not reveal obvious advantage or disadvantage.

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

Commentary: 
