# Discussion: Practical concerns and blindspots (beyond what's in the paper)

## 👋 Opening

Hi Mas Sabrang & Team,

I've been studying Balungpisah's documentation (whitepaper, Jejak Tapak v1.5, foundation repo) and I'm genuinely excited about the vision. The problem statement in **Section 2** about Indonesia's trust deficit is spot-on, and the three-gate framework in **Section 4** is elegant.

However, as someone who wants this to succeed in practice (not just theory), I have some concerns about issues that seem under-discussed or unaddressed in the current documentation. I don't have all the answers, but I believe these are worth discussing openly before we get too far down the road.

Please take this as discussion-starter, not criticism. I may be missing context or plans that already exist.

---

## 🤖 1. AI SAKSI Trust Gap (Not Addressed in Section 5.1)

**What the paper says:**
- **Section 4.1 (SAKSI):** KB Saksi extracts structured data through conversation
- **Section 5 (Cara Kerja):** AI extracts facts, problems, sentiment, context
- **Section 6 (Peran KB):** AI processes natural language into structured data

**The concern:**
The paper assumes users will trust AI to process their testimony. But is this assumption tested?

**Questions about trust:**
1. Has the team researched Indonesian users' trust in AI systems?
   - In Indonesia, trust in tech/algorithmic systems is not universal
   - Common sentiment: "AI dibikin orang, bisa di-setting," "AI punya bias"

2. What happens when a user challenges AI's extraction?
   - User: "AI salah, ini bukan masalah sebenarnya"
   - User: "AI nggak ngerti local context saya"
   - What's the escalation path?

3. Is there opt-out to talk to human verifier directly?
   - For users who don't trust AI
   - For users who prefer human interaction
   - Or is AI mandatory?

**Why this matters now:**
With 500 reports in 2 months, early adopters are already using AI SAKSI. If they don't trust it, word-of-mouth will be: " sistem ngaco" → adoption stalls.

---

## 💸 2. Inference Cost Sustainability (Not Addressed in Economics)

**What the paper says:**
- **Section 5 (Cara Kerja):** KB SAKSI processes each testimony
- Throughout: AI is core to SAKSI pipeline

**The concern:**
I couldn't find discussion of AI inference costs at scale.

**Rough math (may be wrong):**
- Current: 500 reports / 2 months
- Target scale: ?
- GPT-4 class inference: ~$0.01-0.10 per testimony (depending on length)
- At 10,000 testimonies/month: $100-1,000/month just for AI

**Questions:**
1. What is the planned funding model for AI inference at scale?
2. Have you considered tiered processing to reduce costs?
   - Simple cases: rule-based or smaller models
   - Complex cases: full LLM inference
3. What happens when grant/donation funding runs out?
4. Is there a "cost ceiling" per user?

**Why this matters:**
Unsolved AI inference costs can bankrupt even successful platforms. Better to plan for this now than hit a wall at month 10.

---

## 🧠 3. Hallucination & Liability (Not Addressed in Section 6)

**What the paper says:**
- **Section 6 (Arsitektur Kepercayaan):** Discusses slashing protocol, verifier liability
- **Section 8.2 (Juri Stokastik):** Jury resolves disputes

**The concern:**
Paper discusses human verifier liability. But what about AI liability?

**Scenario:**
```
- AI SAKSI extracts: "There are 5 casualties" (hallucinated)
- Emergency response triggered
- Resources mobilized
- Reality: 0 casualties
- Wasted time, wasted resources, trust damaged
```

**Questions:**
1. Who is liable when AI hallucinates?
   - Platform? AI provider? User who provided testimony?
2. How does system detect and recover from AI errors?
   - Is there "AI mistake" category?
   - What is the correction process?
3. Have you tested AI SAKSI accuracy on real Indonesian testimonies?
   - What is the actual accuracy rate?
   - What is the acceptable error rate?

**Why this matters:**
One high-profile hallucination incident could destroy trust in the entire platform.

---

## 📊 4. Training Data & Bias (Addressed partially in ESCO-ID, but not for AI)

**What the paper says:**
- **Section 8.4 (ESCO-ID):** Recognizes Indonesian cultural knowledge
- **Section 7 (Genesis Layer):** Porting authority from external systems

**The concern:**
Paper discusses cultural bias in human competence. But what about AI training data bias?

**Questions:**
1. Where does AI SAKSI's training data come from?
   - Social media? (mainstream, Jakarta-centric bias?)
   - News data? (mainstream media bias?)
   - Government reports? (bureaucratic bias?)

2. How have you tested for demographic bias?
   - Does AI understand Sundanese as well as Javanese?
   - Does AI understand rural contexts as well as urban?
   - Does AI understand informal language as well as formal?

3. What is the evaluation process for AI fairness?
   - How do you measure bias?
   - What is the threshold for "too biased"?

**Why this matters:**
If AI SAKSI has demographic or geographic bias, the problems it prioritizes will reflect that bias. "What gets measured gets managed" - and if AI measures certain voices more than others, those voices will dominate.

---

## 👥 5. Human Verification Bottleneck (Not Addressed in Section 8.2)

**What the paper says:**
- **Section 8.2 (Juri Stokastik):** 5-7 users selected randomly
- **Section 5.1.1:** Multiple verification types (Type A-D)

**The concern:**
Paper assumes humans are available for verification. But at what scale?

**Math question:**
```
Assumptions:
- AI accuracy: 80% (realistic for novel task)
- 10,000 reports/month
- Human verification needed: 20% = 2,000 reports

Questions:
1. Do we have 2,000 qualified human verifiers?
2. What is the time commitment per verification?
3. What prevents verifier burnout?
4. What if verifiers are concentrated in certain demographics/areas?

Worst case:
- Not enough verifiers in area X
- Reports from area X pile up unverified
- Users think: "Lapor saya diabaikan"
- Churn increases
```

**Have you considered:**
- Verification workload modeling?
- Quality vs. speed tradeoffs?
- Geographic distribution of verifiers?

---

## 🏚️ 6. Digital Divide 2.0 (Not Addressed in Adoption Strategy)

**What the paper says:**
- **Section 9 (Strategi Adopsi):** Three phases
- **Phase 1 (SAKSI):** Collect testimonies
- Implied: App-based interface

**The concern:**
AI makes things more accessible for some, but may create new barriers for others.

**Current barriers (addressed):**
- Smartphone ownership
- Internet access

**New barriers (not addressed):**
- Trust in AI systems (see concern #1)
- Prompt engineering skills (knowing HOW to talk to AI)
- Digital literacy for AI interaction
- Preference for human contact (especially among older adults)

**Questions:**
1. Have you tested with users who are not tech-savvy?
   - Elderly (60+ years)
   - Rural poor
   - Less-educated demographics
2. Is there a "human fallback" for those who can't/won't use AI?
3. What is the drop-off rate when AI interaction begins?
4. Has the team considered alternative entry points?
   - WhatsApp-based reporting?
   - SMS-based?
   - Field agents?

**Why this matters:**
If early adopters are mostly urban, educated, 20-40 years old - that's who the platform will be optimized for. Everyone else becomes "edge case."

---

## 🏛️ 7. Institutional Self-Preservation (Not Addressed in Gov Relations)

**What the paper says:**
- **Section 2.1:** Critique of current bureaucratic system
- **Section 9:** Implies government will adopt if data is good

**The concern:**
Paper assumes government WANTS to listen. But what about bureaucrats who DON'T?

**Perspective from middle management:**
```
Camat receives 100 Balungpisah reports about jembatan rusak
→ Camat's budget: cukup untuk 10 jembatan
→ 90 reports must be ignored
→ Camat thinks: "If I adopt Balungpisah, my incompetence becomes VISIBLE"
→ Camat thinks: "If I ignore Balungpisah, problems stay hidden"
→ Camat's rational self-interest: Block/ignore Balungpisah
```

**Questions:**
1. What is the incentive for middle bureaucrats to adopt?
   - Transparency exposes their weaknesses
   - Data can be used against them
   - Where is the WIIFM (What's In It For Me)?

2. Have you considered institutional resistance tactics?
   - "Biar kami yang proses" (keep it in-house)
   - "Data tidak valid" (challenge methodology)
   - "Bukan kewenangan kami" (jurisdictional buck-passing)

3. What happens when local government feels threatened?
   - Is there defense against sabotage?
   - Is there escalation path when blockers refuse to cooperate?

4. Is there political risk analysis?
   - What if Balungpisah becomes political football?
   - What if one party uses it to attack another?

**Why this matters:**
Good intentions can be stopped by mid-level bureaucrats who have no incentive to cooperate. Paper assumes government is monolithic; real government has factions and self-interest.

---

## ⚖️ 8. Power Dynamics in Small Communities (Not Addressed in Safety)

**What the paper says:**
- **Section 4.1 (SAKSI):** Identity can be protected
- **Section 7.2:** Slashing protocol for bad actors

**The concern:**
Paper acknowledges identity protection. But in small communities, ANONYMITY IS MATHEMATICALLY IMPOSSIBLE.

**Scenario:**
```
- Desa X: 1,000 people
- A reports: "Lurah korupsi dana desa"
- Even if A is "anonymous" in system
- Everyone in village knows: "Apa yang bisa mengetahui hal ini? Ya A saja"
- A is easily identified by context alone

Or worse:
- Verifier B is also from same village
- B must verify A's report against lurah
- B knows: "If I verify, lurah will know it was me"
- B faces social pressure/retaliation
```

**Questions:**
1. How does protection work when everyone knows everyone?
   - Anonymity is porous in small communities
   - Context alone reveals identity

2. What protects verifiers from local pressure?
   - Cross-jurisdiction verification only?
   - What if no outside verifier wants to verify small village issues?

3. Is there a "safe reporting" mechanism?
   - Report outside one's jurisdiction?
   - Report to regional/national (not local)?

**Why this matters:**
If witnesses and verifiers don't feel safe, they won't participate. System fails in areas where it's most needed.

---

## 🔧 9. App-First Distribution (Not Addressed in Go-to-Market)

**What the paper says:**
- Implied: App-based interface
- No discussion of distribution channels

**The concern:**
Building a NEW app has massive adoption friction.

**Where Indonesians ACTUALLY are:**
- WhatsApp: #1 (everyone)
- Instagram: #2 (younger)
- TikTok: #3 (growing)
- Facebook: #4 (older)
- Twitter/X: #5 (niche)
- NEW app: #999 (adoption barrier)

**Questions:**
1. Why require app download at all?
   - Why not WhatsApp bot for reporting?
   - Why not Instagram account for showcasing solved problems?
   - Why not meet people WHERE THEY ARE?

2. What is the go-to-market strategy?
   - Paid ads? (budget?)
   - Influencer partnerships? (who?)
   - NGO partnerships? (which ones?)
   - Grassroots ambassadors? (how selected?)

3. What is the hook for first-time users?
   - Why download Balungpisah instead of opening WhatsApp?
   - What is the value proposition BEFORE network effects kick in?

**Why this matters:**
"Build it and they will come" does NOT work in civic tech. Nextdoor spent millions on hyperlocal marketing. SeeClickFix pivoted to government B2B sales. Brigade is dead.

---

## 🎭 10. Political & Cultural Complexity (Not Addressed in Problem Types)

**What the paper says:**
- **Section 4.2 (TANDANG):** "Siapa pun dapat mengklaim dan menyelesaikan masalah"
- **Section 5.1.1:** Problem types categorized

**The concern:**
Not all problems are created equal. Some are POLITICAL.

**Examples:**
```
Problem A: Jembatan rusak → Technical, solvable
Problem B: Tanah sengketa → Political, complicated
Problem C: Tradisi vs regulasi → Cultural, sensitive
Problem D: Korupsi → Dangerous to report
```

**Questions:**
1. Does system accept ALL problem types?
   - Or are some "too hard" and should be rejected?
   - If rejected, by whom? On what criteria?

2. How to handle power asymmetry?
   - A reports: "Perusahaan tambang tanah saya"
   - Perusahaan has lawyers, money, power
   - A has testimony only
   - Who wins? How?

3. What if cultural practices are reported as "problems"?
   - Molton in masjid: Noise pollution vs. religious tradition?
   - Who decides? Which domain applies?

4. Does system acknowledge LIMITATIONS?
   - "Not everything can be solved through gotong royong"
   - Some problems require courts, politics, revolution
   - Is Balungpisay honest about its scope?

**Why this matters:**
If system tries to solve everything, it will fail at everything. Focus is essential.

---

## 🎯 11. The 8-Month Success Criteria (Not Clearly Defined)

**What the paper says:**
- **Section 9 (Strategi Adopsi):** 3 phases
- Publicly shared goal: 8 months to decide continue

**The concern:**
Success criteria are unclear.

**Questions:**
1. What SPECIFICALLY determines "government listening"?
   - X number of responses?
   - Y number of jurisdictions adopting?
   - Media coverage?
   - Policy changes?

2. What is the minimum viable number?
   - Is 1,000 reports enough? 5,000? 10,000?
   - Is 10 kota/kabupaten enough? 50? 100?
   - Is there a calculated threshold: "Below this number, we fail"?

3. What happens if Month 8 arrives and criteria are partially met?
   - Continue with modifications?
   - Declare success and pivot?
   - Declare failure and sunset?

4. Have you communicated this to the community?
   - Transparency helps us rally toward clear goals
   - Vague goals make it hard to feel ownership

**Why this matters:**
Without clear success criteria, we can't know if we're on track. Month 8 becomes a cliff, not a milestone.

---

## 🎓 12. Genesis Authority (Addressed, but Maybe Optimistic)

**What the paper says:**
- **Section 8.1:** No permanent authority
- **Genesis Layer (Jejak Tapak 7.1):** Genesis nodes, 10-month sunset

**The concern (already noted in paper, but worth reinforcing):**
10-month sunset is LONG for power to entrench.

**Questions:**
1. Have you considered HARD sunset instead of gradual decay?
   - Instant cutoff at month 10
   - Forces Genesis nodes to earn organic reputation faster
   - Prevents "soft capture"

2. What prevents Genesis circular vouching?
   - Genesis A vouches Genesis B
   - Genesis B vouches Genesis A
   - Both become Keystones
   - System effectively oligarchic

3. What is the forced rotation mechanism?
   - Sunset random 20% every 3 months
   - Instead of all at month 10
   - Prevents一次性 transfer of power

**Why this matters:**
Good intentions in design don't always survive implementation. Power tends to concentrate. Safeguards need to be stronger.

---

## 💬 Closing

**I want this to work.**

That's why I'm raising these concerns now, at month 2 with 500 reports, rather than watching from the sidelines at month 8.

**I don't have all the answers.** But I believe:
- These concerns are valid even if solutions exist
- Discussing them openly strengthens the platform
- Community scrutiny only makes Balungpisah better

**I'd love to hear:**
- "We've thought about this and here's our plan"
- "That's a blindspot we hadn't considered"
- "Good question, let's discuss"

**Let's make Balungpisah work in practice, not just on paper.**

Terima kasih Mas Sabrang & team for your work.

Salam,
[Your Name]
Community Contributor
