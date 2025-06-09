# Voice AI Kata: NDIS Phone Triage MVP (Updated)

## System Overview
Voice-first AI triage system where NDIS participants call a phone number to report issues. AI handles the conversation during off-hours or when all staff are busy, captures information, and creates prioritized cases that staff can review and manage through a back-office UI.

**Core Problem:** NDIS office receives 50+ calls daily, but only operates 9-5. After-hours callers get voicemail, causing delays. During business hours, all phones may be occupied. Voice AI provides 24/7 intake with intelligent triage and overflow management.

---

## User Stories & Acceptance Criteria

### **Story 1: Basic Call Handling** [1 point]
**As a** participant  
**I want to** call and have the AI answer immediately  
**So that** I can report my issue anytime

**Description:**
Simple phone system that answers calls with a greeting and can record basic audio input using speech-to-text.

**Acceptance Criteria:**
- **Given** I dial the triage number **When** call connects **Then** AI greets me with "Hello, this is NDIS support. How can I help you today?"

---

### **Story 2: Speech-to-Text Capture** [2 points]
**As a** voice AI system  
**I want to** convert caller speech to text accurately  
**So that** I can process what participants are saying

**Description:**
Integrate speech recognition (e.g., Whisper, Google Speech) to convert caller audio to text for processing.

**Acceptance Criteria:**
- **Given** caller says "My name is Sarah Johnson" **When** speech is processed **Then** system captures text "My name is Sarah Johnson"
- **Given** unclear audio **When** speech confidence is low **Then** system asks "Could you repeat that please?"

---

### **Story 3: Text-to-Speech Responses** [2 points]
**As a** participant  
**I want to** hear clear spoken responses from the AI  
**So that** I know the system understood me and what to do next

**Description:**
Convert AI responses to natural-sounding speech using TTS (e.g., ElevenLabs, Azure Speech).

**Acceptance Criteria:**
- **Given** AI needs to respond with "Thank you, I've recorded your name" **When** speaking to caller **Then** response is clearly audible and natural-sounding
- **Given** AI asks a question **When** speaking **Then** caller can easily understand what information is being requested

---

### **Story 4: Name Extraction** [3 points]
**As a** voice AI  
**I want to** extract the caller's name from natural speech  
**So that** I can personalize the conversation and record their identity

**Description:**
Use LLM to extract names from conversational speech patterns like "Hi, this is John" or "My name is Sarah Smith".

**Acceptance Criteria:**
- **Given** caller says "Hi, this is John Smith calling" **When** processed by AI **Then** name "John Smith" is extracted and confirmed
- **Given** caller says "Um, Sarah here" **When** processed **Then** AI asks "Just to confirm, your name is Sarah?"

---

### **Story 5: Office Hours Detection** [3 points]
**As a** system  
**I want to** determine if the call is during business hours  
**So that** I can route appropriately or explain after-hours service

**Description:**
Check current Perth time against business hours (9 AM - 5 PM weekdays) and inform callers about after-hours service.

**Acceptance Criteria:**
- **Given** caller calls at 7 PM **When** call connects **Then** AI says "You've reached us outside business hours, but I can help take your details"
- **Given** caller calls at 10 AM on Tuesday **When** all staff busy **Then** AI says "All our staff are currently busy, would you like to wait or shall I take your details for a callback?"

---

### **Story 6: Phone Number Extraction** [4 points]
**As a** voice AI  
**I want to** capture and validate phone numbers from speech  
**So that** we can call participants back if needed

**Description:**
Extract phone numbers from speech, handling various formats ("zero four one two" vs "oh four one two").

**Acceptance Criteria:**
- **Given** caller says "my number is zero four one two three four five six seven eight" **When** processed **Then** system captures "0412345678"
- **Given** phone number is captured **When** confirming **Then** AI spells out digits "zero four one two three four five six seven eight"

---

### **Story 7: NDIS Number Collection** [4 points]
**As a** voice AI  
**I want to** collect and validate 9-digit NDIS participant numbers  
**So that** cases are linked to correct participant records

**Description:**
Specifically ask for NDIS numbers, handle digit-by-digit spelling, and validate format.

**Acceptance Criteria:**
- **Given** AI asks "What's your NDIS participant number?" **When** caller responds with 9 digits **Then** number is captured correctly
- **Given** caller provides wrong number of digits **When** validation runs **Then** AI asks "NDIS numbers have 9 digits, could you repeat that?"

---

### **Story 8: Issue Description Capture** [4 points]
**As a** voice AI  
**I want to** let callers describe their issues in their own words  
**So that** we capture the full context of their problem

**Description:**
Open-ended speech capture allowing participants to explain their situation naturally, with gentle prompting for clarity.

**Acceptance Criteria:**
- **Given** AI asks "Can you tell me about the issue you're experiencing?" **When** caller speaks for 30+ seconds **Then** full description is captured accurately
- **Given** caller gives very brief answer **When** response is short **Then** AI asks "Can you tell me a bit more about what happened?"

---

### **Story 9: Basic Back Office Authentication** [6 points]
**As a** NDIS staff member  
**I want to** log into a secure back office system  
**So that** I can access participant case information

**Description:**
Simple login system with username/password for NDIS staff to access the case management interface.

**Acceptance Criteria:**
- **Given** valid staff credentials **When** logging into back office **Then** access is granted to case dashboard
- **Given** invalid credentials **When** attempting login **Then** access is denied with clear error message

---

### **Story 10: Case Creation and Storage** [6 points]
**As a** voice AI system  
**I want to** create structured case records from voice conversations  
**So that** staff can review all captured information

**Description:**
Store all captured information (name, NDIS number, phone, issue description, timestamp) as structured case records.

**Acceptance Criteria:**
- **Given** completed voice conversation **When** call ends **Then** case record is created with all collected data
- **Given** case is created **When** storing **Then** includes call timestamp, duration, and audio recording reference

---

### **Story 11: Issue Categorization and Priority** [8 points]
**As a** triage system  
**I want to** automatically categorize issues and assign priority levels  
**So that** urgent cases get immediate attention

**Description:**
Use LLM to analyze issue descriptions and assign categories (Funding, Provider, Equipment) and priority levels (Low/Medium/High/Emergency).

**Acceptance Criteria:**
- **Given** caller describes "my support worker isn't showing up and I can't get to medical appointment" **When** LLM processes **Then** categorized as "Provider Services" with "High" priority
- **Given** emergency keywords detected **When** analyzing **Then** priority set to "Emergency" and case flagged for immediate callback

---

### **Story 12: Back Office Case Dashboard** [8 points]
**As a** NDIS staff member  
**I want to** view all incoming cases in a prioritized list  
**So that** I can handle urgent matters first

**Description:**
Web dashboard showing cases sorted by priority, with filters for status, category, and time. Display key information at a glance.

**Acceptance Criteria:**
- **Given** staff access dashboard **When** viewing cases **Then** sees list sorted by priority with High/Emergency cases at top
- **Given** case list displayed **When** viewing **Then** shows participant name, NDIS number, category, priority, and time received
- **Given** multiple filters available **When** filtering **Then** can view cases by status (New/In Progress/Resolved) and category

---

### **Story 13: Call Queue Management** [9 points]
**As a** system  
**I want to** offer callback options when all staff are busy  
**So that** participants don't wait on hold indefinitely

**Description:**
Detect when all staff lines are busy during business hours and offer immediate AI triage or callback option with time estimates.

**Acceptance Criteria:**
- **Given** all staff busy during business hours **When** caller connects **Then** AI offers "Would you like me to help you now, or would you prefer a callback within 2 hours?"
- **Given** caller chooses callback **When** selecting option **Then** AI collects phone number and creates priority callback task
- **Given** callback is scheduled **When** confirming **Then** caller receives estimated callback time

---

### **Story 14: Case Detail View** [12 points]
**As a** NDIS staff member  
**I want to** view complete case details and update status  
**So that** I can work on cases efficiently and track progress

**Description:**
Detailed case view showing full conversation transcript, audio playback, participant history, and status management.

**Acceptance Criteria:**
- **Given** staff clicks on case **When** viewing details **Then** sees full transcript, audio player, and participant contact details
- **Given** case detail view **When** updating status **Then** can mark as "In Progress", "Awaiting Info", or "Resolved" with notes
- **Given** case requires callback **When** managing **Then** can schedule callback time and add notes for follow-up

---

### **Story 15: Real-time Case Updates** [12 points]
**As a** back office user  
**I want to** see new cases appear automatically  
**So that** urgent cases get immediate attention without page refreshes

**Description:**
Live dashboard updates showing new cases as they arrive, with visual/audio alerts for high-priority cases.

**Acceptance Criteria:**
- **Given** new case is created **When** AI completes conversation **Then** case appears on dashboard immediately without refresh
- **Given** emergency case detected **When** flagged as urgent **Then** dashboard shows red alert and plays notification sound
- **Given** staff viewing dashboard **When** new case arrives **Then** case counter updates and new case highlighted

---

### **Story 16: Voice System Performance Monitoring** [16 points]
**As a** system administrator  
**I want** comprehensive monitoring and analytics  
**So that** I can ensure system reliability and optimize performance

**Description:**
Complete monitoring dashboard tracking voice recognition accuracy, call completion rates, system load, and case resolution metrics.

**Acceptance Criteria:**
- **Given** voice calls processed **When** monitoring system **Then** tracks speech accuracy >85%, call completion rates, and average conversation duration
- **Given** multiple performance metrics **When** viewing analytics **Then** shows daily/weekly trends for call volume, after-hours usage, and case priorities
- **Given** system performance issues **When** thresholds exceeded **Then** alerts sent to administrators with specific error details and suggested actions

---

**Total Points: 100**