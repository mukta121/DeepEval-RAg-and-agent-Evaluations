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
