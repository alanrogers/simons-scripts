# simons-scripts

This repo contains the slurm scripts (written by Nathan Harris) that the
rogers lab used with data from the Simons Genome Diversity Project. The 
scripts download the data, filter it, and convert it into .raf format.

There are two subdirectories: "eur" deals with French and British samples;
"yri" deals with Yoruban samples.

The simons project provides a separate vcf file for each sample. The
scripts in this repo make a .raf file for each individual and then
join these using Legofit's `joinraf` program to combine these
individual files into one for the population.

An alternative would be to join the .vcf files into a single .vcf and
then run "raf" on that.

