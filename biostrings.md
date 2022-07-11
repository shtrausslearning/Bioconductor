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

```R
# File Containing One Sequence
fasta_n = readDNAStringSet('/kaggle/input/bioinformatics/sequences/example.fasta')
fasta_n # print read data 
class(fasta_n) # print read class format
names(fasta_n) # print name of sequence
```
