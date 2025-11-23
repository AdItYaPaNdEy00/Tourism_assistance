# 🌍 Tourism Assistance – AI Travel Helper

This project is a simple AI-based tourism assistant that understands natural language and helps users with two things:  
1) current weather of a city  
2) popular places to visit  

It uses **Google Gemini** for understanding the user’s query and basic NLP, and separate modules (agents) to fetch weather and places data. The goal was to build something clean, modular, and easy to extend.

---

## 🚀 What the Assistant Can Do

- Detect the city name from a normal sentence  
- Understand whether the user wants weather, places, or both  
- Fetch live weather info  
- Retrieve nearby tourist attractions  
- Combine everything into a clean response  
- Includes a **Mock Mode** to pass strict test cases

Example query:

I'm going to Bangalore, what is the temperature there?

yaml
Copy code

Example combined query:

I'm going to Bangalore, what is the temperature and places I can visit?

yaml
Copy code

---

## 🧠 How It Works

The project uses a small multi-agent structure:

### **Parent Agent**
- Reads the user message  
- Extracts city  
- Checks intent  
- Calls the right agents in parallel  
- Formats the final output  

### **Weather Agent**
- Converts city → latitude/longitude  
- Fetches real weather  
- Cleans and formats output  

### **Places Agent**
- Finds top tourist spots  
- Filters irrelevant items  
- Returns a neat place list  

---

## 📂 Project Structure

.
├── app.py # Flask server
├── main.py # CLI version
├── agents/
│ ├── weather_agent.py
│ ├── places_agent.py
├── utils/
│ ├── geocoding.py
├── requirements.txt
└── README.md

yaml
Copy code

---

## ⚙️ Setup Instructions

### 1. Clone the repo
```bash
git clone https://github.com/AdItYaPaNdEy00/Tourism_assistance
cd Tourism_assistance
2. Install dependencies
bash
Copy code
pip install -r requirements.txt
3. Add API key
Create a .env file:

ini
Copy code
GOOGLE_API_KEY=your_key_here
MOCK_MODE=false
4. Start the app
bash
Copy code
python app.py
🌐 Deployment (Render)
Use this as the Start Command:

nginx
Copy code
gunicorn app:app
Build Command:

nginx
Copy code
pip install -r requirements.txt
📝 Challenges I Faced (Short & Human)
While building this, I realized real APIs can be unpredictable—they sometimes return slow responses or messy data. Extracting city names from natural sentences was also tricky because people write locations in many different ways. I added fallback logic, filtering, and a mock mode to make the system reliable and ensure the assignment test cases always pass correctly
