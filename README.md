# SADs

This is a pipeline that will analyze species abundance distributions (SADs) for transposable elements across multiple genomes.  

To begin the analysis, you should have two things in the main directory: 

1. specieslist.txt --> A text file listing all genome abbreviations.  I prefer 6-digit codes (Canus Lupis = CanLup) but it is up to the user

2. originals --> A directory with a bedfile for each genome and labeled with abbeviation: CanLup.bed

3. bedfiles --> An empty directory for processed bedfiles (Step 1)

4. scripts --> A directory for all shell and R scripts.  I prefer to move the shell and R script I am currently working with into the main directory
until I have completed that step.  Then I move them back to scripts.  All shell scripts are named to match the R script it uses. 
Example: keep5bedfiles.sh uses keep5bedfiles.R

5. output --> A directory for any outputs that might be useful later.  I will move an output file to this directory after I complete a step if I think
it might be useful.  Ex: KEEP5BEDFILES.oxxxxx


Step 1: Process original bedfiles
- This will take the original bedfiles located in the directory: originals
- It will use the specieslist.txt
- It will keep only TEs in the top 5 orders (LINE, SINE, LTR, RC, & DNA)
- It will keep only TEs that have a minimum of 100 hits
- It will create new bedfiles

To do this step: 
- Move keep5bedfiles.R and keep5bedfiles.sh from the scripts dir to the main dir
- sbatch keep5bedfiles.sh
- when complete, move keep5bedfiles.R and keep5bedfiles.sh back to scripts dir
- move new bedfiles to bedfiles dir
- move output file to output dir

Step 2: Determine species richness (S) and total abundance (N) for each genome
- This will take the processed bedfiles in the dir: bedfiles
- It will use the specieslist.txt
- It will calculate and store: genome abbrev, species richness, and total abundance
- And add these to a text file: max.txt

To do this step: 
- Move maxSmaxN.R and maxSmaxN.sh from the scripts dir to the main dir
- Create a text file called max.txt that is tab separated with columns: genome S N
- sbatch maxSmaxN.sh
- when complete, move maxSmaxN.R and maxSmaxN.sh back to the scripts dir
- delete output file
- Open max.txt and detemine the maximum S and the maximum N


