# Awesome-LLM-Planning-Capability
[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of papers and resources based on our survey paper [**"PlanGenLLMs: A Modern Survey of LLM Planning Capabilities"**](https://arxiv.org/abs/2502.11221), which is published at **ACL 2025**.

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
    - [Introduction](#evaluation-introduction)
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


## LLM Planning Foundations

### Task Decomposition
1. **Describe, Explain, Plan and Select: Interactive Planning with LLMs Enables Open-World Multi-Task Agents** `NeurIPS 2023` 

    *Zihao Wang, Shaofei Cai, Guanzhou Chen, Anji Liu, Xiaojian Ma, Yitao Liang* [[PDF](https://arxiv.org/pdf/2302.01560)] [[Code](https://github.com/CraftJarvis/MC-Planner)]

2. **ProgPrompt: Generating Situated Robot Task Plans using Large Language Models.** `ICRA 2023` 
  
    *Ishika Singh, Valts Blukis, Arsalan Mousavian, Ankit Goyal, Danfei Xu, Jonathan Tremblay, Dieter Fox, Jesse Thomason, Animesh Garg* [[PDF](https://arxiv.org/abs/2209.11302)] [[Code](https://github.com/NVlabs/progprompt-vh)]

3. **Can Graph Learning Improve Planning in LLM-based Agents?** `NeurIPS 2024`
  
    *Xixi Wu, Yifei Shen, Caihua Shan, Kaitao Song, Siwei Wang, Bohang Zhang, Jiarui Feng, Hong Cheng, Wei Chen, Yun Xiong, Dongsheng Li* [[PDF](https://arxiv.org/pdf/2405.19119)] [[Code](https://github.com/WxxShirley/GNN4TaskPlan)]

4. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
  
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

5. **SelfGoal: Your Language Agents Already Know How to Achieve High-level Goals** `NACCL 2025` 
  
    *Ruihan Yang, Jiangjie Chen, Yikai Zhang, Siyu Yuan, Aili Chen, Kyle Richardson, Yanghua Xiao, Deqing Yang* [[PDF](https://arxiv.org/pdf/2406.04784)] [[Code](https://github.com/rhyang2021/SELFGOAL)]

6. **Adapt: As-needed decomposition and planning with language models** `NAACL 2024 Findings`
  
    *Archiki Prasad, Alexander Koller, Mareike Hartmann, Peter Clark, Ashish Sabharwal, Mohit Bansal, Tushar Khot* [[PDF](https://arxiv.org/pdf/2311.05772)] [[Code](https://github.com/archiki/ADaPT)]


### LLM + Classic Planners
1. **LLM+P: Empowering Large Language Models with Optimal Planning Proficiency** `Preprint`

    *Bo Liu, Yuqian Jiang, Xiaohan Zhang, Qiang Liu, Shiqi Zhang, Joydeep Biswas, Peter Stone* [[PDF](https://arxiv.org/pdf/2304.11477)] [[Code](https://github.com/Cranial-XIX/llm-pddl)]

2. **Dynamic Planning with a LLM** `NeurIPS 2024 LanGame Workshop`

    *Gautier Dagan, Frank Keller, Alex Lascarides* [[PDF](https://arxiv.org/pdf/2308.06391)] [[Code](https://github.com/itl-ed/llm-dp)]

3. **Leveraging Pre-trained Large Language Models to Construct and Utilize World Models for Model-based Task Planning** `NeurIPS 2023`

    *Lin Guan, Karthik Valmeekam, Sarath Sreedharan, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2305.14909)] [[Code](https://github.com/GuanSuns/LLMs-World-Models-for-Planning)]

4. **Language Agent Tree Search Unifies Reasoning Acting and Planning in Language Models** `ICML 2024`

    *Andy Zhou, Kai Yan, Michal Shlapentokh-Rothman, Haohan Wang, Yu-Xiong Wang* [[PDF](https://arxiv.org/pdf/2310.04406)] [[Code](https://github.com/lapisrocks/LanguageAgentTreeSearch)]

5. **On the Planning Abilities of Large Language Models (A Critical Investigation with a Proposed Benchmark)** `NeurIPS 2023`

    *Karthik Valmeekam, Sarath Sreedharan, Matthew Marquez, Alberto Olmo, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2302.06706)] [[Code](https://github.com/karthikv792/LLMs-Planning)]

6. **What's the Plan? Evaluating and Developing Planning-Aware Techniques for Language Models** `Preprint`

    *Eran Hirsch, Guy Uziel, Ateret Anaby-Tavor* [[PDF](https://arxiv.org/pdf/2402.11489)]

7. **Tree Search for Language Model Agents** `Preprint`

    *Jing Yu Koh, Stephen McAleer, Daniel Fried, Ruslan Salakhutdinov* [[PDF](https://arxiv.org/pdf/2302.06706)] [[Code](https://github.com/kohjingyu/search-agents)]


### Search Algorithm
1. **Tree of Thoughts: Deliberate Problem Solving with Large Language Models** `NeurIPS 2023`

    *Shunyu Yao, Dian Yu, Jeffrey Zhao, Izhak Shafran, Thomas L. Griffiths, Yuan Cao, Karthik Narasimhan* [[PDF](https://arxiv.org/pdf/2305.10601)] [[Code](https://github.com/princeton-nlp/tree-of-thought-llm)]

2. **Thought of Search: Planning with Language Models Through The Lens of Efficiency** `NeurIPS 2024`

    *Michael Katz, Harsha Kokel, Kavitha Srinivas, Shirin Sohrabi* [[PDF](https://arxiv.org/pdf/2404.11833)]

3. **Large Language Models as Commonsense Knowledge for Large-Scale Task Planning** `NeurIPS 2023`

    *Zirui Zhao, Wee Sun Lee, David Hsu* [[PDF](https://arxiv.org/pdf/2305.14078)] [[Code](https://github.com/1989Ryan/llm-mcts)]

4. **Reasoning with Language Model is Planning with World Model** ``

    *Shibo Hao, Yi Gu, Haodi Ma, Joshua Jiahua Hong, Zhen Wang, Daisy Zhe Wang, Zhiting Hu* [[PDF](https://arxiv.org/pdf/2305.14992)] [[Code](https://github.com/Ber666/RAP)]

5. **Language Agent Tree Search Unifies Reasoning Acting and Planning in Language Models** `ICML 2024`

    *Andy Zhou, Kai Yan, Michal Shlapentokh-Rothman, Haohan Wang, Yu-Xiong Wang* [[PDF](https://arxiv.org/pdf/2310.04406)] [[Code](https://github.com/lapisrocks/LanguageAgentTreeSearch)]

6. **What's the Plan? Evaluating and Developing Planning-Aware Techniques for Language Models** `Preprint`

    *Eran Hirsch, Guy Uziel, Ateret Anaby-Tavor* [[PDF](https://arxiv.org/pdf/2402.11489)]

7. **Tree Search for Language Model Agents** `Preprint`

    *Jing Yu Koh, Stephen McAleer, Daniel Fried, Ruslan Salakhutdinov* [[PDF](https://arxiv.org/pdf/2302.06706)] [[Code](https://github.com/kohjingyu/search-agents)]

8. **Monte Carlo Planning with Large Language Model for Text-Based Game Agents** `ICLR 2025`

    *Zijing Shi, Meng Fang, Ling Chen* [[PDF](https://arxiv.org/pdf/2504.16855)] [[Code](https://github.com/winni18/MC-DML)]

9. **Scaling Autonomous Agents via Automatic Reward Modeling And Planning** `ICLR 2025`

    *Zhenfang Chen, Delin Chen, Rui Sun, Wenjun Liu, Chuang Gan* [[PDF](https://arxiv.org/pdf/2502.12130)] [[Code](https://github.com/heaplax/ARMAP)]


### Fine-Tuning
1. **Visually-Grounded Planning without Vision: Language Models Infer Detailed Plans from High-level Instructions** `EMNLP 2020 Findings`

    *Peter A. Jansen* [[PDF](https://arxiv.org/pdf/2009.14259)]

2. **Learning to Reason over Scene Graphs: A Case Study of Finetuning GPT-2 into a Robot Language Model for Grounded Task Planning** `Frontiers in Robotics and AI`
   
    *Georgia Chalvatzaki, Ali Younes, Daljeet Nandha, An Le, Leonardo F. R. Ribeiro, Iryna Gurevych* [[PDF](https://arxiv.org/pdf/2305.07716)]

3. **Trial and Error: Exploration-Based Trajectory Optimization for LLM Agents** `ACL 2024`

    *Yifan Song, Da Yin, Xiang Yue, Jie Huang, Sujian Li, Bill Yuchen Lin* [[PDF](https://arxiv.org/pdf/2403.02502)] [[Code](https://github.com/Yifan-Song793/ETO)]

4. **Agent-FLAN: Designing Data and Methods of Effective Agent Tuning for Large Language Models** `ACL 2024 Findings`

    *Zehui Chen, Kuikun Liu, Qiuchen Wang, Wenwei Zhang, Jiangning Liu, Dahua Lin, Kai Chen, Feng Zhao* [[PDF](https://arxiv.org/pdf/2403.12881)] [[Code](https://github.com/InternLM/Agent-FLAN)]

5. **AgentOhana: Design Unified Data and Training Pipeline for Effective Agent Learning** `NAACL 2025`

    *Jianguo Zhang, Tian Lan, Rithesh Murthy, Zhiwei Liu, Weiran Yao, Ming Zhu, Juntao Tan, Thai Hoang, Zuxin Liu, Liangwei Yang, Yihao Feng, Shirley Kokane, Tulika Awalgaonkar, Juan Carlos Niebles, Silvio Savarese, Shelby Heinecke, Huan Wang, Caiming Xiong* [[PDF](https://arxiv.org/pdf/2402.15506)] [[Code](https://github.com/SalesforceAIResearch/xLAM)]

6. **Learning From Failure: Integrating Negative Examples when Fine-tuning Large Language Models as Agents** `NAACL 2025`

    *Renxi Wang, Haonan Li, Xudong Han, Yixuan Zhang, Timothy Baldwin* [[PDF](https://arxiv.org/pdf/2402.11651)] [[Code](https://github.com/Reason-Wang/NAT)]


## Performance Criteria

### Completeness

#### Plan Correctness
1. **Leveraging Pre-trained Large Language Models to Construct and Utilize World Models for Model-based Task Planning** `NeurIPS 2023`

    *Lin Guan, Karthik Valmeekam, Sarath Sreedharan, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2305.14909)] [[Code](https://github.com/GuanSuns/LLMs-World-Models-for-Planning)]

2.  **Large Language Models Can Solve Real-World Planning Rigorously with Formal Verification Tools** `NAACL 2025`
    
    *Yilun Hao, Yongchao Chen, Yang Zhang, Chuchu Fan* [[PDF](https://arxiv.org/pdf/2404.11891)] [[Code](https://github.com/yih301/LLM_Formal_Travel_Planner)]


#### Plan Achievability
1. **Can Large Language Models be Good Path Planners? A Benchmark and Investigation on Spatial-temporal Reasoning** `ICLR 2024 Workshop on Large Language Model (LLM) Agents`

    *Mohamed Aghzal, Erion Plaku, Ziyu Yao* [[PDF](https://arxiv.org/pdf/2310.03249)] [[Code](https://github.com/MohamedAghzal/llms-as-path-planners)]

2. **LLMs Still Can't Plan; Can LRMs? A Preliminary Evaluation of OpenAI's o1 on PlanBench** `Preprint`

    *Karthik Valmeekam, Kaya Stechly, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2409.13373)]

3. **Thought of Search: Planning with Language Models Through The Lens of Efficiency** `NeurIPS 2024`

    *Michael Katz, Harsha Kokel, Kavitha Srinivas, Shirin Sohrabi* [[PDF](https://arxiv.org/pdf/2404.11833)]


### Executability

#### Object Grounding
1. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
   
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

2. **Inner Monologue: Embodied Reasoning through Planning with Language Models** `CoRL 2022`
   
    *Wenlong Huang, Fei Xia, Ted Xiao, Harris Chan, Jacky Liang, Pete Florence, Andy Zeng, Jonathan Tompson, Igor Mordatch, Yevgen Chebotar, Pierre Sermanet, Noah Brown, Tomas Jackson, Linda Luu, Sergey Levine, Karol Hausman, Brian Ichter* [[PDF](https://arxiv.org/pdf/2207.05608)]

3. **Do As I Can, Not As I Say: Grounding Language in Robotic Affordances**  `Preprint`
   
    *Michael Ahn, Anthony Brohan, Noah Brown, Yevgen Chebotar, Omar Cortes, Byron David, Chelsea Finn, Chuyuan Fu, Keerthana Gopalakrishnan, Karol Hausman, Alex Herzog, Daniel Ho, Jasmine Hsu, Julian Ibarz, Brian Ichter, Alex Irpan, Eric Jang, Rosario Jauregui Ruano, Kyle Jeffrey, Sally Jesmonth, Nikhil J Joshi, Ryan Julian, Dmitry Kalashnikov, Yuheng Kuang, Kuang-Huei Lee, Sergey Levine, Yao Lu, Linda Luu, Carolina Parada, Peter Pastor, Jornell Quiambao, Kanishka Rao, Jarek Rettinghouse, Diego Reyes, Pierre Sermanet, Nicolas Sievers, Clayton Tan, Alexander Toshev, Vincent Vanhoucke, Fei Xia, Ted Xiao, Peng Xu, Sichun Xu, Mengyuan Yan, Andy Zeng* [[PDF](https://arxiv.org/pdf/2204.01691)] [[Code](https://github.com/google-research/google-research/tree/master/saycan)]

4. **LLM-Planner: Few-Shot Grounded Planning for Embodied Agents with Large Language Models** `ICCV 2023`
   
    *Chan Hee Song, Jiaman Wu, Clayton Washington, Brian M. Sadler, Wei-Lun Chao, Yu Su* [[PDF](https://arxiv.org/pdf/2212.04088)] [[Code](https://github.com/OSU-NLP-Group/LLM-Planner/)]

5. **Skill Induction and Planning with Latent Language** `ACL 2022`
   
    *Pratyusha Sharma, Antonio Torralba, Jacob Andreas* [[PDF](https://arxiv.org/pdf/2110.01517)]

6. **Adapt: As-needed decomposition and planning with language models** `NAACL 2024 Findings`
  
    *Archiki Prasad, Alexander Koller, Mareike Hartmann, Peter Clark, Ashish Sabharwal, Mohit Bansal, Tushar Khot* [[PDF](https://arxiv.org/pdf/2311.05772)] [[Code](https://github.com/archiki/ADaPT)]

7. **Dynamic Planning with a LLM** `NeurIPS 2024 LanGame Workshop`

    *Gautier Dagan, Frank Keller, Alex Lascarides* [[PDF](https://arxiv.org/pdf/2308.06391)] [[Code](https://github.com/itl-ed/llm-dp)]

8. **Large Language Models as Commonsense Knowledge for Large-Scale Task Planning** `NeurIPS 2023`

    *Zirui Zhao, Wee Sun Lee, David Hsu* [[PDF](https://arxiv.org/pdf/2305.14078)] [[Code](https://github.com/1989Ryan/llm-mcts)]

9. **On Grounded Planning for Embodied Tasks with Language Models** `AAAI 2023`

    *Bill Yuchen Lin, Chengsong Huang, Qian Liu, Wenda Gu, Sam Sommerer, Xiang Ren* [[PDF](https://arxiv.org/pdf/2209.00465)] [[Code](https://github.com/INK-USC/G-PlanET)]


#### Action Grounding
1. **LLM-Planner: Few-Shot Grounded Planning for Embodied Agents with Large Language Models** `ICCV 2023`
   
    *Chan Hee Song, Jiaman Wu, Clayton Washington, Brian M. Sadler, Wei-Lun Chao, Yu Su* [[PDF](https://arxiv.org/pdf/2212.04088)] [[Code](https://github.com/OSU-NLP-Group/LLM-Planner/)]

2. **Grounding LLMs For Robot Task Planning Using Closed-loop State Feedback** `Preprint`
   
    *Vineet Bhat, Ali Umut Kaypak, Prashanth Krishnamurthy, Ramesh Karri, Farshad Khorrami* [[PDF](https://arxiv.org/pdf/2402.08546)]

3. **Planning with Large Language Models via Corrective Re-prompting** `NeurIPS 2022 Foundation Models for Decision Making Workshop`

    *Shreyas Sundara Raman, Vanya Cohen, Eric Rosen, Ifrah Idrees, David Paulius and Stefanie Tellex* [[PDF](https://openreview.net/pdf?id=cMDMRBe1TKs)] 

4. **SayCanPay: Heuristic Planning with Large Language Models using Learnable Domain Knowledge** `AAAI 2024`

    *Rishi Hazra, Pedro Zuidberg Dos Martires, Luc De Raedt* [[PDF](https://arxiv.org/pdf/2308.12682)] [[Code](https://github.com/RishiHazra/saycanpay)]


#### Sample-then-Filter
1. **Distilling Script Knowledge from Large Language Models for Constrained Language Planning** `ACL 2023`

    *Siyu Yuan, Jiangjie Chen, Ziquan Fu, Xuyang Ge, Soham Shah, Charles Robert Jankowski, Yanghua Xiao, Deqing Yang* [[PDF](https://arxiv.org/pdf/2305.05252)] [[Code](https://github.com/siyuyuan/coscript)]

2. **PlaSma: Making Small Language Models Better Procedural Knowledge Models for (Counterfactual) Planning** `ICLR 2024`

    *Faeze Brahman, Chandra Bhagavatula, Valentina Pyatkin, Jena D. Hwang, Xiang Lorraine Li, Hirona J. Arai, Soumya Sanyal, Keisuke Sakaguchi, Xiang Ren, Yejin Choi* [[PDF](https://arxiv.org/pdf/2305.19472)] [[Code](https://github.com/allenai/PlaSma)]

3. **Trust the PRoC3S: Solving Long-Horizon Robotics Problems with LLMs and Constraint Satisfaction** `CoRL 2024`
   
    *Aidan Curtis, Nishanth Kumar, Jing Cao, Tomás Lozano-Pérez, Leslie Pack Kaelbling* [[PDF](https://arxiv.org/pdf/2406.05572)] [[Code](https://github.com/Learning-and-Intelligent-Systems/proc3s)]


#### Closed-Loop Systems
1. **Planning with Large Language Models via Corrective Re-prompting** `NeurIPS 2022 Foundation Models for Decision Making Workshop`

    *Shreyas Sundara Raman, Vanya Cohen, Eric Rosen, Ifrah Idrees, David Paulius and Stefanie Tellex* [[PDF](https://openreview.net/pdf?id=cMDMRBe1TKs)] 

2. **ProgPrompt: Generating Situated Robot Task Plans using Large Language Models.** `ICRA 2023` 
  
    *Ishika Singh, Valts Blukis, Arsalan Mousavian, Ankit Goyal, Danfei Xu, Jonathan Tremblay, Dieter Fox, Jesse Thomason, Animesh Garg* [[PDF](https://arxiv.org/abs/2209.11302)] [[Code](https://github.com/NVlabs/progprompt-vh)]

3. **Adapt: As-needed decomposition and planning with language models** `NAACL 2024 Findings`
  
    *Archiki Prasad, Alexander Koller, Mareike Hartmann, Peter Clark, Ashish Sabharwal, Mohit Bansal, Tushar Khot* [[PDF](https://arxiv.org/pdf/2311.05772)] [[Code](https://github.com/archiki/ADaPT)]

4. **SelfGoal: Your Language Agents Already Know How to Achieve High-level Goals** `NACCL 2025` 
  
    *Ruihan Yang, Jiangjie Chen, Yikai Zhang, Siyu Yuan, Aili Chen, Kyle Richardson, Yanghua Xiao, Deqing Yang* [[PDF](https://arxiv.org/pdf/2406.04784)] [[Code](https://github.com/rhyang2021/SELFGOAL)]

5. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
  
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

6. **ISR-LLM: Iterative Self-Refined Large Language Model for Long-Horizon Sequential Task Planning** `ICRA 2024`

    *Zhehua Zhou, Jiayang Song, Kunpeng Yao, Zhan Shu, Lei Ma* [[PDF](https://arxiv.org/pdf/2308.13724)] [[Code](https://github.com/zhehuazhou/ISR-LLM)]


### Optimality

#### LLM + Optimizer
1. **To the Globe (TTG): Towards Language-Driven Guaranteed Travel Planning** `EMNLP 2025 System Demonstrations`

    *Da Ju, Song Jiang, Andrew Cohen, Aaron Foss, Sasha Mitts, Arman Zharmagambetov, Brandon Amos, Xian Li, Justine T Kao, Maryam Fazel-Zarandi, Yuandong Tian* [[PDF](https://arxiv.org/pdf/2410.16456)]

2. **Planning Anything with Rigor: General-Purpose Zero-Shot Planning with LLM-based Formalized Programming** `ICLR 2025`

    *Yilun Hao, Yang Zhang, Chuchu Fan* [[PDF](https://arxiv.org/pdf/2410.12112)] [[Code](https://github.com/yih301/LLMFP)]


#### A* Search-Based Methods
1. **ToolChain*: Efficient Action Space Navigation in Large Language Models with A* Search** `ICLR 2024`

    *Yuchen Zhuang, Xiang Chen, Tong Yu, Saayan Mitra, Victor Bursztyn, Ryan A. Rossi, Somdeb Sarkhel, Chao Zhang* [[PDF](https://arxiv.org/pdf/2310.13227)]

2. **SayCanPay: Heuristic Planning with Large Language Models using Learnable Domain Knowledge** `AAAI 2024`

    *Rishi Hazra, Pedro Zuidberg Dos Martires, Luc De Raedt* [[PDF](https://arxiv.org/pdf/2308.12682)] [[Code](https://github.com/RishiHazra/saycanpay)]

3. **Beyond A\*: Better Planning with Transformers via Search Dynamics Bootstrapping** `COLM 2024`

    *Lucas Lehnert, Sainbayar Sukhbaatar, DiJia Su, Qinqing Zheng, Paul Mcvay, Michael Rabbat, Yuandong Tian* [[PDF](https://arxiv.org/pdf/2402.14083)] [[Code](https://github.com/facebookresearch/searchformer)]


### Representation

#### LLM-as-a-Translator
1. **Translating Natural Language to Planning Goals with Large-Language Models** `Preprint`
    *Yaqi Xie, Chen Yu, Tongyao Zhu, Jinbin Bai, Ze Gong, Harold Soh* [[PDF](https://arxiv.org/pdf/2302.05128)] [[Code](https://github.com/clear-nus/gpt-pddl)]

2. **ISR-LLM: Iterative Self-Refined Large Language Model for Long-Horizon Sequential Task Planning** `ICRA 2024`

    *Zhehua Zhou, Jiayang Song, Kunpeng Yao, Zhan Shu, Lei Ma* [[PDF](https://arxiv.org/pdf/2308.13724)] [[Code](https://github.com/zhehuazhou/ISR-LLM)]

3. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
  
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

4. **Generalized Planning in PDDL Domains with Pretrained Large Language Models** `AAAI 2024`

    *Tom Silver, Soham Dan, Kavitha Srinivas, Joshua B. Tenenbaum, Leslie Pack Kaelbling, Michael Katz* [[PDF](https://arxiv.org/pdf/2305.11014)] [[Code](https://github.com/tomsilver/llm-genplan/)]

5. **LLM+P: Empowering Large Language Models with Optimal Planning Proficiency** `Preprint`

    *Bo Liu, Yuqian Jiang, Xiaohan Zhang, Qiang Liu, Shiqi Zhang, Joydeep Biswas, Peter Stone* [[PDF](https://arxiv.org/pdf/2304.11477)] [[Code](https://github.com/Cranial-XIX/llm-pddl)]

6. **Data-Efficient Learning of Natural Language to Linear Temporal Logic Translators for Robot Task Specification** `ICRA 2023`

    *Jiayi Pan, Glen Chou, Dmitry Berenson* [[PDF](https://arxiv.org/pdf/2303.08006)] [[Code](https://github.com/Cranial-XIX/llm-pddl)]

7. **Dynamic Planning with a LLM** `NeurIPS 2024 LanGame Workshop`

    *Gautier Dagan, Frank Keller, Alex Lascarides* [[PDF](https://arxiv.org/pdf/2308.06391)] [[Code](https://github.com/itl-ed/llm-dp)]

8. **Leveraging Pre-trained Large Language Models to Construct and Utilize World Models for Model-based Task Planning** `NeurIPS 2023`

    *Lin Guan, Karthik Valmeekam, Sarath Sreedharan, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2305.14909)] [[Code](https://github.com/GuanSuns/LLMs-World-Models-for-Planning)]


#### LLM-as-a-Planner
1. **On Grounded Planning for Embodied Tasks with Language Models** `AAAI 2023`

    *Bill Yuchen Lin, Chengsong Huang, Qian Liu, Wenda Gu, Sam Sommerer, Xiang Ren* [[PDF](https://arxiv.org/pdf/2209.00465)] [[Code](https://github.com/INK-USC/G-PlanET)]

2. **Chain-of-Symbol Prompting Elicits Planning in Large Langauge Models** `COLM 2024`
   
    *Hanxu Hu, Hongyuan Lu, Huajian Zhang, Yun-Ze Song, Wai Lam, Yue Zhang* [[PDF](https://arxiv.org/pdf/2305.10276)] [[Code](https://github.com/hanxuhu/chain-of-symbol-planning)]

3. **Can Large Language Models be Good Path Planners? A Benchmark and Investigation on Spatial-temporal Reasoning** `ICLR 2024 Workshop on Large Language Model (LLM) Agents`

    *Mohamed Aghzal, Erion Plaku, Ziyu Yao* [[PDF](https://arxiv.org/pdf/2310.03249)] [[Code](https://github.com/MohamedAghzal/llms-as-path-planners)]

4. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
  
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

5. **Graph-enhanced Large Language Models in Asynchronous Plan Reasoning** `ICML 2024`
   
    *Fangru Lin, Emanuele La Malfa, Valentin Hofmann, Elle Michelle Yang, Anthony Cohn, Janet B. Pierrehumbert* [[PDF](https://arxiv.org/pdf/2402.02805)] [[Code](https://github.com/fangru-lin/graph-llm-asynchow-plan)]

6. **Do As I Can, Not As I Say: Grounding Language in Robotic Affordances**  `Preprint`
   
    *Michael Ahn, Anthony Brohan, Noah Brown, Yevgen Chebotar, Omar Cortes, Byron David, Chelsea Finn, Chuyuan Fu, Keerthana Gopalakrishnan, Karol Hausman, Alex Herzog, Daniel Ho, Jasmine Hsu, Julian Ibarz, Brian Ichter, Alex Irpan, Eric Jang, Rosario Jauregui Ruano, Kyle Jeffrey, Sally Jesmonth, Nikhil J Joshi, Ryan Julian, Dmitry Kalashnikov, Yuheng Kuang, Kuang-Huei Lee, Sergey Levine, Yao Lu, Linda Luu, Carolina Parada, Peter Pastor, Jornell Quiambao, Kanishka Rao, Jarek Rettinghouse, Diego Reyes, Pierre Sermanet, Nicolas Sievers, Clayton Tan, Alexander Toshev, Vincent Vanhoucke, Fei Xia, Ted Xiao, Peng Xu, Sichun Xu, Mengyuan Yan, Andy Zeng* [[PDF](https://arxiv.org/pdf/2204.01691)] [[Code](https://github.com/google-research/google-research/tree/master/saycan)]

7. **Can Graph Learning Improve Planning in LLM-based Agents?** `NeurIPS 2024`
   
    *Xixi Wu, Yifei Shen, Caihua Shan, Kaitao Song, Siwei Wang, Bohang Zhang, Jiarui Feng, Hong Cheng, Wei Chen, Yun Xiong, Dongsheng Li* [[PDF](https://arxiv.org/pdf/2405.19119)] [[Code](https://github.com/WxxShirley/GNN4TaskPlan)]

8. **Generalized Planning in PDDL Domains with Pretrained Large Language Models** `AAAI 2024`

    *Tom Silver, Soham Dan, Kavitha Srinivas, Joshua B. Tenenbaum, Leslie Pack Kaelbling, Michael Katz* [[PDF](https://arxiv.org/pdf/2305.11014)] [[Code](https://github.com/tomsilver/llm-genplan/)]

9. **ProgPrompt: Generating Situated Robot Task Plans using Large Language Models.** `ICRA 2023` 
  
    *Ishika Singh, Valts Blukis, Arsalan Mousavian, Ankit Goyal, Danfei Xu, Jonathan Tremblay, Dieter Fox, Jesse Thomason, Animesh Garg* [[PDF](https://arxiv.org/abs/2209.11302)] [[Code](https://github.com/NVlabs/progprompt-vh)]

10. **Pre-Trained Language Models for Interactive Decision-Making** `NeurIPS 2022`

    *Shuang Li, Xavier Puig, Chris Paxton, Yilun Du, Clinton Wang, Linxi Fan, Tao Chen, De-An Huang, Ekin Akyürek, Anima Anandkumar, Jacob Andreas, Igor Mordatch, Antonio Torralba, Yuke Zhu* [[PDF](https://arxiv.org/pdf/2202.01771)] [[Code](https://github.com/ShuangLI59/Pre-Trained-Language-Models-for-Interactive-Decision-Making)]


### Gneralization

#### Fine-Tuning
1. **Learning to Reason over Scene Graphs: A Case Study of Finetuning GPT-2 into a Robot Language Model for Grounded Task Planning** `Frontiers in Robotics and AI`
   
    *Georgia Chalvatzaki, Ali Younes, Daljeet Nandha, An Le, Leonardo F. R. Ribeiro, Iryna Gurevych* [[PDF](https://arxiv.org/pdf/2305.07716)]

2. **Trial and Error: Exploration-Based Trajectory Optimization for LLM Agents** `ACL 2024`

    *Yifan Song, Da Yin, Xiang Yue, Jie Huang, Sujian Li, Bill Yuchen Lin* [[PDF](https://arxiv.org/pdf/2403.02502)] [[Code](https://github.com/Yifan-Song793/ETO)]

3. **Agent-FLAN: Designing Data and Methods of Effective Agent Tuning for Large Language Models** `ACL 2024 Findings`

    *Zehui Chen, Kuikun Liu, Qiuchen Wang, Wenwei Zhang, Jiangning Liu, Dahua Lin, Kai Chen, Feng Zhao* [[PDF](https://arxiv.org/pdf/2403.12881)] [[Code](https://github.com/InternLM/Agent-FLAN)]

4. **AgentOhana: Design Unified Data and Training Pipeline for Effective Agent Learning** `NAACL 2025`

    *Jianguo Zhang, Tian Lan, Rithesh Murthy, Zhiwei Liu, Weiran Yao, Ming Zhu, Juntao Tan, Thai Hoang, Zuxin Liu, Liangwei Yang, Yihao Feng, Shirley Kokane, Tulika Awalgaonkar, Juan Carlos Niebles, Silvio Savarese, Shelby Heinecke, Huan Wang, Caiming Xiong* [[PDF](https://arxiv.org/pdf/2402.15506)] [[Code](https://github.com/SalesforceAIResearch/xLAM)]

5. **Learning From Failure: Integrating Negative Examples when Fine-tuning Large Language Models as Agents** `NAACL 2025`

    *Renxi Wang, Haonan Li, Xudong Han, Yixuan Zhang, Timothy Baldwin* [[PDF](https://arxiv.org/pdf/2402.11651)] [[Code](https://github.com/Reason-Wang/NAT)]


#### Generalized Planning
1. **Generalized Planning in PDDL Domains with Pretrained Large Language Models** `AAAI 2024`

    *Tom Silver, Soham Dan, Kavitha Srinivas, Joshua B. Tenenbaum, Leslie Pack Kaelbling, Michael Katz* [[PDF](https://arxiv.org/pdf/2305.11014)] [[Code](https://github.com/tomsilver/llm-genplan/)]


#### Skill Storage
1. **Voyager: An Open-Ended Embodied Agent with Large Language Models** `TMLR`

  *Guanzhi Wang, Yuqi Xie, Yunfan Jiang, Ajay Mandlekar, Chaowei Xiao, Yuke Zhu, Linxi Fan, Anima Anandkumar* [[PDF](https://arxiv.org/pdf/2305.16291)] [[Code](https://github.com/MineDojo/Voyager)]


### Efficiency

#### Reduced LLM and World Model Calls
1. **AdaPlanner: Adaptive Planning from Feedback with Language Models** `NeurIPS 2023`
  
    *Haotian Sun, Yuchen Zhuang, Lingkai Kong, Bo Dai, Chao Zhang* [[PDF](https://arxiv.org/pdf/2305.16653)] [[Code](https://github.com/haotiansun14/AdaPlanner)]

2. **Query-Efficient Planning with Language Models** `Preprint`
   
    *Gonzalo Gonzalez-Pumariega, Wayne Chen, Kushal Kedia, Sanjiban Choudhury* [[PDF](https://arxiv.org/pdf/2412.06162)] [[Code](https://github.com/portal-cornell/llms-for-planning)]

3. **Thought of Search: Planning with Language Models Through The Lens of Efficiency** `NeurIPS 2024`

    *Michael Katz, Harsha Kokel, Kavitha Srinivas, Shirin Sohrabi* [[PDF](https://arxiv.org/pdf/2404.11833)]

4. **Tree-Planner: Efficient Close-loop Task Planning with Large Language Models** `ICLR 2024`
   
    *Mengkang Hu, Yao Mu, Xinmiao Yu, Mingyu Ding, Shiguang Wu, Wenqi Shao, Qiguang Chen, Bin Wang, Yu Qiao, Ping Luo* [[PDF](https://arxiv.org/pdf/2310.08582)] [[Code](https://github.com/Aaron617/tree-planner)]


#### Shorter inputs and Outputs
1. **Chain-of-Symbol Prompting Elicits Planning in Large Langauge Models** `COLM 2024`
   
    *Hanxu Hu, Hongyuan Lu, Huajian Zhang, Yun-Ze Song, Wai Lam, Yue Zhang* [[PDF](https://arxiv.org/pdf/2305.10276)] [[Code](https://github.com/hanxuhu/chain-of-symbol-planning)]

2. **Beyond A\*: Better Planning with Transformers via Search Dynamics Bootstrapping** `COLM 2024`

    *Lucas Lehnert, Sainbayar Sukhbaatar, DiJia Su, Qinqing Zheng, Paul Mcvay, Michael Rabbat, Yuandong Tian* [[PDF](https://arxiv.org/pdf/2402.14083)] [[Code](https://github.com/facebookresearch/searchformer)]

3. **Describe, Explain, Plan and Select: Interactive Planning with LLMs Enables Open-World Multi-Task Agents** `NeurIPS 2023` 

    *Zihao Wang, Shaofei Cai, Guanzhou Chen, Anji Liu, Xiaojian Ma, Yitao Liang* [[PDF](https://arxiv.org/pdf/2302.01560)] [[Code](https://github.com/CraftJarvis/MC-Planner)]

4. **Dynamic Planning with a LLM** `NeurIPS 2024 LanGame Workshop`

    *Gautier Dagan, Frank Keller, Alex Lascarides* [[PDF](https://arxiv.org/pdf/2308.06391)] [[Code](https://github.com/itl-ed/llm-dp)]


#### Smaller Model Size
1. **PlaSma: Making Small Language Models Better Procedural Knowledge Models for (Counterfactual) Planning** `ICLR 2024`

    *Faeze Brahman, Chandra Bhagavatula, Valentina Pyatkin, Jena D. Hwang, Xiang Lorraine Li, Hirona J. Arai, Soumya Sanyal, Keisuke Sakaguchi, Xiang Ren, Yejin Choi* [[PDF](https://arxiv.org/pdf/2305.19472)] [[Code](https://github.com/allenai/PlaSma)]


## Evaluation

### Datasets

#### Planning-Focused

**Embodied Environment**

1. **BlocksWorld** [[Code](https://huggingface.co/datasets/chiayewken/blocksworld)]

2. **Logistics** [[Code](https://github.com/karthikv792/LLMs-Planning/tree/main/plan-bench/pddlgenerators/logistics)]

3. `PlanBench` **PlanBench: An Extensible Benchmark for Evaluating Large Language Models on Planning and Reasoning about Change** `NeurIPS 2023 Track on Datasets and Benchmarks`
    *Karthik Valmeekam, Matthew Marquez, Alberto Olmo, Sarath Sreedharan, Subbarao Kambhampati* [[PDF](https://arxiv.org/pdf/2206.10498)] [[Code](https://github.com/karthikv792/LLMs-Planning/tree/main)]

4. `ALFRED` **ALFRED: A Benchmark for Interpreting Grounded Instructions for Everyday Tasks** `CVPR 2020`

    *Mohit Shridhar, Jesse Thomason, Daniel Gordon, Yonatan Bisk, Winson Han, Roozbeh Mottaghi, Luke Zettlemoyer, Dieter Fox* [[PDF](https://arxiv.org/pdf/1912.01734)] [[Code](https://askforalfred.com/)]

5. `VirtualHome` **VirtualHome: Simulating Household Activities via Programs** `CVPR 2018`
   
    *Xavier Puig, Kevin Ra, Marko Boben, Jiaman Li, Tingwu Wang, Sanja Fidler, Antonio Torralba* [[PDF](https://arxiv.org/pdf/1806.07011)] [[Code](http://virtual-home.org/)]

6. `ALFWorld` **ALFWorld: Aligning Text and Embodied Environments for Interactive Learning** `ICLR 2021`

    *Mohit Shridhar, Xingdi Yuan, Marc-Alexandre Côté, Yonatan Bisk, Adam Trischler, Matthew Hausknecht* [[PDF](https://arxiv.org/pdf/2010.03768)] [[Code](https://alfworld.github.io/)]

7. `Embodied Agent Interface` `Executability-Focused` **Embodied Agent Interface: Benchmarking LLMs for Embodied Decision Making** `NeurIPS 2024 Track on Datasets and Benchmarks` 
   
    *Manling Li, Shiyu Zhao, Qineng Wang, Kangrui Wang, Yu Zhou, Sanjana Srivastava, Cem Gokmen, Tony Lee, Li Erran Li, Ruohan Zhang, Weiyu Liu, Percy Liang, Li Fei-Fei, Jiayuan Mao, Jiajun Wu* [[PDF](https://arxiv.org/pdf/2410.07166)] [[Code](https://embodied-agent-interface.github.io/)]

8. `Open Grounded Planning` `Executability-Focused` **Open Grounded Planning: Challenges and Benchmark Construction** `ACL 2024` 

    *Shiguang Guo, Ziliang Deng, Hongyu Lin, Yaojie Lu, Xianpei Han, Le Sun* [[PDF](https://arxiv.org/pdf/2406.02903)] [[Code](https://github.com/Shiguang-Guo/Open-Grounded-Planning)]

9. `PPNL` `Executability-Focused` `Completeness-Focused` **Can Large Language Models be Good Path Planners? A Benchmark and Investigation on Spatial-temporal Reasoning** `ICLR 2024 Workshop on Large Language Model (LLM) Agents` 

    *Mohamed Aghzal, Erion Plaku, Ziyu Yao* [[PDF](https://arxiv.org/pdf/2310.03249)] [[Code](https://github.com/MohamedAghzal/llms-as-path-planners)]

10. `AsyncHow` `Optimality-Focused` Graph-enhanced Large Language Models in Asynchronous Plan Reasoning `ICML 2024` 
    
    *Fangru Lin, Emanuele La Malfa, Valentin Hofmann, Elle Michelle Yang, Anthony Cohn, Janet B. Pierrehumbert* [[PDF](https://arxiv.org/pdf/2402.02805)] [[Code](https://github.com/fangru-lin/graph-llm-asynchow-plan)]

11. `Planetarium` `Representation-Focused` **Planetarium: A Rigorous Benchmark for Translating Text to Structured Planning Languages** `NAACL 2025` 
    
    *Max Zuo, Francisco Piedrahita Velez, Xiaochen Li, Michael L. Littman, Stephen H. Bach* [[PDF](https://arxiv.org/pdf/2407.03321)] [[Code](https://github.com/BatsResearch/planetarium)]

12. `PARTNR` **PARTNR: A Benchmark for Planning and Reasoning in Embodied Multi-agent Tasks** `ICLR 2025`

    *Matthew Chang, Gunjan Chhablani, Alexander Clegg, Mikael Dallaire Cote, Ruta Desai, Michal Hlavac, Vladimir Karashchuk, Jacob Krantz, Roozbeh Mottaghi, Priyam Parashar, Siddharth Patki, Ishita Prasad, Xavier Puig, Akshara Rai, Ram Ramrakhya, Daniel Tran, Joanne Truong, John M. Turner, Eric Undersander, Tsung-Yen Yang* [[PDF](https://arxiv.org/pdf/2411.00081)] [[Code](https://aihabitat.org/partnr/)]

13. `Robotouille` `Optimality-Focused` **Robotouille: An Asynchronous Planning Benchmark for LLM Agents** `ICLR 2025` 

    *Gonzalo Gonzalez-Pumariega, Leong Su Yean, Neha Sunkara, Sanjiban Choudhury* [[PDF](https://arxiv.org/pdf/2502.05227)] [[Code](https://portal.cs.cornell.edu/robotouille/)]

**Task Scheduling**

14. `TravelPlanner` `Executability-Foucsed` **TravelPlanner: A Benchmark for Real-World Planning with Language Agents** `ICML 2024` 

    *Jian Xie, Kai Zhang, Jiangjie Chen, Tinghui Zhu, Renze Lou, Yuandong Tian, Yanghua Xiao, Yu Su* [[PDF](https://arxiv.org/pdf/2402.01622)] [[Code](https://osu-nlp-group.github.io/TravelPlanner/)]

15. `Natural Plan` **NATURAL PLAN: Benchmarking LLMs on Natural Language Planning** `Preprint`

    *Huaixiu Steven Zheng, Swaroop Mishra, Hugh Zhang, Xinyun Chen, Minmin Chen, Azade Nova, Le Hou, Heng-Tze Cheng, Quoc V. Le, Ed H. Chi, Denny Zhou*  [[PDF](https://arxiv.org/pdf/2406.04520)] [[Code](https://github.com/google-deepmind/natural-plan)]

**Game**

16. **MineCraft**  [[Code](https://github.com/MineDojo/Voyager/blob/main/installation/minecraft_instance_install.md)]

17. `SmartPlay` **SmartPlay: A Benchmark for LLMs as Intelligent Agents** `ICLR 2024`
    
    *Yue Wu, Xuan Tang, Tom M. Mitchell, Yuanzhi Li* [[PDF](https://arxiv.org/pdf/2310.01557)] [[Code](https://github.com/microsoft/SmartPlay)]

18. `AUCARENA` **Put Your Money Where Your Mouth Is: Evaluating Strategic Planning and Execution of LLM Agents in an Auction Arena** `Preprint`

    *Jiangjie Chen, Siyu Yuan, Rong Ye, Bodhisattwa Prasad Majumder, Kyle Richardson* [[PDF](https://arxiv.org/pdf/2310.05746)] [[Code](https://auction-arena.github.io/)]

19. `GAMABench` **How Far Are We on the Decision-Making of LLMs? Evaluating LLMs' Gaming Ability in Multi-Agent Environments** `ICLR 2025`

    *Jen-tse Huang, Eric John Li, Man Ho Lam, Tian Liang, Wenxuan Wang, Youliang Yuan, Wenxiang Jiao, Xing Wang, Zhaopeng Tu, Michael R. Lyu* [[PDF](https://arxiv.org/pdf/2403.11807)] [[Code](https://github.com/CUHK-ARISE/GAMABench)]


**Task Decomposition**

20. `CoScript` `Executability-Focused` **Distilling Script Knowledge from Large Language Models for Constrained Language Planning** `ACL 2023` 

    *Siyu Yuan, Jiangjie Chen, Ziquan Fu, Xuyang Ge, Soham Shah, Charles Robert Jankowski, Yanghua Xiao, Deqing Yang* [[PDF](https://arxiv.org/pdf/2305.05252)] [[Code](https://github.com/siyuyuan/coscript)]

21. `TaskLAMA` **TaskLAMA: Probing the Complex Task Understanding of Language Models** `AAAI 2024`

    *Quan Yuan, Mehran Kazemi, Xin Xu, Isaac Noble, Vaiva Imbrasaite, Deepak Ramachandran* [[PDF](https://arxiv.org/pdf/2308.15299)]

22. `WorldAPIs` **WorldAPIs: The World Is Worth How Many APIs? A Thought Experiment** `ACL 2024 NLRSE Workshop`
    
    *Jiefu Ou, Arda Uzunoglu, Benjamin Van Durme, Daniel Khashabi* [[PDF](https://arxiv.org/pdf/2407.07778)] 


#### Downstream Tasks

**Reasoning**

1. `PrOntoQA` **Language Models Are Greedy Reasoners: A Systematic Formal Analysis of Chain-of-Thought** `ICLR 2023`

    *Abulhair Saparov, He He* [[PDF](https://arxiv.org/pdf/2210.01240)] [[Code](https://github.com/asaparov/prontoqa)]

2. `GSM8K` **Training Verifiers to Solve Math Word Problems** `Preprint`

    *Karl Cobbe, Vineet Kosaraju, Mohammad Bavarian, Mark Chen, Heewoo Jun, Lukasz Kaiser, Matthias Plappert, Jerry Tworek, Jacob Hilton, Reiichiro Nakano, Christopher Hesse, John Schulman* [[PDF](https://arxiv.org/pdf/2110.14168)] [[Code](https://github.com/openai/grade-school-math)]

3.  `AgentBench`**AgentBench: Evaluating LLMs as Agents** `Preprint`
  
    *Xiao Liu, Hao Yu, Hanchen Zhang, Yifan Xu, Xuanyu Lei, Hanyu Lai, Yu Gu, Hangliang Ding, Kaiwen Men, Kejuan Yang, Shudan Zhang, Xiang Deng, Aohan Zeng, Zhengxiao Du, Chenhui Zhang, Sheng Shen, Tianjun Zhang, Yu Su, Huan Sun, Minlie Huang, Yuxiao Dong, Jie Tang* [[PDF](https://arxiv.org/pdf/2308.03688)] [[Code](https://llmbench.ai/agent)]

4. `SWE-Bench` **SWE-bench: Can Language Models Resolve Real-World GitHub Issues?** `ICLR 2024`

    *Carlos E. Jimenez, John Yang, Alexander Wettig, Shunyu Yao, Kexin Pei, Ofir Press, Karthik Narasimhan* [[PDF](https://arxiv.org/pdf/2310.06770)] [[Code](https://www.swebench.com/)]


**Tool Usage**

5. `ToolBench` **On the Tool Manipulation Capability of Open-source Large Language Models** `Preprint`
   
    *Qiantong Xu, Fenglu Hong, Bo Li, Changran Hu, Zhengyu Chen, Jian Zhang* [[PDF](https://arxiv.org/pdf/2305.16504)] [[Code](https://github.com/sambanova/toolbench)]

6. `API-Bank` **API-Bank: A Comprehensive Benchmark for Tool-Augmented LLMs** `EMNLP 2023`

    *Minghao Li, Yingxiu Zhao, Bowen Yu, Feifan Song, Hangyu Li, Haiyang Yu, Zhoujun Li, Fei Huang, Yongbin Li* [[PDF](https://arxiv.org/pdf/2304.08244)] [[Code](https://github.com/AlibabaResearch/DAMO-ConvAI/tree/main/api-bank)]

7. `TPTU` **TPTU: Large Language Model-based AI Agents for Task Planning and Tool Usage** `Preprint`

    *Jingqing Ruan, Yihong Chen, Bin Zhang, Zhiwei Xu, Tianpeng Bao, Guoqing Du, Shiwei Shi, Hangyu Mao, Ziyue Li, Xingyu Zeng, Rui Zhao* [[PDF](https://arxiv.org/pdf/2308.03427)] 


**Web**

8. `WebArena` **WebArena: A Realistic Web Environment for Building Autonomous Agents** `ICLR 2024`

    *Shuyan Zhou, Frank F. Xu, Hao Zhu, Xuhui Zhou, Robert Lo, Abishek Sridhar, Xianyi Cheng, Tianyue Ou, Yonatan Bisk, Daniel Fried, Uri Alon, Graham Neubig* [[PDF](https://arxiv.org/pdf/2307.13854)] [[Code](https://webarena.dev/)]

9. `Mind2Web` **Mind2Web: Towards a Generalist Agent for the Web** `NeurIPS 2023 Track on Datasets and Benchmarks.`

    *Xiang Deng, Yu Gu, Boyuan Zheng, Shijie Chen, Samuel Stevens, Boshi Wang, Huan Sun, Yu Su* [[PDF](https://arxiv.org/pdf/2306.06070)] [[Code](https://osu-nlp-group.github.io/Mind2Web/)]


**Programming**

10. `CodePlan` **CodePlan: Repository-level Coding using LLMs and Planning** `FSE 2024`
    *Ramakrishna Bairi, Atharv Sonwane, Aditya Kanade, Vageesh D C, Arun Iyer, Suresh Parthasarathy, Sriram Rajamani, B. Ashok, Shashank Shet* [[PDF](https://arxiv.org/pdf/2309.12499)] [[Code](https://github.com/microsoft/codeplan)]

11. `Spider` **Spider: A Large-Scale Human-Labeled Dataset for Complex and Cross-Domain Semantic Parsing and Text-to-SQL Task** `EMNLP 2018`

    *Tao Yu, Rui Zhang, Kai Yang, Michihiro Yasunaga, Dongxu Wang, Zifan Li, James Ma, Irene Li, Qingning Yao, Shanelle Roman, Zilin Zhang, Dragomir Radev* [[PDF](https://arxiv.org/pdf/1809.08887)] [[Code](https://yale-lily.github.io/spider)]

12. `Bird` **Can LLM Already Serve as A Database Interface? A BIg Bench for Large-Scale Database Grounded Text-to-SQLs** `NeurIPS 2023 Track on Datasets and Benchmarks.`

    *Jinyang Li, Binyuan Hui, Ge Qu, Jiaxi Yang, Binhua Li, Bowen Li, Bailin Wang, Bowen Qin, Rongyu Cao, Ruiying Geng, Nan Huo, Xuanhe Zhou, Chenhao Ma, Guoliang Li, Kevin C.C. Chang, Fei Huang, Reynold Cheng, Yongbin Li* [[PDF](https://arxiv.org/pdf/2305.03111)] [[Code](https://bird-bench.github.io/)]


**Generation**

13. **VideoDirectorGPT: Consistent Multi-scene Video Generation via LLM-Guided Planning** `COLM 2024`
    
    *Han Lin, Abhay Zala, Jaemin Cho, Mohit Bansal* [[PDF](https://arxiv.org/pdf/2309.15091)] [[Code](https://videodirectorgpt.github.io/)]

14. **DiagrammerGPT: Generating Open-Domain, Open-Platform Diagrams via LLM Planning** `COLM 2024`

    *Abhay Zala, Han Lin, Jaemin Cho, Mohit Bansal* [[PDF](https://arxiv.org/pdf/2310.12128)] [[Code](https://diagrammergpt.github.io/)]

15. **Step-by-Step: Separating Planning from Realization in Neural Data-to-Text Generation** `NAACL 2019`
    *Amit Moryossef, Yoav Goldberg, Ido Dagan* [[PDF](https://arxiv.org/pdf/1904.03396)] [[Code](https://github.com/AmitMY/chimera)]

### Methods (Representative Works)

#### Verifier or Groundtruth

**Verifier**

1. `VAL` **VAL: automatic plan validation, continuous effects and mixed initiative planning using PDDL** `IEEE International Conference on Tools with Artificial Intelligence`

    *Richard Howey, Derek Long, and Maria Fox* [[PDF](https://ieeexplore.ieee.org/document/1374201)]

2. `BUTLER` **ALFWorld: Aligning Text and Embodied Environments for Interactive Learning** `ICLR 2021`

    *Mohit Shridhar, Xingdi Yuan, Marc-Alexandre Côté, Yonatan Bisk, Adam Trischler, Matthew Hausknecht* [[PDF](https://arxiv.org/pdf/2010.03768)] [[Code](https://alfworld.github.io/)]

**Groundtruth**

1. **NATURAL PLAN: Benchmarking LLMs on Natural Language Planning** `Preprint`

    *Huaixiu Steven Zheng, Swaroop Mishra, Hugh Zhang, Xinyun Chen, Minmin Chen, Azade Nova, Le Hou, Heng-Tze Cheng, Quoc V. Le, Ed H. Chi, Denny Zhou*  [[PDF](https://arxiv.org/pdf/2406.04520)] [[Code](https://github.com/google-deepmind/natural-plan)]

2. **Can Large Language Models be Good Path Planners? A Benchmark and Investigation on Spatial-temporal Reasoning** `ICLR 2024 Workshop on Large Language Model (LLM) Agents` 

    *Mohamed Aghzal, Erion Plaku, Ziyu Yao* [[PDF](https://arxiv.org/pdf/2310.03249)] [[Code](https://github.com/MohamedAghzal/llms-as-path-planners)]

3. **Skill Induction and Planning with Latent Language** `ACL 2022`

    *Pratyusha Sharma, Antonio Torralba, Jacob Andreas* [[PDF](https://arxiv.org/pdf/2110.01517)] [[Code](https://sites.google.com/view/skill-induction-latent-lang/)]


#### Human Evaluation (Representative Works)

1. **PlaSma: Making Small Language Models Better Procedural Knowledge Models for (Counterfactual) Planning** `ICLR 2024`

    *Faeze Brahman, Chandra Bhagavatula, Valentina Pyatkin, Jena D. Hwang, Xiang Lorraine Li, Hirona J. Arai, Soumya Sanyal, Keisuke Sakaguchi, Xiang Ren, Yejin Choi* [[PDF](https://arxiv.org/pdf/2305.19472)] [[Code](https://github.com/allenai/PlaSma)]

2. **CAPE: Corrective Actions from Precondition Errors using Large Language Models** `ICRA 2024`
   
    *Shreyas Sundara Raman, Vanya Cohen, Ifrah Idrees, Eric Rosen, Ray Mooney, Stefanie Tellex, David Paulius* [[PDF](https://arxiv.org/pdf/2211.09935)] [[Code](https://shreyas-s-raman.github.io/CAPE/)]

3. **Embodied Task Planning with Large Language Models** `Preprint`

    *Zhenyu Wu, Ziwei Wang, Xiuwei Xu, Jiwen Lu, Haibin Yan* [[PDF](https://arxiv.org/pdf/2307.01848)] [[Code](https://gary3410.github.io/TaPA/)]

4. **Multimodal Procedural Planning via Dual Text-Image Prompting** `ENMLP 2024 Findings`

    *Yujie Lu, Pan Lu, Zhiyu Chen, Wanrong Zhu, Xin Eric Wang, William Yang Wang* [[PDF](https://arxiv.org/pdf/2305.01795)] [[Code](https://openreview.net/forum?id=jTsnuWsda2)]


#### LLM-as-a-Judge

1. **Open Grounded Planning: Challenges and Benchmark Construction** `ACL 2024` 

    *Shiguang Guo, Ziliang Deng, Hongyu Lin, Yaojie Lu, Xianpei Han, Le Sun* [[PDF](https://arxiv.org/pdf/2406.02903)] [[Code](https://github.com/Shiguang-Guo/Open-Grounded-Planning)]

2. **BioPlanner: Automatic Evaluation of LLMs on Protocol Planning in Biology** `EMNLP 2023`

    *Odhran O'Donoghue, Aleksandar Shtedritski, John Ginger, Ralph Abboud, Ali Essa Ghareeb, Justin Booth, Samuel G Rodriques* [[PDF](https://arxiv.org/pdf/2310.10632)] [[Code](https://github.com/bioplanner/bioplanner)]


### Metrics

This table summarizes commonly used evaluation metrics for each performance criterion, along with representative studies. For definitions of these metrics, please refer to our [survey]((https://arxiv.org/abs/2502.11221)) (Section 9) or the individual papers cited in the table.

| Criteria       | Metrics (Representative Works)                                |
| -------------- | ------------------------------------------------------------ |
| Completeness   | Success Rate  [(Valmeekam et al. 2023)](https://arxiv.org/abs/2302.06706); Goal Condition Recall  [(Hu et al., 2023)](https://arxiv.org/abs/2310.08582); Step Success Rate  [(Deng et al., 2023)](https://arxiv.org/abs/2306.06070); Exact Match Score [(Aghzal et al., 2024)](https://arxiv.org/abs/2406.12000); True Negative Rate and False Negative Rate  [(Valmeekam et al. 2023)](https://arxiv.org/abs/2302.06706); Unreachable Accuracy  [(Aghzal et al., 2023)](https://arxiv.org/abs/2310.03249). |
| Executability  | Executability Rate [(Hazra et al., 2024)](https://arxiv.org/abs/2308.12682); Constraint Pass Rate [(Xie et al., 2024)](https://arxiv.org/abs/2402.01622). |
| Optimality     | Optimality Rate [(Lehnert et al., 2024)](https://arxiv.org/abs/2402.14083).                                             |
| Efficiency     | Inference Time [(Brahman et al., 2024)](https://arxiv.org/abs/2305.19472); Number of Output and Input Tokens [(Hu et al., 2024)](https://arxiv.org/abs/2305.10276); Number of plan Steps [(Raman et al., 2022)](https://openreview.net/pdf?id=cMDMRBe1TKs); Number of LLM and World Model Calls [(Sun et al., 2024)](https://arxiv.org/abs/2305.16653); Model Size [(Brahman et al., 2024)](https://arxiv.org/abs/2305.19472). |
| Representation | Number of Parseable Problems [(Zuo et al. 2024)](https://arxiv.org/abs/2407.03321).                                |
| Generalization | All above metrics can also be applied to unseen scenarios to assess generalization. |

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







