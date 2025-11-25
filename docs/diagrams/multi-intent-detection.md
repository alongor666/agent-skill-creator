# Multi-Intent Detection System Visualizations

## Intent Hierarchy Architecture

```mermaid
graph TB
    Query[User Query:<br/>"Analyze stocks, create charts, and save results"] --> Primary

    Primary[Primary Intent] --> P1[analyze]

    Secondary[Secondary Intents] --> S1[and_visualize]
    Secondary --> S2[and_save]

    Contextual[Contextual Intents] --> C1[detailed_analysis]

    Meta[Meta Intent] --> M1[just_show_me]

    Primary --> Router{Intent Router}
    Secondary --> Router
    Contextual --> Router
    Meta --> Router

    Router --> Cap1[Capability 1:<br/>Stock Analysis]
    Router --> Cap2[Capability 2:<br/>Chart Generation]
    Router --> Cap3[Capability 3:<br/>Data Persistence]

    Cap1 --> Result[📊 Complete Result]
    Cap2 --> Result
    Cap3 --> Result

    style Query fill:#e3f2fd
    style Primary fill:#4caf50
    style Secondary fill:#2196f3
    style Contextual fill:#ff9800
    style Meta fill:#9c27b0
    style Result fill:#4caf50
```

## Intent Classification Process

```mermaid
sequenceDiagram
    participant User
    participant Parser as Multi-Intent Parser
    participant Primary as Primary Detector
    participant Secondary as Secondary Detector
    participant Context as Context Analyzer
    participant Validator as Capability Validator
    participant Router as Intent Router

    User->>Parser: "Analyze stocks and visualize trends"
    Parser->>Primary: Extract primary intent
    Primary-->>Parser: Intent: "analyze" (95% confidence)

    Parser->>Secondary: Extract secondary intents
    Secondary-->>Parser: Intents: ["and_visualize"] (88% confidence)

    Parser->>Context: Extract contextual modifiers
    Context-->>Parser: Context: ["real_time"] (82% confidence)

    Parser->>Validator: Validate against skill capabilities
    Validator-->>Parser: ✅ All intents supported

    Parser->>Router: Create execution plan
    Router-->>User: Execute multi-capability response
```

## Intent Type Examples

```mermaid
mindmap
  root((Multi-Intent<br/>Detection))
    Primary Intents
      analyze
        Analyze data
        Evaluate performance
        Study trends
      create
        Create agent
        Build workflow
        Generate report
      compare
        Compare options
        Rank alternatives
        Benchmark
      monitor
        Track changes
        Watch metrics
        Observe patterns
    Secondary Intents
      and_visualize
        Create charts
        Show graphs
        Display dashboard
      and_save
        Save to file
        Export results
        Archive data
      and_explain
        Explain results
        Provide reasoning
        Detail methodology
      and_alert
        Set up notifications
        Create triggers
        Monitor thresholds
    Contextual Intents
      quick_summary
        Brief overview
        Key highlights
        Executive summary
      detailed_analysis
        In-depth review
        Comprehensive report
        Full breakdown
      real_time
        Live data
        Current status
        Up-to-date info
      historical
        Past data
        Trends over time
        Historical analysis
```

## Complex Query Parsing Example

```mermaid
graph TB
    Query["User Query:<br/>'Analyze my stock portfolio performance,<br/>compare it with market benchmarks,<br/>create visualizations, and alert me if<br/>any stock drops more than 5%'"]

    Query --> P[Primary Intent<br/>Confidence: 95%]
    P --> P1[analyze]

    Query --> S[Secondary Intents<br/>Average Confidence: 87%]
    S --> S1[and_compare]
    S --> S2[and_visualize]
    S --> S3[and_alert]

    Query --> C[Contextual Intent<br/>Confidence: 80%]
    C --> C1[detailed_analysis]

    Query --> M[Meta Intent<br/>Confidence: 75%]
    M --> M1[automate_for_me]

    P1 --> Plan{Execution Plan}
    S1 --> Plan
    S2 --> Plan
    S3 --> Plan
    C1 --> Plan
    M1 --> Plan

    Plan --> Step1[Step 1: Analyze Portfolio<br/>Calculate returns, risk]
    Plan --> Step2[Step 2: Compare Benchmarks<br/>S&P 500, sector indices]
    Plan --> Step3[Step 3: Create Visualizations<br/>Charts, graphs, dashboard]
    Plan --> Step4[Step 4: Set Up Alerts<br/>-5% threshold monitoring]

    style Query fill:#e1f5ff
    style P fill:#4caf50
    style S fill:#2196f3
    style C fill:#ff9800
    style M fill:#9c27b0
    style Plan fill:#ffd54f
```

## Intent Confidence Scoring

```mermaid
graph LR
    subgraph "High Confidence (90-100%)"
        H1["'Create an agent'<br/>Primary: create<br/>98% confidence"]
        H2["'Analyze and visualize'<br/>Primary: analyze<br/>Secondary: visualize<br/>95% / 92%"]
    end

    subgraph "Medium Confidence (70-89%)"
        M1["'Help me with stocks'<br/>Primary: unknown<br/>Context: financial<br/>75% confidence"]
        M2["'Show me trends'<br/>Primary: monitor<br/>Context: real_time<br/>80% / 72%"]
    end

    subgraph "Low Confidence (<70%)"
        L1["'What should I do?'<br/>Primary: unknown<br/>Meta: help_me_decide<br/>45% confidence"]
    end

    H1 --> D1[✅ Execute Directly]
    H2 --> D1

    M1 --> D2[⚠️ Clarify Intent]
    M2 --> D2

    L1 --> D3[❌ Request Clarification]

    style H1 fill:#c8e6c9
    style H2 fill:#c8e6c9
    style M1 fill:#fff9c4
    style M2 fill:#fff9c4
    style L1 fill:#ffcdd2
```

## Intent Routing Decision Tree

```mermaid
graph TB
    Start[Parse User Query] --> Primary{Primary Intent<br/>Detected?}

    Primary -->|Yes, High Confidence| Secondary{Secondary Intents?}
    Primary -->|Low Confidence| Clarify1[Request Clarification]

    Secondary -->|Yes| Validate{All Intents<br/>Supported?}
    Secondary -->|No| SingleIntent[Execute Single Intent]

    Validate -->|Yes| CreatePlan[Create Multi-Step<br/>Execution Plan]
    Validate -->|No| Fallback[Execute Supported<br/>Intents Only]

    CreatePlan --> Priority{Prioritize<br/>Intents}

    Priority --> Seq[Sequential Execution:<br/>Primary → Secondary]
    Priority --> Par[Parallel Execution:<br/>Independent Intents]

    Seq --> Execute1[Execute Plan]
    Par --> Execute1

    Execute1 --> Monitor{Monitor<br/>Execution}

    Monitor -->|Success| Result[✅ Complete Result]
    Monitor -->|Partial Success| PartialResult[⚠️ Partial Result +<br/>Error Report]
    Monitor -->|Failure| Error[❌ Error +<br/>Fallback Options]

    style Start fill:#e3f2fd
    style Primary fill:#ffd54f
    style CreatePlan fill:#4caf50
    style Result fill:#4caf50
    style PartialResult fill:#ff9800
    style Error fill:#f44336
```

## Real-World Multi-Intent Examples

```mermaid
graph TB
    subgraph "Example 1: Financial Analysis"
        E1["Query: 'Analyze AAPL stock performance,<br/>compare with MSFT, and show me charts'"]
        E1 --> E1P[Primary: analyze<br/>95% conf]
        E1 --> E1S1[Secondary: compare<br/>90% conf]
        E1 --> E1S2[Secondary: visualize<br/>88% conf]
        E1P --> E1R[Result: Analysis + Comparison + Charts]
        E1S1 --> E1R
        E1S2 --> E1R
    end

    subgraph "Example 2: Research Workflow"
        E2["Query: 'Search research papers on AI,<br/>summarize key findings, and create report'"]
        E2 --> E2P[Primary: search<br/>92% conf]
        E2 --> E2S1[Secondary: summarize<br/>85% conf]
        E2 --> E2S2[Secondary: create_report<br/>87% conf]
        E2P --> E2R[Result: Papers + Summary + Report]
        E2S1 --> E2R
        E2S2 --> E2R
    end

    subgraph "Example 3: E-commerce Analytics"
        E3["Query: 'Monitor sales in real-time,<br/>alert me on drops, visualize trends'"]
        E3 --> E3P[Primary: monitor<br/>93% conf]
        E3 --> E3S1[Secondary: alert<br/>91% conf]
        E3 --> E3S2[Secondary: visualize<br/>89% conf]
        E3 --> E3C[Context: real_time<br/>86% conf]
        E3P --> E3R[Result: Live Dashboard +<br/>Alert System + Visualizations]
        E3S1 --> E3R
        E3S2 --> E3R
        E3C --> E3R
    end

    style E1 fill:#e8f5e9
    style E2 fill:#e3f2fd
    style E3 fill:#fff3e0
    style E1R fill:#4caf50
    style E2R fill:#2196f3
    style E3R fill:#ff9800
```

## Intent Accuracy Improvement (v3.0 → v3.1)

```mermaid
graph LR
    subgraph "v3.0"
        V30[Single Intent Only<br/>Accuracy: 70%]
        V30 --> V30F["❌ Fails on:<br/>'analyze and compare'<br/>'create and visualize'"]
    end

    subgraph "v3.1"
        V31[Multi-Intent Support<br/>Accuracy: 95%]
        V31 --> V31S["✅ Succeeds on:<br/>'analyze and compare'<br/>'create and visualize'<br/>'monitor and alert'"]
    end

    V30 -.->|Upgrade| V31

    style V30 fill:#ffcdd2
    style V30F fill:#f44336
    style V31 fill:#c8e6c9
    style V31S fill:#4caf50
```
