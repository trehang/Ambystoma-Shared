# How to download the _Ambystoma mexicanum_ genome 

1. Navigate to this link
  - https://genome.ucsc.edu/cgi-bin/hgGateway?genome=AmexG.v6&hubUrl=http://ambystoma.uky.edu/hubExamples/hubAssembly/hub_AmexG_v6/hub.txt
  - GCA_002915635.3 was used in this assignment. 
2. On the command line, navigate to the directory where you will save your genome. 
3. Run "wget <genome_link_you_copied>".
4. The saved text file is compressed and the filename ends in the extension .gz 
5. Unzip the .gz file with gunzip <genome_file.gz>, and the result will be an unzipped fasta file.
6. Since _Ambystoma_ has such a large genome, a bash script needs to be run to further analyze the genome. 
7. A bash script was run like so:

#!/bin/bash
#SBATCH --partition=short
#SBATCH --job-name=ambystoma_MM
#SBATCH --time=24:00:00
#SBATCH --nodes=1
#SBATCH --cpus-per-task=2
#SBATCH --mem=256G
#SBATCH --output=%j.output
#SBATCH --error=%j.error

cd /scratch/macwan.m/GCA_002915635.3
grep '>' GCA_002915635.3.fa

8. After the job was completed, an output file was produced with a list of chromosomes from the _Ambystoma mexicanum_ genome. 
