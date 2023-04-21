# MEGAN BUFF Lab notebook
# clear
    - puts you down to a fresh screen#
# pwd 
    - print working directory 
# ls 
    - prints the names of the files and directories in the current directory in alphabetical order
# cd
    - change directory
    - cd shell_data ; change directories into shell data
# man ls
    - manual for the command written after it 
# cd ..
    - back out one level
# ls -a
    - list EVERYTHING including hidden directories 

 - A full path always starts with a /. A relative path does not.
# ~ 
    - shortcut for home directory 
# ls *.fastq
    - list all files with .fastq at the end 
- The * character is a special type of character called a wildcard, which can be used to represent any number of any type of character. Thus, *.fastq matches every file that ends with .fastq.
# echo *.fastq
    - pattern matches characters (produces same output as ls *)
# history
    - to see a numbered list of recent commands
# cat
    - print out all of the contents in a file 
        - Use the “/” key to begin a search. Enter the word you would like to search for and press enter. The screen will jump to the next location where that word is found.
# head
    - opens up the beginning of a file
# cp 
    - copy
# mkdir
    - make a new directory 
        - Enter mkdir followed by a space, then the directory name you want to create
# mv
    - move files and rename files 
        - rename: $ mv SRR098026-copy.fastq SRR098026-backup.fastq
# grep NNNNNNNNNN SRR098026.fastq
    - Every single line in the SRR098026 file that contains at least 10 consecutive Ns is printed to the terminal
    - use the -B argument for grep to return a specific number of lines before each match
    - -A argument returns a specific number of lines after each matching line. 
# grep -B1 -A2 NNNNNNNNNN SRR098026.fastq
    - we want the line before and the two lines after each matching line
# grep -B1 -A2 NNNNNNNNNN SRR098026.fastq > bad_reads.txt
    - redirect all the records in our fastq file that contain the N sequence and put them in a file called bad_reads
# wc 
    - word count 
# wc bad_reads.txt
    - number of words,lines and characters
# wc -l bad_reads.txt
    - number of lines 
# grep -B1 -A2 NNNNNNNNNN SRR098026.fastq | less
    - can now see the output from our grep call within the less interface
# grep -B1 -A2 NNNNNNNNNN SRR098026.fastq | wc -l 
    - count the lines in a file before creating a new file
# -v 
    - stands for --invert-match meaning grep will now only display the lines which do not match the searched pattern
# mkdir -p ~/dc_workshop/data/untrimmed_fastq/
    - allows mkdir to create the new directory, even if one of the parent directories does not already exist
# gunzip SRR2584863_1.fastq.gz
    - unzip the file so we can look at the fastq format
# head -n 4 SRR2584863_1.fastq
    - view the first complete read in one of the files our dataset by using head to look at the first four lines.
HOW BIG ARE THE FILES?
    # ls -l -h
# fastqc *.fastq*
    - run FastQC on all of the FASTQ files in this directory
- Keep our data files and our results files separate, so we will move these output files into a new directory 
    - mkdir -p ~/dc_workshop/results/fastqc_untrimmed_reads
    - mv *.zip ~/dc_workshop/results/fastqc_untrimmed_reads/
    -  mv *.html ~/dc_workshop/results/fastqc_untrimmed_reads/
# mv (file name)(new name)
# Add your name to the bottom of the bad_reads.fastq 
    append file
    $ echo "Megan" >> bad_reads.fastq
    $ cat bad_reads.fastq
# Add your name to the top of the bad_reads.fastq
    echo 'Megan' > MyNameFile 
    cat bad_reads.fastq >> MyNameFile
    head MyNameFile
# control c = cancel
enter server: ssh meb1159@ron.sr.unh.edu
password: meganbuff17
# control z
  - pause whatever is running in the current command line 
# bg
  - push whatever was running to the background so you can continue to use command line 
How big are these files?
 Use:
     ls -lhS
# ls -ltrth data/ref_genome/
    - creates list in order of creation time 

Line	Description
1	    Always begins with ‘@’ and then information about the read
2	    The actual DNA sequence
3	    Always begins with a ‘+’ and sometimes the same info in line 1
4	    Has a string of characters which represent the quality scores; must have same number of characters as line 2

Friday 2/3/2023
 ls
# list command, lists all of the files in my working directory
 pwd
# stands for print working directory
# folders are seperated with slashes
# tab will auto fill the rest of the name of your folder if you have the start of it 
# if you hit tab several times it will open up all of your folder and directory options 
# control c will cancel whatever you're doing so if you get stuck or locked up try that 
# put a hashtag before all notes that are not commands 
 PS1='$'
# setting a variable to get rid of the text on the command line
 cd
# change directories 
 rm
# means remove
ssh username@servername.edu
# connects my terminal to the teachning cluster RON on campus
# new terminal fixes all problems
username meb1159
password meganbuff17

Friday 2/10/23
enter server: ssh meb1159@ron.sr.unh.edu
password: meganbuff17
 mkdir
# make new directory, before hitting enter name new directory 
 cp
# copy file 
- slashes as you move to the right indicate folders in folders 
- put a period at the end to open a folder in your home directory 
- start typing and hit tab to autofill 
.tar is like a zip file its all compacted
 tar -xf shell_data.tar
# decompresses tar files 
 ls-f 
 ls lrth
 man (command)
 # gives a brief explanation of the command you put in and shows additional options 
-hit Q in the terminal to get back 
look into fastQ using head (fastq file name)
grep
# searches through files really quickly 
# grep 'abcd' file name 
# searching for anything that matches abcd
The up arrowwill bring you back through all of the commands you've previously run 
The pipe/pike? | (right above return button)
# helps commands work within one another 
wc
# word count 
wc-l
# word count and the list 
cd ~
# brings you back to your directory 

Friday 2/17/23
meb1159@ron - home directory
absolute path: code from the base of computer to the intended location 
    always starts with a forward slash 
relative path: moved into the next step with one step realtive to our last location   
cd .. /
 # back out of one directory 
 cd .. / ../
 # back out two directories 
 cd ~
  # back to home directory even if no clue where you are 
  Control C
  # didn't run command above 

        Exercise 3a: Three ways to change directories to HOME from untrimmed_fastq
        1. cd/home/users/meb1159/gen711/shell_data/untrimmed_fastq/
        2. cd .. / .. / .. /
        3. cd ~

Revealing Hidden Files:
 1. ls -a   
  # shows hidden directories 
 2.  cd .hidden/
  # changes directories into the hidden file 
 3. ls 
  # what's in the hidden file
 4. head (file name)
 # open the file 
OR
 cat
 # cat (file name)

*
 #  makes anything match
 ls *fastq
    shows us everything in fastq form not every file 
meb1159@ron:~/gen711/shell_data/untrimmed_fastq$ ls /bin/c*
  the star after the c means c is what matches, anything after the the c doesn't have to match 

  echo '    '
   # repeats whatever is between the apostrophes 
  echo *( )
   # shows you everything that matches that description 
   # very much like ls*
Ways to go back to things you previously ran:
 control R
    # reverse search 
history 
    # prints your history to the screen 

search through an output using 'grep'

filter 
grep 'NNNNN' SRQ... 
# shows us everything with that sequence in it

grep -A -B
 # "i want to grab some number of lines before match and some number of lines after match"
 # grep -A2 -B1
 # save two lines before and one line after 

 Friday 2/24/22

Review:
- Change Working Directories:
    cd gen711/shell_data/untrimmed_fastq
- Word search files with grep
  - N indicates a no match or a poor match 
- cd ~ 
   # home from no matter where you were 
- cd ../
   # move backwards one folder 
- ls-a
   # shows both directories and hidden files  
cat shell_data/.hidden/youfoundit.text
   # open the hidden file
- *
   # literally means anything 
ls /bin/c*
 # list of all the files in 'bin' that start with c 
ls /bin/c* | wc -l
 # gives you a final count of how many files in bin start with C
ls /bin/c* > c_programs.txt
 # 

New:
realpath [name of directory]
 # shows you the exact path to get where you want to end up 
 | directs the output on one to the input of another 
 > 
 # means redirect 
 >> 
 # apend file 
cp /tmp/*.fastq.gz .
 #
gunzip *fastq.gz
 # expand all files that end in fastq.gz from zip format 
gunzip
 - opening up the condensed files 
fastqc -h
# the help page for fastqc gives you a little summary and how to use it 
fastqc
#
 fastqc *fastq 
 - everything that ends in fastq
mkdir
 # make new directory 
mkdir -p
 # making directory pathway, creates everything in the whole line 
  mkdir -p  ~/dc_workshop/data/untrimmed_fastq
     - made data folder in dc_workshop
    mkdir -p ~/dc_workshop/results/fastqc 
     - made results folder in dc_workshop
less
#
outdir 
 # -o
realpath 
 # shows you the exact path to get to the location you specified 
control z 
  # pause whatever is running in the current command line 
 bg
  # push whatever was running to the background so you can continue to use command line 
 top
  # shows you everything that is running on the cluster right now 
 q
  # back to command line from top or less -S
-h 
 - means human readable 
conda activate genomics
 - opening an environnment preloaded with everything we need 
 # conda activate genomics 
jobs
 - shows everything that is currently running 
kill %1
 # killed the first job a.k.a stop it from running 
mv *.zip
 # move everything that ends in zip to  
unzip *zip
 # just like gunzip 
cat */summary.txt
 - within this directory  groups things together 
cat */summary.txt | grep 'P
 - shows you everything that "passed" 
Notes:
 Each read has 4 lines to it 
 Read
 +
 B.... base call quality 
 
 How big are these files?
 Use:
     ls -lhS


Friday 3/3/23
   'command,shift,P'
      # opens up a menu of options 
   'command, s' 
      # saves
- with new saved command if you write command in new line on lab notebook and hit 'control enter' to send it to the terminal 
   sftp username@meb1159@ron.sr.unh.edu
      # 
realpath
   ls /tmp/fastqc_output/*_1_fastqc/Images/*png
      # 
   get /tmp/fastqc_output/SRR2584863_2_fastqc/Images/per_sequence_quality.png
      # 

Friday 3/24/23
    curl -L -o data/ref_genome/ecoli_rel606.fasta.gz ftp://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/017/985/GCA_000017985.1_ASM1798v1/GCA_000017985.1_ASM1798v1_genomic.fna.gz
        #
    gunzip data/ref_genome/ecoli_rel606.fasta.gz
        #unzip the downloaded file 
    curl -L -o sub.tar.gz https://ndownloader.figshare.com/files/14418248
        #
sometimes when files are downloaded they are in tar format instead of zip which requires its own "unzipping"
    tar xvf sub.tar.gz
        #
    mv sub/ ~/dc_workshop/data/trimmed_fastq_small
        #mkdit
    sam-alignment files
    bam- compressed alignment file 
conda env listbcftools mpileup -O b-o results/bcf/SRR2584866_raw.bcf -f data/ref_genome/ecoli_rel606.fasta results/bam/SRR2584866.aligned.sorted.bam
    # list of environments in the cluster 
condr activate genomics-plus
    # enter the genomics plus environment 
bwa index data/ref_genome/ecoli_rel606.fasta
    #
ls -ltrth data/ref_genome/
    # creates list in order of creation time 
bwa mem data/ref_genome/ecoli_rel606.fasta data/trimmed_fastq_small/SRR2584866_1.trim.sub.fastq data/trimmed_fastq_small/SRR2584866_2.trim.sub.fastq > results/sam/SRR2584866.aligned.sam
    first thing- reference genome file 
    second thing- forward read 
    thrid thing- reverse read 
take fastq and run alignment indicate that at the end of a file like (.aligned.sam)
file name: results/sam/SRR2584866.aligned.sam
less -S results/sam/SRR2584866.aligned.sam
    # open up the data in that file 
'q' 
    #jumps to the bottom of a long file 
wc -l 
    # count the number of lines in the file 
accurate number of lines in a file: 
     grep -v 
        #inverse grep, finds something that matches to it it won't give us what matches but will give us everything else 
    grep -v '^@' results/sam/SRR2584866.aligned.sam | wc -l

    -up and down arrows can push most recent command into open command line 
samtools view -S -b results/sam/SRR2584866.aligned.sam > results/sam/SRR2584866.aligned.bam
    #convert whole file into bam and save it in the noted location 

samtools sort -o results/bam/SRR2584866.aligned.sorted.bam results/bam/SRR2584866.aligned.bam 

bcftools mpileup -Ob -o results/bam/SRR2584866_raw.bcf -f data/ref_genome/ecoli_rel606.fasta results/bam/SRR2584866.aligned.sorted.bam 

$ bcftools call --ploidy 1 -m -v -o results/vcf/SRR2584866_variants.vcf results/bcf/SRR2584866_raw.bcf 

Friday 3/31/23
    review used today:
        cd ../ to go backwards 
        mkdir to make directory 
        ls to see what folders and files you have where 
 open a new window, sftp meb1159@ron.sr.unh.edu
    #establish secure connection 
get /home/users/meb1159/dc_workshop/data ref_genome/ecoli_rel606.fasta
    # download the files 

    /home/users/meb1159/dc_workshop/results/bam/SRR2584866.aligned.sorted.bam
    /home/users/meb1159/dc_workshop/results/sam/SRR2584866.aligned.sorted.sam

Friday 4/14/23

repositories on Github is kind of like goodgle docs, way to share data to other people and either allow their changes or deny them 
- putting all results and information for final projects into respositories 
    make repo
        - 
- can edit in web interface or edit in vscode and upload changes to github 
## in vscode makes a new section 
- code format for plots in in provided example 

Project layout:
Title
Authors 
Background
Methods
Findings  

- Making our own repositorys 
 - hit '+' 
 - hit 'new repository' 
 - give it a name, description and set limits 

 git clone [http link]
  - pulls whole repository into folder on vscode 

github: jthmiller/gen711-811-example

Group: Nicole, Kim, Me

create a pull request to send something to be published on shared page... nicole has to approve it 

https://github.com/meb1159/lab-notebook 

Friday 4/21/2023 
link to main info repository: https://github.com/jthmiller/eDNA-metabarcoding-intro/tree/Gen711-811
    link to our data: /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-1
    
#Steps to complete this lab:
1. Run Fastp to trim the 'poly-g' tails of the reads
2. Import the directory of reads with qiime and save the output in your directory
3. Use the 'cutadapt' program in qiime to trim off the primers

made directory-  mkdir trimmedfastqs
activated conda - conda activate genomics

touch testfile.txt
    # made a tester file with nothing in it to play with 

cp /tmp/gen711_project_data/fastp.sh ~/fastp.sh
cp /tmp/meb1159/711-final-project/fastp.sh ~/fastp.sh
    # copied the fastp.sh to our home directory 
chmod +x ~/fastp.sh
    # changing the permissions of the file we just copied 

cp /tmp/meb1159/711-final-project/fastp.sh ~/fastp.sh

./fastp.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-2 trimmed_fastqs
    # 150 is thepoly g length cut off, with the directory of the reads to trim and the directory to store the reads in 
./fastp.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-1 trimmed_fastqs
    # # 150 is thepoly g length cut off, with the directory of the reads to trim and the directory to store the reads in 

conda env list  
conda activate qiime-2022.8

qiime tools import \--type "SampleData[PairedEndSequencesWithQuality]"  \ --input-format CasavaOneEightSingleLanePerSampleDirFmt \ --input-path /home/users/meb1159/trimmed_fastqs \ --output-path <path to an output directory>/<a name for the output files> \
    ## import the directory of poly-G trimmed FASTQ files into a single 'qiime file'

qiime cutadapt trim-paired \
    --i-demultiplexed-sequences <path to the file from step 2> \
    --p-cores 4 \
    --p-front-f <the forward primer sequence> \
    --p-discard-untrimmed \
    --p-match-adapter-wildcards \
    --verbose \
    --o-trimmed-sequences <path to an output directory>/<name for the output files>.qza
    ## remove the primers and adapters of each pair of sequences

qiime demux summarize \
--i-data <path to the file from step above> \
--o-visualization  <path to an output directory>/<a name for the output files>.qzv 
    ## make a summary of the summary.qzv file