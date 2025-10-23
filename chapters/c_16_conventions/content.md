# Conventions and Processes

My conventions.

## Naming conventions

Name things and tag'em.

Use this name format: __*X(7)-TYPE-DDD[-Y(10)]*__

where:

- __*XXXXXXX*__ application name. might be less digits but no more than 7.

- __*TYPE*__ is a type, like acl, sg. No more than 5 letters.

- __*DDD*__ stands for decimal digits (0-9). Do not write down initial 0s, i.e. 2 is ok, but 02 or 002 are wrong.

- __*-YYYYYYYYYY*__ is an optional function name, as you would use it in the tag.

Examples:

    demo1-acl-1
    demo1-acl-2
    demo1-sg-1
    demo1-key-1
    demo2-acl-11
    demo1-s3-2
    demo1-s3-3-photos
    demo1-s3-3-resumes

At all times we use DNS compatible names. No spaces, no underscores.

## Tags

Recommendeg tags:

- app-name: x(7). For example, demo01.

- app-function: X(10). A concept inside your application

- budget-id: X(10). An identifier for budgeting.

- env-type:
  - dev
  - sit
  - crp
  - uat
  - prd

## Test processes and Environment types

Some clients might do with less than 5 enviroments, so we will adjust to their practice.

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
