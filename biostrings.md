There are two alphabets we whould be familar with <code>nucleotide</code> & <code>amino acids</code>
- Example Nucleotide biological sequence: 'ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC'
- Example Amino acid biological sequence: 'HEAGAWGHEE'

### Defining sequences

- In R, we use **characters** as opposed to **strings** for content in **""** marks

- define characters of dna & amino acids
chr_n1 = "ACTTCACCAGCTCCCTGGCGGTAAGTTGATCAAAGGAAAC"
chr_n2 = "TTTCGGGTAAGTAAATATATGTTTCACTACTTCCTTTCGG"
chr_aa1 = 'PAWHEAE'
chr_aa2 = 'HEAGAWGHEE'

- ''' Nucleotide String '''
s1_n <- DNAString(chr_n1) # DNAString objects
s2_n <- DNAString(chr_n2)
s2_n

- ''' Amino Acid String '''
s1_aa = AAString(chr_aa1)  # AAString Object
s2_aa = AA
