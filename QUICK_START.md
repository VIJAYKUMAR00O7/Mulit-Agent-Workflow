# 🚀 Quick Start Guide

## 5-Minute Setup

### Step 1: Clone/Download Files
```bash
# Create a project directory
mkdir multi-agent-workflow
cd multi-agent-workflow

# Download the notebook and supporting files
# - L2_fixed.ipynb
# - README.md
# - env.template
# - requirements.txt
```

### Step 2: Set Up Environment
```bash
# Create virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On Mac/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Step 3: Configure API Keys

#### Option A: Using .env file (Recommended)
```bash
# Copy template
cp env.template .env

# Edit .env file with your API keys
# Replace placeholder values with actual keys
```

#### Option B: Direct in notebook
```python
import os
os.environ['OPENAI_API_KEY'] = 'your-key-here'
os.environ['TAVILY_API_KEY'] = 'your-key-here'
```

### Step 4: Launch Jupyter
```bash
jupyter notebook L2_fixed.ipynb
```

### Step 5: Run Your First Query
Execute all cells, then run:
```python
query = "What are the top 5 tech companies by market cap?"
state = {
    "messages": [HumanMessage(content=query)],
    "user_query": query,
    "enabled_agents": ["web_researcher", "synthesizer"],
}
result = graph.invoke(state)
print(result["final_answer"])
```

## 🎯 Quick Test (No API Keys)

Want to test without API keys? The system includes mock data:

```python
# This will work even without API keys!
query = "Chart the current market capitalization of the top 5 banks in the US?"
state = {
    "messages": [HumanMessage(content=query)],
    "user_query": query,
    "enabled_agents": ["web_researcher", "chart_generator", "synthesizer"],
}
result = graph.invoke(state)
```

## 📝 Common Commands

### Check Installation
```python
# Verify packages
import langchain
import langgraph
import tavily
print(f"LangChain: {langchain.__version__}")
print(f"LangGraph: {langgraph.__version__}")
```

### Test API Keys
```python
# Test OpenAI
from langchain_openai import ChatOpenAI
llm = ChatOpenAI(model="gpt-4o-mini")
llm.invoke("Hello!")

# Test Tavily (if key available)
from langchain_community.tools.tavily_search import TavilySearchResults
search = TavilySearchResults(max_results=1)
search.invoke("test query")
```

### Enable Debug Mode
```python
# Add verbose logging
import logging
logging.basicConfig(level=logging.DEBUG)
```

## 🔧 Troubleshooting

### Error: "No module named 'langchain'"
```bash
pip install -r requirements.txt
```

### Error: "Invalid API Key"
```bash
# Check your .env file exists and contains valid keys
cat .env
```

### Error: "Rate limit exceeded"
```python
# Add delay between queries
import time
time.sleep(60)  # Wait 60 seconds
```

## 📊 Example Queries to Try

1. **Financial Analysis**
   ```python
   "Chart the stock performance of Tesla vs Ford over the last year"
   ```

2. **Market Research**
   ```python
   "What are the latest AI startup funding rounds in 2024?"
   ```

3. **Competitive Analysis**
   ```python
   "Compare cloud service market share between AWS, Azure, and GCP"
   ```

4. **Regulatory Updates**
   ```python
   "Summarize recent cryptocurrency regulations in the EU"
   ```

## 🎨 Customization Tips

### Use Fewer Agents (Faster)
```python
enabled_agents = ["web_researcher", "synthesizer"]  # Skip chart generation
```

### Force Chart Generation
```python
enabled_agents = ["web_researcher", "chart_generator", "chart_summarizer", "synthesizer"]
```

### Change LLM Model
```python
llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=0.7)  # Faster, cheaper
```

## 📚 Next Steps

1. ✅ Run the example queries
2. 📝 Try your own questions
3. 🔧 Customize agent behaviors
4. 🚀 Add new agents
5. 📊 Experiment with different visualizations

## Need Help?

- 📖 Read the full README.md
- 🔍 Check FIXES_SUMMARY.md for recent updates
- 💬 Review notebook markdown cells for context
- 🐛 Enable debug logging for detailed traces

---
**Ready in 5 minutes! 🎉**