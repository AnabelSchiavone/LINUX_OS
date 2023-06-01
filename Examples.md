# LINUX_OS
This repo features projects where the CLI was utilised in conjunction with Bash Scripting 

**QUESTION 1 – DATA MANIPULATION**

_Create a file called "table.csv" containing all the lines of /femalenames.txt with all white space between words changed into a single comma._

Touch table.csv
Cp /femalenames.txt table.csv
Vim table.csv
:%s/\s\+"/,/g
:wq
Chmod 777 table.csv
./table.csv r

**QUESTION 2 – LIST SORTING **

_Create a file called "alphabetical.txt" in your home directory containing the lines of femalenames.txt ordered alphabetically by NAME._

Touch alphabetical.txt 
Sort femalenames.txt > alphabetical.txt 

**QUESTION 3 – LIST CUT**

_Create a file called "names.txt" containing only the first column of femalenames.txt in its existing order._

Touch names.txt
cut -f1 -d’,’ table.csv > name.txt

**QUESTION 4 – SEARCH PREFIX**

_Create a bash script called searchprefix.sh which takes two arguments, a string and a file (in that order). The output should be each line which matches the string from the beginning of the line. For example, given a string "ANA" the line starting with "ANABEL" will be printed, but the line starting with "SUSANA" will not._

#!/bin/bash
cat $2 | grep ^$1

**QUESTION 5 – MULTIPLE FILE STRING DETECTION **

_Create a file called "anne-files.txt" containing the list of names of files in /Gutenberg which contain the STRING 'Anne' inside them (including Annemarie and Annetta). Ensure there is one filename per line (WITH THE FULL PATHNAME), that there are no extra blank lines in anne-files.txt, and that no filename occurs more than once. Each line should only contain the filename, no additional detail._

Grep -l Anne* /Gutenberg* | sort -u > anne-files.txt 

**QUESTION 6 – GREP AND WORDS **

_Create a file called "anne-words.txt" containing only the lines of /12frd10.txt containing the name (WORD) 'Anne'. Note that 'Annette' and 'Annemarie' do not count. lines should be in the same order as in 12frd10.txt._

Grep -w Anne /12frd10.txt > anne-words.txt 

**QUESTION 7 – GREP AND REGULAR EXPRESSION **

_Create a file called "natmat.txt" containing, IN THE ORIGINAL ORDER, only the lines of /femalenames.txt starting with the string 'NAT' or 'MAT'. _
 
 grep '^\(NAT\|MAT\)' /femalenames.txt > natmat.txt

**QUESTION 8 – NAME FREQUENCY **

_Create a bash script called namefreq.sh which takes one argument - a name. The output should be the FREQUENCY of that name's use, which is the entry in the second column os /course/linuxgym/census/femalenames.txt
#!/bin/bash_

grep -w $1 table.csv | cut -f2 -d,

**QUESTION 9 – SINGLE FILE WORD DETECTION**

_Write a bash script called gender.sh which takes one argument - a name. The script should print "female" if the word appears in the file /course/linuxgym/census/femalenames.txt, and "male" otherwise._

#!/bin/bash
if 
grep -qiw "$1" /course/linuxgym/census/femalenames.txt; then
  echo "female"
else
  echo "male"
fi

QUESTION 10 – SAME FREQUENCY 
Create a bash script called samefreq.sh which takes one argument - a name. The output should be the ALPHABETICALLY ORDERED list of all name's with the same frequency (popularity) as measured in the second column of the table: /femalenames.txt

#!/bin/bash
pop=`grep -w $1 /femalenames.txt | awk '{ print $2 }'`
grep -w $pop /femalenames.txt | awk '{print $1}' | sort


