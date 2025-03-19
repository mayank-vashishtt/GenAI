# Understanding TF-IDF and BM25

## 1. Term Frequency (TF)
Term Frequency (TF) measures how often a term appears in a document.

### Formula:
\[
TF = \frac{f_t}{N}
\]
where:
- \( f_t \) = Number of times the term appears in the document.
- \( N \) = Total number of words in the document.

### Example Calculation:
If the word "apple" appears **3 times** in a document of **100 words**, then:
\[
TF = \frac{3}{100} = 0.03
\]

## 2. Inverse Document Frequency (IDF)
Inverse Document Frequency (IDF) gives less importance to common words like "the" and more importance to rare words.

### Formula:
\[
IDF = \log\left(\frac{N_d}{DF_t}\right)
\]
where:
- \( N_d \) = Total number of documents in the corpus.
- \( DF_t \) = Number of documents containing the term.

### Example Calculation:
If there are **10,000 documents** and the word "apple" appears in **1,000 documents**, then:
\[
IDF = \log\left(\frac{10,000}{1,000}\right) = \log(10) = 1
\]

## 3. TF-IDF Score
### Formula:
\[
TF-IDF = TF \times IDF
\]

Using previous values:
\[
TF-IDF = 0.03 \times 1 = 0.03
\]

## 4. BM25 (Best Matching 25)
BM25 is an improved ranking function that considers **frequency saturation** and **document length normalization**.

### BM25 Formula:
\[
BM25 = IDF \times \frac{TF \times (k_1 + 1)}{TF + k_1 \times (1 - b + b \times \frac{L}{L_{avg}})}
\]
where:
- \( k_1 \) = Controls how much TF influences the score. (Default: **1.2 to 2.0**)
- \( b \) = Controls document length normalization. (Default: **0.75**)
- \( L \) = Length of the document.
- \( L_{avg} \) = Average document length in the corpus.

### How BM25 Improves Relevance:
- **Frequency Saturation**: Unlike TF-IDF, it prevents overly frequent words from having too much influence.
- **Length Normalization**: Longer documents are normalized so they don't always rank higher just because of length.

## 5. Comparison: TF-IDF vs. BM25
| Feature          | TF-IDF | BM25 |
|-----------------|--------|------|
| Frequency Saturation | No     | Yes  |
| Document Length Normalization | No     | Yes  |
| Weighting Flexibility | No     | Yes  |
| Performance in Search Engines | Good   | Better |

### When to Use What?
- **TF-IDF**: Good for keyword extraction and basic ranking.
- **BM25**: Better for search engines, document ranking, and information retrieval.

## Conclusion
BM25 is a more refined version of TF-IDF, making it more effective for search engines and retrieval tasks.

