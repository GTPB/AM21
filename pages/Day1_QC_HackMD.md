<center><img src="https://i.imgur.com/sCqXiVG.png" alt="drawing" width="300"/></center>

# Quality control & removal of optical duplicates

<center><img src="https://i.imgur.com/CP1SD8S.png" alt="drawing" width="300"/></center>
<p align="middle">

:::success
In this exercise you will be working with a shotgun metagenomic data from the human gut sample, more specific the faeces of premature babies. The objectives of the practical is to see if the data set is complete, get to know your data and to perform quality control on this next-generation sequence data. You will also remove optical duplicates present in the data. The DNA has been produced on a Illumina MiSeq machine 2 x 300 bp paired-end (PE) reads.

**In this exercise you will:**

1. How to use the exercise documents
2. Make sure all your data is there using **md5sum**
3. Get to know the FASTQ file format
4. Simple FASTQ/FASTA manipulations using **SeqKit**
5. Perform quality control of the sequence data using **FastQC**
6. Remove optical duplicates using **Clumpify**
:::

## 1. How to use the exercise documents
:::success
💡 This part introduce how the exercise documents in this course should be used
:::

The first thing to notice is that there are links to the different sections in the exercise in the left hand menu of each exercise together with a green box containng a short introduction to the exercise or tool you will be using

You will also find links to external web sites describing most of the tools you will be using throughout the exercises

You can copy and paste commands directly from this HTML and into your terminal if you don't want to write the complete commands yourself

The commands are written in boxes like this:

	any command

File paths to data are also written like the commands, for example: <kbd>path/to/files</kbd>

The tilde (~) symbol means home directory, therefore <kbd>~/practicals/</kbd> is the same as <kbd>/home/practicals</kbd>

We try to write tool in **bold letters** and filnames in boxes like this `filename`, but we are only human...

The tasks you will be performing will be annonced like this:

<span style="color:blue">I] Read this line which is printed in blue 

You will be given questions troughout the execises. The questions will be given like this:

❓ Can you read this?

The solution to the exercises is found below each question like this:

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
The solutions will be printed on a grey background
</details>

<br/>

Hints, notes and useful information are (often) put in blue boxes like below:

:::info
:information_source: IMPORTANT SHORTCUTS THAT WILL SAVE YOU LOTS OF TIME

* **Shortcut for copying from the web browser = `ctrl + c`**
* **Shortcut for pasting into the terminal = `ctrl + shift + c`**
:::

:::danger
**Remember:** As a quality control that you are on the right track with your data, we want you to fill in some of the basic statistic metrics in this table: [https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:16%;background:#291;text-align:center;">
   <span style="color:white"><span>Part 1 finished</span>
 </div>
</div>

## 2. Make sure all your data is there

<center><img src="https://i.imgur.com/XlGPlRR.png" alt="drawing" width="300"/></center>
<p align="middle">


:::success
💡 It is very common that data is produced at a different location than where the analysis is preformed, and the data need to be transferred between two machines. It can happen that the file transfer is interrupted leading to incomplete transfer of the data.

Many tools cannot tell if the data you use as input for your analysis is complete. It is therefore reccomendable to ensure that the data you are going to analyse is identical to the data from where you copied it from. File checksums can ensure data integrity. 

We have calculated the checksum using the tool **md5sum** before transferring the files to the shared disk. The MD5 checksum for the data is in the file `md5_data.txt`. 
:::

<span style="color:blue">I] The data for this exercise is in the directory <kbd>~/practical/2/rawdata</kbd>. Move to the directory and view what is in the directory:

	cd ~/practical/2/rawdata

<span style="color:blue">II] Open the `md5_data.txt` file and look at the content in a text editor. It should have one checksum per file.

<span style="color:blue">III] Check that the sum is correct for your files by typing in the **terminal**:

	md5sum -c md5_data.txt
	
If the files are complete, the test should return **'OK'** for all files

<span style="color:blue">Optional: You can try to generate MD5 checksum on a file and output it to a file:
 
	md5sum filename > md5_test.txt

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:33%;background:#291;text-align:center;">
   <span style="color:white"><span>Part 2 finished</span>
 </div>
</div>

## 3. Get to know the FASTQ file format

<center><img src="https://i.imgur.com/ouIQZZe.png" alt="drawing" width="800"/></center>

<br/>

:::success
💡FASTQ format is a text-based format for storing both a biological sequence (usually nucleotide sequence) and its corresponding quality scores. Both the sequence letter and quality score are each encoded with a single ASCII character for brevity.

A FASTQ file normally uses four lines per sequence.

* Line 1 begins with a '@' character and is followed by a sequence identifier and an optional description (like a FASTA title line).
* Line 2 is the raw sequence letters.
* Line 3 begins with a '+' character and is optionally followed by the same sequence identifier (and any description) again.
* Line 4 encodes the quality values for the sequence in Line 2, and must contain the same number of symbols as letters in the sequence.
:::

:::info
:information_source: The FASTQ files containing the sequence reads are normally compressed with **gzip**. The command 'file' let you test the type of file.
:::

<span style="color:blue">I] In the directory where the compressed FASTQ files are located, type:

	file sample1_R1.fastq.gz
	
❓ What type of file is this?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Compressed file
</details>

<br/>

:::info
:information_source: To look at the content you must either uncompress the files, or you can use **zcat** to preview the content. **head** is a preview tool. '|' pipes the output from one command into the next command. 
:::

<span style="color:blue">II] Try to run the following command:

	zcat sample1_R1.fastq.gz | head
	
❓ Each sequence read has four lines. What information does these lines contain? 
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Sequence name, base calls, quality, line separator
</details>

<br/>

<span style="color:blue">III] You can preview more of the file, eg. the 100 first lines by:

	zcat sample1_R1.fastq.gz | head -n 100

It may be useful to know how many sequences a FASTQ file contain. Also it is useful to convert FASTQ files to FASTA format.

<span style="color:blue">IV] Count numbers of sequence reads in the compressed file: 

	zcat sample1_R1.fastq.gz | paste - - - - | wc -l

❓ Are there equal number of sequence reads in both the paired FASTQ files?

:::danger
Fill in the answer in the shared [Google docs table](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:50%;background:#291;text-align:center;">
   <span style="color:white"><span>Part 3 finished</span>
 </div>
</div>

## 4. Simple FASTQ/FASTA manipulations using SeqKit

<center><img src="https://i.imgur.com/ouIQZZe.png" alt="drawing" width="800"/></center>

<br/>

:::success
💡**Seqkit** is a nice and extremely fast tool for processing sequences in the FASTA or FASTQ format. You can use the **Seqkit** to convert the FASTQ file to a FASTA file in addition to other manipulations such as extracting subsequences from FASTA/Q file with reads ID (a name list file). 

Instructions for usage can be found [here](http://bioinf.shenwei.me/seqkit/#subcommands).
:::

:::info
:information_source: In order to run **Seqkit** you need activate the correct **Conda** environment.
:::

<span style="color:blue">I] In the directory <kbd>~/practical/2/</kbd>, create a directory named <kbd>seqkit</kbd> and move to the directory

<span style="color:blue">II] Make a symbolic links to the raw data:

	ln -s ~/practical/2/rawdata/sample1_R* .
	
<span style="color:blue">III] Use **Seqkit** to produce simple statistics of your files with the subcommand `stats`:

	seqkit stats *.fastq.gz

<span style="color:blue">IV] Try to use the `-a` flag

❓ What is the main difference between the outputs?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
The -a flag prints all statistics, including quality measures
</details>

<br/>

❓ What is the average length of the sequence reads in `sample1_R1.fastq.gz`?

:::danger
Fill in the answer in the shared [Google docs table](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

❓ How many percent of the sequence reads in `sample1_R1.fastq.gz` have an average above Q30?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
91.63 %
</details>

<br/>

<span style="color:blue">V] View the top two sequence reads in the forward FASTQ file using the subcommand `head`:

	seqkit head -n 2 sample1_R1.fastq.gz

<span style="color:blue">VI] View the top two sequence reads in the forward FASTQ file using the subcommand `range`:

	seqkit range -r 1:2 sample1_R1.fastq.gz

<span style="color:blue">VII] View the last two sequence reads in the forward FASTQ file using the subcommand `range`:

	seqkit range -r -2:-1 sample1_R1.fastq.gz

<span style="color:blue">VIII] You can combine several subcommands, eg. to produce simple statistics for the first 100 sequence reads:

	cat sample1_R1.fastq.gz | seqkit range -r 1:100 | seqkit stats -a

<span style="color:blue">IX] Convert fastq.gz to FASTA using the subcommand `fq2fa`: 

	seqkit fq2fa sample1_R1.fastq.gz -o sample1_R1.fasta

:::info
:information_source: **HINT**: here is a unix one-liner to do the same. You can try it optionally:

	gunzip -c sample1_R1.fastq.gz | awk '{if(NR%4==1) {printf(">%s\n",substr($0,2));} else if(NR%4==2) print;}' > sample1_R1.fasta
:::

<span style="color:blue">X] Have a look at the FASTA file:

	head sample1_R1.fasta
	
❓ What is the main difference between a FASTQ and a FASTA file?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
FASTQ has 4 lines pr read, FASTA only 2. FASTQ contain information about basecalling quality
</details>

<br/>

<span style="color:blue">XI] Convert the reverse FASTQ to FASTA: 

	seqkit fq2fa sample1_R2.fastq.gz -o sample1_R2.fasta

<span style="color:blue">XII] Concatenate the two FASTA files (head to tail) using **cat** and write out the new file:

	cat sample1_R1.fasta sample1_R2.fasta > sample1_cat.fasta

It is possible to use **Seqkit** in order to subsample sequences by number or proportion. 

<span style="color:blue">XIII] Subsample 100 read pairs from the FASTQ files using the subcommand `sample`:

	seqkit sample -n 100  -s 0 sample1_R1.fastq.gz -o sub_sample1_R1.fastq.gz
	seqkit sample -n 100  -s 0 sample1_R2.fastq.gz -o sub_sample1_R2.fastq.gz
	
	# -n, sample by number (result may not exactly match)
	# -s, random seed

❓ How many sequence reads are there in the reduced file: 
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
```zcat sub_sample1_R1.fastq.gz | echo $((`wc -l`/4))``` = R1: 100 reads
</details>

<br/>

<span style="color:blue">XIV] Subsample 10% of the reads from the R1 FASTQ file using the subcommand `sample`. Hint: the flag `-p` = sample by proportion.

<br/>

❓ Count the number of sequence in one of the reduced files. How many sequence reads were there?

:::danger
Fill in the answer in the shared [Google docs table](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

:::info
:information_source: If you remember from the lecture, the FASTQ header contains information from the sequencing machine, among other the position on the flow cell:

<br/>

<center><img src="https://i.imgur.com/CLQXx0t.png" alt="drawing" width="800"/></center>

<br/>

If you check the FASTQ headers in your `porp_sample1_R1.fastq.gz` you will notice that the sequence reads were produced on different tiles on the flow cell.
</div>
:::

<span style="color:blue">XV] Use the subcommand `grep` to extract all sequence reads from tile 2119. Hint: read the uncompressed file into the memory using `zcat`:

❓How many sequence reads were there from tile 2119 in `porp_sample1_R1.fastq.gz`?

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
7581 reads

```zcat porp_sample1_R1.fastq.gz | seqkit grep -n -r -p M01337:63:000000000-AK46N:1:2119 | seqkit stats```
</details>

<br/>

<span style="color:blue">XVI] You can use the subcommand `grep` to extract all sequence reads that has a certain sequence pattern. Extract all reads containing the pattern TTCCATCCACCCC from `porp_sample1_R1.fastq.gz`. Hint: read the uncompressed file into the memory using `zcat`:

❓How many sequence reads contained the pattern TTCCATCCACCCC in `porp_sample1_R1.fastq.gz`?

<br/>

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
2 reads

```zcat porp_sample1_R1.fastq.gz | seqkit grep -s -i -p TTCCATCCACCCC | seqkit stats```
</details>

<br/>

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:66%;background:#291;text-align:center;">
   <span style="color:white"><span>Part 4 finished</span>
 </div>
</div>

## 5. Quality control using FastQC

<center><img src="https://i.imgur.com/7O70vEM.png" alt="drawing" width="800"/></center>

<br/>

:::success
💡We will perform the quality control of the raw data  with **FastQC**, a program that has a graphical interface. 

Instructions and examples of the **FastQC** usage can be found [here](http://www.bioinformatics.babraham.ac.uk/projects/fastqc/) and [here](https://biof-edu.colorado.edu/videos/dowell-short-read-class/day-4/fastqc-manual).
:::

:::info
:information_source: In order to run **FastQC** you need activate the correct **Conda** environment.
:::
 
<span style="color:blue">I] In the directory <kbd>~/practical/2/</kbd>, create a directory named <kbd>fastqc</kbd> and move to the directory

<span style="color:blue">II] Make a symbolic links to the raw data:

	ln -s ~/practical/2/rawdata/sample1_R* .

<span style="color:blue">III] Start **FastQC** by typing `fastqc` in a terminal. After a few second the graphical **FastQC** interface will appear. 

<center><img src="https://i.imgur.com/weAF7F6.png" alt="drawing" width="800"/></center>

<br/>

<span style="color:blue">VI] In the **FastQC** GUI, click on **"File"** and select the two compressed FASTQ files `sample1_R1.fastq.gz` and `sample1_R2.fastq.gz` in the <kbd>~/practical/2/rawdata</kbd> directory.

:::info
:information_source: **FastQC** operates a queuing system where only one file is opened at a time, and new files will wait until existing files have been processed

The left hand side of the main interactive display show a summary of the modules which were run and an evaluation of the results.
:::

❓ What does green tick, the orange triangle and the red cross indicate?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Entirely normal (green tick)

Slightly abnormal (orange triangle)

Very unusual (red cross)
</details>

<br/>

❓ How many sequence reads does each of your dataset consist of? 
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
3041465 reads in R1 and 3041465 reads in R2
</details>

<br/>

❓ What is the sequence length range? 
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Sequence length 35-301
</details>

<br/>

❓ What is the GC content of the metagenomic sequence data? 

:::danger
Fill in the answer in the shared [Google docs table](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

❓ What quality format are your sequence reads in?

<center><img src="https://i.imgur.com/4htZLd2.png" alt="drawing" width="800"/></center>

<br/>

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Illumina 1.9
</details>

<br/>

❓ What does a quality score of 30 indicate about the accuracy? 

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Probability of Incorrect Base Call 1 in 1000
</details>

<br/>

❓ Which of the sequence files would you say have the best base calling quality?

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
R1
</details>

<br/>

:::info
:information_source: The '**Per Base Sequence Quality**' shows an overview of the range of quality values across all bases at each position in the FASTQ file. The y-axis on the graph shows the quality scores. The higher the score the better the base call. The quality of calls on most platforms will degrade as the run progresses, so it is common to see base calls falling into the orange area towards the end of a read.

1. The central red line is the median value
1. The yellow box represents the inter-quartile range (25-75%)
1. The upper and lower whiskers represent the 10% and 90% points
1. The blue line represents the mean quality
:::

❓ What are the major differences between the quality of the reads in R1 and in R2?

<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
A bit lower quality in R2 + it drops more dramatically towards the end
</details>

<br/>

<span style="color:blue">V] View the '**Per Base Sequence Content plots**'. In a random library you would expect that there would be little to no difference between the different bases of a sequence run, so the lines in this plot should run parallel with each other. 

❓Does your sequence reads have any biases?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Bias in the start, according to Illumina this is a calibration phase for the sequencing machine
</details>

<br/>

:::info
:information_source: Illumina believes this effect is caused by the "not so random" nature of the random priming process used in the protocol. This may explain why there is a slight overall G/C bias in the starting positions of each read. The first 12 bases probably represent the sites that were being primed by the hexamers used in the random priming process. Look at the '**K-mer content plot**' and see which K-mers are overrepresented and in which position they are.
:::

<span style="color:blue">VI] Have a look at the other modules, especially the one marked with a red cross. Can you say something about the quality of these sequences, e.g duplication level, etc?

❓ How many reads in `sample1_R2.fastq.gz` have some sequences that are overrepresented and what is the overrepresented sequence?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
4631 reads, NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN
</details>

<br/>

❓ Look at the "Per tile sequence quality". What does this plot tell you about the data?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
The data for both samples are very good. Brighter colours means lower quality from the average quality for each tile
</details>

<br/>

❓ Look at the "Per sequence GC content". The displayed Theoretical Distribution assumes a uniform GC content for all reads. Why do you think your data deviates from this?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Sequences from metagenomic samples derives from different species that may have very different nucleotide composition.
</details>

<br/>

<span style="color:blue">VII] Save the HTML reports before closing **FastQC**.

<br/>

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:83%;background:#291;text-align:center;">
   <span style="color:white"><span>Part 5 finished</span>
 </div>
</div>


## 6. Remove optical duplicates from NGS data

<center><img src="https://i.imgur.com/KCI3FVv.jpg" alt="drawing" width="800"/></center>

:::success
💡It is good practice to remove optical duplicates for all sequence data produced by HiSeq 2500, MiSeq or NextSeq platforms for any kind of project in which you expect high library complexity (such as WGS). Optical duplicates are duplicates with very close coordinates on the flow cell. And by duplicate removal, it means removing all duplicate copies except one. **Clumpify** is a tool that removes duplicates and maximise gzip compression. **Clumpify** outputs paired, synchronised read pairs.

Read more [here](https://www.biostars.org/p/225338/#230178)
:::

<span style="color:blue">I] In the directory <kbd>~/practical/2/</kbd>, create a directory named <kbd>clumpify</kbd> and move to the directory

<span style="color:blue">II] Make a symbolic links to the raw data:

	ln -s ~/practical/2/rawdata/sample1_R* .

<span style="color:blue">III] Remove optical duplicates and tile-edge duplicates. **NB! YOU HAVE TO SET DISTANCE (replace the X in "dist=X")**. 

:::info
:information_source: Try to look at the parameter options for this tool:

<br/>

	clumpify.sh in1=sample1_R1.fastq.gz in2=sample1_R2.fastq.gz out1=sample1_clumped_R1.fastq.gz out2=sample1_clumped_R2.fastq.gz dedupe optical dist=X -Xmx8g
			
	# dedupe, Remove duplicates - combined with optical dist = Remove optical duplicates
	# optical dist=X, duplicates within X pixels of each other
	# -Xmx8g, set memory to 8 GB RAM
	
	OUTPUT: 
	sample1_clumped_R1.fastq.gz
	sample1_clumped_R2.fastq.gz
:::

<span style="color:blue">IV] When **Clumpify** finishes, look at the number of reads and file size of the original FASTQ files and the "clumpified" files.

❓ What does the flag in1 do?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Specify first input file
</details>

<br/>

❓ What does the flag out1= do?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Name first output file
</details>

<br/>

❓ How many duplicates were identified?

:::danger
Fill in the answer in the shared [Google docs table](https://docs.google.com/spreadsheets/d/1JQmH5j6ygClMxUfMn654lhGKU560LoSAXW61DA03Zg8/edit?usp=sharing)
:::

❓ How many percent smaller is the size of the "clumpified" file of R1 relative to the original file?
<details>
<summary>Solution - Click to expand 
</summary>
<div style="background-color:#c9cace">
Almost 40 less%
</details>

<br/>

As you can see, even only a small number of reads were removed as being optical duplicates, the file compression is greatly improved by **Clumpify**. Gzip compression becomes much more efficient by reordering reads so that reads with similar sequence are nearby.

<summary><span style="font-weight:bold">Progress tracker</summary>
<div style="padding:1px;background:#CCC;">
 <div style="width:100%;background:#291;text-align:center;">
   <span style="color:white"><span>Complete</span>
 </div>
</div>

<br/>

:::warning
That was the end of this practical - Good job 👍
:::
