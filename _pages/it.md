---
layout: archive
title: "Technical Infrastructure"
permalink: /it/
author_profile: true
toc: true
---

{% include base_path %}


CoBiODA Bioinformatics Hub allows access to a complex technical infrastructure on which is built the data flow for computation and statistical analys of omics data at  [ipmc](http://ipmc.cnrs.fr).
<br>

![IPMC data flow](/images/ipmc_data_flow.png "IPMC data flow"){: style="float: left"}


<br><br>


## UCA GenomiX Bego (march 2022) and Carra (feb. 2019) statistical server

![bego](/images/bego.png "bego"){: style="float: left"}

Directly hosted at IPMC (B23 IT room, administrated by Patrick Chalbet), Bego and Carra allow for statistical analysis within R environment (R server: [bego](http://bego.ipmc.cnrs.fr:8787/) and [carra](http://carra.ipmc.cnrs.fr:8787/)). Bego offers the possibility to run Python notebooks via VSCode software and SSH remote connexion. You will need to be granted a Linux account on the 2 machines, contact [kevin Lebrigand](mailto:lebrigand@ipmc.cnrs.fr).

<i>Configuration (bego) HPE DL380 2 x Xeon-G 6248 2x20 cores, 2Tb RAM, 40Tb disk, 1 GPU Nvidia A100, Debian</i>
<br>
<i>Configuration (carra) DELL PowerEdge R440, Xeon 4 cores, 128Gb RAM, 10 Tb disk, Debian</i>


## Azzurra UniCA MSI grid (2020, upgrade 4D-OMICS plan for june 2024)

![azzurra](/images/azzurra.jpg "azzurra"){: style="float: left"}

Hosted at INRIA (Sophia-Antipolis) this computing grid, administred by Maeva Antoine from the MSI offers a vast amount of possibilities for primary data analysis. Please refers to their dedicated web page for a listing of the computing ressources: [https://calculs.univ-cotedazur.fr/?page_id=450&lang=en](https://calculs.univ-cotedazur.fr/?page_id=450&lang=en). To be granted for access on the computing grid, you can contact directly [Maeva Antoine](mailto:Maeva.ANTOINE@univ-cotedazur.fr), you will need to fill the forms accessible here: [https://calculs.univ-cotedazur.fr/?page_id=1140](https://calculs.univ-cotedazur.fr/?page_id=1140). Note that within the 4D-Omics Equipex+ initiative it is plan to upgrade Azzurra cluster to double its capabilities in terms of CPUs and disk storage when the cluster will be transfered to Valrose Univerity in an IT room labeled "Data center Sud".


<br>

## Mediante and ODIN web server (caire, sept. 2014)

4D-Omics initiative, coordinated by Pascal Barbry, has granted the setup of a specific web server (replaing caire) that will host both [Mediante](https://www.genomique.info:8443/merge/index) (information system of UCA GenomiX platform) and the [Omics Data Integration Network](https://www.genomique.info:8443/odin/index) application dedicated to the management of data analysis concerning genomics, proteomics, flow cytometry and imaging-based spatial transcriptomics accross the different UniCA institutes of biology.

<i>Configuration (caire) : DELL PowerEdge R720, Intel Xeon 2x4 cores, 48Gb RAM, 19Tb disk, Debian</i>
