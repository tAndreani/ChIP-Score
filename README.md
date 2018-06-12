# ChIP-Score
ChIP-Score is a method capable to distinguish DNA regions that are bounded by several functional unrelated proteins and replicates within genomic locations of the same cell type. Also, the tool can report noisy regions that tend to be not reproducible for all the transcription factors binding sites under investigation.


# Idea Behind the tool
ChIP-seq is a standard technology in wet laboratories because it allows to map the genomic regions in which a transcription factor of interest is binding asserting its role. Regulatory genomics labs have extensively used this technique to describe how, where and which gene is under the control of a transcription factor. However, in the last years, several labs have reported some limitations. In fact, regions of developmentally regulated, housekeeping and tRNA genes have shown un-specificity for DNA bining proteins in a consistent manner (1,2,3,4). On other hand, there are some genomic regions that are attractors of Transcription Factors named "High Occupancy Target" (HOT) (5). It is still a debate whether these HOT regions are functional unit of the genome or simply artefact of ChIP techniques. It will be important to distiguish real attractor DNA regions of a Transcription Factor Vs artefact for future analysis. For this we have developed ChIP-score, a method that can report Noisy and Sticky regions for a given cell type of interest. We refer to the term sticky as regions with low specificity in the binding sites according to the reproducibility score.


# Conceptualization
Obtain the DNA binding of a given transcription factor (or protein) requires the presence of replicates in the experimental design and concordant regions among the replicates can give a confidence on its reliability. Using this concept at the basis of the method, a reproducibility score is developed based on how many time a fixed DNA region, that we named bin, is bounded by a protein among the replicates in the ChIP experiment. If a minimum number of three replicates for a given protein in a cell type are considered, reproducible regions will be those having a significant peak (FDR <= 5%) in all the replicates for a given bin. As expected, the length of the peaks variate between the replicates and for this reason, the board of the bin that do not reach the number three will be annotated as part of the reproducible region. Contrary, regions with a peak but that never reach the number of three will be annotated as not reproducible. If in between bins with 0 "Sum vector" there is a maximum value of 3 the whole region is reproducible. Opposite if there is not a maximum value of 3 the region is not reproducible. Aggregating reproducible regions for the same cell type and different proteins will result in unspecific bounded regions (Sticky). Opposite aggregating not reproducible regions for the same cell type and different proteins will result in Noisy regions.


![peaks](https://user-images.githubusercontent.com/6462162/40009504-8453ddac-57a2-11e8-98ce-1c874821e177.png)

Fig. 1) Step to identify reproducible and not reproducible regions considering the boarder of each bin. 


# References
1. Teytelman Leonid, et al. "Highly expressed loci are vulnerable to misleading ChIP localization of multiple unrelated proteins." Proceedings of the National Academy of Sciences 110.46 (2013): 18602-18607.  

2. Park Daechan, et al. "Widespread misinterpretable ChIP-seq bias in yeast." PLoS One 8.12 (2013): e83506.  

3. Jain Dhawal, et al. "Active promoters give rise to false positive ‘Phantom Peaks’ in ChIP-seq experiments." Nucleic acids research 43.14 (2015): 6959-6968.   

4. Wreczycka Katarzyna, et al. "HOT or not: Examining the basis of high-occupancy target regions." bioRxiv (2017).

5. Foley Joseph W., and Arend Sidow. "Transcription-factor occupancy at HOT regions quantitatively predicts RNA polymerase recruitment in five human cell lines." BMC genomics 14.1 (2013): 720.
