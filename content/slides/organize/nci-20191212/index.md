---
title: Organizing Data Science Projects
url: "/slides/organize/nci-20191212/"
image: "/slides/organize/nci/cover.jpg"
description: ""
ratio: "16:9"
themes:
- apron
- adirondack
- descartes
- slides
classes:
- feature-qrcode

---
class: title, smokescreen
background-image: url(https://media.defense.gov/2017/Jun/22/2001767169/-1/-1/0/170519-F-OR423-002.JPG)

# Organizing Data Science Projects

## CBIIT/FNL Workshop -- December 12, 2019

---
class: col-2

# About

## Justin M. Fear

- IRTA Fellow (NIDDK/NIH)
  - <i class="fas fa-dna"></i> Genomics
  - <i class="fas fa-project-diagram"></i> Gene Regulation
  - <img src="/datascience_presentations/images/drosophila-wt.jpg" width="4%"/> Drosophila

- Contact:
  - <i class="fab fa-github"></i> [@jfear](https://github.com/jfear)
  - <i class="fas fa-envelope-open-text"></i> justin.fear@nih.gov

<!-- TODO Fix publication URL -->
.qrcode.db.pa-3.w-90pct.ml-4[]
<http://talks.geneticsunderground.com>

---
class: title, smokescreen
background-image: url("/datascience_presentations/images/organization.jpg")

# Why Project Organization <!-- Part 1 -->

---
class: img-right-full, roomy

# Find things quickly

![](https://cdn.pixabay.com/photo/2017/02/13/16/10/scooby-doo-2063042_960_720.png)

- Find the code used to generate result
- Tweak a plot
- Pickup where you left off

.myheader[\> Why Project Organization]

---
class: img-right, roomy

# Share code and results

![](https://i.imgflip.com/1ulazs.jpg)

- Send snippets to collaborator
- Show colleague what you did
- Track tangential analysis

.myheader[\> Why Project Organization]

---
class: img-right, roomy

# Recover from data disasters

![](https://live.staticflickr.com/4017/4529320513_ba3d22388f_z.jpg)

- Oops we swapped sample names
- Forgot to give you these addition 10 samples
- The file we sent you was truncated
- I accidentally deleted your folder on the share drive

.myheader[\> Why Project Organization]

---
class: img-caption, roomy

![](https://miro.medium.com/max/1838/1*ACoKY0p7DSt4FGcZNjkP2Q.jpeg)

# Reproducible Research

.myheader[\> Why Project Organization]

---
class: title, smokescreen
background-image: url(https://summary.org/wp-content/uploads/2018/12/Messy02.jpeg)

# Don't Do This <!-- Part 2 -->

## How to make a mess

---
class: col-2

# Poor uses of file names

## Version Control

<pre><code class="Shell">
├── deg_lmm_v1.sh
├── deg_lmm_v2.sh
├── deg_lmm_final.sh
<mark class="highlight">├── deg_jmf_final_v2.sh</mark>
</code></pre>

- If you name something final, you will always have another version.

## Workflow

<pre><code class="Shell">
├── deg_step1_jmf_v1.sh
├── deg_step2_jmf_v1.sh
<mark class="highlight">├── deg_step2a_jmf_v1.sh</mark>
├── deg_step3_jmf_v1.sh
</code></pre>

- Adding or re-ordering steps is confusing at best.

.absolute.center.w-6-12th.pa-1.l-3-12th.b-1.ba.bw-3.br-4.bg-white-60pct[
Make file names descriptive and concise.
]

.myheader[\> Don't do this]

---
class: img-right-full, compact

# Poor uses of folders

![](/datascience_presentations/images/lots_o_files.png)

## One folder to rule them all

- Hard to browse ≥ 30 files
- Search requires you to know what you are looking for

## Too many folders

- Lots folder levels are hard to browse too
- Easy to loose files

.w-10-12th.pa-1.ba.bw-3.br-4.bg-white-60pct.fs-90[
Make your own folder hierarchy and stick to it.
]

.myheader[\> Don't do this]

---
class: col-2, compact

# Poor uses of scripts

## Comment and Uncomment

```bash
# Run first
# wget ...
# export FILE="./this_file.txt"
# ... 300 more lines of code ...

# Run third
export FILE="./that_file.yaml"
do_more_stuff()
```

- Doesn't track what was done
- Generates different results if run in different order

## Copy and Paste

- A script is meant to be run
- Don't copy and paste from a script

> Beginners often write lots of comments describing each step.
> They the copy and paste from the script onto the command line.

.myheader[\> Please don't do this]

---
class: title, smokescreen
background-image: url(http://www.freestufffinder.com/wp-content/uploads/2018/08/tina-marie-kondo-folding-method.jpg)

# How to get organized <!-- Part 3 -->

---
class: img-right-full, compact

# Master Your Weapons <!-- Part 3a: Tools -->

![](https://p2.piqsels.com/preview/213/564/1010/yoda-lego-legoland-star-wars.jpg)

- Development Environment
- Version Control
- Workflow Tools

---
class: col-2

# Development Environment

- Command Line Editors
  - Vim, Emacs, Nano
- Data Science IDEs
  - <img src="/datascience_presentations/images/rstudio.png" width="30%" style="vertical-align: middle;">
  - <img src="/datascience_presentations/images/jupyter_logo.png" width="15%" style="vertical-align: middle;">

---
class: img-left-full, compact

# Tools of the trade (VCS)

![](/datascience_presentations/images/git_commit.png)

## Version Control Software

- Use VCS such as git
> VCS is like MS Words track changes

- Use the cloud to store to your code
> Github, GitLab, and Bitbucket are common places to store
> your version controlled code.
>
> You can make code private or public, and it is available 
> anywhere with internet.

---
class: img-right

# Tools of the trade (Workflows)

![](/datascience_presentations/images/rnaseq.png)

- Orchestrate analysis using workflow software
  - Galaxy
  - Make
  - Snakemake

---
class: img-right

# Project Folder Organization

![](/datascience_presentations/images/example_folder.png)

- Folder structure is personal preference
- Folder names are personal preference

## There are general .red[*best practices*]

---

.absolute.l-7-12th.w-40pct[

# 1. Use the same folder structure and names across projects

]

![](example_folder.png# absolute l-0 t-0 h-100pct)

---
class: compact

# 2. Separate original data, generated data, and scripts

## .red[Not stored in version control]

.fl.db.w-40pct[
```bash
├── data # original and external
├── lcdb-references # multi-project
├── output # generate output
```

- Improves mobility
- Delineates what you generated
- Allows reuse of common data across projects

.bq-shrink[
> I work on multiple computers.
> I store data in a single location and mount the drive remotely.
> I can do more locally instead of messing with Biowulf.
]

]

.fr.db.w-55pct[
```bash
data # original and external
├── external
│   ├── DroID_DPiM_2018-03-29.txt # website
│   ├── Ferrari_et_al_2006.tsv # paper
│   ├── Ferrari_et_al_2006.readme # paper details 
│   ├── FlyBase/ # community
│   └── maria/ # collaborator
├── rnaseq_samples # our data
│   ├── ...
│   └── w1118_LG_m_r4_B_C12.fastq.gz
└── singleCellSeqData # out data
    ├── ...
    └── SV_9_10X_Te/
```

]

---
.absolute.l-2.w-30pct[

# 3. Uses workflows to orchestrate

```bash
./example1-wf
├── config
│   ├── config.yaml
│   └── sampletable.tsv
├── scripts/
└── Snakefile
```
]

![](/datascience_presentations/images/snakefile.png# absolute l-40pct t-0 h-100pct)

---
.absolute.l-2.w-40pct[

# 4. Modularize reusable code

```bash
lcdb-wf@56c948d  #submodules
src/    # project level package
├── my_project
│   ├── io.py
│   ├── plotting.py
│   └── stats.py
├── tests/
│   ├── test_io.py
│   └── test_stats.py
└── setup.py
```
]

![](/datascience_presentations/images/modularize.png# absolute l-50pct t-0 w-50pct)

---
class: compact

.absolute.l-2.w-40pct[

# 5. Use a style guide and linters

* Consistent style improves readability
* Just google my language and style guide
* Linters catch syntax erros and point out style problems.
    - `flake8   # python`
    - `lintr    # R`

* Fix ugly code with software
    - `black   # python`
    - `styler   # R`
]

.fr.db.w-50pct[
<pre><code class="R" style="font-size: .9rem">
for (i in seq(10)) {
for (j in seq(100)) {
if (i == j) {
print(TRUE)
} else if (i %% j == 0) {
print("modulo")
} else {
print(FALSE)
}
}
}
</code></pre>

<pre><code class="R" style="font-size: .9rem">
for (i in seq(10)) {
  for (j in seq(100)) {
    if (i == j) {
      print(TRUE)
    } else if (i %% j == 0) {
      print("modulo")
    } else {
      print(FALSE)
    }
  }
}
</code></pre>
]

---
class: compact

# 6. Split out configuration for consistency

.absolute.l-2.w-40pct[
```bash
./config   # Project config
    ├── common.yaml
    ├── gene_sets.yaml
    └── colors.yaml

./example1-wf   # Workflow config
    ├── config
    │   ├── config.yaml
    │   └── sampletable.tsv

```
]

.fr.db.w-50pct[

## Project config

Contains info that is needed across the project.

* Project name and github url
* Assembly and Annotation
* alpha level

## Workflow config

Anything you may tweak in the future.

* Various thresholds
* Workflow specific references
* Various Mappings (i.e. file name to title)

]

---
class: fit-h1, compact

# 7. Use containers and environments (portability and reproducibility)

One of the hardest problems in data science is managing software.

.absolute.l-2.w-40pct[
```bash
./environment.yaml  # project env

./envs   # specific tools conda envs
    ├── deseq2.yaml
    ├── scrublet.yaml
    ├── seurat2.yaml
    └── seurat3.yaml


```
]

.fr.db.w-50pct[

## Containers (Docker, Singularity)

* Completely reproducible system
    * Kernel and Software

## Environments (Conda, pipenv)

* Install and manage software versions
* Different versions of software can be installed in different environments

]

---
class: title, smokescreen
background-image: url(https://www.mayerdan.com/assets/img/ring-binders.jpg)

# 8., 9., 10. Documentation <!-- Part 4 -->

## What is not documented, stays not documented

---

# What to document (Everything!)

.ul-space[
* How was the data generated
* Record all "experiments"
.red[
- failed attempts
- comparing different methods
]
* Record the reasoning for any decision points
* Clearly describe how to get final results
]

**6 months from now, your future-self will thank you!**

---

# Where to document (Everywhere!)

.ul-space[
* Sample/Resource Table
* README
* Top of scripts
* Function/Class Docstrings
* Code comments (but not too many)
* Literate Programming (i.e. notebooks)
* Project Blog
]

---
layout: true
.myheader[\>Where to document]

---
class: compact

# Sample Table

```bash
./example1-wf
    ├── config
    │   ├── config.yaml
    │   └── sampletable.tsv
```

| samplename | orig_filename         | group | wellID | row | col | num_parts | sex | testis | ovary | fatbody | ercc |
|------------|-----------------------|-------|--------|-----|-----|-----------|-----|--------|-------|---------|------|
| A1_OCP     | ....A1_OCP_1.fastq.gz | OCP   | A1     | A   | 1   | 25        | f   | 0      | 1     | 0       | A    |
| A6_TCP     | ....A6_TCP_2.fastq.gz | TCP   | A6     | A   | 6   | 15        | m   | 1      | 0     | 0       | B    |

Add as much information about your samples.

---

# Top of Scripts

.fl.db.w-50pct[
.ul-space[
* Describe what the script does
* Any major decisions that you made
* Anything to help you remember
]
]

![](/datascience_presentations/images/script_doc.png# absolute l-6-12th t-0 h-100pct)

---

# Functions and Classes

.fl.db.w-50pct[
.ul-space[
* Any function you will call from another script.
* Add type hints if it is confusing what goes in.
* Add examples to clearly show what the function does.
]
]

![](modularize.png# absolute l-6-12th t-0 w-50pct)

---

# Literate Programming

.fl.db.w-50pct[
```bash
./notebook
    ├── 2019-08-01_bulk_deg.Rmd
    └── 2019-08-10_bulk_ma.ipynb

./docs
    ├── cell_number_counts.ipynb
    └── permutation_summary.ipynb
```

.ul-space[
* Jupyter Notebooks
* R Notebooks and Rmarkdown
]
]

![](/datascience_presentations/images/jupyter.png# absolute l-6-12th t-0 w-50pct)

.footer[https://github.com/markusschanta/awesome-jupyter]

---

# Dedicated Project Blog

.ul-space[
* Aggregate notebooks
    - `bookdown  # R`
    - `jupyter webbook  # python`
* Various static site generators
    - Pelican
    - Nikola
    - jekyll
    - **hugo**
]

![](/datascience_presentations/images/blog.png# absolute l-6-12th t-0 w-50pct)

---

# 10 Best Practices <!-- Summary -->

<ol>
<li>Use the same structure and names across projects</li>
<li>Separate original data, generated data, and scripts</li>
<li>Use workflows to orchestrate</li>
<li>Split out configuration for consistency</li>
<li>Modularize reusable code</li>
<li>Use a style guide and linters</li>
<li>Use containers and environments</li>
<li style="font-size: 1em;">Document as you go</li>
<li style="font-size: 1.2em;">Document as you go</li>
<li style="font-size: 1.6em; font-weigth: bold">Document as you go!</li>
</ol>

---
class: title, fogscreen
background-image: url(http://www.paautism.org/LinkClick.aspx?fileticket=A1L9cYFyoTg%3D&tabid=101&portalid=0&mid=771&language=en-US)

# Resources

---
layout: true

---
.myheader[\>Resources]
* Cookiecutter
* Github
* Bitbucket
* Snakemake
* Data Science git-flow
