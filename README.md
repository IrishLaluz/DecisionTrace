# DecisionTrace

**DecisionTrace is a simple, powerful tool for creating an audit trail of your AI's decisions. Think of it as a flight data recorder for your AI.**

It ensures that every important decision your AI makes is logged in a secure, tamper-evident way, so you can always go back and understand *why* a decision was made.

## Features

-   **Append-Only Log:** Creates a secure, unchangeable log of AI decisions.
-   **Integrity Chain:** Uses a hash chain (like a lightweight blockchain) to prevent tampering and guarantee the chronological order of decisions.
-   **Replay Capability:** Easily "replay" any past decision to see the full context: the prompt, the model used, the output, and more.
-   **Verification:** A simple command to verify the entire log's integrity and detect any corruption or tampering.

## Quick Start

### 1. Installation

First, clone the repository. Then, navigate into the `decisiontrace` directory and install the tool:

```bash
# Install the package in editable mode
pip install -e .
```
This adds the `decisiontrace` command to your system.

### 2. How to Use

#### Log a Decision
Create a `.json` file (e.g., `my_decision.json`) with your AI's decision details:
```json
{
  "model": "llama3.2:1b-instruct",
  "config": { "temperature": 0.7 },
  "prompt": "Should we approve this loan?",
  "context_sources": ["policy_v4.pdf", "user_credit_report.json"],
  "output": "Approval recommended based on high credit score.",
  "confidence": 0.95,
  "risk_flags": ["user_pii_involved"]
}
```
Then, log it:
```bash
decisiontrace log my_decision.json
```

#### Replay a Decision
Use the `decision_id` from the log output to see the full details of a past decision:
```bash
decisiontrace replay <your-decision-id>
```

#### Verify the Log
Check the entire history for tampering:
```bash
decisiontrace verify
```

That's it! You now have a secure, auditable log of your AI's decisions.