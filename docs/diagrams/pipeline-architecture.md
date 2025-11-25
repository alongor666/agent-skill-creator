# Pipeline Architecture Diagrams

## Simple Pipeline (2-3 Stages)

```mermaid
graph LR
    A[Data Processing Pipeline] --> B[Stage 1:<br/>Data Ingestion]
    B --> C[Stage 2:<br/>Transformation]
    C --> D[Stage 3:<br/>Analysis]

    B --> B1[Raw Data<br/>dados_crudos.json]
    C --> C1[Clean Data<br/>dados_limpos.json]
    D --> D1[Insights<br/>insights.json]

    style A fill:#667eea
    style B fill:#764ba2
    style C fill:#f093fb
    style D fill:#4facfe
```

## Complex Pipeline (Research Workflow)

```mermaid
graph TB
    A[Research Workflow Pipeline] --> B[Problem Definition]
    B --> C[Literature Search]
    C --> D[Data Collection]
    D --> E[Analysis Engine]
    E --> F[Visualization]
    F --> G[Report Generation]

    B --> B1[research_scope.json]
    C --> C1[articles_found.json]
    D --> D1[experimental_data.json]
    E --> E1[statistical_results.json]
    F --> F1[charts.json]
    G --> G1[research_report.pdf]

    B1 --> C
    C1 --> D
    D1 --> E
    E1 --> F
    F1 --> G

    style A fill:#f093fb
    style B fill:#667eea
    style C fill:#764ba2
    style D fill:#f093fb
    style E fill:#4facfe
    style F fill:#00f2fe
    style G fill:#43e97b
```

## Business Intelligence Pipeline

```mermaid
flowchart TD
    Start([Business Data Sources]) --> A[Stage 1:<br/>Data Sources Connection]
    A --> B[Stage 2:<br/>ETL Process]
    B --> C[Stage 3:<br/>Analytics Engine]
    C --> D[Stage 4:<br/>Dashboard Creation]
    C --> E[Stage 5:<br/>Alert System]

    A --> A1[(Raw Data)]
    B --> B1[(Processed Data)]
    C --> C1[(KPI Metrics)]
    D --> D1[📊 Dashboard]
    E --> E1[🔔 Alerts]

    D1 --> End1([Business Users])
    E1 --> End2([Stakeholders])

    style Start fill:#e3f2fd
    style A fill:#bbdefb
    style B fill:#90caf9
    style C fill:#64b5f6
    style D fill:#42a5f5
    style E fill:#2196f3
    style End1 fill:#c8e6c9
    style End2 fill:#c8e6c9
```

## E-commerce Analytics Pipeline

```mermaid
graph LR
    subgraph "Data Collection"
        A[Sales Data Ingestion] --> B[Data Enrichment]
    end

    subgraph "Analysis"
        B --> C[Customer Analytics]
        C --> D[Behavior Analysis]
    end

    subgraph "Delivery"
        D --> E[Reporting Dashboard]
        D --> F[Alert Engine]
    end

    A --> A1[Multiple Sources:<br/>Web, Mobile, POS]
    B --> B1[Enrich with:<br/>Customer Data]
    C --> C1[Segments &<br/>Patterns]
    E --> E1[Real-time<br/>Dashboard]
    F --> F1[Important<br/>Metrics Alerts]

    style A fill:#e1bee7
    style B fill:#ce93d8
    style C fill:#ba68c8
    style D fill:#ab47bc
    style E fill:#9c27b0
    style F fill:#8e24aa
```

## HR Automation Pipeline

```mermaid
graph TB
    Start([Hiring Need]) --> A[Candidate Sourcing]
    A --> B[Resume Screening]
    B --> C[Interview Scheduling]
    C --> D[Interview Evaluation]
    D --> E[Offer Management]
    E --> F[Onboarding Automation]
    F --> End([New Employee])

    A -.-> A1[Job Boards<br/>LinkedIn<br/>Referrals]
    B -.-> B1[AI Screening<br/>Keyword Match<br/>Score Ranking]
    C -.-> C1[Calendar Sync<br/>Auto-scheduling<br/>Reminders]
    D -.-> D1[Structured Forms<br/>Scoring System<br/>Comparison]
    E -.-> E1[Offer Letters<br/>Negotiation Tracking<br/>Acceptance]
    F -.-> F1[Document Collection<br/>Training Schedule<br/>Equipment Setup]

    style Start fill:#fff9c4
    style A fill:#fff59d
    style B fill:#fff176
    style C fill:#ffee58
    style D fill:#ffeb3b
    style E fill:#fdd835
    style F fill:#fbc02d
    style End fill:#c8e6c9
```

## Pipeline Decision Logic

```mermaid
graph TD
    A[Article Analysis] --> B{Detect Structure}
    B -->|Sequential Steps<br/>Found| C{Pipeline Confidence}
    B -->|Independent<br/>Workflows| D[Component Architecture]

    C -->|>80%<br/>Confidence| E[Create Pipeline Skill]
    C -->|<80%<br/>Confidence| F[Hybrid Architecture]

    E --> G[Pipeline Skill:<br/>domain-pipeline-cskill/]
    F --> H[Hybrid Skill:<br/>domain-hybrid-cskill/]
    D --> I[Component Skills:<br/>domain-suite-cskill/]

    G --> J[Linear Flow<br/>Stage 1 → 2 → 3]
    H --> K[Core Pipeline +<br/>Optional Components]
    I --> L[Independent<br/>Workflows]

    style B fill:#ffd54f
    style C fill:#ffca28
    style E fill:#4caf50
    style F fill:#ff9800
    style D fill:#2196f3
```

## Pipeline vs Components Comparison

```mermaid
graph TB
    subgraph "Pipeline Approach"
        P1[One Sequential Flow] --> P2[Automatic Orchestration]
        P2 --> P3[Data Flows Through]
        P3 --> P4[Cumulative Value]
    end

    subgraph "Component Approach"
        C1[Multiple Independent] --> C2[Manual Coordination]
        C2 --> C3[Isolated Data]
        C3 --> C4[Additive Value]
    end

    P4 --> Result1[Best for:<br/>• Single process<br/>• End-to-end flow<br/>• Sequential steps]
    C4 --> Result2[Best for:<br/>• Multiple processes<br/>• Modularity<br/>• Specialization]

    style P1 fill:#e8f5e9
    style P2 fill:#c8e6c9
    style P3 fill:#a5d6a7
    style P4 fill:#81c784
    style C1 fill:#e3f2fd
    style C2 fill:#bbdefb
    style C3 fill:#90caf9
    style C4 fill:#64b5f6
```

## Real-World Pipeline Flow Example

```mermaid
sequenceDiagram
    participant User
    participant Pipeline as E-commerce Pipeline
    participant Stage1 as Sales Ingestion
    participant Stage2 as Enrichment
    participant Stage3 as Analytics
    participant Stage4 as Dashboard
    participant Stage5 as Alerts

    User->>Pipeline: Request daily analytics
    Pipeline->>Stage1: Fetch sales data
    activate Stage1
    Stage1-->>Pipeline: raw_sales.json
    deactivate Stage1

    Pipeline->>Stage2: Enrich with customer data
    activate Stage2
    Stage2-->>Pipeline: enriched_sales.json
    deactivate Stage2

    Pipeline->>Stage3: Analyze behavior patterns
    activate Stage3
    Stage3-->>Pipeline: analytics_results.json
    deactivate Stage3

    Pipeline->>Stage4: Generate dashboard
    activate Stage4
    Stage4-->>User: 📊 Interactive Dashboard
    deactivate Stage4

    Pipeline->>Stage5: Check alert conditions
    activate Stage5
    Stage5-->>User: 🔔 Important Alerts
    deactivate Stage5

    Note over User,Stage5: Complete flow in 30 seconds<br/>vs 2 hours manual work
```
