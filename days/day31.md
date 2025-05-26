## Overview (Visão geral)

---
### Comparing Traditional Recipe (Comparando Receitas Tradicionais)

The concept of knowledge distillation in the field of AI and deep learning (DL) refers to the process of transferring knowledge from a large,
complex model (teacher) to a smaller, more efficient model (student) Gou et al. (2021).
This technique is pivotal in mitigating the challenges posed by the computational
demands and resource constraints of deploying large-scale models in practical applications.

**O conceito da destilação de conhecimento na área de IA e aprendizagem profunda (DL) refere-se ao processo de transferência de conhecimento de um modelo amplo e complexo (professor) para um modelo menor e mais eficiente (aluno) (Gou et al. (2021).<br>
Essa técnica é fundamental para mitigar os desafios impostos pelas demandas computacionais e restrições de recursos oriundos da implantação de modelos em aplicações práticas.**

Historically, knowledge distillation techniques, prior to the era of LLMs, primarily concentrated on transferring knowledge from complex,
often cumbersome neural networks to more compact and efficient architectures Sanh et al. (2019); Kim and Rush (2016).
his process was largely driven by the need to deploy machine learning models in resource-constrained environments, such as mobile devices or edge computing platforms,
where the computational power and memory are limited. 

**Historicamente, as técnicas de destilação de conhecimento, antes da era dos LLMs, concentravam-se principalmente na transferência de conhecimento de redes neurais complexas,
muitas vezes pesadas, para arquiteturas mais compactas e eficientes (Sanh et al., 2019); Kim e Rush (2016).<br>
Este processo foi amplamente impulsionado pela necessidade de implantar modelos de aprendizado de máquina em ambientes com recursos limitados, como dispositivos móveis ou plataformas de computação de ponta,
onde o poder computacional e a memória são limitados.**

The focus was predominantly on ad-hoc neural architecture selection and training objectives tailored for single tasks.
These earlier methods involved training a smaller student network to mimic the output of a larger teacher network,
often through techniques like soft target training, where the student learns from the softened softmax output of the teacher.
Please refer to the survey Gou et al. (2021) for more details on general knowledge distillation techniques in AI and DL.

**O foco estava predominantemente na seleção de arquitetura neural ad-hoc e em objetivos de treinamento adaptados para tarefas individuais.<br>
Esses métodos anteriores envolviam o treinamento de uma rede menor para imitar a saída de uma rede maior,
frequentemente por meio de técnicas como soft-targets (alvos suavizados), em que o aluno aprende com a saída suavizada do professor.<br>
Consulte a pesquisa de Gou et al. (2021) para obter mais detalhes sobre técnicas de destilação de conhecimento geral em IA e DL.**

In contrast, the advent of LLMs has revolutionized the knowledge distillation landscape.
The current era of knowledge distillation in LLMs shifts the focus from mere architecture compression to knowledge elicitation and transfer Taori et al. (2023);
Chaudhary (2023); Tunstall et al. (2023).

**Em contraste, o advento dos LLMs revolucionou o cenário da destilação do conhecimento.<br>
A era atual da destilação do conhecimento em LLMs desloca o foco da mera compressão da arquitetura para a elicitação e transferência de conhecimento. Taori et al. (2023);
Chaudhary (2023); Tunstall et al. (2023).**

This paradigm change is largely due to the expansive and deep-seated knowledge that LLMs like GPT-4 and Gemini possess.
And the inaccessible parameters of LLMs make it hard to compress them by using pruning Han et al. (2016) or quantization Liu et al. (2023a) techniques.

**Essa mudança de paradigma se deve, em grande parte, ao conhecimento amplo e profundo que LLMs como GPT-4 e Gemini possuem.<br>
Os parâmetros inacessíveis dos LLMs dificultam sua compactação por meio de técnicas de poda (Han et al., 2016) ou quantização (Liu et al., 2023a).**

Unlike the earlier era, where the goal was to replicate the output behavior of the teacher model or reduce the model size,
the current focus in LLM-based knowledge distillation is to elicit the specific knowledge these models have.

**Diferentemente da era anterior, em que o objetivo era replicar o comportamento de saída do modelo professor ou compressão de tamanho,
o foco atual na destilação de conhecimento baseada em LLM é extrair o conhecimento específico que esses modelos possuem.**

The key to this modern approach lies in heuristic and carefully designed prompts, which are used to elicit specific knowledge Ding et al. (2023b)
or capabilities Chaudhary (2023) from the LLMs.
These prompts are crafted to tap into the LLM’s understanding and capabilities in various domains,
ranging from natural language understanding He et al. (2023a) to more complex cognitive tasks like reasoning Hsieh et al. (2023)
and problem-solving Qiao et al. (2024).

**A chave para essa abordagem moderna reside em prompts cuidadosamente elaborados, que são usados ​​para extrair conhecimento específico (Ding et al., 2023b)
dos LLMs.<br>
Esses prompts são elaborados para explorar a compreensão do LLM em vários domínios,
desde a compreensão da linguagem natural (He et al., 2023a) até tarefas cognitivas mais complexas, como raciocínio (Hsieh et al., 2023)
e resolução de problemas (Qiao et al., 2024).**

The use of prompts as a means of knowledge elicitation offers a more flexible and dynamic approach to distillation.
It allows for a more targeted extraction of knowledge, focusing on specific skills or domains of interest.
This method is particularly effective in harnessing the emergent abilities of LLMs, where the models exhibit capabilities beyond their explicit training objectives.

**O uso de prompts como meio de extração de conhecimento oferece uma abordagem mais flexível e dinâmica para a destilação.<br>
Permite uma extração de conhecimento mais direcionada, com foco em habilidades ou domínios de interesse específicos.
Este método é particularmente eficaz no aproveitamento das habilidades emergentes de LLMs, onde os modelos demonstram capacidades que vão além de seus objetivos explícitos de treinamento.**

Furthermore, this era of knowledge distillation also emphasizes the transfer of more abstract qualities such as reasoning patterns Mitra et al. (2023),
preference alignment Cui et al. (2023a), and value alignment Sun et al. (2024b).
This is in stark contrast to the earlier focus on output replication Taori et al. (2023),
indicating a shift towards a more holistic and comprehensive transfer of cognitive capabilities.

**Além disso, esta era de destilação do conhecimento também enfatiza a transferência de qualidades mais abstratas, como padrões de raciocínio de Mitra et al. (2023),
alinhamento de preferências de Cui et al. (2023a) e alinhamento de valores de Sun et al. (2024b).<br>
Isso contrasta fortemente com o foco anterior na replicação de resultados de Taori et al. (2023),
indicando uma mudança em direção a uma transferência mais holística e abrangente de capacidades cognitivas.**

The current techniques involve not just the replication of outputs, but also the emulation of the thought processes Mitra et al. (2023)
and decision-making Asai et al. (2023) patterns of the teacher model.

**As técnicas atuais envolvem não apenas a replicação de resultados, mas também a emulação dos processos de pensamento (Mitra et al., 2023)
e dos padrões de tomada de decisão (Asai et al., 2023)) do modelo do professor.**

This involves complex strategies like chain-of-thought prompting, where the student model is trained to learn the reasoning process of the teacher,
thereby enhancing its problem-solving and decision-making capabilities.

**Isso envolve estratégias complexas, como a estimulação por cadeia de pensamento, em que o modelo do aluno é treinado para aprender o processo de raciocínio do professor,
aprimorando assim suas capacidades de resolução de problemas e tomada de decisões.**

---
### Relation to Data Augmentation (DA) - Relação com Aumento de Dados

In the era of LLMs, Data Augmentation (DA) Wang et al. (2022a); Ye et al. (2022)
emerges as a critical paradigm integral to the process of knowledge distillation.
Unlike traditional DA techniques such as paraphrasing Gangal et al. (2022) or back-translation Longpre et al. (2019),
which primarily aim at expanding the training dataset in a somewhat mechanical manner,
DA within the context of LLMs focuses on the generation of novel, context-rich training data tailored to specific domains and skills.

**Na era dos LLMs, o Aumento de Dados (AD) Wang et al. (2022a); Ye et al. (2022)
surge como um paradigma crítico e integral ao processo de destilação do conhecimento.<br>
Ao contrário das técnicas tradicionais de AD, como a paráfrase de Gangal et al. (2022) ou a retrotradução de Longpre et al. (2019),
que visam principalmente expandir o conjunto de dados de treinamento de forma um tanto mecânica,
o AD no contexto dos LLMs concentra-se na geração de dados de treinamento novos e ricos em contexto, adaptados a domínios e habilidades específicos.**

The relationship between DA and KD in LLMs is both symbiotic and foundational. By leveraging a set of seed knowledge,
KD employs DA to prompt LLMs to produce explicit data that encapsulates specific skills or domain expertise Chaudhary (2023);
West et al. (2022). This method stands out as a potent mechanism for bridging the knowledge and capability gap between proprietary and open-source models.
Through DA, LLMs are prompted to create targeted, high-quality datasets that are not merely larger in volume but are also rich in diversity and specificity.
This approach enables the distillation process to be more effective,
ensuring that the distilled models not only replicate the teacher model’s output behavior but also embody its deep-seated understanding and cognitive strategies.

**A relação entre DA e KD em LLMs é simbiótica e fundamental.<br>
Ao usar um conjunto de conhecimento inicial,
KD emprega DA para induzir LLMs a produzir dados explícitos que encapsulam habilidades específicas ou expertise de domínio (Chaudhary, 2023);
West et al. (2022).<br>
Este método se destaca como um mecanismo potente para preencher a lacuna de conhecimento e capacidade entre modelos proprietários e de código aberto.<br>
Por meio da DA, LLMs são induzidos a criar conjuntos de dados direcionados e de alta qualidade que não são apenas maiores em volume, mas também ricos em diversidade e especificidade.<br>
Essa abordagem permite que o processo de destilação seja mais eficaz,
garantindo que os modelos destilados não apenas reproduzam o comportamento de saída do modelo do professor, mas também incorporem sua compreensão e estratégias cognitivas arraigadas.**

DA acts as a force multiplier,
enabling the distilled models to acquire and refine capabilities that would otherwise require exponentially larger datasets and computational resources.
It facilitates a more effective transfer of knowledge,
focusing on the qualitative aspects of learning rather than quantitative expansion.

**O Aumento de Dados atua como um multiplicador de força,
permitindo que os modelos destilados adquiram e refinem capacidades que, de outra forma, exigiriam conjuntos de dados e recursos computacionais exponencialmente maiores.<br>
Ela facilita uma transferência de conhecimento mais eficaz,
com foco nos aspectos qualitativos da aprendizagem em vez da expansão quantitativa.**

This strategic use of DA within KD processes underscores a pivotal shift towards a more efficient, sustainable,
and accessible approach to harnessing the power of LLMs. It empowers open-source models with the ability to approximate the contextual adeptness,
ethical alignment, and deep semantic insights characteristic of their proprietary counterparts,
thereby democratizing access to advanced AI capabilities and fostering innovation across a broader spectrum of applications and users.

**Esse uso estratégico de Aumento de Dados nos processos de Destilação destaca uma mudança crucial em direção a uma abordagem mais eficiente, sustentável
e acessível para aproveitar o poder dos LLMs.<br>
Ela capacita modelos de código aberto com a capacidade de aproximar a adequação contextual,
o alinhamento ético e os profundos insights semânticos característicos de suas contrapartes proprietárias,
democratizando assim o acesso a recursos avançados de IA e fomentando a inovação em um espectro mais amplo de aplicações e usuários.**

---
### Distillation Pipeline in LLM Era - Pipeline de Destilação na era LLM

![image](https://github.com/user-attachments/assets/337e4780-f638-434a-9d2f-a8326864d506)

The general distillation pipeline of LLMs is a structured and methodical process aimed at transferring knowledge
from a sophisticated teacher model to a less complex student model.
This pipeline is integral for leveraging the advanced capabilities of models like GPT-4 or Gemini
in more accessible and efficient open-source counterparts.

**O pipeline de destilação geral dos LLMs é um processo estruturado e metódico que visa transferir conhecimento
de um modelo sofisticado de professor para um modelo menos complexo de aluno.<br>
Esse pipeline é essencial para alavancar os recursos avançados de modelos como GPT-4 ou Gemini
em versões de código aberto mais acessíveis e eficientes.**

The outline of this pipeline can be broadly categorized into four distinct stages, each playing a crucial role
in the successful distillation of knowledge. An illustration is shown in Figure 4. The detailed pipeline could also be seen in Figure 2.

**O esboço desse pipeline pode ser amplamente categorizado em quatro etapas distintas, cada uma desempenhando um papel crucial
na destilação bem-sucedida do conhecimento. Uma ilustração é mostrada na Figura 4. O pipeline detalhado também pode ser visto na Figura 2.**

**I. Target Skill - Habilidade Alvo**<br>
The first stage involves directing the teacher LLM towards a specific target skill or domain.
This is achieved through carefully crafted instructions or templates that guide the LLM’s focus.
These instructions are designed to elicit responses that demonstrate the LLM’s proficiency in a particular area,
be it a specialized domain like healthcare or law, or a skill such as reasoning or language understanding.

**A primeira etapa envolve direcionar o professor (LLM) para uma habilidade ou domínio específico.<br>
Isso é alcançado por meio de instruções ou modelos cuidadosamente elaborados que orientam o foco do LLM.<br>
Essas instruções são elaboradas para obter respostas que demonstrem a proficiência do LLM em uma área específica,
seja uma área especializada, como saúde ou direito, ou uma habilidade como raciocínio ou compreensão de idiomas.**

**II. Seed Knowledge as Input - Conhecimento Semente como Entrada**<br>
Once the target area is defined, the next step is to feed the teacher LLM with seed knowledge.
This seed knowledge typically comprises a small dataset or specific data clues relevant to the elicit skill or domain knowledge from the teacher LLM.
It acts as a catalyst, prompting the teacher LLM to generate more elaborate and detailed outputs based on this initial information.
The seed knowledge is crucial as it provides a foundation upon which the teacher model can build and expand,
thereby creating more comprehensive and in-depth knowledge examples.

**Uma vez definida a área-alvo, o próximo passo é alimentar o professor (LLM) com conhecimento inicial.<br>
Esse conhecimento inicial normalmente compreende um pequeno conjunto de dados ou pistas de dados específicas relevantes para extrair conhecimento de habilidades ou domínio do professor(LLM).<br>
Ele atua como um catalisador, levando o professor (LLM) a gerar resultados mais elaborados e detalhados com base nessas informações iniciais.<br>
O conhecimento inicial é crucial, pois fornece uma base sobre a qual o conhecimento do modelo professor pode ser construído e expandido,
criando, assim, exemplos de conhecimento mais abrangentes e aprofundados.**

**III. Generation of Knowledge - Geração de Conhecimento**<br>
In response to the seed knowledge and steering instructions,
the teacher LLM generates knowledge examples.
These examples are predominantly in the form of question-and-answer (QA) dialogues or narrative explanations,
aligning with the natural language processing/understanding capabilities of the LLM.
In certain specialized cases, the outputs may also include logits or hidden features,
although this is less common due to the complexity and specific requirements of such data forms.
The generated knowledge examples constitute the core of the distillation knowledge, encapsulating the advanced understanding and skills of the teacher LLM.

**Em resposta ao conhecimento inicial e às instruções de orientação,
o professor gera exemplos de conhecimento.<br>
Esses exemplos são predominantemente na forma de diálogos de perguntas e respostas (QA) ou explicações narrativas,
alinhando-se com as capacidades de processamento/compreensão da linguagem natural do LLM.<br>
Em certos casos especializados, as saídas também podem incluir logits ou recursos ocultos,
embora isso seja menos comum devido à complexidade e aos requisitos específicos de tais formatos de dados.<br>
Os exemplos de conhecimento gerados constituem o núcleo do conhecimento de destilação, encapsulando a compreensão e as habilidades avançadas do professor (LLM)**

**IV. Training the Student Model with a Specific Learning Objective - Treinamento do Modelo Aluno com um Objetivo de Aprendizagem Específica**<br>
The final stage involves the utilization of the generated knowledge examples to train the student model.
This training is guided by a loss function that aligns with the learning objectives.
The loss function quantifies the student model’s performance in replicating or adapting the knowledge from the teacher model.
By minimizing this loss, the student model learns to emulate the target skills or domain knowledge of the teacher, thereby acquiring similar capabilities.
The process involves iteratively adjusting the student model’s parameters to reduce the discrepancy between its outputs and those of the teacher model,
ensuring the effective transfer of knowledge.

Following our exploration of the distillation pipeline and the foundational concepts underlying knowledge distillation in the LLM era,
we now turn our focus to the specific algorithms that have gained prominence in this era.

**A etapa final envolve a utilização do conhecimento gerado para treinar o modelo aluno.<br>
Este treinamento é guiado por uma função de perda alinhada aos objetivos de aprendizagem.<br>
A função de perda quantifica o desempenho do modelo aluno na replicação do conhecimento do modelo professor.<br>
Ao minimizar essa perda, o modelo aluno aprende a emular as habilidades-alvo ou o conhecimento de domínio do professor, adquirindo, assim, capacidades semelhantes.<br>
O processo envolve o ajuste iterativo dos parâmetros do modelo aluno para reduzir a discrepância entre seus resultados e os do modelo professor,
garantindo a transferência eficaz do conhecimento.**

**Após nossa exploração do pipeline de destilação e dos conceitos fundamentais que fundamentam a destilação do conhecimento na era do LLM,
agora voltamos nosso foco para os algoritmos específicos que ganharam destaque nessa era.**

![image](https://github.com/user-attachments/assets/4263190c-8832-4ee1-8a4f-12432059ea6a)
