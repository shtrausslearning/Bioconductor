### 1 | Biological Alphabets 

There are two alphabets we whould be familar with <code>nucleotide</code> & <code>amino acids</code>
- Example Nucleotide biological sequence: 'ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC'
- Example Amino acid biological sequence: 'HEAGAWGHEE'

### 2 | Defining sequences <code>XString</code>

- In R, we use **characters** as opposed to **strings** for content in **""** marks
- define characters of dna & amino acids
  - chr_n1 = "ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC"
  - chr_n2 = "TTTCGGGTAAGTAAATATATGTTTCACTACTTCCTTTCGG"
  - chr_aa1 = 'PAWHEAE'
  - chr_aa2 = 'HEAGAWGHEE'

- <code>Nucleotide</code> String
  - s1_n <- DNAString(chr_n1) # DNAString objects
  - s2_n <- DNAString(chr_n2)
  - s2_n # print DNA string

- <code>Amino Acid</code> String
  - s1_aa = AAString(chr_aa1)  # AAString Object
  - s2_aa = AA

### 3 | Defining sets of strings <code>XStringSet</code>

Stringsets can contain just a **single string** or **multiple strings**
  
- Define a new XStringSet from chacaters (3 sequences)
  - str_concat = c("ACGT","GTCA","GCTA") # concat to make vector w/ c()
  - n_set <- AAStringSet(str_concat)

- Define a new XStringSet from characers (1 sequence)
  - n_set_1 <- DNAStringSet(c("ACGT"))
