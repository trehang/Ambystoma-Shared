# Analyzing A Genome! 
## How to download the _Ambystoma mexicanum_ genome
1. To download the genome of your animal, first use the following two commands:
    - curl -o datasets https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/datasets
    - curl -o dataformat https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/dataformat
      followed by the command: chmod +x datasets format
2. Now, you will want to navigate to NCBI to find the genome accession number of your desired animal. When found, use the command ./datasets download genome accession 'genome accession number'. We used GCA_002915635.3 as this was the accession # for Ambystoma mexicanum. 
4. Once you run this command, you will need to unzip the file using ncbi_dataset.zip.
   If your genome is particularly large like ours, you will need to run a job using a bash script. 

5. Open nano and write a "bash script" to tell the cluster what it needs to do:
-  #!/bin/bash
- #SBATCH --partition=short
- #SBATCH --job-name=ambystoma_MM
- #SBATCH --time=24:00:00
- #SBATCH --nodes=1
- #SBATCH --cpus-per-task=2
- #SBATCH --mem=256G
- #SBATCH --output=%j.output
- #SBATCH --error=%j.error

- cd /scratch/volkova.a/amby_dataset/data_amb/GCA_002915635.3
- grep '>' GCA_002915635.3_AmbMex60DD_genomic.fna

8. The job was run with the command sbatch <bash_file_name>
9. The job was checked for completion with command squeue -u username
10. After the job was completed, an output file was produced with a list of chromosomes from the _Ambystoma mexicanum_ genome! If the output file was not in the correct directory (scratch) you can move it over from your current working directory to scratch by typing in cp <File_name> scratch  


Before you can do anything with your genomes data, navigate to your output from the previous step and write the command "cat <outputfile>". This should generate a long list of data, representing your genomes chromosomes.
1. Pick which chromosome you wish to analyze. My group and I decided to look at chromosome 14p which is represented by the sequence identifier of 'CM030330.1 Ambystoma mexicanum strain DD151 chromosome 14p, whole genome shotgun sequence'
2. Using the echo 'identifier' > gen.txt command followed by the seqtk subseq 'identifier' gen.txt > chromosome_14.txt command, you will create a new file with only your desired chromosomes sequence. When opening the files within scratch using the ls command, you should see a file name called chromosome_14.txt that contains the requested sequence.

## Finding the Reverse Complement
Now that you have your desired chromosome as a text file, you can find the reverse complement!
1. First start off by loading the following commands into your workspace: module load emboss/6.6.0 and seqtk/1.3
2. Now use, the command revseq chromosome_14.txt chromosome_14.rev to create the reverse complement of the sequence
   The first line produced:
   --> AATCCCACACAACCAGCTACAccacctgagaactccatggcttacactactccgatgaag
   
## Finding the Amino Acid Sequence 
1. Use the command transeq 'chromosome_14.txt' 'chromosome_14_amino_acid.txt'
2. Then enter the command head followed by the new file name 'chromosome_14_amino_acid.txt' to load the sequence
   The first line produced:
  --> GFLCLLFPSPWDKFFLLT*RPFQFLRWPSCLQPLPCRSLGTTSLFPL

## Finding the Entire Genome's Content
1. Once again run the commands: module load emboss/6.6.0 and module load seqtk/1.3
2. Run the command seqtk comp 'GCA_002915635.3_AmbMex60DD_genomic.fna' | awk 'OFS="\t" {sumA+=$3; sumC+=$4; sumG+=$5; sumT+=$6} END {print "A:"sumA,"C:"sumC,"G:"sumG,"T:"sumT}' 
