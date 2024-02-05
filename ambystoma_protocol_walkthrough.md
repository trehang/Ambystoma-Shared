## How to generate the reverse complement of the sequence
- Download the genome into your scratch workbench
- navigate to Scratch using cd /scratch/username
- since the _Ambystoma_ genome is so big, a batch script must be run to further analyze the genome.
- there will be an output and error file, look at the contents of the output using <cat 40691190.output>
- load two modules in scratch 
    - module load emboss/6.6.0
    - module load seqtk/1.3
- use module list to double check that the modules are loaded
- run the command <echo 'PGSH02027157.1' > list.txt> to create a new file, list.txt, with one line. This line is the chromosome identifier.
- run the command <seqtk subseq GCA_002915635.3_AmbMex60DD_genomic.fna list.txt > PGSH02027157.1.txt> to create a new text file with the extracted sequence from the larger genome file
- generate the reverse complement of this extracted sequence using the command <revseq PGSH02027157.1.txt PGSH02027157.1.rev>
- there are now two new files, PGSH02027157.1.txt and PGSH02027157.1.rev. One is the original sequence and the other is the reverse complement of the sequence. 

## How to calculate the GC content of a file 
- load both modules as before
    - module load emboss/6.6.0
    - module load seqtk/1.3
- Use this command to calculate the nucleotide content of your sequence
    - seqtk comp downloaded_genome.fa | awk 'OFS="\t" {sumA+=$3; sumC+=$4; sumG+=$5; sumT+=$6} END {print "A:"sumA,"C:"sumC,"G:"sumG,"T:"sumT}'
- This will print out the amounts of each nucleotide A:, C:, G:, T:
To get  the A C G T content, we used the command "seqtk comp PGSH02000029.1"
- The content values were A: 32455, C: 8082 G: 7755 T: 7690
- We used the formula "(G+C)/Total_nuc)*100 = 28.3%  (GC Content)
## How to predict the amino acid sequence of mRNA 
- Run: module load emboss/6.6.0 (unless already loaded in workspace)
- Use the command transeq from the emboss/6.6.0 module to translate the nuceleic acid sequence into amino acids
      - transeq <nucleotide_sequence_filename> <new_protein_filename>
      our command was as follows "transeq PGSH02000029.1.rev PGSH02000029.1.pep"
  to ensure the sequence was translated, we used the command "cat PGSH02000029.1.pep"
  The response displayed was: "Reversed: RSID"
