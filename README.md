# my-Python-project3
DNA-check
[DNA_check.py](https://github.com/user-attachments/files/25207038/DNA_check.py)
import matplotlib.pyplot as plt
from collections import Counter

# Step 1: Input DNA sequence
dna_sequence = input("Enter a DNA sequence (A, T, G, C only): ").upper()
valid_nucleotides = set("ATGC")
dna_sequence = ''.join([n for n in dna_sequence if n in valid_nucleotides])

if not dna_sequence:
    print("No valid DNA letters entered.")
    exit()

# Step 2: Nucleotide frequency
nucleotide_counts = Counter(dna_sequence)
print("\nNucleotide Frequencies:")
for nucleotide, count in nucleotide_counts.items():
    print(f"{nucleotide}: {count}")

# Step 3: Codon (triplet) frequency
codons = [dna_sequence[i:i+3] for i in range(0, len(dna_sequence)-2, 3)]
codon_counts = Counter(codons)

print("\nMost common codons (top 10):")
for codon, count in codon_counts.most_common(10):
    print(f"{codon}: {count}")

# Step 4: Visualization
# Nucleotide frequency bar chart
plt.figure(figsize=(10,5))
plt.bar(nucleotide_counts.keys(), nucleotide_counts.values(), color=['green', 'red', 'blue', 'yellow'])
plt.title("Nucleotide Frequency")
plt.xlabel("Nucleotide")
plt.ylabel("Count")
plt.show()

# Codon frequency bar chart (top 10)
top_codons = codon_counts.most_common(10)
labels = [codon for codon, count in top_codons]
values = [count for codon, count in top_codons]

plt.figure(figsize=(12,6))
plt.bar(labels, values, color='purple')
plt.title("Top 10 Codon Frequencies")
plt.xlabel("Codon")
plt.ylabel("Count")
plt.show()
