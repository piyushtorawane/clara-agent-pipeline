# 🚀 Clara AI Agent Configuration Pipeline

This repository contains an automated pipeline that converts **call transcripts into structured AI agent configurations**.

The system generates an initial **Agent Configuration (v1)** from demo transcripts and updates the configuration to **v2** using onboarding transcripts while producing a **changelog of updates**.

The workflows are implemented using **n8n** with **AI-powered information extraction**.

---

# 🧠 System Overview

The pipeline behaves like a small internal product that:

- Converts **unstructured transcripts → structured agent configuration**
- Maintains **versioned outputs (v1 → v2)**
- Tracks configuration updates automatically
- Requires minimal manual intervention
- Produces reproducible outputs

Two automated workflows are implemented.

---

# 🧩 Workflow 1 — Demo → Agent Configuration v1

This workflow generates the **initial agent configuration** from demo call transcripts.

![Demo Workflow](workflows/demo_to_agent_v1.png)

### Steps

1. Download demo transcript
2. Extract text from transcript file
3. Extract business information using AI
4. Generate **Account Memo**
5. Generate **Agent Specification**
6. Save outputs to version **v1**

### Output Location

outputs/accounts/account_001/v1/

### Files Generated

account_memo.json  
agent_spec.json

---

# 🔄 Workflow 2 — Onboarding → Agent Configuration v2

This workflow updates the existing configuration using onboarding transcripts.

![Onboarding Workflow](workflows/onboarding_to_agent_v2.png)

### Steps

1. Download onboarding transcript
2. Extract updated business information using AI
3. Load existing **Account Memo (v1)**
4. Merge new information with existing configuration
5. Generate updated **Account Memo**
6. Generate updated **Agent Specification**
7. Generate **Changelog**
8. Save outputs as version **v2**

### Output Location

outputs/accounts/account_001/v2/

### Files Generated

account_memo.json  
agent_spec.json  
changelog.json

---

# 📊 Versioned Outputs

### Version 1

account_memo.json  
agent_spec.json  

### Version 2

account_memo.json  
agent_spec.json  
changelog.json  

The changelog records differences between versions such as:

- New services added
- Updated business hours
- Updated emergency routing rules

---

# 📂 Repository Structure

clara-agent-pipeline

workflows/  
&nbsp;&nbsp;&nbsp;&nbsp;demo_to_agent_v1.json  
&nbsp;&nbsp;&nbsp;&nbsp;onboarding_to_agent_v2.json  
&nbsp;&nbsp;&nbsp;&nbsp;demo_to_agent_v1.png  
&nbsp;&nbsp;&nbsp;&nbsp;onboarding_to_agent_v2.png  

dataset/  
&nbsp;&nbsp;&nbsp;&nbsp;demo/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;demo1.txt  

&nbsp;&nbsp;&nbsp;&nbsp;onboarding/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;onboarding1.txt  

outputs/  
&nbsp;&nbsp;&nbsp;&nbsp;accounts/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;account_001/  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v1/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;account_memo.json  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;agent_spec.json  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v2/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;account_memo.json  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;agent_spec.json  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;changelog.json  

changelog/  
&nbsp;&nbsp;&nbsp;&nbsp;changelog.json  

scripts/  

README.md  

---

# ⚙️ Technologies Used

- **n8n** — workflow automation
- **LLM-based information extraction**
- **JSON structured outputs**
- **Google Drive integration for file storage**

---

# 🎯 Design Goals

This pipeline was designed to:

- Convert **unstructured transcripts into structured agent configurations**
- Maintain **version controlled outputs**
- Automatically **track configuration changes**
- Provide **repeatable workflows**
- Require **minimal manual intervention**

---

# 💡 Result

The system functions as a **configuration management pipeline for AI agents**, automatically converting operational call transcripts into **structured and versioned AI agent behavior definitions**.
