# Smart Timetable Generator – Build Checklist

Goal:
Build a **constraint optimization based timetable generator** using **OR-Tools**, first as a **Streamlit MVP**, then as a **scalable SaaS product**.

---

# Phase 0 – Product Definition

## Define Problem

* [ ] Document the problem clearly
* [ ] Identify target users

  * [ ] Students
  * [ ] Teachers
  * [ ] Small coaching institutes
* [ ] Define the main pain points

  * [ ] Manual timetable creation
  * [ ] Subject imbalance
  * [ ] Scheduling conflicts

## Define Product Scope

* [ ] Decide MVP features
* [ ] Decide constraints supported
* [ ] Define optimization goals

MVP features:

* Generate timetable automatically
* Avoid subject overlap
* Respect subject weekly hours
* Visual timetable output
* Download timetable

---

# Phase 1 – Repository Setup

## Create Project Repository

* [ ] Create GitHub repo
* [ ] Add README.md
* [ ] Add LICENSE
* [ ] Add CHECKLIST.md
* [ ] Add sample dataset

Repository structure:

```
smart-timetable-generator/

backend/
solver/
frontend/
streamlit_app/
data/
docs/
tests/

README.md
CHECKLIST.md
requirements.txt
```

---

# Phase 2 – Mathematical Modeling (Core OR Component)

## Define Problem Variables

Decision variable:

X[subject, day, slot]

* [ ] Binary variable definition
* [ ] Each variable represents assignment

Example:

```
X[Math, Monday, Slot1] = 1
```

---

## Define Constraints

### Subject Hours Constraint

* [ ] Each subject must appear required number of times

Example:

Math = 5 hours/week

---

### Slot Constraint

* [ ] Only one subject per slot

---

### Daily Limit Constraint

* [ ] Optional: subject cannot repeat more than twice per day

---

### Soft Constraints (Optimization)

* [ ] Spread subjects across week
* [ ] Avoid subject clustering

---

## Define Objective Function

Example objective:

Minimize:

* subject clustering
* uneven distribution
* empty slots

---

# Phase 3 – Optimization Engine (OR Tools)

## Setup Solver Module

Folder:

```
solver/
```

Files:

```
model.py
constraints.py
objective.py
solver_runner.py
```

---

## Implementation Tasks

### Model Builder

* [ ] Create variable matrix
* [ ] Define days
* [ ] Define time slots

---

### Constraint Builder

* [ ] Implement subject hours constraint
* [ ] Implement slot constraint
* [ ] Implement daily repetition constraint

---

### Objective Builder

* [ ] Implement timetable balancing
* [ ] Add soft penalties

---

### Solver Runner

* [ ] Run OR Tools CP-SAT solver
* [ ] Extract solution
* [ ] Convert to timetable format

---

# Phase 4 – Data Layer

## Input Schema

Create data model:

```
subjects
hours_per_week
days
slots_per_day
```

Example:

```
subjects = {
 "Math":5,
 "Physics":4,
 "Chemistry":3
}
```

---

## Data Validation

* [ ] Validate subject hours
* [ ] Validate slots available
* [ ] Check infeasible configurations

---

# Phase 5 – Streamlit MVP UI

Goal: Build a **fully working interactive prototype**.

Folder:

```
streamlit_app/
```

File:

```
app.py
```

---

## UI Components

### App Layout

* [ ] Title
* [ ] Sidebar input
* [ ] Generate button
* [ ] Timetable output

---

### User Inputs

* [ ] Number of days
* [ ] Slots per day
* [ ] Add subjects
* [ ] Define hours per subject

---

### Dynamic Subject Input

* [ ] Add subject button
* [ ] Editable table

---

### Generate Button

When clicked:

* [ ] Collect user input
* [ ] Call solver
* [ ] Display timetable

---

## Timetable Visualization

* [ ] Display grid table
* [ ] Color code subjects
* [ ] Allow download

---

# Phase 6 – Output Features

## Export Options

* [ ] CSV export
* [ ] PDF export
* [ ] Image export

---

## Visualization

* [ ] Weekly grid layout
* [ ] Subject color mapping
* [ ] Clean UI formatting

---

# Phase 7 – Testing

## Unit Testing

Folder:

```
tests/
```

Tasks:

* [ ] Solver correctness tests
* [ ] Constraint validation tests
* [ ] Edge case testing

Examples:

* Too many subject hours
* Too few slots

---

# Phase 8 – Documentation

## README Sections

* [ ] Project Overview
* [ ] Problem Statement
* [ ] Mathematical Model
* [ ] System Architecture
* [ ] Installation Guide
* [ ] Example Usage
* [ ] Screenshots

---

## Mathematical Model Documentation

Create:

```
docs/model.md
```

Include:

* decision variables
* constraints
* objective function

---

# Phase 9 – Architecture Design (Production Version)

Future SaaS architecture.

```
Frontend (React / Next.js)
        |
API Layer (FastAPI)
        |
Optimization Service
        |
PostgreSQL
```

---

## Backend Modules

```
backend/

api/
services/
models/
solver_adapter/
```

Tasks:

* [ ] Create REST APIs
* [ ] Connect solver
* [ ] Store generated timetables

---

# Phase 10 – API Design

Endpoints:

```
POST /generate-timetable
GET /timetable/{id}
```

Tasks:

* [ ] Input validation
* [ ] Async solver execution
* [ ] Response formatting

---

# Phase 11 – Full Frontend (Cursor Build)

Later replace Streamlit.

Tech stack:

* Next.js
* Tailwind
* React

---

## Frontend Features

### Dashboard

* [ ] Create timetable project
* [ ] Input subjects
* [ ] Configure schedule

---

### Timetable Editor

* [ ] Grid UI
* [ ] Drag-drop editing
* [ ] Regenerate timetable

---

# Phase 12 – Performance Optimization

* [ ] Add solver timeout
* [ ] Limit max subjects
* [ ] Improve solver speed

Example:

```
max_solver_time = 10 seconds
```

---

# Phase 13 – Deployment

## Streamlit Version

* [ ] Deploy on Streamlit Cloud

---

## Full SaaS Version

* [ ] Deploy backend (Render / Railway)
* [ ] Deploy frontend (Vercel)
* [ ] Setup database

---

# Phase 14 – Portfolio Strength

To make this project **strong for OR roles**, ensure:

* [ ] Mathematical modeling documented
* [ ] Clean solver implementation
* [ ] Architecture diagrams
* [ ] Real screenshots
* [ ] Example datasets

---

# Phase 15 – Bonus Features

Future improvements:

* [ ] Teacher scheduling
* [ ] Room allocation
* [ ] Multi-class timetables
* [ ] Exam study planner

---

# Final Deliverables

Before marking project complete:

* [ ] Working Streamlit demo
* [ ] Well documented solver
* [ ] Architecture diagram
* [ ] Screenshots
* [ ] Clean GitHub repo

---

# Portfolio Impact

This project demonstrates:

* Operational Research modeling
* Constraint optimization
* Production system design
* Real world application of OR
* Full stack product thinking

---

Estimated Build Time:

MVP: 2–3 days
Full portfolio project: 2–3 weeks
