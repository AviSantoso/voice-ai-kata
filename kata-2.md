# Voice AI Kata: Real Estate Info Gathering MVP

## System Overview
Voice-first AI system for **Real Estate** handling **Information Collection**. **Potential tenants and property inquiries** call to **gather rental application details and property interest information**. AI handles conversations during **after-hours and weekends** or when all agents are busy, captures **contact details, property preferences, income verification, and rental history**, and creates prioritized leads for agents to review and follow up.

**Core Problem:** Real estate agency receives 80+ property inquiry calls daily, but agents are often out showing properties or in meetings. Weekend open house inquiries go to voicemail. Voice AI provides 24/7 lead capture with automated rental application pre-screening and property matching.

---

## User Stories & Acceptance Criteria

### **Story 1: Basic Call Handling** [1 point]
**As a** potential tenant  
**I want to** call and have the AI answer immediately  
**So that** I can inquire about properties anytime

**Description:**
Simple phone system that answers calls with professional real estate greeting and can record basic audio input using speech-to-text.

**Acceptance Criteria:**
- **Given** I dial the agency number **When** call connects **Then** AI greets me with "Hello, you've reached Premium Properties. How can I help you today?"

---

### **Story 2: Speech-to-Text Capture** [2 points]
**As a** voice AI system  
**I want to** convert caller speech to text accurately  
**So that** I can process tenant inquiries and application details

**Description:**
Integrate speech recognition to convert caller audio to text for processing rental inquiries and personal information.

**Acceptance Criteria:**
- **Given** caller says "I'm interested in the apartment on Smith Street" **When** speech is processed **Then** system captures text accurately
- **Given** unclear audio **When** speech confidence is low **Then** system asks "Could you repeat that please?"

---

### **Story 3: Text-to-Speech Responses** [3 points]
**As a** potential tenant  
**I want to** hear clear spoken responses from the AI  
**So that** I understand what information is needed for my application

**Description:**
Convert AI responses to professional-sounding speech suitable for real estate interactions.

**Acceptance Criteria:**
- **Given** AI needs to ask for income details **When** speaking to caller **Then** response sounds professional and clear
- **Given** AI provides property information **When** speaking **Then** caller can easily understand address and rental details

---

### **Story 4: Contact Information Collection** [2 points]
**As a** voice AI  
**I want to** capture caller's name and phone number  
**So that** agents can follow up on property inquiries

**Description:**
Extract names and phone numbers from conversational speech, handling various formats and confirming details.

**Acceptance Criteria:**
- **Given** caller says "This is Jennifer Martinez, my number is 0412 345 678" **When** processed by AI **Then** contact details are captured and confirmed
- **Given** contact info collected **When** confirming **Then** AI repeats back "So that's Jennifer Martinez on zero four one two three four five six seven eight"

---

### **Story 5: Property Address Identification** [4 points]
**As a** voice AI  
**I want to** identify which property the caller is asking about  
**So that** I can provide relevant information and record their interest

**Description:**
Match caller descriptions to property database using addresses, landmarks, or property features mentioned.

**Acceptance Criteria:**
- **Given** caller says "the two bedroom unit on Smith Street" **When** property matching runs **Then** system identifies correct property and confirms address
- **Given** unclear property description **When** multiple matches found **Then** AI asks clarifying questions like "Is that the one with the balcony or the ground floor unit?"

---

### **Story 6: Business Hours and Agent Availability** [4 points]
**As a** system  
**I want to** determine if agents are available  
**So that** I can route calls appropriately or explain after-hours service

**Description:**
Check current time against business hours and agent availability, routing to AI collection during busy/off periods.

**Acceptance Criteria:**
- **Given** caller calls at 7 PM **When** call connects **Then** AI says "Our agents are currently unavailable, but I can help collect your details for a callback tomorrow"
- **Given** caller calls during business hours **When** all agents busy with showings **Then** AI says "Our agents are currently with clients, would you like me to take your details?"

---

### **Story 7: Income and Employment Verification** [6 points]
**As a** voice AI  
**I want to** collect employment and income details  
**So that** agents can pre-qualify potential tenants

**Description:**
Gather employment status, employer name, and weekly/annual income information for rental application pre-screening.

**Acceptance Criteria:**
- **Given** AI asks about employment **When** caller responds "I work at Westpac Bank earning $75,000 per year" **Then** employment and income details are captured accurately
- **Given** caller is self-employed **When** income question asked **Then** AI asks "As you're self-employed, what's your average monthly income?"

---

### **Story 8: Rental History Collection** [8 points]
**As a** voice AI  
**I want to** gather previous rental experience  
**So that** agents have tenant background for application assessment

**Description:**
Collect current living situation, previous rental addresses, and rental history including reasons for moving.

**Acceptance Criteria:**
- **Given** AI asks about rental history **When** caller provides details **Then** captures current address, previous rentals, and length of tenancy
- **Given** caller mentions issues with current rental **When** discussing moving reasons **Then** AI records reason sensitively and accurately

---

### **Story 9: Basic Agent Authentication** [3 points]
**As a** real estate agent  
**I want to** log into a secure system  
**So that** I can access lead information and applications

**Description:**
Simple login system for agents to access collected lead information and partial applications.

**Acceptance Criteria:**
- **Given** valid agent credentials **When** logging into dashboard **Then** access is granted to lead management interface
- **Given** invalid credentials **When** attempting login **Then** access denied with clear error message

---

### **Story 10: Lead Record Creation** [6 points]
**As a** voice AI system  
**I want to** create structured lead records from conversations  
**So that** agents can follow up with qualified prospects

**Description:**
Store all collected information as structured lead records with contact details, property interest, and application data.

**Acceptance Criteria:**
- **Given** completed voice conversation **When** call ends **Then** lead record is created with all captured information
- **Given** lead is created **When** storing **Then** includes timestamp, property of interest, and completion status

---

### **Story 11: Application Completeness Assessment** [9 points]
**As a** voice AI system  
**I want to** evaluate how complete each application is  
**So that** agents can prioritize follow-ups with ready-to-proceed applicants

**Description:**
Analyze collected information and assign completeness scores, flagging missing critical details for agent follow-up.

**Acceptance Criteria:**
- **Given** caller provides all required details **When** assessment runs **Then** application marked as "Complete - Ready for Processing"
- **Given** missing income verification **When** evaluating **Then** flagged as "Needs Income Documentation" with specific requirements listed

---

### **Story 12: Agent Lead Dashboard** [12 points]
**As a** real estate agent  
**I want to** view all incoming leads organized by priority  
**So that** I can follow up with the most promising prospects first

**Description:**
Web dashboard showing leads sorted by completeness and property match, with filters for property type and urgency.

**Acceptance Criteria:**
- **Given** agent accesses dashboard **When** viewing leads **Then** sees list sorted by application completeness and property interest
- **Given** lead list displayed **When** viewing **Then** shows prospect name, interested property, income level, and application status
- **Given** filtering options **When** filtering **Then** can view by property type, income bracket, and urgency level

---

### **Story 13: Property Preference Matching** [4 points]
**As a** voice AI  
**I want to** capture detailed property preferences  
**So that** agents can suggest suitable alternatives if preferred property unavailable

**Description:**
Collect budget range, preferred areas, property features, and must-haves to enable property matching.

**Acceptance Criteria:**
- **Given** AI asks about preferences **When** caller specifies "2 bedroom, under $500/week, near train station" **Then** all criteria captured accurately
- **Given** specific requirements mentioned **When** recording preferences **Then** distinguishes between must-haves and nice-to-haves

---

### **Story 14: Lead Detail Management** [8 points]
**As a** real estate agent  
**I want to** view complete lead details and update status  
**So that** I can manage follow-ups and track application progress

**Description:**
Detailed lead view with full conversation transcript, audio playback, and status management for agent workflow.

**Acceptance Criteria:**
- **Given** agent clicks on lead **When** viewing details **Then** sees complete conversation, contact details, and property interest
- **Given** lead detail view **When** updating status **Then** can mark as "Contacted", "Application Sent", "Viewing Scheduled", or "Not Suitable"
- **Given** follow-up needed **When** managing lead **Then** can set callback reminders and add agent notes

---

### **Story 15: Real-time Lead Notifications** [12 points]
**As a** real estate agent  
**I want to** receive immediate alerts for high-priority leads  
**So that** I can respond quickly to qualified prospects

**Description:**
Live dashboard updates with notifications for complete applications and high-income prospects requiring immediate attention.

**Acceptance Criteria:**
- **Given** new lead created **When** AI completes conversation **Then** lead appears on dashboard immediately
- **Given** high-value prospect identified **When** income exceeds threshold **Then** agent receives priority alert with contact details
- **Given** agent viewing dashboard **When** urgent lead arrives **Then** notification sound plays and lead highlighted

---

### **Story 16: Lead Performance Analytics** [16 points]
**As a** agency manager  
**I want** comprehensive lead tracking and conversion analytics  
**So that** I can optimize our lead capture process and agent performance

**Description:**
Complete analytics dashboard tracking call volume, application completion rates, property interest trends, and conversion metrics.

**Acceptance Criteria:**
- **Given** leads processed **When** monitoring system **Then** tracks call-to-application conversion >60%, average conversation duration, and completion rates
- **Given** multiple analytics metrics **When** viewing reports **Then** shows daily/weekly trends for lead quality, property interest patterns, and agent follow-up success
- **Given** performance tracking **When** analyzing conversion **Then** identifies peak inquiry times, most requested property features, and optimal follow-up timing

---

**Total Points: 100**

**Completion Target:** Weekend Sprint / Hackathon Style - Complete as many stories as possible in your available time, aim for working prototype demonstrating core voice AI lead capture and automated workflow capabilities.