## How to generate the reverse complement of the sequence
- Download the genome into your scratch workbench
- navigate to Scratch using cd /scratch/username
- load two modules
    - module load emboss/6.6.0
    - module load seqtk/1.3
- use module list to double check that the modules are loaded

## How to calculate the GC content of a file 
- load both modules as before
    - module load emboss/6.6.0
    - module load seqtk/1.3
- Use this command to calculate the nucleotide content of your sequence
    - seqtk comp downloaded_genome.fa | awk 'OFS="\t" {sumA+=$3; sumC+=$4; sumG+=$5; sumT+=$6} END {print "A:"sumA,"C:"sumC,"G:"sumG,"T:"sumT}'
- This will print out the amounts of each nucleotide A:, C:, G:, T:

## How to predict the amino acid sequence of mRNA 
