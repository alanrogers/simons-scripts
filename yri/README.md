This directory contains the data and files necessary to create raf files.

download.slr is used first to loop over the files you want to download, 
in this case in the file yri.txt. This will download all the files in the
Simons directorym which includes the vcf, tbi, and md5.

sort.slr takes the vcf files, sorts them, and produces a tbi file for the
new sorted vcf. sort.slr takes a slurm array the same size as the number of
samples. These intermediate files are kept for future use.

sbatch --array=0-2 sort.slr

filter.slr filters out sites we do not want, and produces a raf file that 
can be read by sitepat.

sbatch --array=0-2 filter.slr

Finally, these raf files can be joined using join.slr. join.slr is run

(echo -n name' '; ls *raf*) | xargs bash join.slr

where name is the desired output name of the joined raf file and the "ls *raf*"
expression represents the raf files you wish to join.

I prefer to pipe the err and out files from slurm to their own diretory, 
named errout. 
