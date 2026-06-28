---
title: "AI University CLI Core Engine"
subtitle: ""
description: "A product concept for turning a learning prompt and optional source files into a complete university-style course package that can later power an immersive education experience."
date: 2026-06-28
author: "Anthony Cavuoti"
image: ""
tags: ["ai", "education", "cli", "systems"]
categories: ["Tech"]
---

# AI University CLI Core Engine

AI University is an idea for a learning system that treats a single education prompt as the start of a real course, not the start of a chat thread.

The core question is simple:

> What if you could give an AI a learning goal, a folder of materials, or both, and get back a complete university-style course?

Not a summary. Not a list of links. Not a few bullet points.

A full course.

That means a syllabus, schedule, lectures, labs, homework, quizzes, projects, exams, rubrics, answer keys, study guides, source citations, validation reports, and structured metadata that another application could use later.

The long-term version of the idea is more ambitious: a VR university simulator where a learner can sit in lectures, ask questions, complete labs, and move through a generated course as if they were enrolled in a class. But the first build should not start with VR. It should start with the engine underneath it.

The CLI and core engine are the content factory.

## The Problem

AI tools are good at answering questions, but learning is not the same as receiving an answer.

If someone asks, "Teach me distributed systems from first principles," the right response is not a single explanation. A real learning experience has sequence. It starts with prerequisites. It introduces concepts in the right order. It repeats hard ideas in different forms. It gives practice. It checks understanding. It creates projects that force synthesis.

That is what a university course is good at.

The AI University engine would take a prompt like that and expand it into a structured course plan. If the user supplies files, notes, PDFs, images, repositories, datasets, or a whole directory, the engine should use those materials as source context. If the source material is incomplete or contradictory, the engine should say so instead of inventing confidence.

The product is built around one belief:

**A learning prompt deserves a curriculum, not just a response.**

## Why Start With A CLI?

The exciting version of AI University is immersive. A simulated professor. A classroom. A lab room. Interactive questions. A long-form learning path.

But the most important part is not the graphics layer. It is the course-generation system.

A CLI-first approach has practical advantages:

- It can run locally and write plain files.
- It can be tested without a VR runtime.
- It can checkpoint long-running work.
- It can produce artifacts that humans can inspect.
- It can expose stable JSON, YAML, and Markdown outputs for future apps.

The CLI is also the right place to solve the hard engine problems: ingestion, source grounding, planning, validation, resumability, provider abstraction, and artifact packaging.

Once those are reliable, a VR app can consume the course package without needing to reinterpret the original prompt from scratch.

## The User Experience

The simplest version should feel like this:

```bash
aiu course create "Teach me machine learning from first principles" \
  --weeks 24 \
  --lectures-per-week 2 \
  --lecture-hours 2 \
  --lab-policy auto \
  --level beginner \
  --output ./courses/machine-learning
```

The user can also point the engine at source material:

```bash
aiu course create --prompt ./prompt.md \
  --context ./materials \
  --context ./notes.zip \
  --context ./diagrams \
  --output ./courses/custom-course
```

From there, the engine should:

- analyze the learning goal
- inventory and extract source files
- build an index for retrieval and citation
- generate a course blueprint
- ask for approval before expensive generation
- generate the full course in stages
- validate the package
- export human-readable and machine-readable outputs

The approval step matters. A full semester course is large. The system should not spend time and model usage generating dozens of lectures before the user has seen the plan.

## The Course Package

The output should be a real project directory, not an opaque blob.

```txt
course-root/
  course.yaml
  manifest.json
  prompt.md
  course_blueprint.md
  course_blueprint.json
  schedule.json
  source_manifest.json
  ingest_report.json
  validation_report.json
  logs/
  source_index/
  extracted_sources/
  syllabus/
  lectures/
  labs/
  homework/
  quizzes/
  exams/
  projects/
  rubrics/
  answer_keys/
  study_guides/
  vr_handoff/
  exports/
```

The Markdown files make the course readable. The JSON and YAML files make it portable. The logs, manifests, and validation reports make the generation auditable.

That combination is important because a generated course can become huge. A default 24-week course with two lectures per week means 48 lecture transcripts before counting labs, assignments, assessments, and study guides. That cannot be handled as one giant model response.

The engine has to work in stages.

## The Pipeline

The core pipeline looks like this:

```txt
1. Initialize project
2. Ingest sources
3. Index context
4. Analyze learning intent
5. Plan curriculum
6. Ask for approval
7. Generate artifacts
8. Validate the course
9. Package and export
```

Each stage should leave behind useful state. If a generation fails halfway through week eight, the user should be able to resume without starting over. If a lecture needs to be regenerated, the engine should rebuild that lecture without rewriting the entire course.

That requires stable artifact IDs, a dependency graph, and clear source manifests.

For example, a final exam depends on the course learning objectives, the weekly topics, and the material that actually appeared in the lectures. A lecture depends on the approved course blueprint and relevant source chunks. A VR handoff file depends on lecture segments, timing cues, interaction anchors, and scene metadata.

The dependency graph prevents drift.

## What Makes This More Than A Content Generator

The engine is not just producing text. It is producing a structured learning system.

For every course, it should generate:

- a course blueprint
- weekly learning objectives
- lecture transcripts
- labs or lab alternatives
- homework and practice activities
- quizzes and tests
- rubrics and answer keys
- projects when appropriate
- study guides
- source citations
- validation reports
- VR handoff metadata

The validation piece is one of the most important parts.

AI-generated course material can look polished while still being incomplete. A validation engine should check whether expected artifacts exist, whether references are broken, whether assessments map to learning objectives, whether sources were cited, and whether the course schedule is internally consistent.

The product should prefer a warning over fake certainty.

If the supplied source folder does not contain enough information to support a requested advanced course, the engine should say that. If two sources conflict, the engine should flag the conflict. If an unsupported file type is skipped, that should appear in the ingest report.

## The VR Layer Comes Later

The PRD keeps VR out of the CLI MVP, but it does not ignore it.

That is the right split.

The CLI should not render a classroom, animate a professor, synthesize voice, or build a full learner runtime. But it should emit metadata that makes those things possible later:

- lecture segments
- estimated timing
- board and slide cues
- likely student questions
- professor response anchors
- lab setup metadata
- scene cues
- interaction anchors
- course progression hooks

Retrofitting that structure after generating hundreds of pages of course text would be painful. The better move is to include the handoff schema early, even while the first product surface remains command-line only.

The VR product can then become a renderer and interaction layer on top of a reliable course package.

## The Architecture

The system breaks down into a few core pieces:

```txt
CLI Shell
  -> Project Manager
  -> Auth / Provider Manager
  -> MCP Client Manager
  -> Ingestion Engine
  -> Course Orchestrator
  -> Validation Engine
  -> Artifact Store
  -> Exporter
```

The provider layer should be abstract enough to support different model backends over time. The MCP layer gives the engine a standard way to connect to tools, resources, prompt templates, local context, retrieval systems, and future workflows.

The ingestion layer is where the engine earns trust. It needs to handle directories, archives, images, PDFs, notes, repositories, and mixed file sets. It should record what it saw, what it extracted, what failed, and what was used.

The course orchestrator is the brain of the build. It plans, schedules, generates, resumes, and keeps the course coherent across many artifacts.

## The MVP

The minimum useful version is not small, but it is focused.

An MVP should let a user run one command with a learning prompt and optional source directory, review a generated blueprint, approve it, and receive a validated course package.

To count as complete, that first version should include:

- prompt intake from an argument, file, or stdin
- context intake from files, folders, archives, and images
- source manifests and ingest reports
- course blueprint generation
- approval before full generation
- lecture, lab, assignment, assessment, rubric, and answer-key generation
- Markdown plus JSON or YAML outputs
- validation and resumability
- initial VR handoff metadata

The first version does not need to solve interactive learning, automated grading, LMS replacement, accreditation, avatars, voice, or graphics.

It needs to prove that a course can be generated reliably, inspected clearly, resumed safely, and handed off to another application.

## Why This Is Worth Building

The interesting part of AI University is not that it can generate educational content. Lots of tools can do that.

The interesting part is that it treats education as a system.

A course is not one answer. It is a network of lectures, assignments, assessments, objectives, source references, and feedback loops. If the engine can generate that network in a structured way, then the same course package can support multiple experiences:

- a folder of Markdown files for self-study
- a static website
- an LMS export
- a tutoring agent
- a VR classroom
- a future interactive learning runtime

That makes the CLI more than a developer tool. It becomes the foundation for a larger education platform.

The first milestone is not to build the university.

The first milestone is to build the machine that can generate one.

Source concept: AI University CLI/Core Engine PRD.
