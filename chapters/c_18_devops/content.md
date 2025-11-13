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