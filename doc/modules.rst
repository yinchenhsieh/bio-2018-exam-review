Checkpoint Yourself
===================

20 Questions to Check Your Understanding
----------------------------------------

One of the difficulties of this course (for you and for us) was the sheer amount of bioinformatic analysis we needed to cover, and the tools we needed to walk you through. 

We did this mainly by repeating types of tasks in every homework, and giving you a lot of homeworks to practice with.

Since I was responsible for teaching you the **sequence analysis** part of the datalabs/homeworks, I have made a list of questions + answers **for this topic only** for you to test yourself of your own understanding. It is loosely based on Canvas's modules, but follows the overall topics we covered in each of the homeworks.

.. warning:: Again, this is not a comprehensive list. It is just what is my opinion on the main takeaways of all of the datalabs that I gave. **Make sure to review Kelsey + Lucas's parts on population genetics, phylogenetics, and barcoding.**

1. What is bioinformatics?
^^^^^^^^^^^^^^^^^^^^^^^^^^
- combination of biology and information technology
- computer-based analysis of large biological datasets
- development of analysis tools and algorithms
- maintenance of biological databases
- focuses on macromolecular sequences, structures, expression profiles, biochemical pathways

2. Why learn bioinformatics?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- essential for biologists to know how to analyse datasets
- high throughput data requires bioinformatic techniques
- expert human input is still required to benchmark bioinformatic techniques and source data
- it's cool!

3. What is a sequence and why is it important?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- basic unit of storage of biological information
- DNA, RNA, protein sequences mostly studied
- sequence comparison behind almost every aspect of biology

4. What are the bioinformatic characteristics of DNA?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- 4 standard bases: A,T,C,G
- genomic DNA contains genes
- eukaryotes have non-coding introns in addition to exons
- cDNA is reverse-transcribed from mRNA, corresponds to expressed parts of the genome and does not contain introns
- recombinant DNA (from labs) is artificial DNA such as cloning vectors

5. What are the bioinformatic characteristics of RNA?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- 4 standard bases: A,U,C,G (Uracil instead of thymine)
- many forms of RNA (mRNA, tRNA, rRNA, etc.)
- mRNA studied to deduce protein sequences

6. What are the bioinformatic characteristics of protein sequences?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- 20 standard amino acids: A,R,N,D,C,Q,E,G,H,I,L,K,M,F,P,S,T,W,T,V
- each amino acid can be written in full: Alanine, or in a 3-letter code: Ala, or as a 1-letter code: A
- going from DNA to RNA to protein requires a codon table, which represents the triplet code used in translation
- translation tools exist and are useful: `Expasy Translate Tool <https://web.expasy.org/translate/>`_

7. What is FASTA and why is it important?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- FASTA is a text file format specific for biological sequences
- attaches a header (indicated by >) as identifier to a sequence
- most bioinformatic sequence software accepts `.fasta` format
- every bioinformatic database gives sequence info in this format

8. What structures are most studied in bioinformatics?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- protein structures (primary, secondary, tertiary, quaternary)
- solved experimentally by x-ray crystallography or cryo-electron microscopy
- quality measured by resolution: smaller the better 
- mainly published in the Protein Data Bank: `PDB <https://www.rcsb.org/>`_
- RNA structures
- DNA (chromatin) structures

9. Which databases are the most used for sequence analysis?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- `NCBI <https://www.ncbi.nlm.nih.gov/>`_ : umbrella database for all sorts of biological information, also hosts important software
- `PDB <https://www.rcsb.org/>`_ : structural database
- `UniProt <https://www.uniprot.org/>`_ : expert-annotated (SwissProt) and automatically-annotated (TrEMBL) protein database
- `KEGG <https://www.genome.jp/kegg/>`_ : systems biology database, mainly used in our case to find enzyme reactions

10. What are databases used for?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- identification of sequences via sequence similarity search
- extracting upstream and downstream information about a sequence
- getting evolutionary information, comparing across taxonomic branches
- many other uses!

11. What is sequence similarity searching and how do we do it?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- submitting a **query** sequence to extract sequences (called **hits**) that are similar to this query
- we can infer identity, organism, structure, function or evolution of query sequence from similar sequences
- we mainly use NCBI `BLAST <https://blast.ncbi.nlm.nih.gov/Blast.cgi>`_
- BLASTn for nucleotide
- BLASTp for protein sequences
- other types of BLAST are less frequently used and often less sensitive

12. What are alignments and how are they related to sequence similarity searching?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- pairwise or multiple position-based comparisons of sequences based on matching or similar sequence units
- sequence similarity is derived from alignments and alignment scores
- allow for identification of mutations (letter changes), inserts, deletions (seen as gaps)
- protein alignments use substitution matrices to score matches and mismatches (BLOSUM62 or PAM250 are common matrices)
- such matrices allow for detection of distant evolutionary relationships from proteins

13. What are common metrics used to evaluate hits from similarity searches?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- E-value: measures how significant a hit was, in the context of the overall database
- closer to 0 = more significant
- query coverage refers to how much of a hit was aligned with a query sequence
- query percentage identity refers to how much of the aligned part of a hit matched the query

14. Why do we calculate sequence probabilities?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- to find out how biologically significant a certain sequence is
- where significance means how likely we expect to see sequences in a database of a certain size
- mutation probabilities give us good estimates of how many mutations we could expect in a sequence
- so once again we can compare whether the observed matches the predicted number of mutations

15. What is an MSA and how is it important?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- multiple sequence alignment 
- illustrates relationships between two or more sequences
- if sequences are diverse, conserved residues are often key residues associated with maintenance of structural stability or biological function
- protein MSAs give many clues about function and structure
- allow for cross-species comparisons 

16. How do we make and evaluate an MSA?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- input sequences in `ClustalOmega <https://www.ebi.ac.uk/Tools/msa/clustalo/>`_
- view the resulting alignment based on the conservation indication scheme (asterisk: conserved, colon: less conserved, dot: least conserved)
- look for domains (regions of high conservation) as they may be functionally relevant
- look for repeat regions (disordered regions)
- look for highly variable regions as they could indicate a loss of function or gain of alternate function

17. How can we make structural sense of a protein MSA?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- map certain positions of interest back to the structure of a reference protein
- can be done with the PDB Protein Feature View, or by viewing the structure
- positions in certain secondary structures (helices or sheets) can give us clues to function of protein region
- flexible regions of protein (coils or unmodeled regions) often involved in active sites or protein interactions with other molecules

18. What are protein modifications and how can you detect them?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- modifications to amino acids in a protein, such as phosphorylation or acetylation
- allow for activation or deactivation of proteins, so they alter the function
- can be detected by mass spec (modifications change the normal mass of the amino acids) 
- leading to a higher or lower mass
- find out the chemical changes for a modification, and calculate change in atomic composition
- use the Peptide Mass tool to simulate mass spec: `Peptide Mass Tool <https://web.expasy.org/peptide_mass/>`_

19. How is species identification done computationally?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- from sequence information, you do a sequence similarity search via BLAST
- if you have a decently long sequence, a high query coverage, a high percentage identity, and the same organisms in the top hits, you can be relatively sure of the organism and sequence
- many organisms have very similar homologous sequences, so identifying organisms from one sequence usually hard via BLAST, unless sequence is very unique

20. How do you find functions of a sequence, once you have identified it?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- usually similar function to homologous sequences
- if protein usually the name will indicate its function
- otherwise search for it in UniProt or a pathway database such as KEGG
- if it is an enzyme, finding the reaction will also give you the function
- if DNA usually BLAST will indicate what it is (often mRNA that encodes protein)
- if RNA you need to identify what kind of RNA it is, database searching again
