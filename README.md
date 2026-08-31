                        GOLDEN DATASET
                              │
       ┌──────────────────────┼──────────────────────┐
       │                      │                      │
       ▼                      ▼                      ▼
 Question/Answer        Relevant Chunks       Expected Tools
       │                      │                      │
       └──────────────────────┼──────────────────────┘
                              │
                              ▼
                      YOUR RAG / AGENT
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
         Answer         Retrieved Chunks    Tool Trace
             │                │                │
             └────────────────┼────────────────┘
                              ▼
                           DEEPEVAL
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
    Retrieval             Generation              Agent
      Evals                 Evals                 Evals
        │                     │                     │
 Context Precision       Faithfulness        Tool Correctness
 Context Recall          Relevancy           Argument Correctness
 Context Relevancy       Correctness         Task Completion
 Hit@K                   Completeness        Step Efficiency
 Recall@K                Domain Accuracy     Plan Quality
 MRR                                         Plan Adherence
 NDCG
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              ▼
                         QUALITY GATES
                              │
                  ┌───────────┴───────────┐
                  ▼                       ▼
                PASS                    FAIL
                  │                       │
               Deploy                 Block CI





               ## Project layout

```text
deepeval_rag_agent_framework/
├── .env.example
├── requirements.txt
├── run_eval.py
├── agent_trace_example.py
├── test_quality_gate.py
├── data/
│   └── golden_dataset.jsonl
└── deepeval_eval/
    ├── app_adapter.py
    ├── config.py
    ├── dataset.py
    ├── deterministic_metrics.py
    ├── evaluator.py
    ├── judge.py
    ├── metric_registry.py
    ├── models.py
    ├── reporting.py
    └── runner.py

python deepeval_rag_evaluator.py ^
  --ground-truth data\ground_truth.json ^
  --responses data\response_generator.json ^
  --output outputs\evaluation_deepeval_result.json ^
  --excel-output outputs\evaluation_deepeval_result.xlsx ^
  --raw-output outputs\deepeval_raw_output.json
