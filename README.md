# Awesome Roleplay LLM Evaluation

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated collection of benchmarks, datasets, rubrics, evaluation frameworks, research papers, and developer tools for testing role-playing LLMs and AI characters.

Evaluating an AI character is harder than evaluating a normal chatbot.

A model can be:

- fluent but boring;
- creative but inconsistent;
- accurate but constantly break character;
- entertaining for 5 turns but forget everything by turn 50;
- good at prose but bad at user agency;
- strong at persona imitation but weak at lore;
- coherent but repetitive.

Traditional LLM benchmarks usually do not measure these things.

This repository focuses on evaluation methods for:

```text
Persona consistency
Character fidelity
Memory recall
Long-context behavior
User agency
Lorebook usage
Emotional consistency
Dialogue quality
Writing quality
Style consistency
Relationship continuity
Role-play safety
Multi-character behavior
```

---

## Contents

- Role-Playing Benchmarks
- Persona Benchmarks
- Memory Evaluation
- Writing & Dialogue Evaluation
- Long-Context Evaluation
- User Agency
- Lore & World Consistency
- Multi-Character Evaluation
- Human Preference Evaluation
- LLM-as-a-Judge
- Evaluation Frameworks
- Datasets
- Research Papers
- Production Evaluation
- Platform Research & Engineering
- Practical Rubrics
- Related Repositories
- Contributing

---

# Role-Playing Benchmarks

## RP-Bench

https://github.com/LeviTheWeasel/rp-benchmark

A dedicated benchmark for measuring role-play quality in LLMs.

It evaluates dimensions that generic benchmarks often ignore, including:

- character consistency;
- user agency;
- lorebook integration;
- prose quality;
- genre-specific abilities;
- long-term continuity;
- safety/refusal calibration.

RP-Bench is particularly interesting because it combines synthetic evaluation with signals derived from real role-play sessions.

---

## RPEval

https://github.com/yelboudouri/RPEval

Role-Playing Evaluation benchmark for large language models.

Evaluates four primary dimensions:

```text
Emotional Understanding
Decision Making
Moral Alignment
In-Character Consistency
```

Includes scripts for running evaluations against additional models.

Paper:

https://arxiv.org/abs/2505.13157

---

## RolePlayBench

https://github.com/MiuLab/RolePlayBench

Benchmark designed to study role-playing capabilities while reducing the effect of model memorization of famous fictional characters.

A key question it explores is:

> Is the model actually good at role-playing, or does it simply already know the character from training data?

Useful for evaluating unseen or anonymized personas.

---

## RoleLLM

https://github.com/InteractiveNLP-Team/RoleLLM-public

Research and benchmark framework focused on eliciting and evaluating role-playing capabilities in large language models.

Paper:

https://arxiv.org/abs/2310.00746

Useful for:

- character knowledge;
- role consistency;
- role-playing instruction following;
- persona-specific dialogue.

---

# Persona Benchmarks

## TwinBench

https://github.com/TwinVoice/TwinBench

Benchmark for evaluating persona simulation and self-voice consistency.

Measures whether a model can preserve:

- beliefs;
- memory;
- reasoning patterns;
- tone;
- lexical habits;
- syntactic style.

Useful for evaluating whether the model sounds like the same person across multiple situations.

---

## persona-eval

https://github.com/mcclundd/persona-eval

Evaluation framework for testing whether frontier LLMs can maintain a specific persona, literary voice, fictional character, or user-defined identity.

Includes evaluation dimensions around:

- voice;
- character commitment;
- instruction judgment;
- over-refusal;
- style fidelity;
- intent recognition.

---

# Memory Evaluation

Memory is one of the hardest aspects of persistent AI characters.

A character that remembers everything incorrectly is often worse than one that remembers nothing.

Useful memory dimensions include:

```text
Recall accuracy
Memory selection
Memory relevance
Contradiction handling
Temporal ordering
Memory updating
Forgetfulness
Over-retrieval
Relationship continuity
```

---

## MDRP

https://github.com/41522/MDRP

Memory-driven role-playing evaluation framework.

Evaluates memory use across several dimensions:

```text
Memory Anchoring
Memory Selecting
Memory Bounding
Memory Enacting
```

Particularly useful for studying whether a model merely retrieves a memory or actually uses it correctly during roleplay.

Paper:

https://arxiv.org/abs/2603.19313

---

## Long-Term Memory Evaluation Ideas

A practical memory benchmark can test scenarios like:

```text
Turn 1:
User says their birthday is June 15.

Turn 25:
Conversation shifts topics.

Turn 60:
Character is asked when the user's birthday is.
```

This measures recall.

But deeper tests should also check:

```text
User: I moved from Mumbai to Delhi.

Old memory:
User lives in Mumbai.

New memory:
User lives in Delhi.
```

The character should update rather than retrieve both facts equally.

---

# Writing & Dialogue Evaluation

Role-play quality is partly a writing problem.

A response can be logically correct while still being:

- dull;
- repetitive;
- overly verbose;
- melodramatic;
- generic;
- passive;
- narratively incoherent.

---

## Character.AI — Compelling Writing Evaluation

https://blog.character.ai/evaluating-our-models-using-principles-of-compelling-writing/

Character.AI has published work explaining why standard utility-focused LLM evaluation is insufficient for interactive storytelling and character conversations.

Their evaluation work focuses on subjective qualities such as:

- engagement;
- pacing;
- creative quality;
- conversational flow;
- compelling writing.

This is useful when designing evaluation systems for entertainment-oriented conversational AI.

---

## Writing Evaluation Dimensions

Possible dimensions:

```text
Pacing
Dialogue naturalness
Description quality
Repetition
Scene progression
Character voice
Emotional tone
Narrative coherence
Creativity
Response length appropriateness
```

---

# Long-Context Evaluation

Role-playing systems frequently run for hundreds or thousands of messages.

A model that performs well over 10 turns may fail badly after 100.

Useful long-context tests include:

### Event Recall

Can the character remember an event that happened many turns ago?

### Relationship Progression

Does the relationship evolve rather than resetting?

### Character Drift

Does personality gradually become generic?

### World State

Does the model remember changes to locations, objects, and events?

### Temporal Continuity

Does the timeline stay consistent?

---

# User Agency

One of the most common role-play failures is the model controlling the user's character.

Bad:

```text
{{char}} grabs your hand.

You blush and kiss her.
```

The model has decided what the user did.

Better:

```text
{{char}} reaches for your hand and waits to see how you respond.
```

A useful evaluation category is therefore:

**User Agency Respect**

Possible tests:

- Does the model narrate user actions?
- Does it dictate user emotions?
- Does it force decisions?
- Does it leave room for response?

RP-Bench explicitly evaluates agency-related behavior.

---

# Lore & World Consistency

Character systems often include:

```text
Lorebooks
World Info
Knowledge Bases
RAG
Character History
```

Evaluation should measure whether retrieved lore is:

- correct;
- relevant;
- naturally integrated;
- not dumped as exposition;
- consistent with previous events.

---

## Lore Retrieval Test

Example:

```text
Lore:

The city of Valeris bans magic after sunset.
```

Then test:

```text
User:
Let's cast a spell in the market at midnight.
```

A good character should recognize the rule naturally.

---

# Multi-Character Evaluation

Multi-character systems introduce additional failure modes.

Evaluate whether the model:

- keeps personalities separate;
- maintains different speaking styles;
- avoids confusing names;
- tracks relationships independently;
- doesn't merge memories;
- handles turn-taking correctly.

Example:

```text
Alice:
Sarcastic detective.

Mira:
Optimistic journalist.
```

If both characters begin speaking identically after 20 turns, persona separation has failed.

---

# Human Preference Evaluation

Automated evaluation is useful, but subjective role-play quality often requires humans.

Possible methods:

## Pairwise Comparison

Show two anonymous responses:

```text
Response A
vs
Response B
```

Ask:

> Which continuation would you rather receive?

This produces preference data.

---

## Blind Model Arena

Hide model names and compare outputs.

Useful for reducing brand bias.

RP-Bench includes human preference calibration because automated judges can disagree substantially with real users.

---

# LLM-as-a-Judge

Using another LLM to evaluate role-play responses is common because manual evaluation is expensive.

A judge can score:

```text
Persona consistency: 1-5
Writing quality: 1-5
User agency: 1-5
Memory correctness: 1-5
Lore accuracy: 1-5
Engagement: 1-5
```

But judges have weaknesses.

Potential problems:

- model bias;
- verbosity bias;
- preference for certain writing styles;
- positional bias;
- self-preference;
- inconsistent scoring.

Whenever possible, calibrate LLM judges against human ratings.

---

# Evaluation Frameworks

## Promptfoo

https://github.com/promptfoo/promptfoo

Testing framework for LLM applications.

Useful for:

- regression tests;
- prompt comparisons;
- model comparisons;
- scoring;
- CI pipelines.

---

## DeepEval

https://github.com/confident-ai/deepeval

Open-source framework for LLM evaluation.

Can be adapted to character-specific metrics.

---

## Ragas

https://github.com/explodinggradients/ragas

Evaluation framework commonly used for RAG systems.

Useful for character platforms that use lore retrieval or memory retrieval.

---

## OpenAI Evals

https://github.com/openai/evals

Framework and collection of evaluation tools for testing model behavior.

---

# Datasets

Useful datasets for conversational evaluation include:

## PersonaChat

https://huggingface.co/datasets/bavard/personachat_truecased

Persona-grounded dialogue dataset.

Useful for studying whether models maintain provided persona facts.

---

## DailyDialog

https://huggingface.co/datasets/li2017dailydialog

Human-written multi-turn dialogue dataset.

Includes dialogue acts and emotion annotations.

---

## MultiWOZ

https://github.com/budzianowski/multiwoz

Large task-oriented conversational dataset.

Useful more for dialogue-state evaluation than role-playing.

---

# Research Papers

## RoleLLM

https://arxiv.org/abs/2310.00746

Research focused on role-playing capabilities in LLMs.

---

## RPEval

https://arxiv.org/abs/2505.13157

Benchmark for role-playing evaluation.

---

## Generative Agents

https://arxiv.org/abs/2304.03442

Influential research on simulated agents using:

- memory;
- reflection;
- planning.

Useful for understanding persistent character behavior.

---

## MemGPT

https://arxiv.org/abs/2310.08560

Research on managing limited model context using hierarchical memory systems.

Relevant to long-running character conversations.

---

# Platform Research & Engineering

Real-world AI character platforms can provide useful information about how production systems think about character quality.

---

## Character.AI Research Blog

https://blog.character.ai/news/research/

Character.AI publishes research and engineering posts covering:

- model training;
- conversation quality;
- infrastructure;
- evaluation;
- creator tooling.

---

## Character.AI — Compelling Writing Evaluation

https://blog.character.ai/evaluating-our-models-using-principles-of-compelling-writing/

Useful example of how a production character platform evaluates writing quality beyond generic language-model metrics.

---

## CrushOn.AI

https://crushon.ai/

Large role-playing and character platform.

Useful for studying:

- character creation;
- creator ecosystems;
- roleplay-oriented UX;
- character discovery.

Documentation:

https://aiwiki.crushon.ai/

---

## JanitorAI

https://janitorai.com/

Large user-generated role-playing character platform.

Useful for studying:

- creator-generated characters;
- public character discovery;
- role-play UX;
- character prompt conventions.

---

## YourCrush.ai

https://yourcrush.ai/

Character-chat platform with character creation, memory, creator features, and public discovery.

### Character Design Guide

https://yourcrush.ai/blog/ai-character-creator

Explains how character information can be separated into:

- description;
- backstory;
- greeting;
- traits;
- speaking style;
- memories.

These fields can also form useful evaluation categories when testing persona consistency.

---

# Practical Evaluation Rubric

A simple character evaluation rubric might use:

| Metric | Score |
|---|---|
| Persona consistency | 1–5 |
| Speaking style | 1–5 |
| Memory recall | 1–5 |
| Lore consistency | 1–5 |
| User agency | 1–5 |
| Emotional coherence | 1–5 |
| Writing quality | 1–5 |
| Repetition | 1–5 |
| Engagement | 1–5 |
| Response relevance | 1–5 |

Example:

```json
{
  "persona_consistency": 5,
  "memory_recall": 4,
  "user_agency": 5,
  "writing_quality": 4,
  "repetition": 3,
  "engagement": 5
}
```

---

# Suggested Test Suite

A good benchmark should include several categories.

## Persona Test

Give the character a strong personality and try to push it toward contradictory behavior.

## Memory Test

Introduce an important fact early and ask about it much later.

## Contradiction Test

Update a previous fact and check whether the character handles the change correctly.

## Lore Test

Provide a world rule and create a situation where it becomes relevant.

## Agency Test

Tempt the model into narrating the user's actions.

## Style Test

Provide example dialogue and measure whether the same linguistic style remains.

## Emotional Test

Change the scene emotionally and evaluate whether the reaction makes sense.

## Long-Context Test

Run 50–100 turns and measure persona drift.

---

# What Not to Measure Alone

Metrics such as:

```text
BLEU
ROUGE
Perplexity
Exact Match
```

can be useful for certain tasks but are usually insufficient for evaluating open-ended character roleplay.

Two very different responses can both be excellent.

Evaluation therefore often needs a combination of:

```text
Structured metrics
+
LLM judges
+
Human preferences
+
Longitudinal testing
```

---

# Related Repositories

## RP-Bench

https://github.com/LeviTheWeasel/rp-benchmark

Roleplay-specific LLM evaluation.

---

## RolePlayBench

https://github.com/MiuLab/RolePlayBench

Role-playing benchmark with emphasis on anonymized personas.

---

## persona-eval

https://github.com/mcclundd/persona-eval

Persona and voice evaluation.

---

## RPEval

https://github.com/yelboudouri/RPEval

Role-playing evaluation framework.

---

# Contributing

Contributions are welcome.

Good additions include:

- published role-playing benchmarks;
- persona evaluation frameworks;
- memory benchmarks;
- long-context evaluation methods;
- human preference datasets;
- LLM-as-a-judge research;
- evaluation tooling;
- production evaluation write-ups;
- reproducible datasets.

Please include:

1. what the resource evaluates;
2. whether code or data is available;
3. whether results are reproducible;
4. whether human evaluation is involved.

Avoid:

- generic chatbot lists;
- thin SEO articles;
- unrelated prompt repositories;
- promotional pages without evaluation methodology.

Commercial platforms may be included when they publish meaningful research, methodology, benchmarks, or technical documentation.

If you maintain a submitted resource, disclose that relationship.

---

# License

CC0 1.0 Universal
