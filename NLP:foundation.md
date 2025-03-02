# Foundation in Natural Language Processing (NLP)

## What is NLP?
**Natural Language Processing (NLP)** is a field of artificial intelligence (AI) that helps computers understand, interpret, and respond to human language.

## Why Do We Need NLP? (With Example)
Computers do not understand text the way humans do. When we see a sentence, we understand its meaning because of our knowledge of language, grammar, and context. However, computers see words as mere strings of characters.

For example:
- "I love programming."
  - A computer sees it as: `['I', 'love', 'programming', '.']`
  - But it doesn’t know that "love" expresses emotion or that "programming" is an activity.

To make computers understand text, NLP converts human language into a format that machines can process, like numerical data or structured representations.

## How Do Computers See Language?
Computers see text as a **sequence of characters**. Unlike humans, they do not automatically understand words, meanings, or grammar. Instead, they need additional processing steps to extract meaningful information from the text.

To achieve this, we use **text preprocessing, tokenization, and embeddings**.

---
## 1. Text Preprocessing
Before using text in an NLP model, we must **clean and standardize** it. This process is called **text preprocessing**.

### Steps in Text Preprocessing:
1. **Lowercasing**: Convert all text to lowercase to maintain consistency.
   - Example: `"HELLO World"` → `"hello world"`
2. **Removing punctuation**: Remove unnecessary symbols.
   - Example: `"Hello, world!"` → `"Hello world"`
3. **Removing stopwords**: Remove common words like "the", "is", "and" that don’t add significant meaning.
4. **Stemming**: Reduce words to their root form (but not always in a meaningful way).
   - Example: `"running", "runs"` → `"run"`
5. **Lemmatization**: Similar to stemming but returns a proper dictionary word.
   - Example: `"running"` → `"run"`, `"better"` → `"good"`

### Difference Between Stemming and Lemmatization
| Feature | Stemming | Lemmatization |
|---------|---------|--------------|
| Approach | Removes suffixes to get the root word | Converts words to their base/dictionary form |
| Example | "running" → "run" (but "better" → "bet") | "running" → "run", "better" → "good" |
| Accuracy | Less accurate | More accurate |
| Library | `nltk.stem.PorterStemmer()` | `nltk.stem.WordNetLemmatizer()` |

**Why use Lemmatization instead of Stemming?**
- Stemming is faster but can be inaccurate (e.g., "studies" → "studi").
- Lemmatization is more precise but requires more computational power.

---
## 2. Tokenization
**Tokenization** is the process of breaking text into smaller pieces called **tokens**.

### Types of Tokenization:
1. **Word Tokenization**: Splits text into words.
   - Example: `"The quick hello"` → `["The", "quick", "hello"]`
2. **Subword Tokenization**: Breaks words into meaningful subunits.
   - Example: `"unhappiness"` → `["un", "happiness"]`
3. **Sentence Tokenization**: Splits text into sentences.
   - Example: `"Hello! How are you?"` → `["Hello!", "How are you?"]`

### Why is Tokenization Needed?
- **Turns text into structured data** for analysis.
- **Helps with contextual understanding** by separating words or phrases.
- **Handles language variations** (e.g., "haven’t" → ["have", "not"], "don’t" → ["do", "not"], etc.).

### Tokenizers in Python
- **NLTK**: `nltk.word_tokenize(text)`, `nltk.sent_tokenize(text)`
- **spaCy**: `nlp(text).ents`

---
## 3. Embeddings
**Embeddings** convert words into numerical representations (vectors) so computers can understand relationships and meanings between them.

### Why Use Embeddings?
- Computers do not understand words as humans do.
- Word embeddings help computers find similar words based on their meanings.
- Example: The words **"king"** and **"queen"** will have similar vector representations, as they are conceptually related.

### How Do Word Embeddings Work?
1. **One-Hot Encoding**
   - Each word is represented as a binary vector (0s and 1s).
   - Problem: Does not capture word relationships.
   
2. **Word2Vec (Word Embeddings Model)**
   - Converts words into dense numerical vectors.
   - Similar words have similar vectors (e.g., "dog" and "puppy").
   - Trained using neural networks.

### Example: Word2Vec in Python
```python
from gensim.models import Word2Vec

sentences = [["I", "love", "machine", "learning"],
             ["I", "enjoy", "deep", "learning"]]

model = Word2Vec(sentences, vector_size=10, window=2, min_count=1, workers=4)
print(model.wv["love"])  # Vector representation of "love"
```

**Why is One-Hot Encoding Not Ideal?**
- It assigns a unique binary vector to each word, making unrelated words equally distant.
- It does not capture relationships (e.g., "king" and "queen" will be completely different in One-Hot Encoding, but similar in Word2Vec).

---
## Summary
| Concept | Explanation | Example |
|---------|------------|---------|
| **Text Preprocessing** | Cleans and standardizes text | Lowercasing, removing punctuation, stemming, lemmatization |
| **Tokenization** | Breaks text into meaningful units | `"Hello world"` → `["Hello", "world"]` |
| **Embeddings** | Represents words as vectors | "king" and "queen" have similar vectors |

### Why These Steps Matter?
- **Preprocessing** ensures data consistency.
- **Tokenization** breaks text into parts computers can process.
- **Embeddings** help machines understand word meanings and relationships.

By combining these techniques, NLP allows computers to **read, understand, and generate human-like text!** 

