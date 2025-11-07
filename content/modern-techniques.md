# Modern Analytics Techniques

Traditional business analytics was all about looking backward. We'd pull up dashboards and reports to figure out what happened last quarter-sales numbers, website traffic, customer behavior. Essentially, we were historians of our own businesses.

But AI and Machine Learning have changed the game. Instead of just describing the past, we're now building models that actually predict the future ("What's likely to happen next?") and recommend actions ("Here's what you should do about it").

Two things made this possible: we suddenly have access to massive amounts of data, and researchers have built incredibly powerful models that we can use right out of the box.

## 🤗 Transfer Learning & Hugging Face

Here's the old problem: if you wanted to build an AI model that could, say, analyze customer reviews, you needed millions of labeled examples and weeks of training on expensive GPUs. Most companies just couldn't do it.

Now, you can reuse or adapt a model that someone else has already trained on a huge dataset. This is called **Transfer Learning**.

Instead of training a model from scratch (which requires lots of data and time), transfer learning leverages knowledge learned from a source task and applies it to a target task.

- **Source Task**: a large, general problem (e.g., image classification on ImageNet).
- **Target Task**: a smaller or more specific problem (e.g., detecting cracks in bridge images).

The assumption is that the model's learned features - such as shapes, edges, or language patterns - are general enough to help with the new task.

The idea is brilliant in its simplicity. First, someone trains a massive model on basically the entire internet - Wikipedia, books, news articles, everything. Through this process, the model learns how language actually works: grammar, context, reasoning, even some common sense. Then, you take that pre-trained model and fine-tune it on your specific problem using just a tiny dataset - maybe 1,000 customer emails instead of millions. The model transfers all that general knowledge to your narrow use case.

**Hugging Face** is what made this accessible to everyone. Think of it as the GitHub of machine learning.

### 💡 Example Applications of Transfer Learning

| Domain                                | Pretrained Model                  | Target Task                             |
| ------------------------------------- | --------------------------------- | --------------------------------------- |
| **Computer Vision**                   | ResNet or VGG trained on ImageNet | Detect product defects, medical imaging |
| **Natural Language Processing (NLP)** | BERT, GPT, or RoBERTa             | Sentiment analysis, chatbots            |
| **Speech Recognition**                | Wav2Vec, Whisper                  | Transcribe calls, detect emotions       |
| **Finance/Analytics**                 | Pretrained time-series models     | Forecast stock prices, detect anomalies |

### 🏢 What is Hugging Face?

[Hugging Face](https://huggingface.co/) started as a company but has grown into this massive open-source community. They've built the infrastructure that makes cutting-edge ML models available to anyone who can write a few lines of Python.

![Hugging Face Logo](images/modern-techniques/huggingface-logo.png)

&nbsp;

Here's what they provide:

1.  **The Model Hub:** Over 100,000 pre-trained models that you can just download and use. Google, Meta, and thousands of researchers share their models here. Need sentiment analysis? Text summarization? Image classification? There's a model for that.
2.  **The `transformers` Library:** A Python library that handles all the messy details. You can download and run any model from the Hub with surprisingly little code.
3.  **The `pipeline` API:** This is the easiest entry point. A `pipeline` wraps up a pre-trained model and all the pre-processing steps into one simple function you can call.

### 🚀 How to Use a Hugging Face Pipeline

Using a state-of-the-art AI model is easy. First, install the library with `pip install transformers`.

Then, you can set up a pipeline for a specific task in just a few lines of code. Here's an example of sentiment analysis:

```python
from transformers import pipeline

# 1. Initialize the pipeline for a specific task
# The first time you run this, it'll download the model (takes a minute)
classifier = pipeline("sentiment-analysis")

# 2. Now just use it like a function
review = "The product is amazing, but the shipping was too slow."
result = classifier(review)

print(result)
# Output: [{'label': 'POSITIVE', 'score': 0.999...}]
# (Note: The default model gives one overall sentiment)
```

---

## 😊 Sentiment Analysis

Sentiment analysis is used to figure out the emotional tone behind a piece of text. Is it positive, negative, or neutral? This is useful for understanding customer feedback, social media posts, reviews, and more.

In the old days, sentiment analysis was often done using lexicon-based approaches, where each word had a predefined sentiment score. For example, VADER (Valence Aware Dictionary and sEntiment Reasoner) is a classic example of a lexicon-based and rule-based model attuned for short social media texts. Loughran-McDonald is another lexicon specifically designed for financial documents. Lexicon-based methods rely on predefined lists of words with associated sentiment scores, which is why they can struggle with context and nuance.

Modern techniques use contextual models that understand the meaning of entire sentences.

### 📖 The "Old" Way: Lexicon-Based (VADER)

**VADER** (Valence Aware Dictionary and sEntiment Reasoner) is a classic example of a lexicon-based and rule-based model.

### ⚙️ How VADER Works

**Lexicon (Dictionary):** At its core, VADER uses a large, human-validated dictionary that maps words, emojis, and slang to a sentiment score.

    - `"good"`: +1.9
    - `"bad"`: -2.1
    - `":)"`: +1.5
    - `"SUCKS"`: -2.3

It then sums up these scores, normalizes them, and gives you a `compound` score from -1 (most negative) to +1 (most positive).

**✅ Pros of Rule-based Models:**

- **Extremely Fast:** It's just dictionary lookups and simple math.
- **Transparent:** You can easily see _why_ a sentence was scored a certain way.
- **Great for Social Media:** It was specifically designed to understand the informal language of tweets and reviews, including slang, emojis, and capitalization.

**❌ Cons of Rule-based Models:**

- **No Real Context:** It doesn't understand the _meaning_ of a sentence. It only understands the scores of the words in it.
- **Fails on Nuance:** It can't handle sarcasm or complex sentence structures.
- **Domain-Specific:** It performs poorly in specialized domains (like finance or medicine) where a word like "exposure" or "positive" has a different meaning.

### 🤖 The "New" Way: Contextual Models (Hugging Face)

Modern sentiment analysis uses Transformer models (like BERT, RoBERTa, or DistilBERT), which are made accessible through Hugging Face. These are contextual models.

### 🔧 How Hugging Face Models Work

1.  **Pre-training:** These are massive neural networks (often with billions of parameters) that are "pre-trained" by reading a huge portion of the internet.

2.  **Understanding Context:** During this training, they don't just memorize words; they learn the relationships between words. This is the key difference. The model learns that the word "sick" means something different in "I am _sick_" versus "That was a _sick_ guitar solo."

3.  **Fine-Tuning:** The giant, pre-trained model is then "fine-tuned" on a specific task, such as sentiment analysis. It learns to associate its deep understanding of language with specific outputs (like "POSITIVE" or "NEGATIVE").

4.  **Inference (The Pipeline):** The Hugging Face `pipeline` function handles all the complexity for you. It takes your raw text, passes it to the model, and translates the model's complex output into a simple label.

**✅ Pros of Contextual Models:**

- **State-of-the-Art Accuracy:** They are far more accurate because they understand the _meaning and context_ of the entire sentence.
- **Handles Nuance:** They are much better at understanding sarcasm, complex negation, and domain-specific language.
- **Flexible:** You can choose from thousands of models, including models fine-tuned for specific domains (e.g., `twitter-roberta-base-sentiment` or models for financial news).

**❌ Cons of Contextual Models:**

- **Slower:** They require significantly more computation (often needing a GPU for high-speed use).
- **"Black Box":** It's very difficult to know _exactly_ why the model made a specific decision.
- **Larger:** The model files are often hundreds of megabytes or gigabytes, while VADER is tiny.

### ⚖️ Comparing the Two Approaches

```python
import pandas as pd
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
from transformers import pipeline

# Setup VADER
vader_analyzer = SentimentIntensityAnalyzer()

def get_vader_score(text):
    return vader_analyzer.polarity_scores(text)['compound']

# Setup Hugging Faces
# This downloads a model fine-tuned for sentiment analysis
# (This model, distilbert-base-uncased-finetuned-sst-2-english,
# is a good, small, fast default.)
hf_pipeline = pipeline("sentiment-analysis")

def get_hf_score(text):
    # The pipeline returns a list of dictionaries
    # e.g., [{'label': 'NEGATIVE', 'score': 0.999}]
    result = hf_pipeline(text)[0]
    # We'll make negative scores, and positive scores positive
    if result['label'] == 'NEGATIVE':
        return -result['score']
    else:
        return result['score']

# Create test sentences
sentences = [
    "I love this product, it's amazing!",                # 1. Easy Positive
    "This is the worst customer service ever.",         # 2. Easy Negative
    "My flight was delayed 3 hours. Just great.",       # 3. Sarcasm
    "This new feature is sick!",                        # 4. Contextual Slang
    "The movie wasn't bad, actually."                   # 5. Complex Negation
]

#  Compare as a table
data = {
    "Sentence": sentences,
    "VADER Score": [get_vader_score(s) for s in sentences],
    "HuggingFace Score": [get_hf_score(s) for s in sentences]
}
df = pd.DataFrame(data)
print(df)
```

| Sentence                                   | VADER Score | HuggingFace Score |
| ------------------------------------------ | ----------- | ----------------- |
| I love this product, it's amazing!         | 0.8516      | 0.999886          |
| This is the worst customer service ever.   | -0.6249     | -0.999784         |
| My flight was delayed 3 hours. Just great. | 0.4939      | 0.999160          |
| This new feature is sick!                  | -0.5562     | -0.999554         |
| The movie wasn't bad, actually.            | 0.4310      | 0.980462          |

:::{warning} Do not use rule-based models

If you have access to modern contextual models (like Hugging Face), always prefer those over rule-based models like VADER. The accuracy improvements are significant, especially for real-world text that includes sarcasm, slang, and complex sentence structures.

Most benchmarks show that contextual models outperform rule-based models by a wide margin.

:::

---

## 🎯 Zero-Shot Text Classification

This is one of those techniques that feels like magic when you first use it. You can classify text into _your own custom categories_ without training anything or labeling a single example.

Here's how it works: The model already understands language deeply enough that it can compare your text to each of your categories and figure out which one matches best. No training data required.

**Example:** Let's say you're getting flooded with customer support tickets and want to automatically route them. Here's how you'd do it:

```python
from transformers import pipeline

# Set up the zero-shot classifier
zero_shot_classifier = pipeline("zero-shot-classification")

ticket = "My monthly subscription bill is wrong, I was overcharged."
my_categories = ["Billing Inquiry", "Technical Support", "Sales Lead", "Spam"]

result = zero_shot_classifier(ticket, my_categories)

print(result)
# Output:
# {
#  'sequence': 'My monthly subscription bill is wrong, I was overcharged.',
#  'labels': ['Billing Inquiry', 'Technical Support', 'Sales Lead', 'Spam'],
#  'scores': [0.95..., 0.02..., 0.01..., 0.01...]
# }
```

No training, no labeled data. You just tell it what categories you care about.

---

## 🏷️ Named Entity Recognition (NER)

NER is all about pulling structured information out of messy text. The model scans through text and automatically identifies things like people's names, companies, locations, dates, and other key entities. This is incredibly useful for automating data entry or extracting information from documents.

**Example:** Parse a news snippet to find all the companies mentioned:

```python
from transformers import pipeline

ner_pipeline = pipeline("ner", grouped_entities=True)
text = "Tim Cook announced at the Apple conference that Microsoft will be a key partner."

results = ner_pipeline(text)

print(results)
# Output:
# [
#  {'entity_group': 'PER', 'score': 0.99..., 'word': 'Tim Cook', ...},
#  {'entity_group': 'ORG', 'score': 0.99..., 'word': 'Apple', ...},
#  {'entity_group': 'ORG', 'score': 0.99..., 'word': 'Microsoft', ...}
# ]
```

It found Tim Cook (a person) and both Apple and Microsoft (organizations). You could use this to automatically extract company mentions from thousands of news articles or customer feedback.

---

## 📊 Modern Topic Modeling

Let's say you just collected 5,000 open-ended survey responses and your boss asks, "So what are customers actually talking about?" You could read through all of them (good luck), or you could use topic modeling to automatically discover the main themes.

Traditionally, topic modeling relied on statistical methods like LDA (Latent Dirichlet Allocation) or NMF (Non-Negative Matrix Factorization). These methods look for patterns in word co-occurrences but often produce topics that are hard to interpret.

Modern tools like **BERTopic** use the same transformer models we've been discussing. Unlike older statistical methods, these actually understand what words _mean_, so you get much more coherent and useful topics.

**Example:** Analyze survey responses using BERTopic:

```python
from bertopic import BERTopic
import pandas as pd

# In real life, you'd load thousands of responses from a CSV
# df = pd.read_csv("survey_responses.csv")
# docs = df['open_ended_response'].tolist()

# For this example, here's a small set of feedback
docs = [
    "The checkout process was very confusing.",
    "I couldn't find the 'contact us' page on the website.",
    "Why is shipping so expensive? It costs more than the product.",
    "The website is hard to navigate and I got lost.",
    "Please offer free shipping or lower the cost."
]

# Set up BERTopic (it uses Hugging Face models behind the scenes!)
topic_model = BERTopic()

# Analyze the documents
topics, probabilities = topic_model.fit_transform(docs)

# See what topics it found
print(topic_model.get_topic_info())
# You'll see something like:
#   Topic  Count  Name
#   -1     ...    "shipping_cost_website_..."
#    0     ...    "website_navigation_confusing_..."
```

Even with just five responses, it can separate "shipping cost complaints" from "website navigation issues." Imagine what it can do with thousands of responses.

---

## 🕸️ Analyzing Relationships (Network Analysis)

Network analysis (also called graph theory) is about modeling the world as connections. You have **nodes** (the things - people, products, websites) and **edges** (the relationships between them). Once you map out these connections, you can answer questions like: Who's the most influential person in this organization? Which products are always bought together? Where are the bottlenecks in this system?

The go-to Python library for this is `networkx`.

Network analysis relies on representing data as graphs, which can be a bit different from traditional tabular data analysis.

### 🧩 What Is a Graph Data Structure?

A **graph** is a collection of **nodes (vertices)** connected by **edges (links)**. It's a flexible way to represent **relationships** between entities.

- **Nodes (Vertices)** represent _entities_ such as people, cities, or products.
- **Edges (Links)** represent _connections_ or _relationships_ between those entities.

- Edges can be:
  - **Directed** (A → B): order matters (e.g., follower → followed).
  - **Undirected** (A - B): symmetric relationships (e.g., friendships).
- Edges can also carry **weights**, such as distance, cost, or similarity.

📊 **Example:**
In a flight network:

- Nodes == airports
- Edges == routes
- Edge weight == distance or ticket price

### 🧠 Why Graphs Are So Useful in Analytics

Graphs shine whenever relationships are the key to understanding your data - not just the individual data points themselves. Here’s why:

#### Modeling Complex Relationships

Graphs let you naturally model real-world systems:

- Social networks (people → people)
- Supply chains (suppliers → manufacturers → distributors)
- Web links (pages → pages)
- Knowledge graphs (concepts → related concepts)

Traditional relational tables struggle with these many-to-many and recursive relationships.

#### Recommendation Systems

Graphs power many recommendation engines:

- "Users who bought this also bought that" through shared purchase nodes.
- "Friends of your friends" in social graphs.

Algorithms like PageRank, HITS, or Graph Neural Networks (GNNs) build on graph theory.

### 👥 Social & Organizational Network Analysis

Understanding the social structure of an organization can be surprisingly powerful. Who's actually the information hub that everyone relies on? Which teams are isolated? Who bridges different departments?

You can model this by treating people as nodes and their interactions (emails, messages, collaborations) as edges.

**Example:** Find the most central person in a small email network using `networkx` (install with `pip install networkx`):

```python
import networkx as nx

# Here's a sample of who emailed whom
email_data = [
    ('Alice', 'Bob'), ('Alice', 'Charles'), ('Bob', 'Charles'),
    ('David', 'Eve'), ('Eve', 'Alice'), ('David', 'Bob')
]

# Create the network graph
G = nx.Graph()
G.add_edges_from(email_data)

# Calculate degree centrality (basically, who has the most connections?)
centrality = nx.degree_centrality(G)

print(sorted(centrality.items(), key=lambda item: item[1], reverse=True))
# Output:
# [('Alice', 0.6), ('Bob', 0.6), ('Charles', 0.4), ('Eve', 0.4), ('David', 0.4)]
```

Alice and Bob are the most connected people in this network. They're the hubs. If you need to spread information quickly, start with them.

---

## 🛒 Market Basket Analysis & Product Networks

This is the classic recommendation system problem: "Customers who bought this also bought..."

The network approach is pretty intuitive. Each product is a node, and you draw an edge between two products if they were purchased together in the same transaction. Once you have that network built, you can easily find which products are most strongly connected.

**Example:** Find related products:

```python
import networkx as nx

# Each sublist is one customer's shopping basket
transactions = [
    ['Milk', 'Eggs', 'Bread'],
    ['Milk', 'Bread'],
    ['Eggs', 'Diapers'],
    ['Milk', 'Diapers', 'Beer']
]

G = nx.Graph()

# For each transaction, connect all the items to each other
from itertools import combinations
for basket in transactions:
    for (item1, item2) in combinations(basket, 2):
        G.add_edge(item1, item2)

# What products are connected to Milk?
print(list(G.neighbors('Milk')))
# Output: ['Eggs', 'Bread', 'Diapers', 'Beer']
```
