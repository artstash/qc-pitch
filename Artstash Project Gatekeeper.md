# **Product Vision & Process Brief: Project "Gatekeeper"**

**Initiative:** Human-in-the-Loop AI Quality Control (QC Agent)

## **1\. Executive Summary**

Project "Gatekeeper" transforms Artstash’s AI from a passive metadata tagger into an active, iterative participant in the creative versioning loop. Historically, Digital Asset Management (DAM) platforms have functioned as static repositories—digital filing cabinets where files sit idle until a human searches for them. Gatekeeper changes this paradigm. By deploying an Automated QC Agent to act as the first line of defense, we are building a continuous, dynamic workflow where AI and human reviewers seamlessly collaborate in real-time.

We will initially "dogfood" this system internally with Artstash Creative Services to automate their objective Quality Assurance (QA) passes. This internal beta phase is critical; it allows us to rapidly iterate on edge cases, fine-tune the AI's visual recognition capabilities, and perfect the UI before a broader market release. The ultimate goal is to offload repetitive, fatiguing rule-checking to the AI, allowing human reviewers to focus entirely on subjective, high-level creative direction. Once proven, this architecture will scale into a premium SaaS offering, fundamentally changing how creative agencies and gaming studios manage asset at scale.

## **2\. The Problem: The Revision Bottleneck**

Currently, the creative review process across the industry is highly manual, fragmented, and vulnerable to human error. A standard asset typically travels through a convoluted chain: Designer ➔ Project Manager (PM) ➔ Account Manager (AM) ➔ PM ➔ Designer ➔ Client ➔ Designer. Every handoff introduces friction, communication delays, and the potential for lost context.

**The Exponential Math of Manual QC:**

* 1 Main Idea × 3 Sizes × 2 Lengths × 3 Revisions × 2 People \= 36 Reviews per Concept

This math represents only a best-case scenario for a single, simple concept. When variations, platform-specific exports (e.g., TikTok vs. YouTube dimensions), and global localizations are added, this results in hundreds of cumulative manual revisions per concept.

**The Hidden Costs of the Bottleneck:**

* **Cognitive Fatigue:** Human reviewers suffer from "error blindness" when checking dozens of nearly identical videos for minor technical flaws. Missing a trademark symbol or a safe-zone violation becomes inevitable.  
* **Margin Erosion:** Highly paid creative directors and project managers spend hours acting as glorified proofreaders, wasting budget on tasks that do not add creative value.  
* **Workflow Disruption:** Designers are pulled out of deep creative flow states to fix minor, objective errors (like shifting a logo 10 pixels), causing frustration and stalling overall production momentum.

This bottleneck slows down production, exhausts the creative team, delays client delivery, and ultimately limits the volume of work a studio can handle.

## **3\. The Solution: A Collaborative AI-Human System**

We are breaking this vicious cycle by dividing the QC workload based on core strengths, recognizing that AI and humans excel at fundamentally different tasks.

* **The AI Agent (Objective Verification):** The AI handles strict rule adherence. It possesses endless patience and does not suffer from fatigue. It checks for exact font usage, hex-code color matching, logo placement, platform-specific safe-zones, spelling errors, and brand-safety violations (e.g., identifying "blood," "weapons," or inappropriate gestures).  
* **The Human Reviewer (Subjective Direction):** Humans handle creative context and empathy. They focus on narrative pacing, emotional resonance, comedic timing, lighting nuances, and determining if the asset achieves the overarching campaign strategy.

By having the AI autonomously flag the objective errors instantly upon upload, the human reviewer only sees assets that truly need nuanced direction. We are not replacing the human creative eye; we are clearing the brush out of its way, ensuring that human attention is spent exclusively on tasks that require human ingenuity.

## **4\. User Roles & The Handoff Experience**

A successful loop relies on frictionless handoffs and clear expectations between the following actors. Each role experiences a distinct workflow tailored to their needs:

**🎨 Production Team (Designer)**

* **Focus:** Asset creation, deep work, and rapid iteration.  
* **Experience:** The workflow is designed to be invisible to them until they are needed. They do not manage the platform or fill out manual status reports. They simply upload V1s (or sync automatically via Git/Google Drive). When an asset fails QC, they receive an automated Slack ping containing a deep-link. They click the link, open Artstash to see exact timestamped error pins directly on the canvas, fix the issues in their native software (After Effects, Premiere, Maya), and sync V2. The platform handles all version stacking in the background.

**📋 Project Manager / Account Manager (PM/AM)**

* **Focus:** Workflow logic, rule-setting, timeline enforcement, and client handoffs.  
* **Experience:** They act as the architects of the project. They set the initial Brand Guidelines, Technical Specs, and reference materials that the AI will use as its "Rulebook." Their day-to-day shifts from chasing designers to overseeing the macro-level queue. They monitor the high-level reporting dashboards, intervene only when bottlenecks occur, and officially share the polished, "Passed" assets to external clients via secure, white-labeled Artstash links.

**👨‍🎨 Internal QC Reviewer (Creative Services / Creative Director)**

* **Focus:** Nuanced, subjective creative direction and quality elevation.  
* **Experience:** Their dashboard is pre-filtered. They log into a "Needs Review" queue that has already been scrubbed of basic technical errors by the AI. When they open an asset, they see the AI's automated findings. They validate those findings, and use Artstash's timeline drawing/commenting tools to add human context. For example, the AI might flag *"Lighting is 20% darker than brand standard"*, and the reviewer can add *"The AI is right, please bump up the exposure, but keep the shadows cool to match the mood."*

**🤖 The AI QC Agent**

* **Focus:** Autonomous, repetitive verification, and closing the feedback loop.  
* **Experience:** It acts as a tireless, invisible assistant working in the background. It scans incoming assets against the PM's guidelines, marks thumbnails as Pass/Fail, and generates simple timestamped reports. Crucially, the AI acts as the loop-closer: it verifies if the designer actually implemented the human reviewer's feedback on subsequent versions, reading natural language comments and checking the new visual output to ensure compliance before bothering the human reviewer again.

## **5\. The Step-by-Step Interactive QC Loop**

**Step 1: Client Setup & Guidelines**

The PM initiates the project in Artstash. They input the client's Brand Guidelines by uploading brand books, providing exact font files, defining color palettes, and setting technical requirements (e.g., "1080x1920, max 15 seconds"). They also input Tone Guidance (e.g., "Family friendly, no alcohol"). This aggregated data becomes the foundational "Rulebook" for the AI Agent.

**Step 2: V1 Production Upload**

The Production team finishes V1 of a single asset or a massive batch of 100+ videos. They upload the files directly into Artstash or allow the system to auto-sync via existing folder structures. As long as correct naming conventions are used, Artstash automatically routes the files to the correct project space.

**Step 3: The AI Gatekeeper (Pre-Check)**

Before a human is ever notified, the AI Agent intercepts the upload and scans the asset against the PM's Rulebook.

* If it spots a violation, it drops a visual annotation pin directly on the canvas or timeline. It generates a simple, actionable report (e.g., *"Blood visible at 0:12s"* or *"Missing App Store buttons on end card"*).  
* The asset is tagged as Failed and enters the human review queue. If it passes flawlessly, it skips directly to the 'For Review' queue, saving an entire human touchpoint.

**Step 4: Internal QC (Human Context)**

The Human QC Reviewer opens the failed asset. They immediately see the AI's pins on the timeline. They validate the AI's findings, ensuring no false positives, and add their own subjective feedback using comments and visual annotations. They hit submit, which consolidates all AI-generated technical fixes and human-generated creative tweaks into one unified, prioritized to-do list for the designer.

**Step 5: Notification & Iteration**

Artstash fires a targeted, automated Slack or email notification to the specific Production team member. The designer views the exact timestamps of the errors—without having to scrub through the video themselves. They fix the issues in their native software and upload V2. Artstash automatically stacks this as a new version, preserving the entire history of comments and AI flags for accountability.

**Step 6: AI Re-evaluation (The Verification Pass)**

*This is the core innovation of the workflow.* When V2 is uploaded, the AI Agent wakes up again. It does not just check the baseline rules; it reads the human comments left on V1 (e.g., *"make background warmer and shift logo left"*). It scans V2 to verify if those specific subjective requests were completed alongside the objective rules. If the changes are verified, the AI autonomously resolves the comments, clears the error pins, and marks the asset as Passed.

**Step 7: Client Handoff & Final Review**

Assets marked as Passed (cleared of all internal AI and human flags) are gathered by the PM. The status is updated to "For Review," and a secure, clean Artstash presentation link is generated. The external client receives a pristine viewing experience, completely insulated from the messy, internal revision loops that occurred to get the asset to that state.

## **6\. Telemetry & Reporting**

To monitor the health of this new automated pipeline, and to prove the value of the platform, the system will generate two distinct reporting views. These dashboards transform subjective project management feelings into hard, actionable data based on how frequently the QC Agent is used:

### **A. Ongoing / End-of-Week Report (Internal)**

Designed for internal usage where assets are sent to QC continuously as work comes in. This dashboard helps internal team leads manage capacity and identify training opportunities.

* **Metrics:** Total number of assets passed through the QC Agent this week, average time saved per asset, and total active projects.  
* **Pass/Fail Rate:** Percentage of assets that Passed vs. Failed on their first attempt, tracking team efficiency over time.  
* **Error Drill-down & Trend Analysis:** A clickable list of the top reasons for failing the QC check (e.g., "Spelling mistake \- 45 occurrences", "Logo placement wrong \- 12 occurrences"). Clicking the reason links directly to the flagged assets. If "Wrong Font" is constantly the top failure, management knows they need to update the team's local template files.

### **B. Batch Upload Report (External/Vendor)**

Designed for external vendor management, where hundreds of completed videos or localized assets are run through the QC Agent in massive, simultaneous batches. This is crucial for studios outsourcing large volumes of work.

* **Metrics:** Total number of assets processed in the specific batch upload and the exact duration of the AI processing time compared to estimated human review time.  
* **Pass/Fail Rate:** Percentage of the batch that Passed vs. Failed, serving as a direct quality score for the vendor.  
* **Batch Error Drill-down (Vendor Scoring):** A clickable list of failure reasons specific to that batch. This allows PMs to quickly identify recurring issues from specific third-party vendors. If Vendor A consistently fails safe-zone checks while Vendor B passes 99% of the time, this data can be used directly during contract renegotiations or future project routing.