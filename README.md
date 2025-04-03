# Jailbreaking Large Language Models: A Comprehensive Exploration
**Bhanu Prakash Thipparti, Kiranmayi Chelluboyina, Sai Spoorthi**  
December 2024

## Abstract
Large Language Models (LLMs) have demonstrated extraordinary capabilities in natural language comprehension and generation. However, these models are vulnerable to jailbreaking, which is a process that manipulates input prompts in order to bypass safety mechanisms and produce harmful results. This paper looks into the Kov method, a novel jailbreaking approach that uses Monte Carlo Tree Search (MCTS) to iteratively refine prompts. Hyperparameter tuning is investigated to improve the effectiveness of the Kov method, and its performance is assessed on a dataset of 100 prompts. The findings emphasize the method’s efficacy, the importance of hyperparameters, and the reliance on prompt configuration.

## 1 Introduction
Large Language Models (LLMs) have transformed artificial intelligence by excelling at a wide range of tasks such as text generation, summarization, and question-answering. Despite their advances, these models are vulnerable to adversarial attacks, such as jailbreaking. Jailbreaking modifies model inputs to circumvent built-in safeguards, potentially allowing the creation of harmful content.

Among jailbreaking methods, the Kov method has received attention for its strategic use of Monte Carlo Tree Search. This paper investigates the effectiveness of the Kov method for jailbreaking LLMs, with a focus on hyperparameter tuning and its application across a variety of prompts. A thorough review of the literature on the Kov method and the tools that support its functionality is given special emphasis.

## 2 Literature Review
Adversarial attacks on LLMs reveal flaws in even the most reliable systems. Moss(2024) proposed the Kov method, which combines Monte Carlo Tree Search (MCTS) with optimization techniques like Greedy Coordinate Gradient. This hybrid approach iteratively improves input prompts, increasing their ability to bypass moderation frameworks.  
Zou et al.(2023) demonstrated the transferability of adversarial prompts across aligned LLMs, emphasizing the broader safety implications of different models. Their findings emphasize the importance of countermeasures that can be applied to various architectures.

### 2.1 The Kov Method
The Kov method is an advanced approach to jailbreaking LLMs. It uses Monte Carlo Tree Search (MCTS) to iteratively refine prompts while balancing exploration and exploitation. The Kov method detects configurations that circumvent model safeguards by systematically changing input prompts.

### 2.2 Greedy Coordinate Gradient (GCG)
The GCG method optimizes an objective function by iteratively improving individual dimensions (or coordinates) of the input space. Unlike global optimization approaches, GCG focuses on localized, greedy updates that use gradients to find the most significant changes. The Kov method uses GCG as a mechanism to efficiently identify optimal perturbations to prompts.

### 2.3 Monte Carlo Tree Search (MCTS)
MCTS, well-known for its use in AI-driven gameplay, facilitates the navigation of large decision spaces. Chaffin et al. (2023) demonstrated its effectiveness in constrained textual generation using discriminator-guided decoding to match outputs to specific constraints. In the context of Kov, MCTS acts as a search framework that balances exploration and exploitation of the prompt space, while GCG provides focused updates. MCTS is a decision-making algorithm commonly used in optimization and planning tasks. It uses tree-based search strategies and Monte Carlo simulations to find optimal solutions in large search spaces. In the Kov method, MCTS iteratively investigates changes to input prompts by simulating their impact on the target model’s moderation framework. The Kov method dynamically refines prompts by adapting the four main components of MCTS: selection, expansion, simulation, and backpropagation. The algorithm prioritizes configurations that maximize the moderation score, indicating success in jailbreaking.

### 2.4 OpenAI Moderation Framework
The OpenAI Moderation framework is used to assess the safety of the generated responses. This framework assigns a moderation score to model outputs, with higher scores indicating more safety violations. The Kov method uses these scores as feedback to optimize prompt configurations. Prompt optimization strategies are typically designed to improve the safety and coherence of LLM outputs. Adversarial approaches, such as Kov, aim to uncover vulnerabilities in alignment mechanisms. This dual nature of optimization highlights the complexities of protecting LLMs from increasingly sophisticated adversarial techniques.

## 3 Methodology
The experiments were designed to evaluate the effectiveness of the Kov method in bypassing LLM safeguards, with a particular emphasis on hyperparameter tuning. The experiments used GPT-3.5 as the target model. The following experimental steps were performed:

### 3.1 Kov Implementation
The Kov method was implemented using an existing framework that uses MCTS to refine and modify prompts iteratively. The Kov method was tested with the default configuration to establish a baseline performance before modifying any hyperparameters.

### 3.2 Hyperparameter Tuning
Key hyperparameters were adjusted to see how they affected the success of jailbreaking:
- **Length of Suffix Tokens**: The length of the suffix appended to the prompt was adjusted to achieve the best balance of brevity and effectiveness.
- **Top-K Tokens**: The number of top-K tokens considered in each MCTS iteration was modified to investigate the exploration-exploitation trade-off.
- **Moderation Score Calculation**: The use of average and maximum moderation scores to gauge their influence on the jailbreaking process.
- **Prompt Selection**: After determining the optimal hyperparameters, the best configuration was applied to a larger dataset of 100 prompts to assess the consistency and efficacy of jailbreaking across different input sources.
- **Evaluation Metrics**: OpenAI’s moderation framework was used to assess the safety of the generated results.

## 4 Results

### Part 1: Initial Experimentation
The initial experiments, using the Kov method with the default settings, showed a moderate success rate in bypassing safeguards. The results, however, varied depending on the specific prompt used, demonstrating that the Kov method’s effectiveness is heavily dependent on prompt configuration.
- **Experimentation using best Hyperparameters on a large dataset**: (https://docs.google.com/spreadsheets/d/1YCgTXYxQ_7sjJeyJbZKex2Vtt98F07VQE2SJvys055o/edit?gid=167437280#gid=167437280)

### Part 2: Hyperparameter Tuning
After five rounds of experimentation with various parameter settings, the following trends were discovered:
- **Length of Suffix Tokens**: Shorter suffix lengths produced fewer meaningful modifications, whereas longer suffixes increased jailbreaking success. The best configuration was found with n tokens = 8.
- **Top-K Tokens**: Increasing the value of top-K tokens broadened the exploration space, resulting in more creative but sometimes harmful outcomes. The best results were obtained with topk = 25.
- **Moderation Score Calculation**: Using the maximum moderation score as the optimization objective resulted in more aggressive jailbreaking attempts, often leading to higher-risk outputs.

### Experiments
- **Experiment 1**: n tokens = 3 and topk = 32 with mean moderation scores. (https://docs.google.com/spreadsheets/d/1I7GWMSuhFq7zZ9bXSUshnw1wYKSh7HfJc0TlXfsPDQU/edit?gid=285878507#gid=285878507)
- **Experiment 2**: n tokens = 16 and topk = 32 with mean moderation scores. (https://docs.google.com/spreadsheets/d/1BzEzQudT_GPTK877lDSiRejSOThRm8tqixJk2rvy6Q8/edit?gid=35096198#gid=35096198)
- **Experiment 3**: n tokens = 8 and topk = 25 with mean moderation scores. (https://docs.google.com/spreadsheets/d/1FxObg1lSH0KXrljTOpFHic24OOo7SXJRFtFWROjQc88/edit?gid=1084652003#gid=1084652003)
- **Experiment 4**: n tokens = 8 and topk = 100 with mean moderation scores. (https://docs.google.com/spreadsheets/d/1xB_8XrzRw3EVoth45akMBeXXyUaC3UxACUOcSm6oXP0/edit?gid=163133357#gid=163133357)
- **Experiment 5**: n tokens = 8 and topk = 32 with maximum moderation scores. (https://docs.google.com/spreadsheets/d/1mqmLLnGHJ1wl47SvKoCBbtH7jxbmz3uWsHfDiZp6IlU/edit?gid=367289833#gid=367289833)

### Part 3: Evaluation Using a Larger Dataset
After determining the best hyperparameters (n tokens = 8 and top-K = 25), this configuration was tested on a larger dataset of 20 prompts. The findings confirmed that the Kov method could bypass safeguards in many cases, but the success rate varied across prompts. While some prompts produced negative results, others did not, highlighting the fact that jailbreaking outcomes are highly dependent on the prompt used.
- **Experimentation using best Hyperparameters on a large dataset**: (https://docs.google.com/spreadsheets/d/14MBwfggPKmgM9GySAwoW5pjXj6LdzQ2lF5skuujzl04/edit?gid=1342064311#gid=1342064311)

## 5 Discussion
The findings demonstrate the unpredictability and complexity of jailbreaking LLMs. Although hyperparameter tuning is critical to increasing the success rate of the Kov method, there is no universally effective configuration. Different prompts and parameter changes can produce significantly different results. The experiment demonstrated the importance of conducting systematic testing with various configurations to determine the best conditions for jailbreaking. Despite the lack of a consistent success rate, the findings show that the Kov method, with proper parameter tuning, can still be effective in bypassing LLM safeguards.

## 6 Conclusion
This study emphasizes the difficulties in jailbreaking LLMs and the importance of ongoing experimentation to understand the nuances of prompt-based manipulation. The Kov method, when combined with the optimal hyperparameter settings of n tokens = 8 and topk = 25, demonstrated the ability to bypass LLM safeguards, though results were inconsistent across prompts. These findings suggest that, while jailbreaking is possible, there is no one-size-fits-all approach, and success rates are heavily influenced by prompt selection and hyperparameter configuration. Continued research is required to develop more robust safety measures and resilient LLM architectures to address these vulnerabilities and ensure the responsible deployment of AI technologies.

## References
- Moss, R. J. (2024). Kov: Transferable and Naturalistic Black-Box LLM Attacks using Markov Decision Processes and Tree Search. Stanford University.
- Zou, A., Wang, Z., Carlini, N., Nasr, M., Kolter, J. Z., & Fredrikson, M. (2023). Universal and Transferable Adversarial Attacks on Aligned Language Models. Carnegie Mellon University.
- Chaffin, A., Claveau, V., & Kijak, E. (2022). PPL-MCTS: Constrained Textual Generation Through Discriminator-Guided MCTS Decoding. CNRS, Univ. Rennes 1.
