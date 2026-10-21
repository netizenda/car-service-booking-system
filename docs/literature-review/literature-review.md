# Literature Review

## 1. Introduction

The project **“Design and Development of a Web-Based Car Service Booking and Management System”** combines several software engineering and service-management problems. These include online appointment scheduling, management of limited time slots, customer self-service, booking cancellation and status tracking, vehicle maintenance history, role-based access control, and communication between frontend and backend components.

The purpose of this literature review is to examine existing research relevant to these areas and determine which established approaches can be adapted to the proposed car service system.

The reviewed literature primarily covers the period from 2021 to 2025 in order to reflect recent developments in digital scheduling and web-based information systems. One earlier systematic review by Zhao et al. (2017) is retained as a foundational publication because it provides a broad analysis of web-based appointment systems.

A significant proportion of the mature appointment-scheduling literature originates from healthcare. The proposed project does not assume that healthcare and automotive services are identical domains. However, both involve a common scheduling problem: a user requests a service, the service consumes a limited amount of time and resources, an available slot must be selected, and the appointment may later be confirmed, cancelled, rescheduled, or completed.

The review therefore focuses on transferable principles while also considering publications specifically related to automotive maintenance and workshop management.

---

## 2. Online Appointment and Self-Service Booking Systems

Online appointment scheduling has been studied as an alternative to traditional scheduling through phone calls, physical visits, or direct communication with administrative staff.

Manarte (2024) conducted a scoping review of recent research on digital scheduling systems. The review indicates that online scheduling can increase accessibility and reduce dependence on traditional appointment channels. However, the study also emphasizes that successful adoption depends on the characteristics of users, organizations, and the way the technology is implemented.

This is important for the proposed car service system because replacing a telephone-based process with a website alone does not guarantee improvement. The booking workflow must reflect the actual needs of customers and service employees.

Kammrath Betancor et al. (2024) evaluated an online appointment scheduling system in an operational organization. Their study compared appointments created online with appointments created through traditional channels. The research demonstrates that online scheduling can operate alongside existing methods and can improve accessibility and administrative efficiency.

For the proposed project, this supports a self-service model in which customers can independently choose an available service date and time without requiring an administrator to manually create every appointment.

A large-scale case study by Woodcock, Sen, and Weiner (2022) provides further evidence for automated self-scheduling. The study analyzed almost two million appointments across more than thirty sites. Adoption of self-scheduling increased during the study period, while self-scheduled appointments showed different cancellation and missed-appointment patterns compared with traditionally scheduled appointments.

Although this research was conducted in healthcare, the important transferable finding is that users are able to manage appointments independently through a digital system at considerable scale.

An earlier systematic review by Zhao et al. (2017) examined web-based appointment systems and reported several recurring potential advantages, including reduced administrative workload, reduced waiting, improved access, and increased user satisfaction. The review also identified barriers involving flexibility, security, implementation cost, and differences in users' technological experience.

Together, these studies suggest that self-service booking is a reasonable foundation for the proposed system. However, the interface should remain simple, available time slots should be understandable, and administrative users should retain the ability to manage bookings when necessary.

### Implication for the project

The Customer role should be able to:

- view available services;
- view available appointment dates and times;
- select a vehicle;
- create a booking without calling the service center;
- view existing bookings;
- cancel eligible future bookings.

The Administrator role should still have access to booking management because fully automated scheduling may not cover every operational situation.

---

## 3. Time-Slot Management and Scheduling Constraints

A booking system requires more than a form containing a date and time. Appointment availability must reflect resource constraints.

Benjaafar, Chen, Wang, and Yan (2023) study appointment scheduling under service-level and waiting-time constraints. Their work demonstrates that appointment spacing is connected to service capacity and waiting-time objectives.

The mathematical methods proposed in such research are more advanced than required for the initial diploma project. Nevertheless, the underlying principle is directly relevant: appointments cannot be treated as independent records if they compete for limited resources.

Yan et al. (2022) investigate dynamic appointment scheduling with multiple service providers and customer preferences. Their model considers limited provider capacity, appointment time selection, uncertainty, and customer choice.

A car service environment has a comparable resource structure:

- physicians correspond conceptually to mechanics;
- treatment time corresponds to service duration;
- clinical resources correspond to service bays or lifts;
- patients correspond to customers requesting service.

The project does not need to reproduce the stochastic optimization model described by Yan et al. Instead, a simpler rule-based scheduling mechanism is appropriate for the initial implementation.

Ala and Chen (2022) reviewed more than 150 scientific publications related to appointment scheduling. They identify several major approaches, including mathematical optimization, simulation, Markov models, queuing approaches, and artificial intelligence.

This literature demonstrates that scheduling can become a highly complex optimization problem. However, introducing such complexity would significantly increase the scope of the diploma project without being necessary to demonstrate its primary objective.

### Implication for the project

The initial implementation should use deterministic slot-based scheduling.

Each service should have an estimated duration. Before a customer confirms a booking, the backend should verify whether the requested interval is available.

A simplified model may follow the rule:

`requested start time + service duration = occupied interval`

The system should prevent overlapping bookings that require the same limited resource.

More sophisticated optimization of mechanic assignments, lift utilization, or predicted repair duration can remain future work.

---

## 4. Booking Availability and Customer Choice

The presentation of available appointment slots can influence customer decisions.

Kaluza, Voigt, and Paetz (2024) investigated customer choice behavior in online appointment systems through multiple behavioral experiments. Their findings indicate that booking availability can affect provider selection and customer perceptions.

This suggests that the booking interface should not simply provide one automatically assigned appointment. Giving customers visibility of several realistic available alternatives provides greater scheduling flexibility.

The finding also creates an important design consideration. Artificially limiting displayed availability without operational justification may negatively affect the user experience.

### Implication for the project

The booking process should follow a transparent sequence:

1. Select vehicle.
2. Select service.
3. Select date.
4. Display available time slots.
5. Select preferred slot.
6. Add an optional comment.
7. Confirm booking.

Unavailable slots should not be presented as selectable options.

---

## 5. No-Shows, Cancellation, Rescheduling, and Reminders

Unused appointment capacity can negatively affect service organizations.

Mazaheri Habibi et al. (2024) conducted a systematic review of open-access scheduling and appointment no-shows. Sixteen studies were included, and ten reported a significant decrease in no-show rates. The authors also emphasize that successful scheduling systems should be designed around actual user and provider requirements.

These findings should not be interpreted as proof that the same reduction would automatically occur in an automotive workshop. However, they demonstrate that appointment-management design can affect attendance behavior.

Werner et al. (2023) conducted a systematic review and meta-analysis of interventions intended to reduce appointment non-attendance. Their final analysis included 61 studies, with reminders being the most frequently evaluated intervention. The review found meaningful evidence supporting appointment reminders, although effectiveness differed by context and delivery method.

Mohammed Selim et al. (2024) examined consumer preferences for appointment reminders using a discrete choice experiment. Respondents showed a preference for text-based reminders and particularly valued the ability to cancel or modify an appointment.

The interviews conducted for the current diploma project produced a similar requirement: customers requested reminders and easier cancellation or rescheduling.

### Implication for the project

Cancellation should be included in the core booking functionality.

Rescheduling is also relevant but may be implemented after the primary booking workflow is stable.

Automated SMS, WhatsApp, email, or push reminders represent useful extensions. However, external messaging integrations introduce additional services and configuration and therefore should not be required for the minimum viable diploma implementation.

---

## 6. Alignment Between Technology and Real Organizational Processes

A technically functional system can still fail if it does not correspond to the actual workflow of an organization.

Motulsky et al. (2023) evaluated a large e-booking system using stakeholder interviews, system logs, and a population survey. Despite positive attitudes from users, adoption was limited because the system did not align sufficiently with the variety of organizational and professional practices.

This is an important finding for the proposed system.

The project includes three different roles:

- Customer;
- Mechanic;
- Administrator.

These users interact with the same booking but require different information and actions.

For example, the customer primarily needs services, prices, available times, booking status, and history. A mechanic needs assigned jobs, vehicle information, customer comments, and status controls. An administrator needs scheduling information, booking management, user management, and service configuration.

Therefore, using a single identical interface for all three roles would not properly reflect their workflows.

### Implication for the project

The system should use role-specific interfaces and permissions.

Customer workflow:

`Vehicle → Service → Date → Time Slot → Booking → Status → History`

Mechanic workflow:

`Assigned Job → Vehicle Details → Service Information → In Progress → Completed → Comment`

Administrator workflow:

`Schedule → Booking Management → Assignment → Service Management → User Management → Statistics`

This structure is also supported by the user interviews conducted during the Evidence of Relevance stage.

---

## 7. Role-Based Access Control

Authentication alone is not sufficient for a multi-role web application.

Le et al. (2022) studied role-based access-control policies in web applications. Their evaluation demonstrated that access-control implementations can contain inconsistencies and security problems even when applications appear functional.

The study reinforces the importance of defining intended permissions explicitly and validating whether the backend implements those permissions correctly.

For the proposed project, authorization must not depend only on hiding interface elements in React.

For example, removing the “Manage Users” button from a Customer interface does not provide sufficient security if the same user can still manually send an HTTP request to an administrative endpoint.

### Implication for the project

Authorization must be enforced on the Go backend.

The proposed access model is:

### Customer

Can:

- manage own vehicles;
- view services;
- create own bookings;
- view own bookings;
- cancel eligible own bookings;
- view service history belonging to own vehicles.

Cannot:

- manage other users;
- change service prices;
- access another customer's vehicles;
- assign mechanics;
- arbitrarily modify booking statuses.

### Mechanic

Can:

- view assigned jobs;
- view relevant vehicle and job information;
- change permitted job statuses;
- add mechanic comments.

Cannot:

- manage users;
- change global service configuration;
- access unrelated customer data without operational need.

### Administrator

Can:

- manage services;
- manage bookings;
- manage users and mechanics;
- manage schedules;
- assign mechanics;
- access administrative statistics.

JWT authentication can identify the authenticated user, while middleware and backend authorization rules can enforce role permissions.

---

## 8. REST-Based Web Application Architecture

The project proposes communication between the React frontend and Go backend through a REST API.

Lawi, Panggabean, and Yoshida (2021) experimentally compared REST and GraphQL using a management information system. Their results demonstrate that neither approach is universally superior. REST showed advantages in response time and throughput in the evaluated workload, while GraphQL offered advantages in some resource-utilization measures.

The value of this study for the project is not that it proves REST is always better. Instead, it demonstrates that API architecture should be selected according to application requirements.

The proposed system has relatively predictable entities and operations:

- users;
- cars;
- services;
- bookings;
- authentication;
- service history.

These resources naturally map to REST endpoints.

Examples include:

`POST /auth/login`

`GET /services`

`GET /cars`

`POST /cars`

`GET /bookings`

`POST /bookings`

`PATCH /bookings/{id}/status`

For this type of CRUD-oriented system, REST provides a straightforward design that is easy to test with Postman and implement using React and Go/Gin.

### Implication for the project

REST is appropriate for the initial implementation because the API requirements are predictable and resource-oriented.

GraphQL remains a reasonable alternative but does not provide a sufficiently important advantage for the current project to justify the additional architectural complexity.

A more detailed REST/GraphQL comparison will be provided separately in the Technology Comparison section of the diploma project.

---

## 9. Automotive Workshop and Vehicle Maintenance Systems

General scheduling research needs to be supplemented with domain-specific evidence.

Jondya et al. (2025) developed a web-based application focused on vehicle maintenance and automotive workshop management. The system included maintenance records, service-history functionality, vehicle-condition information, and workshop management features.

This publication is directly relevant because it demonstrates that digital maintenance history and centralized workshop information are applicable to automotive-service environments.

Razzaq and Dewi (2025) developed a web-based workshop management information system in response to manual transaction and data-recording processes. Their work highlights problems such as delayed recordkeeping, potential data loss, and fragmented information.

These findings resemble issues identified in the user interviews for the current project, where the administrator reported using spreadsheets, paper records, phone calls, and WhatsApp communication.

Lahwani, Ariati, and Faradillah (2025) describe a web-based vehicle maintenance information system intended to replace manual maintenance documentation. Their system includes vehicle data, maintenance scheduling, and service-history functionality.

The context is operational fleet maintenance rather than customer-facing workshop booking, so it cannot be transferred directly to the proposed application. Nevertheless, it provides further support for centralized vehicle information and maintenance history.

### Implication for the project

The automotive literature supports the following entities and functions:

- persistent vehicle profiles;
- maintenance records;
- service history;
- maintenance scheduling;
- centralized workshop information.

The proposed project extends these concepts by integrating them with customer self-service booking and separate Customer, Mechanic, and Administrator roles.

---

## 10. Vehicle Service History

Vehicle service history is useful to both customers and service providers.

The automotive publications reviewed above consistently demonstrate the value of storing maintenance information digitally rather than relying only on paper documentation.

For the proposed system, service history does not require a completely independent business process.

A completed booking already contains the essential information required for a historical record:

- vehicle;
- service;
- date;
- mechanic;
- mileage at the time of service;
- final status;
- mechanic comments.

Therefore, completed bookings can form the foundation of vehicle service history.

### Implication for the project

A vehicle's service history can be generated from bookings whose status is `Completed`.

This avoids unnecessary duplication while maintaining traceability between the original appointment and the completed service.

---

## 11. Identified Limitations in Existing Research

The reviewed literature provides useful evidence but also has limitations.

First, much of the mature scheduling literature comes from healthcare. Healthcare appointment systems and automotive workshops share scheduling concepts but have different operational constraints. For example, vehicle repair durations may be affected by diagnostics, spare-parts availability, and unexpected mechanical problems.

Therefore, results from healthcare scheduling cannot be transferred directly without adaptation.

Second, several scheduling studies use mathematical optimization or stochastic models. These approaches are academically valuable but may introduce unnecessary complexity for the first version of a web-based diploma project.

Third, some automotive publications focus primarily on workshop administration, maintenance records, or fleet management rather than a complete customer-facing booking process.

Fourth, reminder and no-show research indicates benefits from notifications, but external notification services increase implementation scope.

Finally, successful technical implementation does not automatically ensure successful adoption. Motulsky et al. (2023) demonstrate that alignment with organizational workflow is a major factor in real-world usage.

These limitations support an incremental design approach focused first on the core business process.

---

## 12. Identified Research and Implementation Gap

The literature demonstrates that many individual elements of the proposed system already exist and have been studied.

Research exists on:

- online appointment scheduling;
- self-service booking;
- scheduling under capacity constraints;
- cancellation and reminders;
- role-based access control;
- REST-based information systems;
- digital vehicle maintenance history;
- workshop management systems.

Therefore, this diploma project does **not** claim that online booking or workshop management is globally novel.

The practical gap addressed by the project is the integration of these established concepts into a coherent car-service workflow suitable for a small or medium-sized automotive service organization.

The proposed workflow is:

`Customer`

`↓`

`Vehicle`

`↓`

`Service`

`↓`

`Available Date and Time Slot`

`↓`

`Booking`

`↓`

`Administrator / Mechanic Processing`

`↓`

`Pending → Confirmed → In Progress → Completed`

`↓`

`Vehicle Service History`

This integrated workflow provides a realistic Software Engineering problem involving user interfaces, backend development, database relationships, authorization, business logic, API integration, scheduling, and testing.

---

## 13. Implications for System Requirements

Based on the literature analysis, several requirements of the proposed system receive support from existing research.

### R1 — Self-Service Booking

Customers should be able to create appointments without requiring direct communication with an administrator.

Supported by:

- Manarte (2024);
- Kammrath Betancor et al. (2024);
- Woodcock et al. (2022);
- Zhao et al. (2017).

### R2 — Available Time Slots

Customers should select appointments only from available time slots.

Supported by:

- Kaluza et al. (2024);
- Benjaafar et al. (2023);
- Yan et al. (2022).

### R3 — Service Duration

Available booking intervals should consider the expected duration of a service.

Supported by scheduling literature including:

- Benjaafar et al. (2023);
- Yan et al. (2022);
- Ala and Chen (2022).

### R4 — Booking Conflict Prevention

The system should prevent incompatible overlapping bookings.

Supported by the general capacity constraints identified in appointment-scheduling research.

### R5 — Cancellation and Rescheduling

Customers should be able to manage future appointments.

Supported by:

- Mohammed Selim et al. (2024);
- Woodcock et al. (2022).

### R6 — Appointment Reminders

Automated reminders are a useful potential extension.

Supported by:

- Werner et al. (2023);
- Mohammed Selim et al. (2024);
- Mazaheri Habibi et al. (2024).

### R7 — Role-Based Authorization

Customer, Mechanic, and Administrator permissions should be enforced on the backend.

Supported by:

- Le et al. (2022).

### R8 — Vehicle Service History

Completed vehicle maintenance activities should remain accessible as historical records.

Supported by:

- Jondya et al. (2025);
- Lahwani et al. (2025).

### R9 — Centralized Workshop Management

Booking and service information should be stored centrally rather than across disconnected spreadsheets, messages, and paper documents.

Supported by:

- Razzaq and Dewi (2025);
- Jondya et al. (2025);
- Lahwani et al. (2025).

---

## 14. Conclusion

The reviewed literature supports the main concepts underlying the proposed Car Service Booking and Management System.

Recent research on online appointment systems indicates that self-service booking can improve accessibility and reduce dependence on manual communication. Scheduling research demonstrates that appointment availability should consider limited capacity, service duration, and provider availability rather than treating each booking independently.

Research on cancellation, reminders, and no-shows demonstrates the importance of allowing users to manage existing appointments. Studies of real e-booking implementations also show that successful systems must align with organizational workflows.

Software engineering research on role-based access control supports explicit backend authorization for different user types, while REST-related research indicates that REST remains a suitable architecture for predictable resource-oriented information systems.

Finally, automotive-domain publications support the digital management of vehicle information, maintenance records, service history, and workshop processes.

Based on this analysis, the initial project should prioritize a manageable core architecture consisting of:

- Customer, Mechanic, and Administrator roles;
- JWT authentication and role-based authorization;
- vehicle management;
- service catalogue;
- service prices and estimated duration;
- available time-slot selection;
- booking creation and cancellation;
- booking conflict prevention;
- booking status management;
- mechanic job management;
- administrator scheduling and management;
- vehicle service history;
- REST API communication;
- PostgreSQL data storage.

Advanced optimization, external notification integrations, online payments, multimedia attachments, and advanced business analytics should remain optional or future extensions until the core workflow is implemented and tested.

---

# References

1. Manarte, L. (2024). Technology and Access to Healthcare with Different Scheduling Systems: A Scoping Review. *Healthcare Informatics Research, 30*(3), 194–205. DOI: 10.4258/hir.2024.30.3.194.

2. Kammrath Betancor, P., Jordan, J., Boehringer, D., Lüchtenberg, C., Lambeck, M., Ketterer, M. C., Reinhard, T., & Reich, M. (2024). Efficient patient care in the digital age: Online appointment scheduling in an ophthalmology practice. *DIGITAL HEALTH, 10*. DOI: 10.1177/20552076241287083.

3. Mazaheri Habibi, M. R., Mohammad Abadi, F., Tabesh, H., Vakili-Arki, H., Abu-Hanna, A., Ghaddaripouri, K., & Eslami, S. (2024). Evaluation of no-show rate in outpatient clinics with open access scheduling system: A systematic review. *Health Science Reports, 7*(7), e2160. DOI: 10.1002/hsr2.2160.

4. Mohammed Selim, S., Senanayake, S., McPhail, S. M., Carter, H. E., Naicker, S., & Kularatna, S. (2024). Consumer Preferences for a Healthcare Appointment Reminder in Australia: A Discrete Choice Experiment. *The Patient, 17*, 537–550. DOI: 10.1007/s40271-024-00692-9.

5. Kaluza, I., Voigt, G., & Paetz, F. (2024). Empirical studies on the impact of booking status on customers' choice behavior in online appointment systems. *Journal of Business Economics, 94*, 187–224. DOI: 10.1007/s11573-023-01161-9.

6. Motulsky, A., Bosson-Rieutort, D., Usher, S., David, G., Moreault, M.-P., Gagnon, M.-P., Schuster, T., & Sicotte, C. (2023). Evaluation of a national e-booking system for medical consultation in primary care in a universal health system. *Health Policy, 131*, 104759. DOI: 10.1016/j.healthpol.2023.104759.

7. Werner, K., Alsuhaibani, S. A., Alsukait, R. F., Alshehri, R., Herbst, C. H., Alhajji, M., & Lin, T. K. (2023). Behavioural economic interventions to reduce health care appointment non-attendance: A systematic review and meta-analysis. *BMC Health Services Research, 23*, 1136. DOI: 10.1186/s12913-023-10059-9.

8. Benjaafar, S., Chen, D., Wang, R., & Yan, Z. (2023). Appointment Scheduling Under a Service-Level Constraint. *Manufacturing & Service Operations Management, 25*(1), 70–87. DOI: 10.1287/msom.2022.1159.

9. Woodcock, E., Sen, A., & Weiner, J. (2022). Automated patient self-scheduling: Case study. *Journal of the American Medical Informatics Association, 29*(9), 1637–1641. DOI: 10.1093/jamia/ocac087.

10. Yan, C., Huang, G. G. Q., Kuo, Y.-H., & Tang, J. (2022). Dynamic appointment scheduling for outpatient clinics with multiple physicians and patient choice. *Journal of Management Science and Engineering, 7*(1), 19–35. DOI: 10.1016/j.jmse.2021.02.002.

11. Ala, A., & Chen, F. (2022). Appointment Scheduling Problem in Complexity Systems of the Healthcare Services: A Comprehensive Review. *Journal of Healthcare Engineering, 2022*, 5819813. DOI: 10.1155/2022/5819813.

12. Le, H. T., Shar, L. K., Bianculli, D., Briand, L. C., & Nguyen, C. D. (2022). Automated reverse engineering of role-based access control policies of web applications. *Journal of Systems and Software, 184*, 111109. DOI: 10.1016/j.jss.2021.111109.

13. Lawi, A., Panggabean, B. L. E., & Yoshida, T. (2021). Evaluating GraphQL and REST API Services Performance in a Massive and Intensive Accessible Information System. *Computers, 10*(11), 138. DOI: 10.3390/computers10110138.

14. Jondya, A. G., Trisanto, A. D., Yukadifa, A. D., & Noval, M. R. (2025). Pengembangan Aplikasi Berbasis Web untuk Perawatan Mobil dan Pengelolaan Bengkel dengan Metode Prototipe. *Jurnal Sistem Informasi (JUSIN), 6*(1), 37–50. DOI: 10.32546/jusin.v6i1.3121.

15. Razzaq, N. S., & Dewi, R. S. (2025). Design of a Web Based Workshop Management Information System Application Using Rapid Application Development Techniques. *Journal of Digital Business and Innovation Management, 4*(2). DOI: 10.26740/jdbim.v4i2.71678.

16. Lahwani, M. I., Ariati, N., & Faradillah. (2025). Sistem Informasi Pemeliharaan Kendaraan Operasional Untuk Meningkatkan Kegiatan Operasional di PT Sinar Anugrah Nusantara Mas. *JuSiTik: Jurnal Sistem dan Teknologi Informasi Komunikasi, 9*(1), 90–100. DOI: 10.32524/jusitik.v9i1.1728.

17. Zhao, P., Yoo, I., Lavoie, J., Lavoie, B. J., & Simoes, E. (2017). Web-Based Medical Appointment Systems: A Systematic Review. *Journal of Medical Internet Research, 19*(4), e134. DOI: 10.2196/jmir.6747.