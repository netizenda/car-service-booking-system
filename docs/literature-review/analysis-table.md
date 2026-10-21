# Literature Analysis Table

## Purpose

This document provides a structured analysis of the publications selected for the literature review of the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The analysis focuses on the research method, major findings, limitations, and relevance of each publication to the proposed system.

> **Note:** The “Limitations” column includes both limitations explicitly reported by the authors and clearly identified scope limitations when transferring findings from another domain, such as healthcare, to the automotive service context.

---

## 1. Core Scientific Literature

| ID | Publication / Topic | Research Method | Key Findings | Limitations / Caution | Relevance to Our Project |
|---|---|---|---|---|---|
| **S1** | **Manarte (2024)** — Online scheduling systems | Scoping review following PRISMA-ScR. Searches were conducted in Scopus and Web of Science. 23 recent peer-reviewed studies were included. | Online scheduling can improve access to services and reduce dependence on traditional scheduling channels. The review also shows that outcomes depend on implementation context and user characteristics. | Only Scopus and Web of Science were searched; English-language recent publications were selected; the screening process was conducted by one author. The reviewed domain is healthcare. | Supports the general decision to provide web-based self-service appointment booking. Also shows that the system must consider usability and real user needs rather than simply digitizing the existing process. |
| **S2** | **Kammrath Betancor et al. (2024)** — Online appointment scheduling in practice | Prospective single-center observational study conducted over 12 weeks in an ophthalmology practice, comparing online and traditional appointment booking. | Online appointment scheduling can improve accessibility, administrative efficiency, and resource utilization. It demonstrates that real organizations can operate online and offline scheduling simultaneously. | Single medical specialty and single organization. Limited demographic information was collected and no formal sample-size calculation was performed. Findings cannot automatically be generalized to other domains. | Supports online time-slot booking and demonstrates the practical value of allowing users to schedule appointments without contacting staff directly. |
| **S3** | **Mazaheri Habibi et al. (2024)** — Open-access scheduling and no-shows | Systematic review using PubMed, Scopus, Web of Science and Google Scholar. 16 studies were included from more than 23,000 initially identified records. | 10 of the 16 included studies reported a significant reduction in no-show rates. Successful implementation depended on user needs, stakeholder participation and appropriate system design. | Authors acknowledge that some relevant studies may have been missed. The characteristics of the scheduling systems were not sufficiently described in many reviewed studies. Most studies were healthcare-specific. | Supports the need for requirements analysis, booking management, cancellation functionality and possible appointment reminders. It also supports designing scheduling around actual user and service-provider needs. |
| **S4** | **Mohammed Selim et al. (2024)** — Appointment reminders | Discrete choice experiment with 361 Australian respondents examining reminder modality, timing, content and interactivity. | Respondents preferred automated text reminders, reminders close to the appointment, and especially the ability to cancel or modify an appointment. Interactivity was an important characteristic. | Only four reminder attributes were studied. The experiment used hypothetical choices and an English-speaking online panel, which may exclude some user groups. Real-world effectiveness was not directly evaluated. | Supports future reminder functionality and provides evidence for allowing users to cancel or reschedule appointments through the system. |
| **S5** | **Kaluza, Voigt & Paetz (2024)** — Customer choice in online booking systems | Three online behavioral experiments / discrete-choice studies examining service-provider selection under different numbers of available appointment slots. | Booking availability affects customer choices, but the relationship is not simple. Customers value scheduling flexibility, while limited availability may also influence perceptions of provider quality. | Experiments used hypothetical choices rather than actual transactions. Findings varied across service categories and participants. | Supports displaying real available slots while avoiding unnecessary artificial restrictions. It also shows that time-slot presentation can influence customer behavior. |
| **S6** | **Motulsky et al. (2023)** — National e-booking system | Mixed-method evaluation combining 40 stakeholder interviews, system audit logs and a population survey of 2,003 respondents. | Users appreciated e-booking, but system adoption was low when the technology was poorly aligned with different organizational and professional workflows. | The research concerns a large public healthcare system in Québec, so organizational conditions differ from a private car service. | Very important for our project: the booking system must fit how administrators and mechanics actually work. This supports the separate Customer, Mechanic and Admin workflows identified during our interviews. |
| **S7** | **Werner et al. (2023)** — Reducing appointment non-attendance | Systematic review and meta-analysis. 61 studies meeting quality criteria were analyzed. Interventions included SMS, telephone and other reminders. | Reminder systems generally provide evidence of improved attendance, although individual study results differ. Many studies reported positive effects of SMS reminders. | Results were mixed across interventions. The authors identify possible publication bias and acknowledge that their search terminology may have excluded relevant interventions. | Supports considering automated appointment reminders as an optional extension and shows that reminders should be evaluated rather than assumed to always work. |
| **S8** | **Benjaafar et al. (2023)** — Appointment scheduling under service constraints | Mathematical and queueing-based scheduling model using sequential scheduling and majorization theory. | Appointment times should account for service capacity and waiting-time constraints. The minimum spacing between appointments changes according to the scheduling conditions. | Analytical model uses controlled assumptions and is not an empirical automotive study. The full mathematical optimization approach would be unnecessarily complex for the initial diploma implementation. | Provides theoretical support for preventing overlapping bookings and considering service duration when generating available time slots. |
| **S9** | **Woodcock, Sen & Weiner (2022)** — Automated self-scheduling | Large observational case study analyzing 1,995,909 appointments across more than 30 practice sites between 2019 and 2021. | Self-scheduling adoption increased over time. Self-scheduled appointments had lower missed-appointment rates and higher cancellation rates, showing that users actively manage appointments through digital tools. | The study concerns one academic healthcare organization. Technology changed during the study and the COVID-19 period could influence results. The study did not directly collect user perspectives. | Strong evidence for customer self-service booking and online cancellation. Demonstrates that self-scheduling can work at substantial scale. |
| **S10** | **Yan et al. (2022)** — Dynamic scheduling with multiple service providers | Mathematical stochastic scheduling model with multiple physicians, customer preferences, time-slot choices and no-show probability; evaluated through computational experiments. | Scheduling decisions should consider both limited provider capacity and customer preferences. Appointment availability and allocation influence system performance. | Uses healthcare-specific assumptions, stochastic overbooking and a profit-based mathematical model that would be too complex for the initial project. | Relevant to future scheduling logic involving multiple mechanics. For the initial version, it supports a simpler rule-based approach using service duration and mechanic/time-slot availability. |
| **S11** | **Ala & Chen (2022)** — Appointment scheduling approaches | Comprehensive literature review covering more than 150 scientific publications on appointment scheduling. | Appointment scheduling has been addressed with simulation, mathematical optimization, Markov models, AI and other methods. Scheduling aims to balance waiting time, resource utilization and service quality. | The review focuses on complex healthcare environments. Many reviewed optimization techniques are beyond the requirements and scope of this diploma project. | Helps justify why our first implementation uses understandable rule-based available time slots rather than complex AI or optimization algorithms. More advanced optimization can be future work. |
| **S12** | **Le et al. (2022)** — Role-Based Access Control in web applications | Development and empirical evaluation of a semi-automated RBAC policy reverse-engineering and validation framework on three open-source and one proprietary web application. | Correctly implemented access control is important for protecting resources. Their approach recovered implemented policies with high accuracy and identified numerous access-control problems. | Focuses primarily on reverse-engineering and validating existing RBAC implementations rather than designing a new application's authorization architecture. Evaluation involved four applications. | Supports clearly defining and testing permissions for **Customer, Mechanic and Admin** instead of relying only on UI-level restrictions. Authorization must also be enforced by the backend. |
| **S13** | **Lawi, Panggabean & Yoshida (2021)** — REST vs GraphQL | Experimental performance evaluation of REST and GraphQL on a real management information system, measuring response time, throughput, CPU and memory usage. | REST performed better in response time and throughput in the tested environment, while GraphQL provided better CPU and memory efficiency. The preferred architecture depends on application access patterns. | Results are based on one information system and workload. Performance results should not be treated as universally valid for every application. | Supports REST as a reasonable architecture for a relatively conventional CRUD and booking system with predictable resources such as users, cars, services and bookings. |

---

## 2. Automotive Domain Literature

| ID | Publication / Topic | Research Method | Key Findings | Limitations / Caution | Relevance to Our Project |
|---|---|---|---|---|---|
| **S14** | **Jondya et al. (2025)** — Web-based car maintenance and workshop management | Prototype-based software development. Data were gathered using questionnaires, interviews and comparison with similar applications, followed by design, implementation and evaluation. | The developed web application supported vehicle maintenance records, service history, vehicle-condition monitoring and workshop operations. Evaluation indicated that users could better track maintenance and workshops could manage repair activities digitally. | Context is primarily a specific Indonesian automotive-service environment. Results from one developed system should not automatically be generalized to all workshops. | Directly supports vehicle profiles, digital service history and centralized communication between car owners and workshops. This is one of the most domain-relevant sources for our project. |
| **S15** | **Razzaq & Dewi (2025)** — Web-based workshop management information system | Qualitative analysis combined with Rapid Application Development (RAD), including requirements analysis, interface design, implementation and User Acceptance Testing. | The developed system improved integrated management of services, mechanics, transactions and workshop data compared with manual recordkeeping. | The research focused on one workshop/business context. Reported UAT results were based on a limited implementation context and should not be generalized broadly. | Supports replacing fragmented manual processes with a centralized workshop management application and validates the usefulness of admin-side management functionality. |
| **S16** | **Lahwani, Ariati & Faradillah (2025)** — Vehicle maintenance information system | Web-based information system developed using the Waterfall SDLC for operational vehicle maintenance. | The system centralized vehicle data, maintenance schedules and service history and was reported to improve accuracy and administrative efficiency. | Focuses on an organization's operational vehicle fleet rather than customer-facing car-service booking. | Supports centralized vehicle information, maintenance history and scheduling, but customer booking functionality remains a gap addressed by our project. |

---

## 3. Foundational Literature

| ID | Publication / Topic | Research Method | Key Findings | Limitations / Caution | Relevance to Our Project |
|---|---|---|---|---|---|
| **S17** | **Zhao et al. (2017)** — Web-based appointment systems | Systematic review. 36 articles describing 21 web-based appointment systems were analyzed. | Many implementations reported reduced no-show rates, lower staff workload, shorter waiting times and improved satisfaction. Reported barriers included cost, flexibility, security/integrity concerns and differences in users' technology experience. | Publication is older than the five-year core literature period and focuses on healthcare. The search was primarily based on MEDLINE/PubMed. | Used as a foundational source demonstrating the established benefits and barriers of web-based appointment scheduling. It complements, rather than replaces, the newer 2021–2025 literature. |

---

## 4. Cross-Source Findings

Analysis of the reviewed literature reveals several recurring themes.

### 4.1 Self-Service Booking

Multiple studies support the use of online self-scheduling systems. Self-service booking can reduce dependence on phone-based communication and allow users to interact with appointment systems directly.

**Project implication:**  
Customers should be able to select a car, service, date and available time slot without contacting an administrator.

---

### 4.2 Scheduling Must Respect Resource Constraints

Scheduling literature demonstrates that appointment systems must account for limited service capacity, service duration and provider availability.

**Project implication:**  
The system should not allow two incompatible appointments to occupy the same resource/time period. Available slots should be calculated using service duration and schedule availability.

---

### 4.3 Cancellation and Rescheduling Are Important

Several publications show that digital users expect to actively manage existing appointments rather than only create them.

**Project implication:**  
Customers should be able to cancel eligible future bookings. Rescheduling should be considered part of the main or extended booking functionality.

---

### 4.4 Reminders May Reduce No-Shows

Systematic reviews generally support reminders, particularly electronic reminders, although their effectiveness differs across contexts.

**Project implication:**  
SMS, WhatsApp or push reminders are useful potential extensions. They are not essential to the first implementation and should only be implemented after the core booking workflow is stable.

---

### 4.5 System Design Must Match Real Workflows

Research on large e-booking deployments demonstrates that technically functional systems may still have poor adoption if they do not correspond to the actual processes of users and organizations.

**Project implication:**  
The Customer, Mechanic and Administrator interfaces should be based on the needs identified during the project's user interviews.

---

### 4.6 Role-Based Authorization Is Necessary

Research on access control in web applications demonstrates the importance of accurately enforcing permissions.

**Project implication:**  
The backend must enforce permissions for Customer, Mechanic and Admin roles. Hiding interface elements on the frontend alone is not sufficient.

---

### 4.7 Automotive Systems Benefit from Centralized Records

Automotive-domain studies report benefits from digitizing vehicle information, service history and workshop management.

**Project implication:**  
Each customer vehicle should have a persistent profile and completed services should form a digital service history.

---

## 5. Identified Research and Implementation Gap

Existing research provides strong evidence for online scheduling, self-service appointment management, service-history information systems and role-based access control.

However, much of the recent scheduling literature focuses on healthcare, while automotive-domain publications tend to concentrate on maintenance records or general workshop management.

The proposed project combines these concepts into one integrated web application focused on a car-service workflow:

**Customer → Vehicle → Service → Available Time Slot → Booking → Mechanic Processing → Completion → Service History**

The project does not claim that this combination is globally unique. Instead, the literature analysis is used to identify established approaches and adapt them to the requirements of the proposed car service booking and management system.