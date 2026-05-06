# Architectural/Design Considerations

## Requirements

### Business Requirements (Business Goals and Objectives)

- Improve retention and learning: Enhance students’ learning experience in the gaps between in-person classes.

- Strict data privacy: Ensure that user data never leaves the local network to third-party providers (avoid the public cloud for sensitive data).

- Cost predictability: Avoid high costs and pay only for what you use with regard to managed GenAI services (SaaS/APIs).

### Functional Requirements (Specific System Capabilities)

The new tools must integrate seamlessly with the existing Learning Portal and Learning Record Store.

The system must execute 5 distinct workflows:

- Pronunciation practice.

- Sentence construction.

- Fast/accurate typing practice.

- Text-based adventure immersion game.

- Tool for extracting vocabulary from movies.

Also the system must be able to query a database (RAG - Vector Database) to base its responses on the core vocabulary (“Core 2000 Words”) and official materials.

### Non-functional Requirements (Performance, Scalability, Security)

- Using technical strategies to reduce the monthly bill for cost optimization.

- Implement a prompt cache (caching of common responses in the cloud) to avoid unnecessary calls to the model.

- Implement input/output guardrails at the API level to filter out malicious traffic, and use containers or isolated environments (sandboxing) for code or agent execution.

### Tooling: GenAI vs. Predictive ML

For the architecture of the learning suite, we will strongly prioritize the use of GenAI Foundation Models over custom predictive machine learning. This decision is based on the following:

- **Zero Training Investment:** By using GenAI, we avoid the massive investment of time and resources required to train predictive models from scratch. The “model owner” (e.g., IBM with Granite) has already done this heavy lifting.

- **Deployment Speed (Low Initial Investment):** GenAI allows us to prototype and launch the 5 applications (especially the immersive game and the sentence builder) quickly, as it does not require the prior collection of massive amounts of labeled data or deep expertise in data science to get started.

- **Flexibility for Multiple Tasks:** While a predictive ML model would require long-term, task-specific development for a single task, a GenAI model can simultaneously handle text generation, grammatical evaluation, and vocabulary extraction using the same endpoint.
