# How to download the _Ambystoma mexicanum_ genome 

- Navigate to this link 
- https://genome.ucsc.edu/cgi-bin/hgGateway?genome=AmexG.v6&hubUrl=http://ambystoma.uky.edu/hubExamples/hubAssembly/hub_AmexG_v6/hub.txt
- GCA_002915635.3 was used in this assignment. 
- On the command line, navigate to the directory where you will save your genome. 
- Run wget <genome_link_you_copied>.
- The saved text file is compressed and the filename ends in the extension .gz 
- Unzip the .gz file with gunzip <genome_file.gz>, and the result will be an unzipped fasta file.
