# dipseq_biosensor_data
Processed sequencing data for MBP and TMBP DIP-seq with cpGFP insertions for biosensor creation.

Raw reads were processed using the code in the dipseq repository to find reads that traversed an insertion event. These events were then aggregated according to the insertion site and merged into a single file per round of screening.

Here is a description of the columns in each merged CSV file.
* insertion_site_name: a unique name for the row.
* sample_matched_3p: the absolute number of reads found in this sample that matched the 3' end of the insert (cpGFP) at this insertion site. Samples can include both technical replicates (runs), which were from the same material but sequenced independently, and also biological replicates (libraries, e.g. lib1 vs lib2)
* sample_matched_5p: same as above, but when the read matched the 5' end of the insert. Used as an internal technical replicate to boost confidence in dispersion estimates.
* insertion_site: the calculated site of insertion in nucleotides from the start codon.
* forward_insertion: if True, the insert (cpGFP) was in the same direction as the backbone sequence inserted into (MBP or TMBP).
* in_frame: if True, the insertion was in-frame with the coding sequence of the backbone inserted into (MBP or TMBP). Note that this is computed independently of forward_insertion such that reverse insertions may be "in frame" even though this cannot be true.
