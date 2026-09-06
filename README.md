# <p align="center"> **SPITFW**</p>
### <p align="center"> **From Instruments to Cockpit.** </p>
### <p align="center"> **From Cockpit to Framework.** </p>
#### <p align="center"> Project Presentation for ETHOS / FrSky Developers and Technical Collaborators </p>
### 1. THE PROJECT IN BRIEF
   SpitFW originated as a personal experiment to explore how far ETHOS and Lua could be pushed to transform a FrSky transmitter display into something more than a standard telemetry screen: a scale-inspired cockpit matching the aircraft being flown.
 
   The initial proving ground was the Spitfire. Starting from simple independent analog instruments, the project progressively evolved into a unified dashboard, then into a full cockpit, and ultimately into a structured, modular framework featuring a central coordinator layer, reusable libraries, and configurable modules.


   Today, the project raises a broader question: Is it possible to build a framework on ETHOS capable of managing configurable, realistic cockpits that can adapt to different aircraft types?
 
<img width="1500" height="688" alt="presentazione 1500" src="https://github.com/user-attachments/assets/3b1a5874-e8e0-4e21-8979-9874b84297c8" />

## <p align="center"> FULL SPITFIRE COCKPIT </p>
### 2. WHERE WE STARTED

The project did not start as a framework. It began with individual instruments, each developed and tested independently:

⦁	Airspeed Indicator (ASI)

⦁	Vertical Speed Indicator (VSI)

⦁	Altimeter (ALT)

⦁	Turn & Slip Indicator

⦁	AH6A Attitude Indicator

⦁	Tachometer (RPM)

⦁	Fuel Gauge and other aircraft systems

Initially, each instrument represented a self-contained graphical and functional experiment consisting of bitmaps, dial background, needle, data source, and update logic.

<img width="1500" height="688" alt="costruzione strumenti" src="https://github.com/user-attachments/assets/56966bf9-b316-403e-ac2e-61a5796b804e" /> 

## <p align="center">  INDIVIDUAL INSTRUMENTS </p>
### 3. WHEN INSTRUMENTS BECAME A DASHBOARD

The next step was bringing these separate instruments together into a single layout. This gave birth to the dashboard concept: moving away from isolated widgets toward a cohesive instrument panel.

However, this evolution revealed technical challenges that do not exist when running a single standalone widget: positioning alignment, layer overlaps, simultaneous rendering updates, bitmap asset management, available RAM, and processing performance.

One approach tested was using larger static background images while allowing only the needles to render over them, aiming to reduce RAM overhead. The results showed that resolving resource constraints required a more fundamental architectural solution.

<img width="1500" height="688" alt="dashboard" src="https://github.com/user-attachments/assets/8cd442a1-6d6b-4a96-8ff2-d4cfcb2ff880" />
 
## <p align="center"> FIRST DASHBOARD </p>
### 4. THE LEAP: FROM DASHBOARD TO COCKPIT

At a certain point, the objective shifted. Displaying telemetry data was no longer enough; the goal became recreating the visual immersion of a real scale cockpit.

The Spitfire was chosen as the primary subject because its flight panel is instantly recognizable and iconic for scale model aviators.

The core paradigm is simple: instead of starting from available telemetry data and deciding how to display it, you start from the aircraft and its cockpit layout, then adapt the telemetry, gauges, graphics, and controls to reproduce that specific cockpit.

<img width="2048" height="1152" alt="cockpit volo" src="https://github.com/user-attachments/assets/f01356ed-ed65-42a5-baa0-e001ea9dd99c" />
 

## <p align="center"> COCKPIT FLIGHT EXPERIENCE </p>
### 5. THE TECHNICAL CHALLENGE: MEMORY MANAGEMENT

The most difficult aspect of the project was not simply writing Lua code. The real challenge was understanding ETHOS system behavior when a graphically intensive project scales up and must manage multiple visual assets simultaneously.

Typical issues encountered included:

⦁	Bitmaps failing to render or load

⦁	System warnings such as "malloc refused" or "malloc not allowed"

⦁	Instruments operating correctly individually, but failing when executed together

⦁	Inconsistencies between cold boot initialization and subsequent reloads

⦁	Memory consumption spikes during initial asset allocation

To mitigate these issues, several optimization strategies were implemented: dynamic caching and controlled release of bitmaps, conditional asset loading based on state, minimizing lcd.invalidate() calls, moving heavy calculations outside the paint() execution loop, pre-caching bitmap dimensions, and implementing smoothing algorithms to reduce needle jitter.


### 6. THE MONOLITHIC PHASE AND THE NEED FOR STRUCTURAL CHANGE

As additional instruments were added, the codebase initially entered a monolithic phase: a single large script continuously incorporating more rendering and system logic. While functional as a temporary baseline, it rapidly became difficult to maintain, debug, and expand.

It became clear that a separation of responsibilities was necessary.

<img width="1376" height="768" alt="DIAGRAMMA 1" src="https://github.com/user-attachments/assets/e2463fbb-51e4-414b-894c-96d6c606e5ba" />
 
## <p align="center"> DIAGRAM 1 - FROM INDIVIDUAL INSTRUMENTS TO A SPITFIRE DASHBOARD </p>

### 7. THE BIRTH OF SPITFW

Out of this requirement, SpitFW was established as an organized architecture structured around three main pillars:

COORDINATION LAYER (REGIA), MODULES, and LIBRARIES.

⦁	THE COORDINATION LAYER (REGIA): Handles and coordinates the overall widget lifecycle execution: create(), read(), write(), wakeup(), paint(), configure(), and event().

⦁	THE MODULES: Every gauge or system operates as an independent module (e.g., ASI, AH6A, RPM, Fuel Gauge, Gear, Flaps, Magnetos).

⦁	THE LIBRARIES: Shared functions are centralized into dedicated library files, handling bitmap management, data source bindings, file I/O, element layout positioning, debugging, and shared utilities.

<img width="1376" height="768" alt="DIAGRAMMA 2" src="https://github.com/user-attachments/assets/972bfe96-80ab-440a-8002-aaa75e234851" />

## <p align="center"> DIAGRAM 2 - SPITFW ARCHITECTURE </p>

### 8. WHY MODULAR ARCHITECTURE MATTERS

Modular design is not just about keeping code organized. It enables a fully configurable cockpit ecosystem where individual instruments can be enabled, disabled, or repositioned without modifying or rewriting the core project logic.

### 9. THE FLIGHT / ENGINE EXPERIMENT

To further investigate ETHOS memory boundaries, a technical experiment was conducted by splitting the system into two separate scripts: one dedicated to primary flight instruments, and the other to engine monitoring systems.

This separation was not intended as the final architectural goal, but rather as a diagnostic test to determine whether memory constraints stemmed from script architecture or the total volume of simultaneous asset allocations required by ETHOS.

Testing confirmed that while individual sub-systems maintain a low memory footprint, simultaneous asset loading during initialization remains the primary allocation bottleneck.

### 10. THE ORIGINAL VISION: A SINGLE UNIFIED COORDINATOR

The FLIGHT / ENGINE split remains a diagnostic lab test, not the ultimate philosophy. The primary aspiration continues to be a single, unified architecture efficient enough to drive a complete, fully detailed cockpit through a single coordinator layer.

### 11. BEYOND THE SPITFIRE

Perhaps the most compelling aspect of SpitFW is that it is not strictly limited to a Spitfire instrument panel. The Spitfire serves as the initial proof-of-concept for a broader, reusable design philosophy.

 <img width="1376" height="768" alt="DIAGRAMMA 3" src="https://github.com/user-attachments/assets/19d492df-00c1-4e78-90c6-1517ab7ea42f" />

## <p align="center"> DIAGRAM 3 - FUTURE VISION: COCKPIT FRAMEWORK </p>

### 12. COCKPIT VS. TOOLS / SYSTEM

Throughout development, a clear conceptual distinction emerged between two functional domains: COCKPIT and TOOLS/SYSTEM.

⦁	COCKPIT DOMAIN: Aircraft-specific gauges, cockpit panels, scale cockpit reproductions, and dedicated flight indicators.

⦁	TOOLS / SYSTEM DOMAIN: Utilities, configuration menus, resource management, and general reusable background services.

In this second domain, studying the organizational structure of mature projects such as WingFlight offers valuable architectural inspiration for tool management, without copying code or structure.

<img width="1376" height="768" alt="DIAGRAMMA 4" src="https://github.com/user-attachments/assets/8e6e1b24-9b1e-426c-9e35-23f502c49557" />
 
## <p align="center"> DIAGRAM 4 - FRAMEWORK ECOSYSTEM: COCKPIT vs TOOLS/SYSTEM </p>

### 13. WHY THIS DIFFERENCE MATTERS

Standard telemetry dashboards and widgets already exist for displaying flight telemetry data. The objective of SpitFW is fundamentally different: not merely presenting data points, but translating telemetry data into an authentic scale aircraft cockpit experience.

A conventional dashboard starts with available telemetry data. This project starts with the aircraft.

### 14. WHY SEEK COMMUNITY COLLABORATION

The project has reached a stage where its core components are fully functional: instruments, modules, shared libraries, configuration structures, and cockpit views.

However, a key technical question remains: What is the most efficient, system-compliant method for managing Lua memory allocation and graphical bitmap assets in complex ETHOS projects?

The goal of seeking community feedback is not to ask anyone to rewrite the codebase, but to gain deeper insights into system internals and refine the framework architecture.

### 15. A PERSONAL, NON-COMMERCIAL PROJECT

SpitFW was born purely out of a passion for radio-controlled scale modeling, historic aviation, the Spitfire, and technical software experimentation.

The project is currently not public, not for commercial reasons, but to preserve its original identity, logic, and core philosophy.Having invested substantial effort into designing its core logic and structure, the goal is to protect the project's coherence and prevent its original concept from being fragmented or distorted.

This does not mean keeping the project closed. On the contrary, it means sharing it with the right technical collaborators in a structured and meaningful way.

### 16. OPENNESS TO COLLABORATION

Should this project prove interesting to ETHOS core developers, FrSky software teams, or qualified technical contributors, the complete framework codebase can be made available privately for technical evaluation.

There is full openness to seeing this concept evolve and grow over time. The author's only hope is to remain involved and continue using and following future developments that may arise from this original concept.

### 17. CONCLUSION

SpitFW started from a single instrument. Then came additional gauges, followed by a dashboard, then a cockpit, a monolithic script, and eventually the necessity to separate concerns into modules, libraries, and a central coordinator.

The ultimate question remains: Is it possible to build a framework capable of transforming an ETHOS radio display into a configurable, realistic scale cockpit adaptable to multiple aircraft?

### SPITFW

From Instruments to Cockpit.<br>
From Cockpit to Framework.

And perhaps, from one airplane to many.

https://github.com/FrSkyRC/ETHOS-Feedback-Community/discussions/6254
