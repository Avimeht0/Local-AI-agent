# Pizza Restaurant AI Q&A Assistant

## STAR Format Project Overview

---

### **S – Situation**
A pizza restaurant wanted to answer customer questions quickly and accurately, using real customer reviews. They needed a system that could understand questions, find the most relevant reviews, and give expert answers based on those reviews. The goal was to improve customer trust and experience, using AI, while keeping everything private and cost-effective by running locally.

---

### **T – Task**
- Build a program that:
  - Lets users ask any question about the restaurant.
  - Searches real customer reviews to find the most helpful ones for the question.
  - Uses a smart AI model to write a good answer, using those reviews.
  - Runs on the restaurant’s own computer (no cloud needed).

---

### **A – Action**

#### **1. Set Up the Environment**
- Used Python for development.
- Used [LangChain](https://python.langchain.com/) to connect all the AI parts.
- Used [Ollama](https://ollama.com/) to run the Llama 3.2 language model locally.

#### **2. Prepare the Reviews**
- Collected customer reviews in a CSV file (`realistic_restaurant_reviews.csv`).
- Each review has a title, review text, rating, and date.

#### **3. Create Vector Embeddings and Store Them**
- Used a model (`mxbai-embed-large`) to turn each review into a vector (a list of numbers that captures the meaning of the text).
- Stored these vectors in a vector database (Chroma) for fast searching.

#### **4. Build the Retriever**
- Set up a retriever that can quickly find the 5 most relevant reviews for any question, based on meaning, not just matching words.

#### **5. Create the Q&A Chain**
- Made a prompt template that gives the AI model the reviews and the user’s question.
- Connected the retriever and the AI model using LangChain.

#### **6. User Interaction**
- Built a simple command-line interface in `main.py`:
  - User types a question.
  - The program finds the best reviews.
  - The AI writes an answer using those reviews.
  - The answer is shown to the user.

---

### **R – Result**
- The assistant gives accurate, helpful answers based on real customer experiences.
- Customers get better, more honest answers, which builds trust.
- The system is private and cost-effective, since it runs locally.
- The same approach can be used for other restaurants or businesses by changing the reviews.

---

## **Why Use Vector Embeddings and a Vector Database?**
- **Traditional search** only matches exact words. If the question and review use different words, it might miss the best answers.
- **Vector embeddings** capture the meaning of text, so the system can find reviews that are similar in meaning, even if the words are different.
- **Vector database** (like Chroma) lets us search these vectors quickly and efficiently.
- **Advantage:** The AI can answer questions more like a human, understanding the intent, not just the words.

---

## **How to Run the Project**

### **1. Install Requirements**
Make sure you have Python 3.10+ installed. Then install the required packages:

```bash
pip install -r requirements.txt
```

You also need to install and run [Ollama](https://ollama.com/) and download the `llama3.2` and `mxbai-embed-large` models.

### **2. Prepare the Reviews File**
Place your `realistic_restaurant_reviews.csv` file in the project directory. It should have columns: `Title`, `Review`, `Rating`, `Date`.

### **3. Run the Program**

```bash
python main.py
```

- Type your question when prompted.
- Type `q` to quit.

---

## **Project Structure**

- `main.py` – The main program. Handles user input, gets reviews, and generates answers.
- `vector.py` – Loads reviews, creates embeddings, stores them in a vector database, and sets up the retriever.
- `realistic_restaurant_reviews.csv` – The file with all customer reviews.

---

## **How Each Part Works (Simple Explanation)**

1. **vector.py**
   - Reads all reviews from the CSV file.
   - Turns each review into a vector (numbers that capture meaning).
   - Stores these vectors in a special database for fast searching.
   - Sets up a retriever to find the most relevant reviews for any question.

2. **main.py**
   - Asks the user for a question.
   - Uses the retriever to get the best reviews.
   - Sends the reviews and question to the AI model.
   - Shows the answer to the user.

---

## **FAQ**

**Q: Why not just search the text directly?**  
A: Direct text search only finds exact words. Vector search finds similar meanings, so it’s much smarter and more helpful.

**Q: Can I use this for other businesses?**  
A: Yes! Just change the reviews file.

**Q: Is my data private?**  
A: Yes, everything runs on your own computer.

---

## **Contact**
For questions or help, contact the project maintainer. 