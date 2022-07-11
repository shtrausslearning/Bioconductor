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

- Define a new XStringSet from characers (1 sequence)

```R
n_set_1 <- DNAStringSet(c("ACGT"))
```

```
DNAStringSet object of length 1:
    width seq
[1]     4 ACGT
```

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

- Converting <code>XString</code> to a <code>XStringSet</code>

```R
str_strset = DNAStringSet(s1_n)
```

```
DNAStringSet object of length 1:
    width seq
[1]    40 ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC
```
