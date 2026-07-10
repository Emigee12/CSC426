1.0 Introduction
1.1 Objective
This specification details the functional and technical criteria for the Incident Reporting 
Platform (IRP). The system serves as a lightweight web utility built to streamline communication 
and data sharing between the university network and its neighboring localities, specifically 
Ayegunle, Etioro, Iwaro, and Akungba.
Questionnaire link: 
https://docs.google.com/forms/d/e/1FAIpQLSf1ZFHpXluuustGWho0IfMdx_PnXCEJkPExpJD9211
9yiM4LQ/viewform
Short link: https://tinyurl.com/emigeequestionnaire
1.1 System Boundary
The IRP is engineered as a responsive Single Page Application (SPA) focused on logging 
localized events and publishing them instantly to a secure public dashboard. To facilitate 
rapid prototyping and testing, data persistence relies entirely on client-side browser 
memory (localStorage), ensuring user anonymity, minimal infrastructure overhead, and 
instantaneous data rendering.
2.0 General Architecture & Users
2.1 Deployment Environment
The platform executes exclusively as a front-end web application running natively inside 
modern desktop and mobile browsers, including Apple Safari, Google Chrome, Microsoft Edge, 
and Mozilla Firefox.
2.2 Target User Personas
• Contributors: Campus students and local town residents requiring a streamlined, 
minimal-data interface to log local incidents.
• Monitors / Stakeholders: Institutional administrative staff or local community 
representatives tasked with tracking live updates on the dashboard.
3.0 System Requirements
3.1 Functional Requirements (FR)
• FR-01: Identity Obfuscation Providing a name during submission is strictly optional. 
Fields left unpopulated must be recorded and rendered under the alias "Anonymous".
• FR-02: Geographic Tagging Submissions require selecting a predefined location 
parameter. Valid options are limited to: Akungba, Iwaro, Etioro, Ayegunle, AAUA 
Students (General), or Other.
• FR-03: Classification & Severity Users must categorize the incident type (e.g., Welfare, 
Infrastructure, Security) and select an urgency designation (Low, Medium, or High).
• FR-04: Payload Compilation Upon submission, the interface must package all user 
inputs alongside an automatic browser-generated timestamp into a clean
3.2 Report Rendering Module
• FR-05: Local Data Fetching The client-side script must actively monitor and read the 
stored JSON records from the browser’s local storage cache.
• FR-06: Reverse-Timeline Layout The main monitoring dashboard must arrange and 
display incoming incidents dynamically, keeping the most recent entries at the top of 
the feed.
• FR-07: Zero-Data Condition When the local database contains no records, the UI must 
display a welcoming placeholder notification: "No reports yet. Be the first to submit."
• FR-08: Color-Coded Urgency Badges The UI must dynamically apply CSS-driven colored 
labels to indicate report severity: Red for High priority, Gold/Yellow for Medium priority, 
and Green for Low priority.
4.0 Non-Functional Requirements (NFR)
4.1 Performance Requirements
• NFR-01: UI Responsiveness & Rendering Latency Because the application avoids serverside database roundtrips, form processing and feed updates must complete within 1 
second using native DOM optimization.
4.2 Security Requirements
• NFR-02: Input Sanitization (XSS Mitigation) To block malicious scripting injections, all 
text fields must pass through an explicit escapeHtml filtering utility. The characters &, <, 
>, ", and ' must be fully
4.3 Usability Requirements
• NFR-03: Adaptable Grid Layout The interface must leverage a flexible CSS Grid design 
pattern. For display viewports narrow than 760px, the layout must seamlessly collapse 
from a multi-column view into a vertically stacked presentation optimized for mobile 
use
