# How to download the _Ambystoma mexicanum_ genome 

1. Navigate to this link
  - https://genome.ucsc.edu/cgi-bin/hgGateway?genome=AmexG.v6&hubUrl=http://ambystoma.uky.edu/hubExamples/hubAssembly/hub_AmexG_v6/hub.txt
  - GCA_002915635.3 was used in this assignment. 
2. On the command line, navigate to the directory where you will save your genome. 
3. Run "wget <genome_link_you_copied>".
4. The saved text file is compressed and the filename ends in the extension .gz 
5. Unzip the .gz file with gunzip <genome_file.gz>, and the result will be an unzipped fasta file.
6. Since _Ambystoma_ has such a large genome, a bash script needs to be run to further analyze the genome. 
