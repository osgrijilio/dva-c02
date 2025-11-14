# DevOps

DevOps is the combination of cultural philosophies, practices, and tools that increases an organization’s ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes. This speed enables organizations to better serve their customers and compete more effectively in the market.

DevOps emphasizes better collaboration and efficiencies so teams can innovate faster and deliver higher value to businesses and customers.

DevOps is a combination of:

- Cultural philosophies for removing barriers and sharing end-to-end responsibility
- Processes developed for speed and quality, that streamline the way people work
- Tools that align with processes and automate repeatable tasks, making the release process more efficient and the application more reliable

## Problems of traditional development practices

- __Waterfall development projects__ are slow, not iterative, resistant to change, and have long release cycles. Some reasons for this include:

  - Requirements are rigid, set at project start, and will likely not change.

  - Development phases are siloed, each starting after the previous phase has ended. Each phase is supported by highly specialized teams.

  - Hand offs from one phase to the other are long, often requiring teams to switch tools and spend time clarifying incomplete or ambiguous information.

  - Testing and security come after implementation, making corrective actions responsive and expensive.

- __Monolithic applications__ are hard to update and deploy because they:

    Are developed and deployed as a unit, so when changes are made, the entire application must be redeployed
    Have tightly coupled functionality, so if the application is large enough, maintenance becomes an issue because developers have a hard time understanding the entire application
    Are implemented using a single development stack, so changing technology is difficult and costly

- __Manual processes__ throughout the application lifecycle are slow, inconsistent, and error-prone. For example, manually setting and configuring the infrastructure is time-consuming. Manually repeating this process is no guarantee that a step will not be missed. Another example is telling the developers to make sure their code is thoroughly tested before pushing it. Even with the best intentions, this manual process is slow, and does not preclude someone from forgetting a test or two.

- __Siloed teams__. Teams supporting the software development lifecycle have traditionally been siloed. Specialized in their skill set, teams such as business, development, quality assurance, specialists, maintenance, and operations, have been separated from each other and require scheduled and rigid hand-offs. Even though these teams have a common goal of delivering and supporting the application, they also have their own priorities, tooling, and processes. It is difficult to achieve efficiencies when project members are reporting to different units and aimed for different targets.

## Benefits of DevOps

- 106x Faster commit to deploy
- 208x More frequent deployments
- 7x Lower change failure rate
- 2604x Faster time to recover

- __Agility__: enabled by development practices, monitoring tools, controls at delivery, small updates

- __Rapid delivery__: core priciples of DevOps are continuous integration and continuous delivery, rapid feedback loop and continuous monitoring. Automation supports Agile.

- __Reliability__: CI/CD can test every change is functional and safe. Monitoring tools to provid feedback.

- __Scale__: Tools are applied to one or many instances. The tools automated manual tasks and can scale.

- __Improved collaboration__: Build more effective teams under a DevOps cultural model, which emphasizes values such as ownership and accountability. Developers and operations teams collaborate closely, share many responsibilities, and combine their workflows. This reduces innefficiencies and saves time. For example, writing code that takes into account the environment in which it is run, reduces handover periods between developers and operations.

- __Security__: The DevOps model uses automatic enforcement rules, fine-grained controls, and configuration management techniques that help to move quickly while retaining leveratge and ensuring compliance policies.
    For example, you can describe and then monitor enforcement at scale, using infrastructure as code and policy as code.

Be aware of:

- Bottlenecks cause by less resources:
  - When creating specifications
  - When reviewing

- Culture, that follows process but permits
  - Wrong test description, that allow
  - Minimal tests
  - Minimal ratio of change

## DevOps methodology

### Objectives

- Discuss the challenges involved in adopting a DevOps culture and describe possible solutions.
- Identify automation opportunities in developing and maintaining applications.
- Describe the benefits of decoupling services or components.
- Define observability and describe its importance to DevOps.
- Explain why security is important in every phase of the pipeline.
- Explain how AWS integrates with third-party tools for automated code delivery and deployments

A shift to DevOps requires creating and nurturing a DevOps culture, which is a culture of transparency, effective and seamless collaboration, and common goals.

There are seven core principles that can help you achieve a DevOps culture.

1. __Create a highly collaborative environment__

    DevOps brings together development and operations to break down silos, align goals, and deliver on common objectives. The whole team (development, testing, security, operations, and others) has end-to-end ownership for the software they release. They work together to optimize the productivity of developers and the reliability of operations. Teams learn from each other's experiences, listen to concerns and perspectives, and streamline their processes to achieve the required results.

    This increased visibility enables processes to be unified and continuously improved to deliver on business goals. The collaboration also creates a high-trust culture that values the efforts of each team member, and transfers knowledge and best practices across teams and the organization.

1. __Automate when possible__

    With DevOps, repeatable tasks are automated, enabling teams to focus on innovation. Automation provides the means to rapid development, testing, and deployment. Identify automation opportunities at every phase, such as code integrations, reviews, testing, security, deployments, and monitoring, using the right tools and services.

    For example, infrastructure-as-code (IaC) can be used for predefined or approved environments, and versioned so that repeatable and consistent environments are built. You can also define regulatory checks and incorporate them in test that continuously run as part of your release pipeline.

1. __Focus on customer needs__

    A customer first mindset is a key factor in driving development. For example, with feedback loops DevOps teams stay in-touch with their customer and develop software that meets the customer needs. With a microservices architecture, they are able to quickly switch direction and align their efforts to those needs. 

    Streamlined processes and automation deliver requested updates faster and keep customer satisfaction high. Monitoring helps teams determine the success of their application and continuously align their customer focused efforts.

1. __Develop small and release often__

    Applications are no longer being developed as one monolithic system with rigid development, testing, and deployment practices. Application architectures are designed with smaller, loosely coupled components. Overarching policies (such as backward compatibility, or change management) are in place and provide governance to development efforts. Teams are organized to match the required system architecture. They have a sense of ownership for their efforts. 

    Adopting modern development practices, such as small and frequent code releases, gives teams the agility they need to be responsive to customer needs and business objectives.

1. __Include security at every phase__

    To support continuous delivery, security must be iterative, incremental, automated, and in every phase of the application lifecycle, instead of something that is done before a release. Educate the development and operations teams to embed security into each step of the application lifecycle. This way, you can identify and resolve potential vulnerabilities before they become major issues and are more expensive to fix. 

    For example, you can include security testing to scan for hard-coded access keys, or usage of restricted ports.

1. __Continuously experiment and learn__

    Inquiry, innovation, learning, and mentoring are encouraged and incorporated into DevOps processes. Teams are innovative and their progress is monitored. With innovation, failure will happen. Leadership accepts failure and teams are encouraged to see failure as a learning opportunity. 

    For example, teams use DevOps tools to spin-up environments on demand, enabling them to experiment and innovate, perhaps on the use of new technology to support a customer requirement.

1. __Continuously improve__

    Thoughtful metrics help teams monitor their progress, evaluate their processes and tools, and work toward common goals and continuous improvement. For example, teams strive to improve development performance measures such as throughput.

    They also strive to increase stability and reduce the mean time to restore service. Using the right monitoring tools, you can set application benchmarks for usual behaviors, and continuously monitor for variations.

