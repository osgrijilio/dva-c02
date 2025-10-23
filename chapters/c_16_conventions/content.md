# Conventions and Processes

My conventions.

## Human Naming conventions

Provide a human readable name and tags.

Format for humans: "XXXXXX TYP DDD"

  XXXXXXX application name. might be less digits but no more than 7.

  D stands for decimal digits  (0-9). Skip typing 0.

  demo1 acl 1
  demo1 acl 2
  demo1 sg 1
  demo1 key 1
  demo2 acl 11

Tags

- app-name: demo01

- budget-id: xxxxxxx

- env-type:
  - dev
  - sit (System Integration Testing). An environment where code from different developers is integrated and tested together. This allows teams to check the interactions between modules)
  - crp (Conference Room Pilot)
  - uat (UAT is the final testing step in the "deploy" phase where real users validate the system against business requirements before going live).
  - prd

## Test processes and Environment types

|Feature | System Integration Testing (SIT) | Conference Room Pilot (CRP) | User Acceptance Testing (UAT)
|-|-|-|-
|Primary Goal | Verify that integrated system components work together according to technical specifications. | Validate and refine end-to-end business processes in a controlled environment. | Obtain final user sign-off by confirming the system meets business requirements and is ready for real-world use.
|When it Occurs | After unit testing is completed and all system components are integrated. | Early in the implementation during the design or build phase, with multiple sessions possible. | After all modifications and bug fixes from previous testing are addressed, just before go-live.
|Who Performs It | Development and QA teams. | Key stakeholders and subject matter experts from the business. | End-users and business process owners.
|Pace and Focus | Methodical testing focused on technical integrity, data flow, and control flow. | Slower and more collaborative, focusing on the end-to-end business process flow. | Faster-paced, with a broader group of users validating the overall business flow.
|Environment Used | Dedicated testing environment. | Staging environment, to be as close to the final system as possible. | Staging environment, replicating the production environment.
|Data Used | Test data created by the development or testing team. | A sample of client data. | The full, production-like client dataset.
|What's Found | Integration issues between modules, data flow errors, and other technical problems. | Missing functional requirements, process inefficiencies, and design flaws. | Last-minute, high-priority "gotchas" or show-stopper bugs.
|Outcome | Approval to move to the next phase, often user acceptance testing. | Refined business processes and a stable configuration for UAT. | A final go/no-go decision and sign-off for deployment to production.
