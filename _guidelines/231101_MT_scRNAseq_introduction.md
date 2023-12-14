---
title: "Introduction au single-cell RNA-seq"
excerpt: ""
collection: guidelines
date: 2023-07-15
---

<i>Author: Marin Truchi</i>

## De l’échelle tissulaire à l’échelle de la cellule unique

Du fait de son rendement, de sa précision et de sa sensibilité, le RNA-seq est un outil puissant pour comparer par analyse différentielle le niveau d’expression de dizaines de milliers de trancrits entre échantillons.
Néanmoins, afin d'atteindre une quantité d'ARN nécessaire au séquençage (~100 ng), les molécules sont isolées à partir de tissues entiers et de plusieurs dizaines de milliers de cellules. La quantification des ARN après séquençage est donc issus d'une moyenne d'expression à travers les différents types cellulaires du tissu, d’où l’appellation « bulk » RNA-seq. Or, cette hétérogénéité cellulaire biaise :
* La détection de gènes différentiellement exprimés spécifiques à une fraction restreinte des populations cellulaires
* L'interprétation de l'analyse différentielle, dans le cas où les modulations transcriptomiques mesurées sont dues aux variations des proportions des types cellulaires prélevés dans le tissu d'un échantillon à l'autre

De plus, la résolution tissulaire des données bulk RNA-seq empêche la description précise de l'expression d'un gène d'intérêt et la caractérisation détaillée d'éventuelles modulations transcriptomiques détectées lors de l'analyse.
Pour pallier ces lacunes, la décennie 2010 a vu l'explosion des protocoles adaptant le RNA-seq afin de réaliser le séquençage des transcrits à l'échelle de la cellule unique, notamment grâce à des techniques d’isolement des cellules, d’amplification des séquences nucléiques et d’emploi de barcodes cellulaires. La combinaison de ces techniques a permis d'automatiser et de raccourcir les expériences de séquençage et d'en optimiser les rendement. Les protocoles actuels autorisent le profilage individuel de dizaines de milliers de cellules par expérience.

<figure>
  <img src="https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fnprot.2017.149/MediaObjects/41596_2018_Article_BFnprot2017149_Fig1_HTML.jpg?as=webp" alt="Svensson V, Vento-Tormo R, & Teichmann S. Nat Protoc. (2018)"/>
  <figcaption>Svensson V, Vento-Tormo R, & Teichmann S. Nat Protoc. (2018)</figcaption>
</figure>

#
## L’approche single-cell RNA-seq basée sur l’isolement par droplets

Parmi ces protocoles, les plus fréquemment employés se basent sur des techniques de manipulation microfluidique afin d'automatiser l'isolement des cellules dans des gouttelettes d'émulsions appelées droplets. Ce protocole débute par une étape de dissociation mécanique et enzymatique du tissu d’intérêt qui permet la mise en suspension des cellules qui sont aussitôt isolées les unes des autres dans des droplets. Chaque droplet contient les réactifs nécessaires à la lyse des cellules, à la capture et à la rétrotranscription de leurs ARN polyadénylés, ainsi qu'une bille de gel sur laquelle sont ancrées des dizaines d'oligonucléotides contenant  :
* une séquence d'hybridation des ARN polyadénylés permettant d’amorcer leur rétrotranscription
* un barcode moléculaire ou « UMI » permettant d’identifier chaque molécule capturée avant amplification et de prévenir les biais de quantification induits par des niveaux d’amplification PCR inégaux
* un barcode cellulaire unique à chaque droplet
* des amorces permettant l’amplification et la lecture des séquences

L'ajout du barcode cellulaire sert à multiplexer la préparation et l'amplification de la librairie de séquençage. La lecture du barcode cellulaire par analyse bioinformatique permet d'assigner chaque molécule à une droplet et par extension à sa cellule d'origine. La quantification finale consiste à compter le nombre de lectures présentant une combinaison unique entre un barcode
cellulaire, un UMI, et un gène associé.



<figure>
  <img src="/images/droplet.PNG" alt="Protocole scRNA-seq basé sur l’isolement par gouttelette"/>
  <figcaption>Protocole scRNA-seq basé sur l’isolement par gouttelette</figcaption>
</figure>


#
## L’analyse bioinformatique de données single-cell RNA-seq
Le scRNA-seq permet la quantification de dizaines de milliers de gènes dans des dizaines de milliers de cellules. Ce profilage exhaustif a pour objectif de distinguer des types ou des états cellulaires stables ou transitoires qui composent les tissus physiologiques et de comparer les modulations transcriptomiques induites par une pathologie, un traitement ou une modification génétique.

Pour atteindre ces objectifs, les données issues du séquençage sont traitées par analyse bioinformatique selon 3 grandes phases.
* La phase d’analyse primaire consiste à convertir les lectures de séquençages obtenues (reads) en matrices de comptes récapitulant l’expression de chaque gène dans chaque cellule.
*  Ces matrices de comptes nécessitent ensuite un traitement particulier, du fait de leurs dimensions et des caractéristiques mathématiques des données qu’elles contiennent. Cette analyse secondaire est réalisée par un enchaînement d’opérations statistiques visant à éliminer les sources de variations techniques et à identifier les principales sources de variations biologiques afin de partitionner les cellules en fonction de la proximité de leurs profils d’expression génique (clustering). Lorsque l’étude nécessite l’analyse de plusieurs jeux de données, ces traitements sont appliqués de sorte à tenir compte des disparités entre échantillons séquencés via un processus d’intégration (correction de batchs).
* Une fois les cellules regroupées en clusters homogènes, la dernière phase de l’analyse consiste à les comparer et à interpréter biologiquement les différences statistiques trouvées, en questionnant notamment les mécanismes de régulation impliqués.

Chacune de ces trois phases, ainsi que l’intégration des données,
implique l’usage de méthodes de biologie computationnelle reposant à la fois sur des concepts mathématiques, sur des connaissances biologiques et sur des ressources de calculs informatiques. Ces développements méthodologiques ont produit une myriade d’outils dédiés à l’analyse de données single-cell RNA-seq. Malgré l’absence de hiérarchie claire pour prioriser l’emploi d’outils équivalents, un consensus s’est formé autour de la procédure globale et des meilleures pratiques à adopter.
Pour en savoir plus sur les concepts, méthodes et outils utilisés, voir l'article dédié à [l'analyse de données single-cell RNA-seq](/guidelines/231101_MT_scRNAseq_introduction "L'analyse bioinformatique de données single-cell RNA-seq").


## Avantages et limitations de l'approche

De part sa résolution, le single-cell RNA-seq permet de capturer une vision d’ensemble de l'hétérogénéité cellulaire d'un tissu d'intérêt et d’explorer individuellement les profils transcriptomiques de ces différents compartiments. Lorsqu’il est question de comparer des conditions pathologiques/traitées et contrôles, cette résolution permet de caractériser les éventuelles modulations induites de manière spécifique à chaque population cellulaire. Cette caractérisation consiste notamment à identifier les signatures de gènes différentiellement exprimés dans chaque population, puis à utiliser des outils capables d'associer ces signatures à des mécanismes fonctionnels comme des voies de régulation, de signalisation ou de différenciation.

Malgré l'apport de cette nouvelle résolution, la génomique fonctionnelle à l’échelle de la cellule unique reste limitée par la faible efficacité de capture des molécules d’intérêts, du fait de la quantité de matériel initiale minimes et de dynamiques de régulation discontinues comme les
phénomènes de « transcriptionnal bursting ». De plus, le temps de demi-vie des ARNm atteint une valeur médiane de 9h chez les mammifères. La détection de ces molécules est donc stochastique, ce qui implique une quantification partielle et bruitée par le phénomène des comptes observés comme nuls (dropouts) dans certaines cellules alors que le gène est exprimé par le reste de la population. Classiquement, environ 90% des éléments d'une matrice de compte sont constitués de valeurs nulles.
Cette particularité propre aux données single cell RNA-seq nécessite des méthodes d’[analyses bioinformatiques](/guidelines/231101_MT_scRNAseq_introduction "L'analyse bioinformatique de données single-cell RNA-seq") dédiées, garantissant l’interprétation biologique des résultats.
Enfin, le transcriptome ne constitue qu'un niveau intermédiaire qui témoigne des régulations génomiques et épigénomiques et qui anticipe la fonction cellulaire majoritairement définie par le protéome.

Pour dépasser ces limitations, de nouveaux développements techniques et méthodologiques sont à suivre, notamment au niveau des capacités de capture des ARN, de l'intégration de données multiomiques, de la [transcriptomique spatiale](/guidelines/231101_MT_scRNAseq_introduction "La transcriptomique spatiale") ou encore du séquençage de type "long-reads".


## Bibliographie

Svensson, V., Vento-Tormo, R. & Teichmann, S. A. Exponential scaling of single-cell RNA-seq in the past decade. Nat. Protoc. 13, 599–604 (2018)

Macosko, E. Z. et al. Highly Parallel Genome-wide Expression Profiling of Individual Cells Using Nanoliter Droplets. Cell 161, 1202–1214 (2015)

Zheng, G. X. Y. et al. Massively parallel digital transcriptional profiling of single cells. Nat.Commun. 8, 14049 (2017)

Rozenblatt-Rosen, O., Stubbington, M. J. T., Regev, A. & Teichmann, S. A. The Human Cell Atlas: from vision to reality. Nature 550, 451–453 (2017).

Schaum, N. et al. Single-cell transcriptomics of 20 mouse organs creates a Tabula Muris. Nature 562, 367–372 (2018).
