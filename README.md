# 📍 AI-Powered Local Hangout Planner (n8n + LLM)

An end-to-end AI recommendation workflow built in **n8n** that ranks nearby places using a custom scoring engine and generates structured recommendations using an LLM.

This project demonstrates how to combine **deterministic rule-based logic** with **generative AI reasoning** to build reliable, context-aware systems.

---

## 🚀 What This Workflow Does

1. Collects nearby places based on location  
2. Applies a custom weighted scoring algorithm  
3. Ranks places by:
   - Group size compatibility  
   - Weather conditions  
   - Crowd risk  
   - Distance penalty  
   - Chain restaurant penalty  
4. Sends ranked results to an LLM  
5. Generates structured JSON recommendations  
6. Returns formatted suggestions via chat  

---

## 🧠 Architecture Overview

**Workflow Pipeline:**

Chat Trigger  
→ Collect Places  
→ Score Places (Custom JS Logic)  
→ Extract Top Picks  
→ LLM (Structured JSON Output)  
→ Format Response  
→ Return to Chat  

*(Add workflow screenshot here)*

---

## ⚙️ Scoring Logic

The scoring engine combines weighted factors:

- **Group Fit (35%)**
- **Weather Fit (25%)**
- **Low Crowd Risk (20%)**
- **Amenity Boost**
- **Distance Penalty**
- **Chain Restaurant Penalty**

### Example Formula

```javascript
score =
(0.35 * group_fit) +
(0.25 * weather_fit) +
(0.20 * (1 - crowd_risk)) +
amenity_boost -
chain_penalty -
distance_penalty
```
This ensures recommendations are **explainable, consistent, and context-aware**.

---

## 🤖 LLM Integration

The LLM:

- Receives only top-ranked places  
- Is constrained to use provided data  
- Returns structured JSON  
- Avoids hallucinations  
- Produces clean, consistent output  

### Example Output Structure

```json
{
  "top_recommendations": [],
  "why_these": "",
  "backup": []
}
```
