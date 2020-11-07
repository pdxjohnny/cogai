# Frequently Asked Questions for Cognitive AI

This is a compilation of questions that have been asked after talks on Cognitive AI or through the public mailing list. Feel free to propose further questions via email to public-cogai@w3.org

## What is the type in each chunk?

The notion of the chunk type is a loose one and provides a way to name a collection of chunks that have something in common. It may be the case that all such chunks must satisfy some ontological constraint, on the other hand, it could be an informal grouping. This corresponds to the distinction between an intensional definition and an extensional definition. Inductive reasoning provides a way to learn models that describe regularities across members of groups.

## How does Cognitive AI cope with uncertainty in input?

This came up in respect to control of robots, where there may be uncertainty in the robot's position, or something unexpected that obstructs the path of a robot's arm. When people reach out to pick up a mug of coffee, the action is initiated by cognition (the cortico-basal ganglia circuit) and delegated to the cortico-cerebellar circuit. The cognitive command involves an appoximate position of the coffee mug. The cerebellum refines this estimate as the arm moves, using information from the visual cortex for the hand and the mug. The decision to grab the mug is conscious, but the actual movement is automatic and under control of the densely packed neural circuitry in the cerebellum. This circuitry learns from experience, e.g. when learning to ride a bicycle, you are initially wobbling all over the place, but soon learn to ride smoothly without apparent conscious effort.

Robots can mimic the brain using computer vision. Objects can be recognised and located through a camera and neural network. The way this is trained, e.g. using a variety of lighting conditions can help to improve the robustness and accuracy of the perceptual models placed in the cortex. These in turn can be used to correct errors in the data for the robot's position, and to replan movements to avoid obstructions. A robot can be designed to use a camera to guide its movement, and to use dead reckoning as a fallback. If something unexpected happens, cognition can be invoked to adapt and replan the command. Most robots are designed to be rigid for accurate positioning. The rigidity means heavier arms and more power to move them around. The cognitive approach to robot control is promising for lightweight robots whose arms flex a little under stress. This means a longer battery life for mobile robots and a lower manufacturing cost.

## How does Cognitive AI learn from examples?

This is essentially explanation based, i.e. where the cognitive agent seeks to explain new examples, and in the process to update its models as needed. Humans are prediction machines that pay attention to novelty to improve their predictions. This allows for continuous  learning throughout one's lifetime. One challenge is to balance what is learned from the current example without distorting what has been learned from past examples. In the brain, the Hippocampus has a major role in learning and memory with a focus on recent events, whilst the Cortex takes a longer term perspective.

## How are rules learned in Cognitive AI?

Rule sets can be acquired in two ways: through manual development or through hierarchical reinforcement learning. The latter involves heuristics for proposing new rules or updates to existing rules. The success or failure of a rule set on a given task can then be used to update the expected utility of a particular rule for that task.  Task repetition then propagates these corrections back through the chain of rules used to execute that task. Case based reasoning, including reasoning by analogy and metacognition can be used to break tasks into sub-tasks and to make better use of prior knowledge and past experience, avoiding the need to learn from scratch. The chunks rule language includes native support for segregating rules by tasks.

## How does Cognitive AI compare to Computational Linguistics and to BERT in respect to NLP?

Both Computational Linguistics, and approaches based upon Deep Learning, avoid directly modelling semantics, and instead rely on statistics across large numbers of text samples as a weak surrogate. This relies on the idea that words with related meanings are frequently found together. For Cognitive AI, natural language is considered as a series of layers, for example, a layer with the sequence of words, the next layer with the corresponding syntactic phrase structure, and a further layer with the semantic representation. Each of these layers can be expressed with chunks, so the process of natural language understanding or generation becomes a matter of mapping between the chunks at different layers. Other layers deal with phonology and morphology.

In Computational Linguistics, the focus is on finding the syntactic parse trees for a given utterance. Natural language is highly ambiguous from a syntactic perspective, with many possible parse trees. Using large statistics across many training samples, a statistical parser can guess at which possible parse trees are more likely than others. This involves techniques like beam search with probabilistic context free grammars (PCFG). For more details, see e.g. Christopher Manning's [lectures on statistical parsing](https://nlp.stanford.edu/courses/lsa354/) (Stanford University).

Google BERT approaches natural language from the perspective of Deep Learning with artificial neural networks. It was originally trained using all of the English language Wikipedia and the Brown corpus.  BERT uses neural networks (Transformer models) that can deal with long range correlations between words, both before and after a given word in an utterance. The networks involve hundreds of millions of parameters, and the consequent need for vast training sets. Whilst BERT doesn't directly model semantics, it can nonetheless be applied to a range of tasks such as finding documents relating to a given query, document classification, and sentiment analysis.

Cognitive AI, by contrast seeks to mimic what is known about how people process language. We seemingly effortlessly deal with ambiguity despite tightly constrained working memory. Human languages are complex, yet easily picked up by young children. This shows that humans are able to master language without the vast statistics needed by approaches like BERT. The approach adopted for Cognitive AI is to process text incrementally, one word at a time, concurrently with the syntactic phrase structure and the associated semantics. Priming effects can be modelled in terms of spreading activation at both the syntactic and semantic layers. The likely meaning of a word is thus influenced by the words that precede it.

Pronouns usually refer to something introduced earlier in the utterance. However, the correct binding of a pronoun to its referent may depend on the words that occur following the pronoun. This can be addressed by associating the pronoun with a superposition of states that is resolved upon encountering subsequent words that constrain the likely meaning. A similar process is used to resolve the bindings of prepositions in terms of concurrent asynchronous search at both the syntactic and semantic layers, using continuation based threaded execution. The syntactic phrase structure is generated through simple robust shift-reduce parsing. The mapping between syntax and semantics is accounted for using paired if-then rules at the syntactic and semantic layers, with shared statistics for natural language understanding and generation. The ability to learn language involves generalisation from examples and figuring out which generalisations are useful given subsequent experience.

## Are there any benchmarks for Cognitive AI?

Not as yet. These could be qualitative benchmarks that demonstrate particular capabilities, or quantitive benchmarks in respect to performance. Benchmarks are related to roadmaps, and play a role in prioritising research and development goals.

## How can performance be scaled up?

Cortical operations on graph databases can be executed in parallel. The cortico-basal ganglia circuit corresponds to a sequential rule engine. Simple implementations slow down with increasing number of facts and rules. It would be impractically slow if the rules were to operate directly on the database. The solution is to have the rules operate on relatively small number of cortical buffers that each hold a single chunk, and to compile rule conditions into a discrimination network that efficiently maps the buffer states to the set of rules with matching conditions (analogous to the RETE algorithm). The next step is to determine the best matching rule, and then to execute its actions. This is a stochastic process influenced by past experience. In the human brain it is thought that the discrimination network corresponds to the Striatum, the rule selection stage to the Pallidum, and rule execution to the Thalamus. The cycle of rule execution is estimated to be approximately 50 milliseconds.  Cortical operations are executed asynchronously and can take considerably longer.

## How mature is Cognitive AI?

One the one hand, there has been decades of work in the cognitive sciences, e.g. on cognitive architectures such as ACT-R. On the other hand, most of that work has focused on research goals specific to particular disciplines. Cognitive AI seeks to build upon the insights gained over the decades in the cognitive sciences, and to apply it to AI.  This is relatively new and consequently still immature, but rapid progress is possible through incremental work on an expanding suite of capabilities.  See the discussion of the roadmap in the GitHub pages for the W3C Cognitive AI Community Group.

## If Cognitive AI mimics human thought, does it make the same kinds of mistakes as humans?

Yes, and just like people, this is a matter of training. A well trained cognitive agent will do well with respect to the tasks it was designed for. Unlike people, trained cognitive agents can be trivially cloned as needed! Systems based upon logical deduction and formal semantics offer mathematic proof given assumptions and inference rules, but are intolerant of inconsistencies and unable to exploit the statistics of past experience. Cognitive AI, inspired by human reasoning, and a combination of graphs and statistics, focuses on what is useful based upon prior knowledge past experience in the face of uncertainty and inconsistency.

## Is there a course on Cognitive AI?

Sadly, not as yet, but you would be welcome to help with developing one. For now there are the talks, the introductory materials on GitHub, the web-based demos, including a sandbox for editing and executing chunks and rules in a web browser.

## How can I get involved?

Please join the W3C Cognitive AI Community Group where your help will be welcomed. Participation is open to all, free of charge: [join group](https://www.w3.org/community/cogai/join).