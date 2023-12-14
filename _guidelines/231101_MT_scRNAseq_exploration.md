---
title: "L'exploration de données single-cell RNA-seq"
excerpt: ""
collection: guidelines
date: 2023-11-27
---

<i>Author: Marin Truchi</i>


L’essor du single-cell RNA-seq a rapidement permis de dépasser la principale limite du "bulk" RNA-seq : passer d’une [résolution tissulaire à la résolution cellulaire](/guidelines/231101_MT_scRNAseq_introduction "Introduction au scRNA-seq"). Il a ainsi redéfini l’hétérogénéité des tissus biologiques en condition physiologique, par la caractérisation précise des profils d’expression de types cellulaires connus et par la mise en évidence de types cellulaires ou d’états cellulaires intermédiaires de processus de développement et de différenciation jusque là inconnus. Le scRNA-seq a également démontré la nécessité de prendre en compte l’hétérogénéité cellulaire dans l’étude des variations transcriptomiques induites par des pathologies, des stimuli, ou des modifications génétiques.

En permanente évolution depuis le début des années 2010, le single-cell RNA-seq est aujourd'hui une technologie mature en termes de protocoles et d’outils d’analyse. Elle s’est ainsi installée comme un nouveau standard de résolution pour la génomique fonctionnelle dont l'application massive et toujours croissante concerne la plupart des systèmes biologiques étudiés à travers le monde.

<figure>
  <img src="/images/scRNAseq.PNG" alt="scRNA-seq PubMed"/>
  <figcaption>L'essor du single-cell RNA-seq</figcaption>
</figure>


## Une quantité considérable de données en libre accès
Cette application massive vise notamment à constituer des "atlas cellulaire", dont la quantité et la répartition histologique des échantillons séquencées permet l'identification et la caractérisation moléculaire précise de l'ensemble des populations cellulaires présentes dans le tissu d'intérêt. Un grand nombre de tissus ont ainsi été cartographiés dans des atlas cellulaires d'organes individuels, voir pour certains dans des atlas issus de collaborations internationales à l'échelle d'organismes complets, tel que le [Human Cell Atlas](https://www.humancellatlas.org/ "The Human Cell Atlas") ou la [Tabula Muris](https://tabula-muris.ds.czbiohub.org/ "Tabula Muris"). En plus de ces atlas physiologiques, certains ont été générés à partir de tissus pathologiques issus de modèles d'études ou d’échantillons cliniques ([Cancers](https://ngdc.cncb.ac.cn/cancerscem/index "Cancer Single-cell Expression Map"), [Alzheimer](https://cellxgene.cziscience.com/collections/1ca90a2d-2943-483d-b678-b809bf464c30 "Seattle Alzheimer’s Disease Brain Cell Atlas"), [IPF](http://www.ipfcellatlas.com/ "IPF Cell Atlas")).

L'objectif de ces différents projets étant également de servir de ressource et de référence pour d'autres études, en s'inscrivant dans un contexte de science ouverte et reproductible, leurs données sont (quasiment) systématiquement disponibles en libre accès dans des dépôts publics (c'est généralement une condition requise pour la publication).

Le format sous lequel ces données sont déposées n'est pas totalement standardisé et varie en fonction des laboratoires, mais il s'agit généralement des matrices de comptes bruts de chaque échantillon et éventuellement des méta-données associées (données cliniques, traitement, annotations ...). Dans ce cas, [l'analyse secondaire](/guidelines/231101_MT_scRNAseq_analysis_1 "l'analyse secondaire") des données est à reproduire, même si dans certains cas les matrices de comptes déposées correspondent à des cellules déjà filtrées et annotées. Les auteurs déposent parfois le fichier d'analyse correspondant aux figures de la publication. Les lectures de séquençages brutes ("reads" au format .fastq) sont quant à elles plus rares du fait de leur taille et des éventuels problèmes d'anonymisation des patients que ces données pourraient poser. Du fait de la relative standardisation des processus d'alignement et de comptage, l'absence de ces données ne pose pas réellement de problèmes pour l'exploration de données publiques, qui peut démarrer à partir des matrices de comptes bruts. Les modalités d'accès à ces données sont indiquées dans les sections dédiées ("Data availability"), généralement en fin de publication. Très souvent, il s'agit d'un numéro d'accès à rentrer dans la base de données [GEO](http://www.ipfcellatlas.com/ "Gene Expression Omnibus") (Gene Expression Omnibus), qui garantit une relative standardisation des formats de fichiers et des informations déposés ainsi qu'un accès rapide à leur téléchargement.

De plus, il est de plus en plus exigé que l'accessibilité aux données s'accompagnent d'une accessibilité aux codes et aux versions de logiciels/packages ayant permis l'analyse et la production de figures, notamment via la plateforme [Github](https://docs.github.com/en/get-started/quickstart/hello-world "Github"). Certains groupes accompagnent même leur publication de portails et d'application web interactives afin de faciliter l'accès à leurs données. Si ces ressources permettent de se faire une première idée sur les données, leur exploitation est limitée par le type et le nombre d'outils de visualisation qu'ils proposent.


## Trouver un dataset publique
Si l'accès aux données est généralement simple, trouver un dataset publique correspondant à un système biologique d'intérêt peut s'avérer plus complexe de par la quantité d'études préexistantes et émergentes, qui empêche la formation et la maintenance d'une base de données publique unique. En effet, si plusieurs bases de données répertoriant des datasets single-cell RNA-seq ont été créées ([PanglaoDB](https://panglaodb.se/index.html "PanglaoDB"), [scRNASeqDB](https://bioinfo.uth.edu/scrnaseqdb/ "scRNASeqDB"), [scNavigator](https://artyomovlab.wustl.edu/scn/ "scNavigator"), [DRscDB](https://www.flyrnai.org/tools/single_cell/web/ "DRscDB"), [single cell Expression Atlas](https://www.ebi.ac.uk/gxa/sc/home "single cell Expression Atlas"), [Single Cell Portal](https://singlecell.broadinstitute.org/single_cell "Single Cell Portal")), elles ne rassemblent qu'une fraction des datasets publiés et ne sont plus maintenues à jour.

Le meilleur moyen de trouver le dataset adéquat consiste plutôt à faire une recherche par mots clés ("organisme" + "organe" + "modèle" + "single-cell RNA-seq"), dans pubmed, GEO ou directement dans google.


# Cas concret : expression des transcrits Kcnk12 et Kcnk13 dans les ganglions de la racine dorsale dans un modèle neuropathique murin

Nicolas Gilbert, doctorant dans l'équipe de Florian Lesage, étudie les canaux potassiques THIK2 et THIK1, encodés par les gènes KCNK12 et KCNK13, notamment exprimés dans les ganglions de la racine dorsale (Dorsal root ganglion ou **DRG**) et dont le rôle est peu connu. Nicolas et son équipe émettent l'hypothèse qu'ils pourraient jouer un rôle dans l'inflammation et la douleur. Afin de caractériser l'expression de ces deux gènes au sein des DRG physiologiques et dans un modèle neuropathique induits par des lésions sciatiques, nous avons cherché un dataset single-cell RNA-seq public correspondant.

## Etape 1 : recherche du dataset

La recherche google suivante : "Dorsal root ganglion neuropathic model single-cell RNA-seq" référence plusieurs publications, dont une revue récente faisant le point sur les différents datasets single-cell RNA-seq, ce qui facilite grandement le choix de celui à explorer.

<figure>
  <img src="/images/DRG_papers.PNG" alt="DRG_papers"/>
</figure>

Plus de 11 publications caractérisant l'hétérogénéité cellulaire des DRG par utilisation du single-cell RNA-seq sont ainsi répertoriées, chacune étant spécifique de par le modèle d'étude et la technologie de séquençage employés. Parmi ces publications, 4 d'entre elles présentent des caractéristiques complémentaires les rendant particulièrement intéressantes à explorer :

#
1. Wang, K., Wang, S., Chen, Y., Wu, D., Hu, X., Lu, Y., et al. (2021). Single-cell transcriptomic analysis of somatosensory neurons uncovers temporal development of neuropathic pain. Cell Res.

→ Les auteurs de cette étude ont réalisé un suivi dynamique des modulations transcriptomiques induites par des lésions sciatiques par single-cell RNA-seq basée sur [l’isolement par droplets](/guidelines/231101_MT_scRNAseq_introduction "isolement par droplets"). Ce modèle de neuropathie (Spared nerve injury ou SNI) étant utilisé expérimentalement par Nicolas et son équipe, ce jeu de données est le plus pertinent pour caractériser l'expression de Kcnk12 et Kcnk13 dans les DRG en condition physiologique et pathologique.

#
2. Jung M, Dourado M, Maksymetz J, Jacobson A, Laufer BI, Baca M, Foreman O, Hackos DH, Riol-Blanco L, Kaminker JS. Cross-species transcriptomic atlas of dorsal root ganglia reveals species-specific programs for sensory function. Nat Commun. 2023

→ Il s'agit d'un atlas visant à répertorier les populations cellulaires des DRG chez l'homme et dans des modèles d'études (souris, cobaye, macaque), de sorte à déterminer les signatures conservées ou espèces-spécifiques et à homogénéiser leur nomenclature. C'est donc une ressource intéressante pour mettre en perpectives les signatures trouvées dans le dataset de Wang et al. De plus, les auteurs proposent un outil de visualisation de l'expression des gènes dans les différents modèles via une application web.

#
3. Li, C. L., Li, K. C., Wu, D., Chen, Y., Luo, H., Zhao, J. R., et al. (2016). Somatosensory neuron types identified by high-coverage single-cell RNA-sequencing and functional heterogeneity. Cell Res.

→ Ce jeu de données plus ancien à la particularité d'avoir été produit par le même laboratoire que celui de Wang et al., mais via une approche single-cell RNA-seq alternative permettant de séquencer seulement quelques centaines de cellules mais avec une profondeur bien supérieure à celle obtenue via l'approche d’isolement par droplets. Les données issues de ce type de protocole ("[Smart-seq](https://www.nature.com/articles/s41587-020-0497-0 "Smart-seq v3")"), bien que rares, peuvent s'avérer précieuses à explorer pour notamment observer l'expression de transcrits peu abondants ou présentant une hétérogénéité d'isoformes, ce qui pourrait être le cas de Kcnk12 et Kcnk13.

#
4. Tavares-Ferreira, D., Shiers, S., Ray, P. R., Wangzhou, A., Jeevakumar, V., Sankaranarayanan, I., et al. (2022). Spatial transcriptomics of dorsal root ganglia identifies molecular signatures of human nociceptors. Sci. Transl. Med.

→ Ce dernier dataset propose des données de [transcriptomique spatiale](https://www.nature.com/articles/s41592-022-01409-2 "Review transcriptomique spatiale"), permettant de visualiser l'expression *in situ* de KCNK12 et KCNK13 sur des coupes de DRG humains. En apportant la dimension spatiale, ces données pourrait compléter l'exploration de l'expression de ces deux gènes.
#
## Etape 2 : Téléchargement et inspection des données de Wang et al., Cell Res. 2021.
La section "Data Availability" de la publication indique que les données analysées dans l'étude sont stockées dans GEO et téléchargeables via le numéro d'accès indiqué.

<figure>
  <img src="/images/GSE_WANG.PNG" alt="GSE Wang et al."/>
</figure>

Une fois le numéro d'accès rentré, nous sommes redirigés vers la page web de la série de données associées à l'étude. Cette page web récapitule les informations principales de la publication (titre, auteur, type d'expérience, résumé), et renseigne sur le design expérimental. En bas de la page, un tableau répertorie les fichiers correspondant aux données déposées, avec leur nom, leur taille et leur format. Normalement, le nom de ces fichiers et les informations indiquées sur la page doivent permettre de facilement faire correspondre chaque fichier à un échantillon ou à une partie de l'analyse présentée dans la publication.
Or, dans ce cas précis, la nomenclature des fichiers déposées par les auteurs n'est pas explicite, hormis pour ceux qui correspondent aux données Smart-seq de Li et al., qui ont été réanalysés pour l'occasion.

<figure>
  <img src="/images/GSE_FILES_WANG.PNG" alt="Data Wang et al."/>
</figure>

Les données originales de l'étude sont réparties en 4 datasets, avec à chaque fois un fichier texte correspondant aux comptes bruts et un fichier texte correspondant aux méta-données. Les deux premiers datasets sont également associés à un fichier "barcodes" qui liste les barcodes cellulaires des droplets sélectionnées. Après inspection des méta-données et relecture de la publication, chaque dataset correspond à une expérience de séquençage distincte, ce qui explique l'hétérogénéité des formats et de la structure des méta-données :

1. Le premier dataset correspond à la première expérience, où des échantillons de DRG ont été séquencés en condition physiologique, ainsi que 6h, 24, 2 jours, 7 jours et 14 jours après des lésions sciatiques (35894 cellules).

2. Le deuxième dataset correspond à une deuxième expérience, où d'autres échantillons de DRG ont été séquencés en condition physiologique, ainsi que 6h ou 24h après des lésions sciatiques (27248 cellules).

3. Le troisième dataset correspond à une troisième expérience, qui repète la première avec les mêmes conditions (35974 cellules).

4. Le dernière dataset correspond à une quatrième expérience, où les auteurs ont reséquencés des échantillons de DRG physiologiques et ont ajouté des échantillons de DRG séquencés 28 jours après lésion sciatique (15127 cellules).

La complexité du design du dataset global, son volume, ainsi que l'hétérogénéité de structures des méta-données et des dimensions des matrices des sous-datasets qui le composent, indiquaient que dans un premier temps il était plus pertinent de restreindre l'analyse au premier dataset.


## Etape 3 : Ré-analyse du premier dataset

### 1. Charger les données dans Rstudio et créer un "objet" d'analyse
L’analyse des données single-cell RNA-seq à partir des matrices de compte se réalise dans un environnement logiciel permettant de charger des librairies d'outils, d'éditer et de compiler des scripts, de visualiser les variables et de représenter graphiquement les données, le tout dans un même language de programmation. Pour le language R, l’analyse des données single-cell RNA-seq est réalisé dans l'environnement de développement (IDE) Rstudio, et se base notamment sur la librairie [seurat](https://satijalab.org/seurat/ "seurat").

Dans ces environnements, les données single-cell RNA-seq sont structurées dans un format qui permet à la fois de stocker les matrices de comptes [gènes x cellules] brutes et transformées, ainsi que les méta-données sur les gènes (Ensembl ID, Symbole) et sur les cellules (Nombre de comptes total, échantillon d'origine, type cellulaire annoté etc), ordonnées en fonction de leur position dans la matrice de comptes. Au fur et à mesure de l'analyse, d'autres informations seront enregistrées dans cet "objet", notamment les résultats des réductions de dimensions.

<figure>
  <img src="/images/sce_object.PNG" alt="Objet d'analyse"/>
</figure>

Tiré de [Orchestrating Single-Cell Analysis with Bioconductor](http://bioconductor.org/books/3.13/OSCA/ "Orchestrating Single-Cell Analysis with Bioconductor")

Une fois importés, les fichiers textes correspondant à la matrice de comptes du premier dataset et aux méta-données associées sont mises en forme dans un object seurat appelé "WangDRG". Cet objet contient la matrice d'expression de 23904 gènes dans 35894 cellules, ainsi que la table des méta-données qui ont été enregistrées par les auteurs. Elles se répartissent en 8 variables qui pour chacune des 35894 cellules renseigne notamment son identifiant (barcode), sa condition, et le type cellulaire qui a été annoté.

<figure>
  <img src="/images/Wang_seurat_obj.PNG" alt="WangDRG seurat object"/>
</figure>

### 2. Transformer les données et réduire leur dimensionalité pour leur visualisation.
En l'état, les données ne sont pas encore exploitable pour visualiser l'expression de nos gènes d'intérêts. En effet, les comptes brutes ne tiennent pas compte des éventuelles fluctuations de la profondeur de séquençage entre les différents échantillons, ou des autres sources de variabilité technique, ce qui risque de biaiser à la fois la quantification de l'expression des gènes ainsi que la projection des données en dimension réduite. Pour y remédier, il faut procéder à une normalisation puis à une intégration des données, avant de réaliser l'ACP puis leur projection en 2 dimensions du (voir [l'article](/guidelines/231101_MT_scRNAseq_analysis_1 "seurat") sur l'analyse de données). Une fois ces étapes effectuées, l'exploration et la visualisation des données peut débuter.

### 3. Visualiser le dataset et l'expression de Kcnk12/Kcnk13.

La première représentation du dataset que l'on peut proposer est la **projection des données en 2 dimensions** via un algorithme type UMAP, toutes conditions réunies.

Les cellules des DRG se regroupent selon leur profil d'expression en 9 populations principales : neurones, cellules satellites gliales, cellules de Schwann, cellules endothéliales vasculaires (VEC), cellules endothéliales vasculaires capillaires (VECC), cellules musculaires lisses vasculaires (VSMC),  fibroblastes, cellules immunitaires et globules rouges (RBC).
Certaines populations sont particulièrement hétérogènes en termes de signature transcriptomique, notamment les neurones. En effet, les auteurs de Wang et al. proposent une classification de 20 populations neuronales sur la base de l'expression de certains marqueurs.

<figure>
  <img src="/images/UMAP_Wang_Neurons.PNG" alt="UMAP_Wang_Neurons"/>
</figure>


Dans une représentation en "**DotPlot**" de l'expression moyenne normalisée des gènes codants pour des canaux potassiques de type K2P détectés dans le dataset, on observe que Kcnk12 est celui le plus exprimé dans les neurones des DRG. Cette représentation nous indique également le pourcentage d'expression des transcrits dans chaque population, c'est à dire la proportion de cellules dans lesquelles on détecte au moins 1 molécule d'ARNm vis à vis de la population totale. On remarque ici la forte spécificité d'expression de Kcnk12, qui est exprimé d'en environ 50% des neurones contre moins de 2% dans les autres populations. Quant à Kcnk13, son expression est plus faible que Kcnk12 dans les neurones, et on détecte un léger signal dans les cellules immunitaires.

Il faut noter qu'ici les valeurs d'expression sont centrées et réduites (calcul de z-score ou on retranche la moyenne et divise par l'écart-type), ce qui permet de représenter l'expression de chaque gène à sa propre échelle, et d'éviter ainsi que les gènes les plus exprimés "écrasent" le signal.

<figure>
  <img src="/images/Kcnks_Wang.PNG" alt="Kcnk12, Kcnk13_Wang"/>
</figure>

Dans cette représentation de l'expression de Kcnk12 et Kcnk13 dans l'espace de dimensions réduites ("**FeaturePlot**"), on observe que ces deux gènes ne sont exprimés que dans une partie des populations neuronales.

<figure>
  <img src="/images/Kcnk12_Kcnk13_Wang.PNG" alt="Kcnk12, Kcnk13_Wang"/>
</figure>

Afin de documenter plus précisément leur expression dans ces populations et dans les différentes conditions, les étapes suivantes consistaient à réaliser l'intégration de l'ensemble des neurones séquencés par les auteurs dans les différents datasets, puis de comparer les populations identifiées avec celles annotées dans l'atlas cellulaire construit par Jung et al., (Nat Commun. 2023).


## Etape 4 : Intégration de l'ensemble des 4 datasets et annotation des neurones

Après avoir importé les matrices de comptes des 4 datasets, homogénéiser les méta-données et les gènes quantifiées, et sélectionner les cellules correspondant à des neurones, on obtient un jeux de données de 27198 cellules. Une fois les données des différents échantillons normalisées et intégrées, l'objectif est d'annoter les clusters correspondant aux différentes populations neuronales de sorte à donner un sens biologique à la description de l'expression de Kcnk12/Kcnk13.

Sur la base des profils d'expression dans l'espace de dimensons réduites obtenu par ACP, on distingue une vingtaine de communautés isolées de manière non supervisée (le nombre de clusters n'est pas prédéfini). Si on projette les annotations originales de Wang et al. sur ces communautés, on remarque que chaque cluster non annoté correspond à peu près à une population définies par ces mêmes auteurs. Cependant, ces annotations sont uniquement réalisées sur la base de l'expression spécifique de gènes, ce qui ne donne aucune information sur la fonction des populations associées.

<figure>
  <img src="/images/Neurons_Annot.PNG" alt="Annotations des Neurones"/>
</figure>

Pour y remédier, on peut également se baser sur l'annotation proposée par Jung et al., visant à établir des signatures transcriptomiques faisant consensus entre plusieurs espèces. Les auteurs ont ainsi identifié 5 grandes classes de neurones conservées dans les DRG :
* A-LTMRs (A-fiber low-threshold mechanoreceptors)
* C-LTMRs (C-fiber low-threshold mechanoreceptors)
* NPs (non-peptidergic nociceptors)
* PEPs (peptidergic nociceptors)
* Cold thermoreceptors

Ces 5 grandes classes sont ensuite divisées en plusieurs sous-types, caractérisées par l'expression de marqueurs spécifiques, pour un total de 11 populations conservées entre mammifères.

<figure>
  <img src="/images/Jung_markers.PNG" alt="Annotations des Neurones de Jung et al."/>
  <figcaption> Jung et al. Cross-species transcriptomic atlas of dorsal root ganglia reveals species-specific programs for sensory function. Nat Commun. 2023 </figcaption>
</figure>

###

En se basant sur l'expression de ces marqueurs dans le dataset intégré de Wang et al., on retrouve l'ensemble de ces 11 populations, auxquelles s'ajoutent 4 clusters spécifiques du dataset de Wang et al. Parmi ces clusters additionnels, on trouve une population marquée par l'expression spécifique de Rfxp1 ainsi que trois populations exprimant des marqueurs de neurones C-LTMRs, NPs et PEPs, mais surexprimant Atf3 et qui correspondent à des états cellulaires spécifiques des DRG de souris ayant subies des lésions sciatiques.   

<figure>
  <img src="/images/Jung_on_Wang.PNG" alt="Annotations finale des Neurones de Wang et al."/>
</figure>

En effet si on suit l' **évolution des proportions relatives** des différentes sous populations en condition contrôle et au cours de la réponse aux lésions sciatiques, on observe une apparition des sous populations "NP Atf3", "PEP Atf3" et "C-LTMR Atf3" à partir de 24h post-lésions. Ces populations représentent environ 25% des cellules séquencées entre le deuxième et le septième jour post-lésions, puis tendent à disparaître dans les semaines suivantes. Lorsqu'on compare l'évolution des proportions relatives entre chaque sous populations, on remarque que les "NP Atf3" et "C-LTMR Atf3" atteignent un pic autour du deuxième jour, tandis que les "PEP Atf3" l'atteignent plutôt à 7 jours post-lésions. A 14 jours, alors que les proportions de "NP Atf3" et de "C-LTMR Atf3" ont drastiquement diminué, celle des "PEP Atf3" reste élevée à 14 jours. A 28 jours, seule une faible proportion de "PEP Atf3" persiste toujours. Au niveau transcriptomque, ces 3 états cellulaires partagent une signature marquée notamment par l'expression d'*Atf3*, *Sprr1a*, *Sox11*, *Gap43*, *Nts*, *Gadd45a*, *Gal* ou *Cdkn1a*, comme l'indique la **heatmap**.
Cette signature est décrite dans la littérature comme celle des "[regeneration-associated genes](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4528284/#:~:text=Regeneration%2Dassociated%20gene%20networks.&text=These%20transcription%20factors%20can%20serve,transcription%20of%20other%20hub%20proteins. "regeneration-associated genes")" (RAGs), indispensable à la régénération des axones endommagés.

<figure>
  <img src="/images/Atf3_subpops.PNG" alt="Focus sous populations surexprimant Atf3"/>
</figure>


## Etape 5 : Visualisation de l'expression de Kcnk12 et Kcnk13

Une fois les différentes populations neuronales annotées, l'expression de Kcnk12 / Kcnk13 peut enfin être visualisée. L'une des représentations graphiques les plus adéquates pour les données single-cell RNA-seq est appelée "**ViolinPlot**. Cette représentation permet de visualiser l'expression d'un unique gène dans chaque cellule du jeux de données, tout en groupant les cellules en fonction de leur annotation (ou de leur échantillon/condition). Le niveau d'expression est représenté sous forme de point (un pour chaque cellule), auquel s'ajoute une courbe de densité qui indique la distribution des comptes et éventuellement un boxplot résumant la médiane, les 1er et 3ème quartile.


<figure>
  <img src="/images/Kcnk12_Kcnk13_Violin.PNG" alt="expression de Kcnk12 et Kcnk13 "/>
</figure>

Pour Kcnk12, son transcrit est exprimé en condition physiologique dans les sous populations de neurones nocicepteurs non-peptidergiques NP1, NP2 et NP3, ainsi que dans la sous population de neurones nocicepteurs peptidergiques PEP1 dans une moindre mesure. On le retrouve également exprimé dans les 3 sous-populations détectées dans les échantillons de DRG de souris ayant subies des lésions sciatiques : "NP Atf3", "PEP Atf3" et "C-LTMR Atf3". L'expression de Kcnk13 est quant à elle globalement plus faible en condition physiologique et semble restreinte aux populations NP1 et C-LTMR. Cependant, elle semble légèrement surexprimée dans les populations neuropathiques équivalentes, soit les "NP Atf3" et les "C-LTMR Atf3".


 Ces profils d'expression suggèrent une surexpression de Kcnk12 et dans une moindre mesure de Kcnk13, dans le modèle de neuropathie. Pour tester cette hypothèse au niveau statistique, l'approche [d'analyse différentielle en pseudobulk](/guidelines/231101_MT_scRNAseq_analysis_2 "L'analyse de données single-cell RNA-seq, Partie 2") paraissait appropriée du fait de la présence de réplicats biologiques dans le dataset intégré.  

Pour réaliser cette analyse différentielle, les cellules des 3 sous-populations neuropathiques ont été groupées pour chaque échantillon avec leur population physiologique associée (NP1/NP2/NP3 pour les NP Atf3, PEP1/PEP2/PEP3 pour les PEP Atf3 et C-LTMR pour les C-LTMR Atf3). Leurs comptes brutes ont ensuite été aggrégés de sorte à former des pseudobulks. Pour chacun des 3 sous ensembles de neurones (NPs, PEPs et C-LTMRs) on obtient 4 échantillons contrôles (1 pour chaque dataset), 3 échantillons SNI 6h et 3 échantillons SNI 24h (dataset 1,2 et 3), 2 échantillons SNI 2j, SNI 7j et SNI 14j (dataset 1 et 3) et 1 échantillon SNI 28j.
Pour comparer les échantillons contrôles à un nombre suffisant d'échantillons pathologiques, une condition SNI "pic" a été créée en rassemblant les échantillons pour lesquels on observe les plus fortes proportions de populations associées à la signature RAGs, soit les conditions SNI 24h, SNI 2j et SNI 7j.

L'expression différentielle entre les 4 échantillons contrôles et les 7 échantillons SNI "pic", représenté sous forme de **boxplot**, indique que Kcnk12 est statistiquement surexprimé  en condition neuropathique dans les neurones PEP. On observe également une tendance de surexpression de Kcnk13 dans cette même population.

<figure>
  <img src="/images/DEA_Kcnk1213.PNG" alt="DEA Kcnk12 + Kcnk13 "/>
</figure>

Si on regarde les résultats des analyses différentielles réalisées sur chacune des 3 sous populations de neurones, on constate que d'autres gènes codant pour des canaux potassiques de type K2P sont différentiellement exprimés dans le modèle SNI : Kcnk18 est down-régulé dans les PEPs et Kcnk16 est surexprimé dans les 3 sous populations.

<figure>
  <img src="/images/DEA_K2P.PNG" alt="DEA K2P"/>
</figure>


## Visualisation du dataset intégré via une application web

Le dataset intégré et analysé correspondant à l'ensemble des neurones des DRG séquencées par Wang et al. est consultable via une [application web](http://carra.ipmc.cnrs.fr:3838/Wang_DRG_neurons/ "application web Wang DRG"). Dans cette application, l'expression des gènes peut être visualisée sous forme de FeaturePlot, de ViolinPlot/Boxplot et de DotPlot/Heatmap, le tout en groupant les cellules par population ou par condition.
