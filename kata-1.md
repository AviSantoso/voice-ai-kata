# "Call Me Maybe" - NDIS Voice AI Triage Quest 🎯

## System Overview
Voice-first AI triage system where NDIS participants call a phone number to report issues. AI handles the conversation during off-hours or when all staff are busy, captures information, and creates prioritized cases that staff can review and manage through a back-office UI.

**Core Problem:** NDIS office receives 50+ calls daily, but only operates 9-5. After-hours callers get voicemail, causing delays. During business hours, all phones may be occupied. Voice AI provides 24/7 intake with intelligent triage and overflow management.

---

## Quest Stories & Victory Conditions 🏆

### **Story 1: Basic Call Handling** [1 XP]
**As a** participant  
**I want to** call and have the AI answer immediately  
**So that** I can report my issue anytime

**Expert Insight:**
From my experience managing call centers for disability services, immediate call pickup is absolutely critical for participant trust and emergency situations. Participants with cognitive disabilities or stress-related conditions can become confused or anxious when calls go unanswered. A consistent, welcoming greeting delivered within 3 rings establishes confidence and reduces call abandonment rates. The greeting must be professional yet warm, clearly identifying the service to prevent confusion. I've seen too many participants hang up when they're unsure they've reached the right number, especially those with hearing impairments who rely on audio cues to confirm connection.

**Victory Conditions:**
- **Given** I dial the triage number **When** call connects **Then** AI greets me with "Hello, this is NDIS support. How can I help you today?"

---

### **Story 2: Speech-to-Text Capture** [2 XP]
**As a** voice AI system  
**I want to** convert caller speech to text accurately  
**So that** I can process what participants are saying

**Expert Insight:**
Accurate speech recognition is the foundation of any voice-based triage system. From working with diverse NDIS participants, I know we must account for speech impediments, accents, background noise, and varying communication styles. Some participants have speech difficulties, others may speak quietly or quickly when stressed. The system needs robust confidence scoring to identify when transcription may be inaccurate. False positives in speech recognition can lead to incorrect case categorization, while false negatives create frustration for participants who feel unheard. Having a fallback strategy for unclear speech is essential for maintaining service quality and participant dignity.

**Victory Conditions:**
- **Given** caller says "My name is Sarah Johnson" **When** speech is processed **Then** system captures text "My name is Sarah Johnson"
- **Given** unclear audio **When** speech confidence is low **Then** system asks "Could you repeat that please?"

---

### **Story 3: Text-to-Speech Responses** [2 XP]
**As a** participant  
**I want to** hear clear spoken responses from the AI  
**So that** I know the system understood me and what to do next

**Expert Insight:**
Natural-sounding text-to-speech is crucial for participant engagement and comprehension. I've observed that robotic or unclear voice synthesis can trigger anxiety in participants, particularly those with autism or cognitive processing differences. The voice should be calm, measured, and consistent in tone to build trust. Speed and pronunciation are critical - participants with hearing impairments or processing delays need clear articulation. The voice should also convey empathy without sounding fake, as participants can detect insincerity, which damages rapport. Consider that some participants may be calling during crisis situations and need a voice that feels supportive rather than mechanical.

**Victory Conditions:**
- **Given** AI needs to respond with "Thank you, I've recorded your name" **When** speaking to caller **Then** response is clearly audible and natural-sounding
- **Given** AI asks a question **When** speaking **Then** caller can easily understand what information is being requested

---

### **Story 4: Name Extraction** [3 XP]
**As a** voice AI  
**I want to** extract the caller's name from natural speech  
**So that** I can personalize the conversation and record their identity

**Expert Insight:**
Name extraction is more complex than it appears, especially with NDIS participants who may have unique names, hyphenated surnames, or preferred names different from official records. Some participants introduce themselves formally ("This is Mary Elizabeth Smith"), others casually ("Hi, it's just Dave"), and some may be confused about which name to use if they have guardianship arrangements. The system needs to handle cultural naming conventions, titles, and situations where participants correct themselves mid-conversation. Accurate name capture is essential for case linking and demonstrates respect for the individual's identity, which is fundamental to person-centered NDIS principles.

**Victory Conditions:**
- **Given** caller says "Hi, this is John Smith calling" **When** processed by AI **Then** name "John Smith" is extracted and confirmed
- **Given** caller says "Um, Sarah here" **When** processed **Then** AI asks "Just to confirm, your name is Sarah?"

---

### **Story 5: Office Hours Detection** [3 XP]
**As a** system  
**I want to** determine if the call is during business hours  
**So that** I can route appropriately or explain after-hours service

**Expert Insight:**
Managing participant expectations around availability is crucial for service delivery and staff workload management. Many NDIS participants work non-traditional hours due to their support needs, or may only feel comfortable calling outside busy periods. Clear communication about after-hours service prevents frustration and ensures participants understand their options. The system must account for public holidays, NDIS-specific closure days, and emergency protocols. Some issues genuinely cannot wait for business hours - medication access, support worker no-shows, or safety concerns. The greeting should reassure participants that after-hours calls are valued while managing realistic expectations about response times.

**Victory Conditions:**
- **Given** caller calls at 7 PM **When** call connects **Then** AI says "You've reached us outside business hours, but I can help take your details"
- **Given** caller calls at 10 AM on Tuesday **When** all staff busy **Then** AI says "All our staff are currently busy, would you like to wait or shall I take your details for a callback?"

---

### **Story 6: Phone Number Extraction** [4 XP]
**As a** voice AI  
**I want to** capture and validate phone numbers from speech  
**So that** we can call participants back if needed

**Expert Insight:**
Phone number collection is critical for case follow-up, but surprisingly challenging in practice. Participants often speak numbers differently ("oh" vs "zero", groupings of 2, 3, or 4 digits), and some have memory or cognitive processing differences that affect number recall. Mobile numbers may be shared between family members or carers, and landlines might have poor audio quality. The system must handle Australian number formats specifically, including older geographic prefixes. Validation should catch common errors without being patronizing. Consider that some participants may be using communication devices or have speech patterns that affect number pronunciation. Always confirm back to ensure accuracy.

**Victory Conditions:**
- **Given** caller says "my number is zero four one two three four five six seven eight" **When** processed **Then** system captures "0412345678"
- **Given** phone number is captured **When** confirming **Then** AI spells out digits "zero four one two three four five six seven eight"

---

### **Story 7: NDIS Number Collection** [4 XP]
**As a** voice AI  
**I want to** collect and validate 9-digit NDIS participant numbers  
**So that** cases are linked to correct participant records

**Expert Insight:**
NDIS participant numbers are essential for case management and funding verification, but participants often struggle to remember or locate them. Some participants have family members or carers who know their number, others keep it written down but may misread it over the phone. The 9-digit format is specific to NDIS, but participants sometimes confuse it with Medicare numbers or other identifiers. The system should guide participants to find their NDIS plan or card if needed, and handle situations where they don't have immediate access. Consider that incorrect numbers could link cases to wrong participants, creating privacy and service delivery issues. The validation must be thorough but patient.

**Victory Conditions:**
- **Given** AI asks "What's your NDIS participant number?" **When** caller responds with 9 digits **Then** number is captured correctly
- **Given** caller provides wrong number of digits **When** validation runs **Then** AI asks "NDIS numbers have 9 digits, could you repeat that?"

---

### **Story 8: Issue Description Capture** [4 XP]
**As a** voice AI  
**I want to** let callers describe their issues in their own words  
**So that** we capture the full context of their problem

**Expert Insight:**
Free-form issue description is where the system either succeeds or fails in capturing participant needs. From my disability services experience, participants often present complex, interconnected problems that don't fit neat categories. They may start with one issue and reveal more serious underlying problems as they talk. Some participants need time to articulate their situation due to processing differences or emotional distress. Others may downplay urgent issues due to learned helplessness or past negative experiences. The AI must encourage detailed descriptions while recognizing when participants are struggling to communicate. Gentle prompting should draw out key details without interrogating. This is often when emergency situations are revealed, so the system must be alert for safety concerns.

**Victory Conditions:**
- **Given** AI asks "Can you tell me about the issue you're experiencing?" **When** caller speaks for 30+ seconds **Then** full description is captured accurately
- **Given** caller gives very brief answer **When** response is short **Then** AI asks "Can you tell me a bit more about what happened?"

---

### **Story 9: Basic Back Office Authentication** [6 XP]
**As a** NDIS staff member  
**I want to** log into a secure back office system  
**So that** I can access participant case information

**Expert Insight:**
Security in NDIS case management cannot be overstated - we're handling highly sensitive personal information about vulnerable individuals. Staff access must be strictly controlled with individual accountability. However, security measures shouldn't impede rapid response to urgent cases. I've seen systems where complex authentication delays emergency responses. The login process needs to balance security with usability, considering that staff may need system access from multiple locations and devices. Failed login attempts should be logged for security monitoring, but legitimate staff shouldn't be locked out during busy periods. Consider implementing session timeouts appropriate for case management workflows while maintaining security standards.

**Victory Conditions:**
- **Given** valid staff credentials **When** logging into back office **Then** access is granted to case dashboard
- **Given** invalid credentials **When** attempting login **Then** access is denied with clear error message

---

### **Story 10: Case Creation and Storage** [6 XP]
**As a** voice AI system  
**I want to** create structured case records from voice conversations  
**So that** staff can review all captured information

**Expert Insight:**
Structured case creation is the bridge between voice interaction and effective case management. Every data point captured during the call becomes crucial for follow-up and service delivery. From managing hundreds of participant cases, I know that incomplete or poorly structured records lead to repeated information gathering, frustrating participants and wasting resources. The case record must preserve the participant's own words alongside structured data, as their specific language often contains important context that categorization might miss. Timestamps are critical for understanding urgency and tracking response times. Audio retention may be necessary for quality assurance and dispute resolution, but must comply with privacy requirements.

**Victory Conditions:**
- **Given** completed voice conversation **When** call ends **Then** case record is created with all collected data
- **Given** case is created **When** storing **Then** includes call timestamp, duration, and audio recording reference

---

### **Story 11: Issue Categorization and Priority** [8 XP]
**As a** triage system  
**I want to** automatically categorize issues and assign priority levels  
**So that** urgent cases get immediate attention

**Expert Insight:**
Effective triage categorization is both an art and a science in disability services. I've developed triage protocols that consider not just the immediate issue, but the participant's vulnerability and support network. A missed support worker visit might be low priority for someone with family backup, but emergency-level for an isolated participant with high medical needs. The system must recognize keywords indicating immediate safety risks, funding deadline pressures, and service continuity threats. Categories should align with staff expertise areas and organizational workflows. However, automated triage can miss nuanced situations, so there must be mechanisms for staff to reassess priority levels. Emergency detection is critical - threats to safety, medication access, or essential support require immediate human intervention.

**Victory Conditions:**
- **Given** caller describes "my support worker isn't showing up and I can't get to medical appointment" **When** LLM processes **Then** categorized as "Provider Services" with "High" priority
- **Given** emergency keywords detected **When** analyzing **Then** priority set to "Emergency" and case flagged for immediate callback

---

### **Story 12: Back Office Case Dashboard** [8 XP]
**As a** NDIS staff member  
**I want to** view all incoming cases in a prioritized list  
**So that** I can handle urgent matters first

**Expert Insight:**
The case dashboard is staff's primary tool for managing participant needs effectively. From managing busy NDIS offices, I know that visual clarity and prioritization save lives - literally. Staff need to immediately identify emergency cases while maintaining awareness of aging lower-priority items that might escalate. The interface must support different working styles - some staff prefer chronological order, others work by category or participant familiarity. Critical information must be visible at a glance without opening cases, but the interface shouldn't be cluttered. Color coding for priorities helps rapid scanning, but must be accessible for colorblind users. The dashboard should support rapid case assignment and prevent duplicate handling of the same issue.

**Victory Conditions:**
- **Given** staff access dashboard **When** viewing cases **Then** sees list sorted by priority with High/Emergency cases at top
- **Given** case list displayed **When** viewing **Then** shows participant name, NDIS number, category, priority, and time received
- **Given** multiple filters available **When** filtering **Then** can view cases by status (New/In Progress/Resolved) and category

---

### **Story 13: Call Queue Management** [9 XP]
**As a** system  
**I want to** offer callback options when all staff are busy  
**So that** participants don't wait on hold indefinitely

**Expert Insight:**
Queue management directly impacts participant experience and office efficiency. From analyzing call patterns, I know that participants often call during crisis situations and cannot wait indefinitely. However, the choice between immediate AI assistance and human callback empowers participants to select what works best for their communication style and situation urgency. Accurate callback time estimates are crucial - overestimating reduces anxiety but may delay emergency responses, while underestimating creates frustration. The system must dynamically adjust estimates based on current case load and staff availability. Some participants prefer human interaction for complex or sensitive issues, while others find AI easier for straightforward reporting. The callback queue must integrate with staff workflow tools to ensure promises are kept.

**Victory Conditions:**
- **Given** all staff busy during business hours **When** caller connects **Then** AI offers "Would you like me to help you now, or would you prefer a callback within 2 hours?"
- **Given** caller chooses callback **When** selecting option **Then** AI collects phone number and creates priority callback task
- **Given** callback is scheduled **When** confirming **Then** caller receives estimated callback time

---

### **Story 14: Case Detail View** [12 XP]
**As a** NDIS staff member  
**I want to** view complete case details and update status  
**So that** I can work on cases efficiently and track progress

**Expert Insight:**
Comprehensive case detail views are essential for effective participant advocacy and service delivery. From handling complex NDIS cases, I know that context is everything - a participant's communication style, previous issues, family dynamics, and service history all influence how to best address current problems. The case view must present information hierarchically, with urgent details prominent and supporting information easily accessible. Audio playback capability is crucial for cases involving emotional distress or complex situations where text alone misses important nuances. Status tracking creates accountability and helps identify systemic issues. Notes must support rich documentation for continuity between staff members, and case histories help identify patterns that might indicate provider or system problems requiring broader intervention.

**Victory Conditions:**
- **Given** staff clicks on case **When** viewing details **Then** sees full transcript, audio player, and participant contact details
- **Given** case detail view **When** updating status **Then** can mark as "In Progress", "Awaiting Info", or "Resolved" with notes
- **Given** case requires callback **When** managing **Then** can schedule callback time and add notes for follow-up

---

### **Story 15: Real-time Case Updates** [12 XP]
**As a** back office user  
**I want to** see new cases appear automatically  
**So that** urgent cases get immediate attention without page refreshes

**Expert Insight:**
Real-time updates are critical in disability services where delays can have serious consequences for participant safety and wellbeing. From managing crisis response teams, I understand that every minute matters for emergency cases - participants in distress need to know help is coming. Automatic dashboard updates ensure staff awareness without requiring constant manual checking, but notifications must be calibrated to avoid alert fatigue. Emergency cases need immediate attention, but constant pings for routine items reduce effectiveness. Visual and audio alerts should be customizable for different staff roles and responsibilities. The system must handle multiple concurrent cases without overwhelming staff, while ensuring nothing falls through the cracks during busy periods.

**Victory Conditions:**
- **Given** new case is created **When** AI completes conversation **Then** case appears on dashboard immediately without refresh
- **Given** emergency case detected **When** flagged as urgent **Then** dashboard shows red alert and plays notification sound
- **Given** staff viewing dashboard **When** new case arrives **Then** case counter updates and new case highlighted

---

### **Story 16: Voice System Performance Monitoring** [16 XP]
**As a** system administrator  
**I want** comprehensive monitoring and analytics  
**So that** I can ensure system reliability and optimize performance

**Expert Insight:**
Comprehensive monitoring is essential for maintaining service quality and identifying improvement opportunities in disability services. From managing technology systems supporting vulnerable populations, I know that performance degradation can have serious real-world consequences when participants can't access help. Speech recognition accuracy below 85% creates frustration and miscommunication, potentially causing participants to abandon calls. Call completion rates indicate system usability and participant satisfaction. Analytics should reveal patterns - peak calling times, common issue types, and seasonal trends that inform staffing and resource allocation. System alerts must distinguish between minor performance variations and critical failures requiring immediate intervention. The monitoring system becomes a quality assurance tool, helping identify training needs and process improvements that enhance participant experience.

**Victory Conditions:**
- **Given** voice calls processed **When** monitoring system **Then** tracks speech accuracy >85%, call completion rates, and average conversation duration
- **Given** multiple performance metrics **When** viewing analytics **Then** shows daily/weekly trends for call volume, after-hours usage, and case priorities
- **Given** system performance issues **When** thresholds exceeded **Then** alerts sent to administrators with specific error details and suggested actions

---

**Total XP Available: 100** 🎯