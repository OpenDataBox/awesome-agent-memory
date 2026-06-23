# Awesome Agent Memory

```
@article{memoryasdata,
    title={Are We Ready For An Agent-Native Memory System?},
    author={Wei Zhou and Xuanhe Zhou and Shaokun Han and Hongming Xu and Guoliang Li and Zhiyu Li and Feiyu Xiong and Fan Wu},
    year={2026},
    note={Under review}
}
```

## Table of Contents

- [Overview](#overview)
- [Memory Systems](#memory-systems)
  - [Sequential Context](#sequential-context)
  - [Structural Topological](#structural-topological)
  - [Multi-Paradigm Hybrid](#multi-paradigm-hybrid)
- [Reference Baselines](#reference-baselines)
  - [Context-Based Baselines](#context-based-baselines)
  - [Retrieval-Based Baselines](#retrieval-based-baselines)
- [Benchmarks](#benchmarks)
- [Surveys on Agent Memory](#surveys-on-agent-memory)

## Overview

Agent memory has rapidly evolved from simple retrieval-augmented mechanisms into a data management system that supports persistent information storage, retrieval, update, consolidation, and dynamic lifecycle governance throughout agent execution. The paper decomposes agent memory into four core modules:

1. **Memory Representation and Storage** -- defines the logical and physical memory format
2. **Memory Extraction** -- transforms raw input streams into logical memory primitives
3. **Memory Retrieval and Routing** -- dynamically identifies and extracts relevant historical context
4. **Memory Maintenance** -- governs the dynamic lifecycle of memory entries (conflict resolution, capacity management, semantic consolidation)

[⬆️top](#table-of-contents)

## Memory Systems

### Sequential Context

Systems that model memory as flat, one-dimensional sequences lacking explicit structural abstractions.

1. **MemoChat: Tuning LLMs to Use Memos for Consistent Long-Range Open-Domain Conversation**
   Junru Lu, Siyu An, Mingbao Lin, et al. *arXiv 2023*. [[Paper](https://arxiv.org/abs/2308.08239)]

2. **Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory**
   Prateek Chhikara, Dev Khant, Saket Aryan, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2504.19413)] [[Github](https://github.com/mem0ai/mem0)]

3. **MEM1: Learning to Synergize Memory and Reasoning for Efficient Long-Horizon Agents**
   Zijian Zhou, Ao Qu, Zhaoxuan Wu, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2506.15841)]

4. **MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent**
   Hongli Yu, Tinghong Chen, Jiangtao Feng, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2507.02259)]

[⬆️top](#table-of-contents)

### Structural Topological

Systems that abstract memory into structured graph and tree topologies with interconnected nodes and edges.

5. **MemTree: From Isolated Conversations to Hierarchical Schemas: Dynamic Tree Memory Representation for LLMs**
   Alireza Rezazadeh, Zichao Li, Wei Wei, Yujia Bao. *ICLR 2025*. [[Paper](https://openreview.net/forum?id=moXtEmCleY)]

6. **Zep: A Temporal Knowledge Graph Architecture for Agent Memory**
   Preston Rasmussen, Pavel Paliychuk, Travis Beauvais, Jesse Ryan. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2501.13956)] [[Github](https://github.com/getzep/zep)]

7. **Mem0 (Graph Mode, Mem0^g)**: Graph-variant of Mem0 that formalizes memory as a directed labeled graph with entity-relation triplets, using a heterogeneous multi-engine (vector + graph DB) backend. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2504.19413)] [[Github](https://github.com/mem0ai/mem0)]

8. **Cognee: Optimizing the Interface Between Knowledge Graphs and LLMs for Complex Reasoning**
   Vasilije Markovic, Lazar Obradovic, Laszlo Hajdu, Jovan Pavlovic. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2505.24478)] [[Github](https://github.com/topoteretes/cognee)]

[⬆️top](#table-of-contents)

### Multi-Paradigm Hybrid

Systems that package memory into complex, multi-part data containers combining unstructured text with structured metadata; some also route memory across heterogeneous backends.

9. **LightMem: Lightweight and Efficient Memory-Augmented Generation**
   Jizhan Fang, Xinle Deng, Haoming Xu, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2510.18866)]

10. **SimpleMem: Efficient Lifelong Memory for LLM Agents**
    Jiaqi Liu, Yaofeng Su, Peng Xia, et al. *arXiv 2026*. [[Paper](https://arxiv.org/abs/2601.02553)]

11. **MemOS: A Memory OS for AI System**
    Zhiyu Li, Shichao Song, Chenyang Xi, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2507.03724)] [[Github](https://github.com/MemTensor/MemOS)]

12. **MemoryOS: Memory OS of AI Agent**
    Jiazheng Kang, Mingming Ji, Zhe Zhao, Ting Bai. *EMNLP 2025*. [[Paper](https://arxiv.org/abs/2506.06326)] [[Github](https://github.com/BAI-LAB/MemoryOS)]

13. **A-MEM: Agentic Memory for LLM Agents**
    Wujiang Xu, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2502.12110)] [[Github](https://github.com/agiresearch/A-mem)]

14. **Letta (MemGPT): Towards LLMs as Operating Systems**
    Charles Packer, Vivian Fang, Shishir G. Patil, et al. *arXiv 2023*. [[Paper](https://arxiv.org/abs/2310.08560)] [[Github](https://github.com/letta-ai/letta)]

[⬆️top](#table-of-contents)

## Reference Baselines

### Context-Based Baselines

1. **Long Context**: A naive baseline that passes the full conversation history directly into the LLM context window without any external memory system. While effective on some tasks, it results in unacceptable latencies and token costs for production deployments.

### Retrieval-Based Baselines

1. **Embedding RAG**: A standard dense retrieval baseline that embeds past interactions into vectors and performs top-k similarity search, without any memory-specific extraction, maintenance, or routing logic.

2. **BM25**: A sparse lexical retrieval baseline using Okapi BM25 scoring for full-text search, evaluated in the appendix experiments.

3. **Contriever**: An unsupervised dense retrieval model used as a retrieval baseline in the appendix experiments. *ICLR 2023*. [[Paper](https://arxiv.org/abs/2112.09118)]

4. **GraphRAG**: A graph-based retrieval-augmented generation approach that constructs a knowledge graph from documents and retrieves via graph traversal. *arXiv 2024*. [[Paper](https://arxiv.org/abs/2404.16130)]

5. **HippoRAG**: A retrieval-augmented generation method inspired by the hippocampal memory indexing theory, using knowledge graph triples and dense vector embeddings. *NeurIPS 2024*. [[Paper](https://arxiv.org/abs/2405.14831)]

[⬆️top](#table-of-contents)

## Benchmarks

The following benchmarks are used to evaluate agent memory systems across five research questions (RQ1--RQ5), covering task effectiveness, retrieval fidelity, update robustness, long-horizon stability, and operational cost.

1. **LoCoMo: Evaluating Very Long-Term Conversational Memory of LLM Agents**
   Adyasha Maharana, Dong-Ho Lee, Sergey Turishcheva, et al. *ACL 2024*. [[Paper](https://arxiv.org/abs/2402.10790)]
   - Long-conversation QA benchmark testing episodic, temporal, open-domain, and single-hop memory over multi-turn interactions (50 multi-modal chats; 9,209 tokens and 304 turns avg.)

2. **LongMemEval: Benchmarking Chat Assistants on Long-Term Interactive Memory**
   Di Wu, Hongwei Wang, Wenhao Yu, et al. *ICLR 2025*. [[Paper](https://arxiv.org/abs/2410.10813)]
   - Multi-session long-memory benchmark evaluating cross-session QA and temporal knowledge updates (500 QA pairs; up to 1.5M tokens)

3. **LongBench v2: Towards Deeper Understanding and Reasoning on Realistic Long-context Multitasks**
   Yushi Bai, Shangqing Tu, Jiajie Zhang, et al. *ACL 2025 / arXiv 2024*. [[Paper](https://arxiv.org/abs/2412.15204)]
   - Extreme long-context benchmark with 503 multiple-choice questions spanning 8K to 2M-word contexts, used for short, medium, and long context-length stability analysis

4. **LifelongAgentBench: Evaluating LLM Agents as Lifelong Learners**
   Junhao Zheng, Xidi Cai, Qiuke Li, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2505.11942)]
   - Evaluates sequential procedural skill transfer across structurally related database, operating system, and knowledge graph tasks (1,396 tasks sharing atomic skills)

5. **MemBench: Towards More Comprehensive Evaluation on the Memory of LLM-based Agents**
   Haoran Tan, Zeyu Zhang, Chen Ma, et al. *ACL 2025 (Findings)*. [[Paper](https://arxiv.org/abs/2506.21605)]
   - Measures memory capabilities across different abstraction levels (factual vs. reflective) and noise conditions, with stress tests up to 100K sessions

6. **MemoryAgentBench: Evaluating Memory in LLM Agents via Incremental Multi-Turn Interactions**
   Yuanzhe Hu, Yu Wang, Julian McAuley. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2507.05257)]
   - Tests four core competencies: accurate retrieval, test-time learning, long-range understanding, and selective forgetting across 14 datasets with context lengths ranging from 103K to 1.44M tokens

[⬆️top](#table-of-contents)

## Surveys on Agent Memory

1. **A Survey on the Memory Mechanism of Large Language Model based Agents**
   Zeyu Zhang, Xiaohe Bo, Chen Ma, et al. *ACM Transactions on Information Systems 2025*. [[Paper](https://arxiv.org/abs/2404.13501)]

2. **Memory in the Age of AI Agents**
   Yuyang Hu, Shichun Liu, Yanwei Yue, et al. *arXiv 2025*. [[Paper](https://arxiv.org/abs/2512.13564)]

3. **Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers**
   Pengfei Du. *arXiv 2026*. [[Paper](https://arxiv.org/abs/2603.07670)]

4. **Memory in the LLM Era: Modular Architectures and Strategies in a Unified Framework**
   Yanchen Wu, Tenghui Lin, Yingli Zhou, et al. *Proceedings of the VLDB Endowment 2026*. [[Paper](https://arxiv.org/abs/2604.01707)]

5. **Graph-based Agent Memory: Taxonomy, Techniques, and Applications**
   Chang Yang, Chuang Zhou, Yilin Xiao, et al. *arXiv 2026*. [[Paper](https://arxiv.org/abs/2602.05665)]

6. **Lifelong Learning of Large Language Model based Agents: A Roadmap**
   Junhao Zheng, Chengming Shi, Xidi Cai, et al. *IEEE Transactions on Pattern Analysis and Machine Intelligence 2025*. [[Paper](https://arxiv.org/abs/2501.07278)]

[⬆️top](#table-of-contents)
