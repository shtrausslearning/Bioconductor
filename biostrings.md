### 1 | Biological Alphabets 

There are two alphabets we whould be familar with <code>nucleotide</code> & <code>amino acids</code>
- Example Nucleotide biological sequence: 'ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC'
- Example Amino acid biological sequence: 'HEAGAWGHEE'

### 2 | A single sequence <code>XString</code>

- In R, we use **characters** as opposed to **strings** for content in **""** marks
- define characters of dna & amino acids

```R
chr_n1 = "ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC"
chr_n2 = "TTTCGGGTAAGTAAATATATGTTTCACTACTTCCTTTCGG"
chr_aa1 = 'PAWHEAE'
chr_aa2 = 'HEAGAWGHEE'
```

- <code>Nucleotide</code> String

```R
s1_n <- DNAString(chr_n1) # DNAString objects
s2_n <- DNAString(chr_n2)
s2_n # print DNA string
```

- <code>Amino Acid</code> String

```R
s1_aa = AAString(chr_aa1)  # AAString Object
s2_aa = AA
```

```
40-letter DNAString object
seq: TTTCGGGTAAGTAAATATATGTTTCACTACTTCCTTTCGG
10-letter AAString object
seq: HEAGAWGHEE
```

### 3 | A collection of sequences <code>XStringSet</code>

Stringsets can contain just a **single string** or **multiple strings**
  
#### 1. define a new string set from string concat
  
- Define a new XStringSet from chacaters (3 sequences)

```
str_concat = c("ACGT","GTCA","GCTA") # concat to make vector w/ c()
n_set <- AAStringSet(str_concat)
```

```
AAStringSet object of length 3:
    width seq
[1]     4 ACGT
[2]     4 GTCA
[3]     4 GCTA
```

#### 2. define a new stringset from a single 

- Define a new <code>XStringSet</code> from <code>characers</code> (1 sequence)

```R
n_set_1 <- DNAStringSet(c("ACGT"))
```

```
DNAStringSet object of length 1:
    width seq
[1]     4 ACGT
```

#### 3. adding names to string set sequences

- Give names to sequences in our stringset <code>n_set</code>

```R
seq_name = c('seq1','seq2','seq3')
names(n_set) <- paste0(seq_name)
```

```
AAStringSet object of length 3:
    width seq                                               names               
[1]     4 ACGT                                              seq1
[2]     4 GTCA                                              seq2
[3]     4 GCTA                                              seq3
```

#### 4. convert a string to a stringset

- Converting <code>XString</code> to a <code>XStringSet</code>

```R
str_strset = DNAStringSet(s1_n)
```

```
DNAStringSet object of length 1:
    width seq
[1]    40 ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC
```

#### 5. extract characters from a sequence in a stringset

- Extracting characters of a string from a stringset 
- first define a stringset with a single sequence

```R
string = n_set[1]
string
class(string)
```

```
AAStringSet object of length 1:
    width seq                                               names               
[1]     4 ACGT                                              seq1
'AAStringSet'
```

- <code>toString</code> to convert to type <code>character</code>

```R
dna_char <- toString(n_set[1])
class(dna_char) # check the class type
dna_char # print character
```

```
'character'
'ACGT'
```

#### 6. extract characters from a sequences in a stringset

- Extracting multiple characters from a <code>stringset</code>

```R
lst <- list() # define empty list

# loop through all in n_set
for(i in 1:length(n_set)) {
    lst <- c(lst,toString(n_set[i]))
}

lst # list containing characters
```

```R
# Set - > Single sequence
string = n_set[[1]] # extract single sequence 
string # print string

# use toString
char = toString(string)
char  # print character
class(char) # print char type
```

```
4-letter AAString object
seq: ACGT
'ACGT'
'character'
```

### 4 | Reading sequences from files

- <code>Biostrings</code> utilises the **FASTA** format,
- <code>names</code> references to the single header that is present in the file (non parsed)

#### 1. Read a DNA sequence(s) file

- Utilising the <code>readDNAStringSet</code> function, we can read a file that contains <code>nucleotide</code> sequences
- Usually those that utilise <code>fna</code> <code>fasta</code> ... formats

```R
# File Containing One Sequence
fasta_n = readDNAStringSet('/kaggle/input/bioinformatics/sequences/example.fasta')
fasta_n # print read data 
class(fasta_n) # print read class format
names(fasta_n) # print name of sequence
```
```
DNAStringSet object of length 1:
    width seq                                               names               
[1]  1231 GGCAGATTCCCCCTAGACCCGCC...TGCTCCCAAATAAACTCCAGAAG HSBGPG Human gene...
'DNAStringSet'
'HSBGPG Human gene for bone gla protein (BGP)'
```

#### 2. Read amino acid sequence(s) file

- We can of course use the biostrings prefix as well <code>Biostrings::</code>
- The curret string contains 10 separate sequences that are separated by breaks
- Due to the simple nature of **FASTA** files, the <code>names</code> function doesn't parse the header
  - Eg. <code>gi|45478712|ref|N...</code> contains various information about the sequence, separated by the <code>|</code> symbol

```R
fasta_aa = Biostrings::readAAStringSet('/kaggle/input/bioinformatics/sequences/NC_005816.faa')
fasta_aa
class(fasta_aa) # AAStringSet object

```

```
AAStringSet object of length 10:
     width seq                                              names               
 [1]   340 MVTFETVMEIKILHKQGMSSRAI...NFDKHPLHHPLSIYDSFCRGVA gi|45478712|ref|N...
 [2]   260 MMMELQHQRLMALAGQLQLESLI...KGESYRLRQKRKAGVIAEANPE gi|45478713|ref|N...
 [3]    64 MNKQQQTALNMARFIRSQSLILL...ELAEELQNSIQARFEAESETGT gi|45478714|ref|N...
 [4]   123 MSKKRRPQKRPRRRRFFHRLRPP...TNPPFSPTTAPYPVTIVLSPTR gi|45478715|ref|N...
 [5]   145 MGGGMISKLFCLALIFLSSSGLA...SGNFIVVKEIKKSIPGCTVYYH gi|45478716|ref|N...
 [6]   357 MSDTMVVNGSGGVPAFLFSGSTL...MSDRRKREGALVQKDIDSGLLK gi|45478717|ref|N...
 [7]   138 MKFHFCDLNHSYKNQEGKIRSRK...YLSGKKPEGVEPREGQEREDLP gi|45478718|ref|N...
 [8]   312 MKKSSIVATIITILSGSANAASS...GGDAAGISNKNYTVTAGLQYRF gi|45478719|ref|N...
 [9]    99 MRTLDEVIASRSPESQTRIKEMA...AMGGKLSLDVELPTGRRVAFHV gi|45478720|ref|N...
[10]    90 MADLKKLQVYGPELPRPYADTVK...YEKLVRIAEDEFTAHLNTLESK gi|45478721|ref|N...
'AAStringSet'
```

- Noting that the enumeration starts with 1 and not with 0 in python

```R
fasta_aa[1] # Still AA StringSet object, but length of 1
```

```
AAStringSet object of length 1:
    width seq                                               names               
[1]   340 MVTFETVMEIKILHKQGMSSRAI...VNFDKHPLHHPLSIYDSFCRGVA gi|45478712|ref|N...
```

- Some other operations, which we may need to use:

```R
width(fasta_aa[1]) # get the length of the sequence 
seq(fasta_aa[1]) # sequence number
names(fasta_aa[1]) # sequence description
char_seq = toString(fasta_aa[1]) # get the character object type of the sequence
class(char_seq) # show object class 
```

```
340
1
'gi|45478712|ref|NP_995567.1| putative transposase [Yersinia pestis biovar Microtus str. 91001]'
'character'
```

### 5 | Saving sequences to FASTA

- Once we have worked with our sequences, we want to save them in a file, in biostrings we can save in the <code>FASTA</code> format
- Suppose we have this sequence set:

```R
n_set # an aastringset we wish to save
```

```
AAStringSet object of length 3:
    width seq                                               names               
[1]     4 ACGT                                              seq1
[2]     4 GTCA                                              seq2
[3]     4 GCTA                                              seq3
```

- We can save the sequenceset using <code>writeXStringSet</code>
  
```R
# Save our XStringSet
writeXStringSet(n_set,
                filepath='/kaggle/working/dna_list.fasta',
                format='fasta')
```
  
#### 6 | Combining Stringsets

```R
# combine characters 
x0 <- DNAStringSet(c("CTCCCAGTAT", "TTCCCGA", "TACCTAGAG"))  # String Set #1
x1 <- DNAStringSet(c("AGGTCGT", "GTCAGTGGTCCCC", "CATTTTAGG")) # String Set #2
x2 <- DNAStringSet(c("TGCTAGCTA", "AGTCTTGC", "AGCTTTCGAG")) # String Set #3

dna_list <- list(x0, x1, x2) # create a list of String Sets
dna_xstrset = do.call(c, dna_list) # concentrate 
dna_xstrset
```

```
DNAStringSet object of length 9:
    width seq
[1]    10 CTCCCAGTAT
[2]     7 TTCCCGA
[3]     9 TACCTAGAG
[4]     7 AGGTCGT
[5]    13 GTCAGTGGTCCCC
[6]     9 CATTTTAGG
[7]     9 TGCTAGCTA
[8]     8 AGTCTTGC
[9]    10 AGCTTTCGAG
```
