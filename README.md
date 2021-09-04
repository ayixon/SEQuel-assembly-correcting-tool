# SEQuel-assembly-correcting-tool
Tests using SEQuel for correcting errors (insertions, deletions, and substitutions) in genome assemblies. 

All credits to the developers: 

Roy Ronen, Christina Boucher, Hamidreza Chitsaz, Pavel Pevzner, SEQuel: improving the accuracy of genome assemblies, Bioinformatics, Volume 28, Issue 12, 15 June 2012, Pages i188–i196, https://doi.org/10.1093/bioinformatics/bts219

# Installing instructions:

1-Under a conda environment install bwa and BLAT                                                                                                

2-Download the SEQuel package from: http://bix.ucsd.edu/SEQuel/download.html

3-Java and perl dependencies must be ok

4-Run the script: $ perl prep.pl -t 23 -r1 miseq_reads_R1.fastq -r2 miseq_reads_R2.fastq -c assembly_X.fasta

    # -p option depends on your processor

5-Look in to the prep.log file for Average External Insert-Size

6-Run SEQuel tool for correction: 

$ java -Xmx100g -jar SEQuel.jar -p 23 -c assembly_X.fasta -ap prep/reads_aln.sam -i 1137
   
    # option -Xmx100g is the actual memory allocation in "my experiments"
    
    you may want to check this parameter accordingly (recomended>4G for prevent the error: Exception in thread "main" java.lang.OutOfMemoryError: GC overhead limit exceeded. 
    
    # option -i must be the Average External Insert-Size in the prep.log file
    
   # more information on the developer page (highly recommended): http://bix.ucsd.edu/SEQuel/man.html
