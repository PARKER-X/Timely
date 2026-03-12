# System Architecture

This document describes the system architecture of the **Smart Timetable Generator**, an optimization-based scheduling system built using constraint programming.

The system is designed to demonstrate:

- Operational Research modeling
- Constraint optimization
- Modular system design
- Scalable SaaS architecture

---

# 1. High-Level Architecture

This diagram shows the overall product architecture.

```mermaid
flowchart LR

User[User Browser]

UI[Frontend UI<br>Streamlit / React]

API[Backend API<br>FastAPI]

Parser[Input Parser<br>Validation Layer]

Solver[Optimization Engine<br>OR-Tools CP-SAT]

DB[(Database<br>PostgreSQL)]

Viz[Visualization Engine]

User --> UI
UI --> API
API --> Parser
Parser --> Solver
Solver --> DB
DB --> Viz
Viz --> UI

```

2. Optimization Engine Architecture

The optimization engine is responsible for building and solving the scheduling model.
```mermaid
flowchart TD

Input[User Input Data]

ModelBuilder[Model Builder]

Variables[Decision Variables]

Constraints[Constraint Builder]

Objective[Objective Function]

Solver[CP-SAT Solver]

SolutionExtractor[Solution Extractor]

Formatter[Timetable Formatter]

Input --> ModelBuilder
ModelBuilder --> Variables
Variables --> Constraints
Constraints --> Objective
Objective --> Solver
Solver --> SolutionExtractor
SolutionExtractor --> Formatter

```

3. Data Flow Architecture

This diagram explains how data moves through the system from user input to final timetable output.
```mermaid
flowchart LR

UserInput[User Inputs Subjects and Schedule]

Validation[Input Validation]

JSON[Structured Input Data]

SolverEngine[Optimization Engine]

SolutionJSON[Optimized Schedule]

GridRenderer[Timetable Grid Renderer]

ExportModule[CSV / PDF Export]

UserInput --> Validation
Validation --> JSON
JSON --> SolverEngine
SolverEngine --> SolutionJSON
SolutionJSON --> GridRenderer
GridRenderer --> ExportModule

```

4. Scalable SaaS Architecture

The system can be extended into a scalable SaaS platform using asynchronous job processing.

```mermaid
User[Users]

Frontend[Frontend<br>Next.js]

Gateway[API Gateway]

Backend[FastAPI Service]

Queue[Task Queue<br>Redis]

Worker[Solver Workers<br>OR-Tools]

DB[(PostgreSQL)]

Storage[(Object Storage)]

User --> Frontend
Frontend --> Gateway
Gateway --> Backend
Backend --> Queue
Queue --> Worker
Worker --> DB
DB --> Backend
Backend --> Frontend
Backend --> Storage

```

5. Solver Execution Pipeline

This diagram shows the internal workflow of the optimization process.

```mermaid
flowchart TD

Start[User Request]

Parse[Parse Input Data]

FeasibilityCheck[Feasibility Check]

BuildModel[Build Optimization Model]

Solve[Run CP-SAT Solver]

ExtractSolution[Extract Schedule]

ValidateSchedule[Validate Constraints]

GenerateOutput[Generate Timetable]

Start --> Parse
Parse --> FeasibilityCheck
FeasibilityCheck --> BuildModel
BuildModel --> Solve
Solve --> ExtractSolution
ExtractSolution --> ValidateSchedule
ValidateSchedule --> GenerateOutput
```
