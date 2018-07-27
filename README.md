## SeqAlign2
### Shiny app for multiple sequence alignment using the msa package from Bioconductor.

Please run the Shiny app through your default web browser (e.g. Chrome, Safari..., see the Trick below if your RStudio does not run this app in web browser). Please do not use the RStudio pop up window/viewer. It might not carry out the app properly.

This shiny app requires the following four libraries: 
shiny, Biostrings, msa, dplyr  

You could use this tool to find if your CRISPR/Cas9 transgenic lines contain targeted mutations, or use it to check if your plasmids contain the sequence you want.  

For CRISPR/Cas9 transgenic lines, we suggest designing your sequencing primers to have the same directionality as the target sequence. The reason is due to the biallelic nature of Cas9 mutants. CRISPR/Cas9-generated mutations are often small deletions or insertions (INDELs). Two different INDELs (or one wild-type and one INDEL for the two alleles) for the two alleles would lead to confusion for Sanger sequencing. By using sequencing primers with the same directionality as the target sequence, you can see the INDEL events happened exactly within the target sequences region. By using sequencing primers with the opposite directionality as the target sequence, you would not be sure where the INDEL events occur.

The biallelic sequences could also be observed in sequencing chromatograms (usually saved in .ab1 format).

This shiny app only takes .seq files.

  * The user interface is self-explanatory:  
    1. First, input the target sequence. Just copy and paste from MS word or excel sheet. 
    2. Select "Reverse complement", if the target sequence needs to be reversed and complemented.
    3. Depending on the different system, you may see "Browse..." or "Choose files" icon for the next part. If you see "Browse...", you can load the .seq files by browsing through your folders.
    4. If you see "Choose files", you can also select .seq files by browsing through your folders. Alternatively, you can drag multiple .seq files directly onto the "Choose files" button. It is easier this way.
    5. You can select which range of DNA sequences you would like to use. The reason to do this is to remove low-quality nucleotides that usually are located at the two ends of Sanger sequencing reads.  
    6. The next step is to give the output file a name. The default name is SeqInfo. Please give a meaningful name for your output file. In the Shiny main panel, you can see whether the target sequence exists in the DNA sequences. In fact, the main panel info is the same as the CSV file that you can download.
    7. Select how the multiple sequence alignment would be arranged. "aligned" means the multiple sequence alignment would be arranged according to alignment. "input" means the multiple sequence alignment will be arranged according to the input and the target sequence is always at the bottom of the alignment. 
  * Note: the CSV and PDF files contain different information. 

## Output files:
You can download both the PDF and CSV files.  
  * The CSV file contains: 
    1. The name of the input file
    2. Length of DNA sequences used in this analysis
    3. Whether the target sequence is in the DNA sequences
    4. DNA sequences employed in the study
  * The PDF file contains the alignment plot.

## Example:
For target sequence, use GTTATCGCGTCTTGTCGAAC.  
For example DNA sequences, find them in the test.zip folder.  
WIth the default setting, the output should be identical to the SeqInfo.pdf and SeqInfo.R files in this repository. 
Part of the output looks like:
![image](https://github.com/hsinyenwu/SeqAlign2/blob/master/partial_output.png "output") 
You can see the target sequence and the mutations in the middle of the plot.
The test 3 sequence got an extra G. The test 4 missed an A. The test 5 could be a larger deletion/insertion after the target sequence.

## References:
Bodenhofer U, Bonatesta E, Horejs-Kainrath C and Hochreiter S (2015). “msa: an R package for multiple sequence alignment.” Bioinformatics, 31(24), pp. 3997–3999.

## System version info:
MSA Version 1.4.5  
RStudio version 0.99.903  
R 3.3.1  
Mac OS X El Capitan  

## Trick:
This one-file shiny app is easier to run. You do not need to set directory and can just execute the code directly. However, it seems that you can only adjust the browser setting using a two-file style shiny app. Once you run any two-file style Shiny app, you can see a drop down manual next to a green arrow. Select "Run External". That choice should make your shiny app run in your default web browser from now on.  
<img src="https://github.com/hsinyenwu/SeqAlign2/blob/master/external.png" width="250">   
If you are running shiny app the first time, you could check out the Coursera course "Developing Data Products". 

Have fun!
