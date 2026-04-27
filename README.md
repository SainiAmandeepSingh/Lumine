# Lumine

### Recipe recommendation app for discounted-grocery shoppers

**Built with:** the BudgetBites team - AmanDeep Saini Singh, Josh Doramal, Giulia Vitali & Elena Elena Shariefie

> **Live demo:** [budgetbites.streamlit.app](https://budgetbites.streamlit.app/)

---

## Overview

Lumine helps shoppers turn discounted-grocery hauls into actual meals. Users upload an Excel file of products they bought on discount, and the app finds recipes that use those ingredients via [TheMealDB API](https://www.themealdb.com/). It also includes a chef-style chatbot powered by local LLMs (gemma:2b and llama2 via [Ollama](https://ollama.com/)) for cooking advice.

## Features

The app is organised into four tabs:

**🤖 Chat with Chef.** A conversational AI assistant for recipe ideas, cooking techniques, and ingredient combinations. Choose between two local models (Chef De-Code and Chef App-etizer) running via Ollama.

**🏠 Your Recipe Haven.** Upload an Excel file with a `Product Name` column. The app normalises your products against TheMealDB's recognised ingredient list, then finds the best-matching recipe based on how many of your ingredients appear in it.

**🎲 Recipe Roulette.** Choose a food category and a cuisine area, and the app surfaces a recipe matching both filters. For when you want guidance but not full freedom of choice.

**🍲 Magic Recipe Mixer.** Displays the chosen recipe with image, ingredient list, instructions, and source link.

## Tech stack

- **Streamlit** — UI and state management
- **TheMealDB API** — recipe and ingredient data
- **Ollama** — local LLM inference (gemma:2b, llama2)
- **LangChain Community** — LLM orchestration
- **pandas + openpyxl** — Excel ingestion

## Setup

```bash
git clone https://github.com/SainiAmandeepSingh/Lumine.git
cd Lumine
pip install -r requirements.txt
```

You'll also need [Ollama](https://ollama.com/) installed locally with the models pulled:

```bash
ollama pull gemma:2b
ollama pull llama2
```

> **Note:** The chatbot tab requires a local Ollama server. The hosted Streamlit Cloud demo cannot run it, since Streamlit Cloud doesn't have an Ollama runtime. The recipe-matching tabs (Recipe Haven, Roulette, Mixer) work in both environments.

## Run

```bash
streamlit run Streamlit.py
```

Or try the [live demo](https://budgetbites.streamlit.app/).

## Repository structure

```
Lumine/
├── Streamlit.py            # Main Streamlit app (all four tabs)
├── requirements.txt
├── Products.xlsx           # Sample product list for testing the upload tab
├── Products Names.xlsx     # Sample product names
├── Josh.xlsx               # Sample test data
└── .devcontainer/          # GitHub Codespaces dev container
```
