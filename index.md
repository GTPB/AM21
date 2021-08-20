---
layout: page
schemadotorg:
  "@context": http://schema.org/
  "@type": CreativeWork
  "genre": TrainingMaterial

  # Course details
       # "name" -> The acronym and extended name of the course, separated by " - "
       # "description" -> Short description of the course
  name: "AM21 - Applied Metagenomics"
  description: ""

  # Keywords -> Consult EDAM:Topic
  keywords:  ""

  # Audience -> Following Elixir-Tess input
  audience: ["Academia/ Research Institution", "Industry", "Non-Profit Organisation", "Healthcare"]

  # Author info
  author:
    - "@type": Organization
      name: "The Gulbenkian Training Programme in Bioinformatics"
      alternateName: "GTPB"
      sameAs: "gtpb.igc.gulbenkian.pt/bicourses/index.html"

  # predominant type of learning resources
  "learningResourceType": ["presentation", "exercise", "scripts", "handout"]

  # Contributor info
  contributor:
    - "@type": Person
      name: "Erik Hjerde"
    - "@type": Person
      name: "Espen Robertsen"
    - "@type": Person
      name: "CO-AUTHOR_3"

  # License & Language & url
  license: https://creativecommons.org/licenses/by/4.0/
  inLanguage: "en-us"
  url: "https://gtpb.github.io/Web_course_template/"
---

## Course Description

This course will give a comprehensive introduction to the research field of metagenomics. It will cover the basic concepts of microbiome analysis of shotgun metagenomic data using state of the art bioinformatics (amplicon sequencing will not be covered). 

The analysis methods that are being introduced are generic for all types of microbiomes, but we will be using data from the human microbiome as showcases. 

The course will start with the main preprocessing steps of raw sequence data, before various downstream analysis will be covered separately. These include taxonomic analysis, assembly, binning, and finally functional analysis with focus on antibiotic resistance genes. The theoretical part for each topic will be introduced via lectures, followed by practical hands-on exercises.

## Target Audience

The course is intended for researchers and students that are, or are planning to work with data analysis of metagenomic data. 

## Detailed Program

To be announced

---

### Learning objectives

The student will have acquired a theoretical basis and practical experience to understand the basic concepts of metagenomic analysis in order to conduct academic studies related to microbiome samples. This includes:

* performing advanced downstream analysis on both taxonomic functional profiles
* performing quality control, assembly and binning of metagenomic sequence data
* performing functional analysis and resistome analysis of metagenomes

### Instructors

**Erik Hjerde** has a background in biology with a PhD in Genomics. During his career he has been working mainly with prokaryotes with focus on genomics and transcriptomics. In the last years, the focus has moved more towards metagenomic analysis on communities from both the human host as well as from various ecological habitats. He is the head of one national (Norwegian) work package within ELIXIR, that focuses on providing bioinformatic end user support and training.

Espen Robertsen

---

The source for this course webpage is [in github](https://github.com/GTPB/Web_course_template).

<br/>

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Web_course_template</span> by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">GTPB</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
