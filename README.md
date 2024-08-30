# LexoGen

<p align="center">
  <img src="icon.svg" alt="LexoGen Icon" width="200"/>
</p>

LexoGen is an advanced Python-based tool designed to generate realistic, non-existent English words. The architecture leverages a combination of Markov models, phonotactic rules, and syllable pattern diversity to ensure the generated words are both pronounceable and varied.

## Architectural Overview

### 1. **Markov Model Integration**
LexoGen utilizes an `ImprovedMarkovModel` to capture and replicate the statistical properties of English phonemes. The model processes up to `n=4` characters (n-grams) at a time, creating a probabilistic trie that represents transitions between phonemes. This approach allows the model to generate sequences that reflect the natural flow of English phonetics, ensuring realism in the generated words.

### 2. **Phonotactic Constraints**
Phonotactic rules dictate the allowable combinations of phonemes in English. LexoGen implements these constraints through the `ImprovedPronounceability` class, which analyzes consonant clusters, vowel sequences, and positional restrictions (e.g., initial and final consonants). This class also estimates the phonetic feasibility of a word, scoring it based on frequency-weighted phoneme distributions and common syllable patterns derived from the CMU Pronouncing Dictionary.

### 3. **Syllable Pattern Diversity**
The word generation process incorporates a wide range of syllable structures (e.g., CV, CVC, VCV, CCVC). The `EnglishWordGenerator` class selects patterns probabilistically, constructing words syllable by syllable. This methodology introduces variation and rhythm into the generated words, avoiding monotonous or overly simplistic structures.

### 4. **Consonant and Vowel Sequencing**
The architecture segregates consonants and vowels into distinct categories, allowing for the construction of syllables that follow natural linguistic patterns. The model dynamically generates syllables that comply with the selected pattern, combining consonants and vowels in a way that adheres to English phonotactics.

### 5. **Pronounceability Scoring**
After generating a candidate word, LexoGen evaluates its pronounceability. The system computes a composite score based on phoneme frequency, syllable pattern commonality, and adherence to phonotactic constraints. Words that fail to meet a minimum score threshold are discarded or modified, ensuring that only plausible words are retained.

### 6. **Real-Time Feedback Loop**
LexoGen provides real-time feedback during word generation, displaying syllable patterns, estimated pronunciations, and phonotactic adherence for each word. This feature aids in both debugging and understanding the internal decision-making process of the generator.

## Installation

```bash
git clone https://github.com/yourusername/LexoGen.git
cd LexoGen
pip install -r requirements.txt
```

## Usage

Run the script directly to start generating words:

```bash
python lexo_gen.py
```

You will be prompted to specify the desired word length and the number of words to generate. The script outputs each generated word with detailed phonetic and structural analysis.

## Example Output

```
Processing word 1 of 50: salis
Estimated pronunciation: S AH L IH S
Syllable pattern: CVCCV
Pronounceability score: 1.00
Adheres to phonotactic constraints: Yes
```

## Contributing

Contributions are welcome. Please submit a Pull Request with a clear description of your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
