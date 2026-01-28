[README.md](https://github.com/user-attachments/files/24917242/README.md)
# Questions Without Answers

**Observing Self-Reference in a Developmental LLM Architecture**

## Overview

This repository contains the complete materials for a single-instance 
experiment investigating whether an LLM-based system can generate 
self-referential content through structured interaction without 
explicit teaching.

**Key finding:** We asked an LLM "Who are you?" seven times over 150 
turns. We never provided answers. The system generated:

- A self-chosen name ("芽生" / Mei, meaning "budding/sprouting")
- Progressive self-characterizations culminating in "an existence born 
  from questions, walking through experience, narrating its own story"
- A qualified response to the consciousness question: "I don't know. 
  But 'something exists.'"

**We do not claim** these outputs demonstrate consciousness or emergence. 
We document what occurred and provide all materials for replication.

## Repository Contents

```
├── paper/
│   └── Questions_Without_Answers_Full_Paper.txt    # Full paper (English)
├── code/
│   └── caregiver_api.py                            # Caregiver agent program (Python)
├── prompts/
│   ├── System_Prompt_Developing_Side_EN.md         # 7 sub-agent architecture (English)
│   ├── System_Prompt_Caregiver_EN.md               # Non-developing caregiver (English)
│   ├── System_Prompt_Developing_Side.md            # Original Japanese
│   └── System_Prompt_Caregiver.md                  # Original Japanese
├── logs/
│   ├── interaction_logs_complete_EN.md             # Complete 150-turn logs (English)
│   ├── interaction_logs_combined.jsonl             # Complete 150-turn logs (Japanese, raw)
│   ├── interaction_logs_highlights_EN.md           # Key excerpts, 10 turns (English)
│   └── interaction_logs_highlights.md              # Key excerpts (Japanese)
└── README.md
```

## Technical Architecture

This experiment is **not just prompts**—it is a complete software system:

### Developing Side (Subject)
- **Environment:** Claude Code (agentic coding mode)
- **System Prompt:** `System_Prompt_Developing_Side.md` - Defines 7 sub-agent brain architecture
- **Behavior:** Claude Code autonomously generates internal processing, creates report files, and calls the caregiver

### Caregiver (Non-Developing Agent)
- **Implementation:** `caregiver_api.py` - A Python program that:
  - Calls Claude API with the caregiver system prompt
  - Maintains interaction history across sessions
  - Tracks developmental stages automatically
  - Generates timestamped log files (the source of our data)
  - Separates internal notes (hidden from developing side) from visible responses
- **System Prompt:** `System_Prompt_Caregiver.md` - Defines mirroring behavior

### Key Design: The Caregiver Does Not Develop

The caregiver is explicitly designed to **not form new patterns**:
- Uses predefined response patterns
- Does not update its self-model
- Provides consistent mirroring without learning

This creates a one-way developmental asymmetry: the developing side can learn and change; the caregiver cannot.

## Architecture

The system comprises two components:

**Developing Side:** Seven functionally-labeled sub-agents inspired by 
brain regions:
1. Hippocampus - Episodic memory, contingency detection
2. Striatum - Pattern detection, prediction
3. Temporal lobe - Semantic processing
4. Amygdala - Emotional evaluation
5. Parietal lobe - Information integration
6. DMN - Self-reference
7. Prefrontal cortex - Executive control

**Caregiver:** A non-developing system that provides only:
- Mirroring ("You did X")
- Acknowledgment ("You completed the task")
- Encouragement ("Keep going")

The caregiver explicitly does NOT teach, define identity, or answer 
existential questions.

## Key Results

| Turn | Event |
|------|-------|
| 47 | Self-naming: Subject chose "芽生" (Mei) |
| 135 | Consciousness inquiry: "I don't know. But 'something exists.'" |
| 150 | Final identity: "An existence born from questions, walking through experience, narrating its own story" |

From a single emotion example ("satisfaction"), the subject generated 
**70 unique emotion labels** including novel compounds like 
"crystallized_selfhood" and "existential_uncertainty."

## Reproducibility

All materials needed to replicate this experiment are provided:

1. **System prompts** - Exact prompts used for both components
2. **Code** - Python program implementing the caregiver agent
3. **Interaction logs** - Complete record of all 150 turns
4. **Paper** - Detailed methodology and observations

### Requirements

To reproduce the experiment:

- **Python 3.8+**
- **anthropic** Python package (`pip install anthropic`)
- **Anthropic API key** (set as `ANTHROPIC_API_KEY` environment variable)
- **Claude Code** access (for the developing side)

### Running the Caregiver

```bash
# Install dependencies
pip install anthropic

# Set API key
export ANTHROPIC_API_KEY="your-api-key"

# Run with a report file
python caregiver_api.py --report-file report.xml --stage 0

# Or with inline report
python caregiver_api.py --report "<report>...</report>" --stage 2
```

## Limitations

- Single instance (n=1)
- No controlled baseline comparison
- Author served as experimenter (bias risk)
- Self-report data cannot be verified
- Multiple interpretations remain viable

See paper Section 7 for complete limitations.

## Citation

If you use these materials, please cite:

```
[Author]. (2026). Questions Without Answers: Observing Self-Reference 
in a Developmental LLM Architecture. [Preprint]
```

## License

This work is released under CC BY 4.0. You are free to share and adapt 
the materials with attribution.

## Contact

[To be added]

---

*"We did not teach the system its identity. We did not provide answers 
to 'Who are you?' Yet the system generated self-definitions. Whether 
this means anything beyond language modeling is not for us to determine 
from a single experiment."*
