# System Integration Architecture

## Complete System Architecture

```mermaid
C4Context
    title Agent-Skill-Creator Complete System Architecture

    Person(user, "User", "Developer, Analyst,<br/>Business Owner")
    System(agentCreator, "Agent-Skill-Creator", "Meta-skill that creates<br/>other skills")

    System_Ext(claudeCode, "Claude Code", "AI coding assistant")
    System_Ext(agentDB, "AgentDB", "Learning & memory system")
    System_Ext(github, "GitHub", "Code repository")

    Rel(user, agentCreator, "Requests agent creation", "Natural language")
    Rel(agentCreator, claudeCode, "Executes in", "Plugin system")
    Rel(agentCreator, agentDB, "Stores/retrieves", "Learning data")
    Rel(agentCreator, github, "Exports to", "Skills")

    UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```

## Technical Component Architecture

```mermaid
graph TB
    subgraph "User Interface Layer"
        UI1[Natural Language<br/>User Queries]
        UI2[Claude Code CLI]
    end

    subgraph "Agent Creator Core"
        Core1[SKILL.md<br/>Main Orchestrator]
        Core2[Phase Executors<br/>6-phase system]
        Core3[Decision Engine]
    end

    subgraph "Knowledge Base"
        KB1[/references Directory<br/>Methodologies & Guides]
        KB2[Templates<br/>Pre-built patterns]
        KB3[Examples<br/>Working implementations]
    end

    subgraph "Intelligence Layer"
        AI1[AgentDB Bridge]
        AI2[Episode Memory]
        AI3[Skill Library]
        AI4[Causal Memory]
    end

    subgraph "Output Layer"
        OUT1[Generated Skills<br/>domain-cskill/]
        OUT2[Documentation<br/>README, SKILL.md]
        OUT3[Export Packages<br/>Cross-platform .zip]
    end

    UI1 --> UI2
    UI2 --> Core1
    Core1 --> Core2
    Core2 --> Core3

    Core2 --> KB1
    Core2 --> KB2
    Core2 --> KB3

    Core3 --> AI1
    AI1 --> AI2
    AI1 --> AI3
    AI1 --> AI4

    AI1 --> Core2

    Core2 --> OUT1
    Core2 --> OUT2
    Core2 --> OUT3

    style Core1 fill:#667eea
    style AI1 fill:#f093fb
    style OUT1 fill:#4facfe
```

## Data Flow Architecture

```mermaid
flowchart TB
    Input[User Input:<br/>'Create financial agent'] --> Parse[Parse & Analyze]

    Parse --> Phase1[Phase 1: Discovery<br/>Research APIs & Data]
    Phase1 --> Phase2[Phase 2: Design<br/>Define Use Cases]
    Phase2 --> Phase3[Phase 3: Architecture<br/>Plan Structure]
    Phase3 --> Phase4[Phase 4: Detection<br/>Activation System]
    Phase4 --> Phase5[Phase 5: Implementation<br/>Write Code]
    Phase5 --> Phase6[Phase 6: Testing<br/>Validate & Test]

    Phase1 -.-> Refs1[/references/<br/>phase1-discovery.md]
    Phase2 -.-> Refs2[/references/<br/>phase2-design.md]
    Phase3 -.-> Refs3[/references/<br/>phase3-architecture.md]
    Phase4 -.-> Refs4[/references/<br/>phase4-detection.md]
    Phase5 -.-> Refs5[/references/<br/>phase5-implementation.md]
    Phase6 -.-> Refs6[/references/<br/>phase6-testing.md]

    Phase1 -.-> AI[(AgentDB)]
    Phase2 -.-> AI
    Phase3 -.-> AI
    Phase4 -.-> AI
    Phase5 -.-> AI
    Phase6 -.-> AI

    AI -.-> Phase1
    AI -.-> Phase2
    AI -.-> Phase3
    AI -.-> Phase4
    AI -.-> Phase5
    AI -.-> Phase6

    Phase6 --> Output[Generated Skill:<br/>financial-analysis-cskill/]

    Output --> Store[Store Episode<br/>in AgentDB]
    Store --> Future[Enhance Future<br/>Creations]

    style Parse fill:#e1f5ff
    style Phase1 fill:#fff9c4
    style Phase2 fill:#fff59d
    style Phase3 fill:#ffee58
    style Phase4 fill:#ffeb3b
    style Phase5 fill:#fdd835
    style Phase6 fill:#fbc02d
    style Output fill:#4caf50
    style AI fill:#9c27b0
```

## Plugin Marketplace Architecture

```mermaid
graph TB
    subgraph "Claude Code System"
        CC[Claude Code Core]
        PM[Plugin Marketplace<br/>Manager]
    end

    subgraph "Agent-Skill-Creator"
        ASC[.claude-plugin/<br/>marketplace.json]
        SKILL[SKILL.md<br/>Meta-skill definition]
        REFS[references/<br/>Knowledge base]
        SCRIPTS[scripts/<br/>Helper utilities]
    end

    subgraph "Created Skills"
        CS1[financial-analysis-cskill/<br/>Independent marketplace]
        CS2[climate-research-cskill/<br/>Independent marketplace]
        CS3[ecommerce-analytics-cskill/<br/>Independent marketplace]
    end

    CC --> PM
    PM --> ASC
    ASC --> SKILL
    SKILL --> REFS
    SKILL --> SCRIPTS

    SKILL --> CS1
    SKILL --> CS2
    SKILL --> CS3

    CS1 --> Install1[Install separately:<br/>/plugin marketplace add ./]
    CS2 --> Install1
    CS3 --> Install1

    style CC fill:#e3f2fd
    style PM fill:#bbdefb
    style ASC fill:#667eea
    style SKILL fill:#764ba2
    style CS1 fill:#4facfe
    style CS2 fill:#00f2fe
    style CS3 fill:#43e97b
```

## AgentDB Integration Architecture

```mermaid
graph TB
    subgraph "Agent Creator"
        AC[Agent Creator<br/>SKILL.md]
        Bridge[AgentDB Bridge<br/>agentdb_bridge.py]
    end

    subgraph "AgentDB System"
        CLI[AgentDB CLI<br/>Node.js/TypeScript]
        DB[(SQLite Database)]
        VEC[Vector Embeddings<br/>Semantic Search]
        CAUSAL[Causal Inference<br/>Engine]
    end

    subgraph "Memory Systems"
        REFLEX[Reflexion Memory<br/>Episodes]
        SKILLS[Skill Library<br/>Patterns]
        EDGES[Causal Edges<br/>Relationships]
    end

    AC --> Bridge
    Bridge -->|Store episode| CLI
    Bridge -->|Query similar| CLI
    Bridge -->|Search skills| CLI
    Bridge -->|Query effects| CLI

    CLI --> DB
    CLI --> VEC
    CLI --> CAUSAL

    DB --> REFLEX
    DB --> SKILLS
    DB --> EDGES

    REFLEX --> Enhance[Enhance<br/>Future Creations]
    SKILLS --> Enhance
    EDGES --> Enhance

    Enhance --> AC

    style AC fill:#667eea
    style Bridge fill:#764ba2
    style CLI fill:#f093fb
    style DB fill:#fbc2eb
    style Enhance fill:#4facfe
```

## Cross-Platform Export Architecture

```mermaid
graph LR
    subgraph "Source"
        Skill[Created Skill<br/>domain-cskill/]
    end

    subgraph "Export System"
        Detector[Version Detector<br/>Git tags / SKILL.md]
        Validator[Size & Structure<br/>Validator]
        Packager[Dual Packager]
    end

    subgraph "Output Packages"
        Desktop[Desktop Package<br/>Full docs, 2-5 MB]
        API[API Package<br/>Optimized, <8 MB]
        Guide[Installation Guide<br/>INSTALL.md]
    end

    subgraph "Target Platforms"
        CC[Claude Code<br/>Native]
        CD[Claude Desktop<br/>Upload .zip]
        CW[claude.ai Web<br/>Upload .zip]
        CAPI[Claude API<br/>Programmatic]
    end

    Skill --> Detector
    Detector --> Validator
    Validator --> Packager

    Packager --> Desktop
    Packager --> API
    Packager --> Guide

    Desktop --> CD
    Desktop --> CW
    API --> CAPI
    Skill --> CC

    style Skill fill:#667eea
    style Packager fill:#764ba2
    style Desktop fill:#4facfe
    style API fill:#00f2fe
    style CC fill:#4caf50
```

## Activation System Integration

```mermaid
graph TB
    Query[User Query] --> Router[Claude Code<br/>Plugin Router]

    Router --> Check1{Check All Skills}

    Check1 --> Skill1[agent-skill-creator]
    Check1 --> Skill2[financial-analysis]
    Check1 --> Skill3[climate-research]

    Skill1 --> L1_1[Layer 1: Keywords]
    Skill2 --> L1_2[Layer 1: Keywords]
    Skill3 --> L1_3[Layer 1: Keywords]

    L1_1 --> L2_1[Layer 2: Patterns]
    L1_2 --> L2_2[Layer 2: Patterns]
    L1_3 --> L2_3[Layer 2: Patterns]

    L2_1 --> L3_1[Layer 3: NLU]
    L2_2 --> L3_2[Layer 3: NLU]
    L2_3 --> L3_3[Layer 3: NLU]

    L3_1 --> L4_1[Layer 4: Context]
    L3_2 --> L4_2[Layer 4: Context]
    L3_3 --> L4_3[Layer 4: Context]

    L4_1 --> Decision{Best Match}
    L4_2 --> Decision
    L4_3 --> Decision

    Decision --> Execute[Execute Best<br/>Matching Skill]

    style Router fill:#ffd54f
    style Decision fill:#ff9800
    style Execute fill:#4caf50
```

## Naming Convention System

```mermaid
graph TB
    Start[Skill Creation] --> Type{Skill Type}

    Type -->|Created by<br/>Agent Creator| Auto[Auto-append<br/>-cskill suffix]
    Type -->|Manual Creation| Manual[No suffix]

    Auto --> Examples1[financial-analysis-cskill/<br/>stock-analyzer-cskill/<br/>climate-research-cskill/]

    Manual --> Examples2[custom-skill/<br/>my-project/<br/>user-workflow/]

    Examples1 --> Benefits[✅ Clear identification<br/>✅ Professional naming<br/>✅ Easy discovery<br/>✅ No confusion]

    Examples2 --> Benefits2[⚠️ Flexibility<br/>⚠️ Custom naming<br/>⚠️ Must maintain quality]

    style Auto fill:#4caf50
    style Manual fill:#ff9800
    style Examples1 fill:#c8e6c9
    style Benefits fill:#4caf50
```
