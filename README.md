# Awesome-LLM-Planning-Capability
[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of papers and resources based on our survey paper [**"PlanGenLLMs: A Modern Survey of LLM Planning Capabilities"**](https://arxiv.org/abs/2502.11221).

![llm-planning](./Figures/llm-planning.png)

**Please cite the paper in [Citation](https://github.com/wll199566/awesome-llm-planning-capability#citation) if you find the paper list and resources in this repository helpful for your research. Thanks!**

## Introduction

LLMs have immense potential for generating plans, transforming an initial world state into a desired goal state. A large body of research has explored the use of LLMs for various planning tasks, from web navigation to travel planning and database querying. However, many of these systems are tailored to specific problems, making it challenging to compare them or determine the best approach for new tasks. There is also a lack of clear and consistent evaluation criteria. Our survey aims to offer a comprehensive overview of current LLM planners to fill this gap. It builds on foundational work by [Kartam and Wilkins (1990)](https://stacks.stanford.edu/file/druid:pt284sd5701/TR008.pdf) and examines six key performance criteria: **completeness**, **executability**, **optimality**, **representation**, **generalization**, and **efficiency**. For each, we provide a thorough analysis of representative works and highlight their strengths and weaknesses. Our paper also identifies crucial future directions, making it a valuable resource for both practitioners and newcomers interested in leveraging LLM planning to support agentic workflows.

## Contents

- [Awesome-LLM-Planning-Capability ](#awesome-llm-planning-capability)
  - [Introduction](#introduction)
  - [Contents](#contents)
  - [LLM Planning Foundations](#llm-planning-foundation)
    - [Introduction](#foundation-introduction)
    - [Task Decomposition](#task-decomposition)
    - [LLM + Classical Planner ](#llm-classical-planner)
    - [Search Algorithm](#search-algorithm)
    - [Fine-Tuning](#fine-tuning)
  - [Performance Criteria](#performance-criteria )
    - [Introduction](#performance-criteria-introduction)
    - [Completeness](#completeness)
      - [Plan Correctness](#plan-correctness)
      - [Plan Achievability](#plan-achievability)
    - [Executability](#executability)
      - [Object Grounding](#object-grounding)
      - [Action Grounding](#action-grounding)
      - [Sample-then-Filter](#sample-then-filter)
      - [Closed-Loop System](#closed-loop-system)
    - [Optimality](#optimality)
      - [LLM + Optimizer ](#llm-optimizer)
      - [A* Search-Based Methods](#a-search-methods)
    - [Representation](#representation)
      - [LLM-as-a-Translator](#llm-as-a-translator)
      - [LLM-as-a-Planner](#llm-as-a-planner)
    - [Generalization](#generalization)
      - [Fine-Tuning](#fine-tuning-generalization)
      - [Generalized Planning](#generalized-planning)
      - [Skill Storage](#generalized-planning)
    - [Efficiency](#efficiency)
      - [Reduced LLM and World Model Calls](#reduce-llm-world-model-calls)
      - [Shorter Inputs and Outputs](#shorter-inputs-outputs)
      - [Smaller Model Size](#smaller-model-size)
  - [Evaluation](#evaluation)
    - [Datasets](#evaluation-datasets)
      - [Planning Focused](#planning-focused-dataset)
      - [Downstream Tasks](#downstream-tasks-datasets)
    - [Methods](#evaluation-methods)
      - [Verifier and Groundtruth](#verifier-groundtruth)
      - [Human Evaluation](#human-evaluation)
      - [LLM-as-a-Judge](#llm-as-a-judge) 
    - [Metrics](#evaluation-metrics)
  - [Other Related Surveys](#other-surveys)
  - [Citations](#citations)

## Citation

Please cite the following paper if you find the resource helpful for your research.

```
@article{wei2025plangenllms,
  title={Plangenllms: A modern survey of llm planning capabilities},
  author={Wei, Hui and Zhang, Zihao and He, Shenghua and Xia, Tian and Pan, Shijia and Liu, Fei},
  journal={arXiv preprint arXiv:2502.11221},
  year={2025}
}
```







