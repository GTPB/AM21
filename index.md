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

### Instructors

    <table>
    <tr><td>
<img src="pages/images/Erik_Hjerde.jpg" height="220px" width="170px" align="left" style="margin-right: 3%; margin-bottom: 0.3em;">
    <b>Erik Hjerde</b> has a background in biology with a PhD in Genomics. During his career he has been working mainly with prokaryotes with focus on genomics
      and transcriptomics. In the last years, the focus has moved more towards metagenomic analysis on communities from both the human host as well as from
      various ecological habitats. He is the head of one national (Norwegian) work package within ELIXIR, that focuses on providing bioinformatic end user 
      support and training.

    </td></tr>


    <tr><td>
<img src="pages/images/Espen_Robertsen.jpeg" height="220px" width="170px" align="left" style="margin-right: 3%; margin-bottom: 0.3em;">
      <b>Espen Robertsen</b> has a background in biology with a PhD in Metagenomics. While still doing some metagenomic research, his main focus recently has 
        been database integrations and software development. Espen is involved in various ELIXIR projects involving sensitive data, pipeline prototyping,
        administration of the useglaxy.no project and various other topics.


    </td></tr>
    </table>
    </html>
### Learning objectives

    On exit from this training course, the sparticipant will have acquired a theoretical basis and practical experience to understand the basic 
    concepts of metagenomic analysis in order to conduct academic studies related to microbiome samples. This includes:

    * performing advanced downstream analysis on both taxonomic functional profiles
    * performing quality control, assembly and binning of metagenomic sequence data
    * performing functional analysis and resistome analysis of metagenomes


  
#### Software

    All software and databases together with the exercise data will be pre-installed on the course machines you will be using during the practical exercises of the course.

    All data can be downloaded locally through [data](assets/data.zip)


## Detailed Program

    <html>
  <table width="910" align="center">

    <tr>
      <td width="130">
        <b>AM21</b>
      </td>
      <td width="470">
        <b>Applied Metagenomics </b>
      </td>
    </tr>


    <tr>
      <td style="background:#FFCC00">
        <b>Tuesday <br>Nov 2nd</b>
      </td>
      <td style="background:#FFCC00">
        <div align="right">
          <b>Day #1 </b>
        </div>
      </td>
    </tr>

    <!--Day One program -->

    <tr>
      <td>09:30 - 10:00</td>
      <td>
        Introduction to the course and self presentation of the participants<br>
      </td>
    </tr>

    <tr>
      <td>10:00 - 11:00</td>
      <td>
        Introduction to Metagenomics<br>
        Metagenomic sequencing technologies<br>
      </td>
    </tr>

    <tr>
      <td>11:00 - 11:30</td>
      <td style="background:#DCDCDC">
        Coffee Break
      </td>
    </tr>

    <tr>
      <td>11:30 - 12:30</td>
      <td>
        Quality Control<br>
        Hands-on<br>
      </td>
    </tr>

    <tr>
      <td>12:30 - 14:00</td>
      <td style="background:#DCDCDC">
        Lunch Break
      </td>
    </tr>

    <tr>
      <td>14:00 - 16:00</td>
      <td>
        Trimming and filtering<br>
        Hands-on<br>
      </td>
    </tr>


    <tr>
      <td>16:00 - 16:30</td>
      <td style="background:#DCDCDC">
        Tea Break
      </td>
    </tr>

    <tr>
      <td>16:30 - 18:00</td>
      <td>
        Taxonomic classification
      </td>
    </tr>


    <tr>
      <td style="background:#FFCC00">
        <b> Wednesday <br> Nov 3rd</b>
      </td>
      <td style="background:#FFCC00">
        <div align="right">
          <b>Day #2
        </div>
      </td>
    </tr>

    <!--Day Two program -->

    <tr>
      <td>09:30 - 10:00</td>
      <td>
        Morning Wrap-up (what have we done so far?)
      </td>
    </tr>

    <tr>
      <td>10:00 - 11:00</td>
      <td>
        Taxonomic classification: Hands-on<br>
      </td>
    </tr>


    <tr>
      <td>11:00 - 11:30</td>
      <td style="background:#DCDCDC">
        Coffee Break
      </td>
    </tr>

    <tr>
      <td>11:30 - 12:30</td>
      <td>
        Taxonomic classification: Hands-on<br>
      </td>
    </tr>

    <tr>
      <td>12:30 - 14:00</td>
      <td style="background:#DCDCDC">
        Lunch Break
      </td>
    </tr>

    <tr>
      <td>14:00 - 16:00</td>
      <td>
        Comparison of sample groups<br>
        Comparison of sample groups: hands-om<br>
      </td>
    </tr>


    <tr>
      <td>16:00 - 16:30</td>
      <td style="background:#DCDCDC">
        Tea Break
      </td>
    </tr>

    <tr>
      <td>16:30 - 18:00</td>
      <td>
        Comparison of sample groups: hands-om<br>
      </td>
    </tr>


    <tr>
      <td style="background:#FFCC00">
        <b>Thursday <br> Nov 4th</b>
      </td>
      <td style="background:#FFCC00">
        <div align="right">
          <b>Day #3</b>
        </div>
      </td>
    </tr>

    <!--Day Three program -->

    <td>09:30 - 10:00</td>
    <td>
      Morning Wrap-up (what have we done so far?)

    </td>
    </tr>

    <tr>
      <td>10:00 - 11:00</td>
      <td>
        Comparison of sample groups: hands-om<br>
      </td>
    </tr>

    <tr>
      <td>11:00 - 11:30</td>
      <td style="background:#DCDCDC">
        Coffee Break
      </td>
    </tr>

    <tr>
      <td>11:30 - 12:30</td>
      <td>
        Comparison of sample groups: hands-om<br>
      </td>
    </tr>

    <tr>
      <td>12:30 - 14:00</td>
      <td style="background:#DCDCDC">
        Lunch Break
      </td>
    </tr>

    <tr>
      <td>14:00 - 16:00</td>
      <td>
        Genome assembly from metagenomes<br>
        Genome assembly from metagenomes: Hands-on<br>
      </td>
    </tr>


    <tr>
      <td>16:00 - 16:30</td>
      <td style="background:#DCDCDC">
        Tea Break
      </td>
    </tr>

    <tr>
      <td>16:30 - 18:00</td>
      <td>
        Genome assembly from metagenomes: Hands-on<br>
      </td>
    </tr>



    <tr>
      <td style="background:#FFCC00">
        <b>Thursday <br> Nov 5th</b>
      </td>
      <td style="background:#FFCC00">
        <div align="right">
          <b>Day #4</b>
        </div>
      </td>
    </tr>

    <!--Day Four program -->

    <td>09:30 - 10:00</td>
    <td>
      Morning Wrap-up (what have we done so far?)
    </td>
    </tr>

    <tr>
      <td>19:00 - 11:00</td>
      <td>
        Metagenomic binning<br>
        Metagenomic binning (and mapping): hands-on<br>
      </td>
    </tr>


    <tr>
      <td>11:00 - 11:30</td>
      <td style="background:#DCDCDC">
        Coffee Break
      </td>
    </tr>

    <tr>
      <td>11:30 - 12:30</td>
      <td>
        Metagenomic binning (and mapping): hands-on<br>
        Functional classification<br>
      </td>
    </tr>

    <tr>
      <td>12:30 - 14:00</td>
      <td style="background:#DCDCDC">
        Lunch Break
      </td>
    </tr>

    <tr>
      <td>14:00 - 16:00</td>
      <td>
        Functional classification: hands-on<br>
        Resistome profiling<br>
      </td>
    </tr>


    <tr>
      <td>16:00 - 16:30</td>
      <td style="background:#DCDCDC">
        Tea Break
      </td>
    </tr>

    <tr>
      <td>16:30 - 18:00</td>
      <td>
        Resistome profiling: hands-on<br>
        Final wrap-up session
      </td>
    </tr>


  </table>
    </html>



---


### Learning materials


1. Introduction
    - Welcome and introduction to ELIXIR
    - [Introduction to metagenomics](assets/01-intro/Day1_Intro_Metagenomics.pdf)
    - Metagenomic sequencing technologies
2. Quality control
    - [Lecture - Quality control](assets/02-qc/2.QC.pdf)
    - [Exercise - Quality control](pages/02-qc/2.qc.html)
3. Trimming and filtering
    - [Lecture - Trimming and filtering](assets/03-trim/3.Trimming_filtering.pdf)
    - [Exercise - Trimming and filtering](pages/03-trim/3.trim.html)
4. Taxonomic classification
    - [Lecture - Taxonomic classification](assets/04-taxonomy/4.Taxonomic_classification.pdf)
    - [Exercise - Taxonomic classification](pages/04-taxonomy/4.taxonomic.html)
5. Comparison of sample groups
    - [Lecture - Comparison of sample groups](assets/05-comparison/5.SampleGroups.pdf)
    - [Exercise - Comparison of sample groups](pages/05-comparison/5.comparison.html)
6. Genome assembly from metagenomes
    - [Lecture - Genome assembly from metagenomes](assets/06-assembly/6.Assembly_Validation.pdf)
    - [Exercise - Genome assembly from metagenomes](pages/06-assembly/6.assembly.html)
7. Metagenomic binning
    - [Lecture - Metagenomic binning](assets/07-binning/7.Binning.pdf)
    - [Exercise - Metagenomic binning](pages/07-binning/7.binning.html)
8. Functional classification
    - [Lecture - Functional classification](assets/08-functional/8.FunctionalAnalysis.pdf)
    - [Exercise - Functional classification](pages/08-functional/8.functional.html)
9. Resistome profiling
    - [Lecture - Resistome profiling](assets/02-resistome/9.resistome.pdf)
    - [Exercise - Resistome profiling](pages/02-resistome/9.resistome.html)


### Introduction to Linux and Anaconda

1. Lecture, demo and hands-on
    - [Introduction to Linux and Anaconda](assets/00-linux/Module_1_Introduction_to_linux_and_anaconda.pdf)

---
<br/>

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Web_course_template</span> by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">GTPB</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
