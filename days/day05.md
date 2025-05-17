## A Survey on Knowledge Distillation of Large Language Models

> https://arxiv.org/html/2402.13116v4#abstract

---
### Abstract (Resumo)

In the era of Large Language Models (LLMs), Knowledge Distillation (KD) emerges as a pivotal methodology
for transferring advanced capabilities from leading proprietary LLMs, such as GPT-4, to their open-source counterparts like LLaMA and Mistral.
Additionally, as open-source LLMs flourish, KD plays a crucial role in both compressing these models,
and facilitating their self-improvement by employing themselves as teachers.

**Na era dos Grandes Modelos de Linguagem (LLMs), a Destilação de Conhecimento (KD) surge como uma metodologia fundamental
para transferir capacidades avançadas dos principais LLMs proprietários, como o GPT-4, para suas contrapartes de código aberto, como LLaMA e Mistral.
Além disso, à medida que os LLMs de código aberto florescem, a KD desempenha um papel crucial tanto na compactação desses modelos
quanto na facilitação de seu autoaperfeiçoamento, empregando-os como professores.**

This paper presents a comprehensive survey of KD’s role within the realm of LLM, highlighting its critical function
in imparting advanced knowledge to smaller models and its utility in model compression and self-improvement.

**Este artigo apresenta uma pesquisa abrangente sobre o papel do KD no âmbito do LLM, destacando sua função crítica
na transmissão de conhecimento avançado para modelos menores e sua utilidade na compressão e autoaperfeiçoamento de modelos.**

Our survey is meticulously structured around three foundational pillars: algorithm, skill, and verticalization,
providing a comprehensive examination of KD mechanisms, the enhancement of specific cognitive abilities,
and their practical implications across diverse fields.

**Nossa pesquisa é meticulosamente estruturada em torno de três pilares fundamentais: algoritmo, habilidade e verticalização,
oferecendo uma análise abrangente dos mecanismos de KD, o aprimoramento de habilidades cognitivas específicas
e suas implicações práticas em diversos campos.**

Crucially, the survey navigates the interaction between data augmentation (DA) and KD, illustrating how DA
emerges as a powerful paradigm within the KD framework to bolster LLMs’ performance.
By leveraging DA to generate context-rich, skill-specific training data, KD transcends traditional boundaries,
enabling open-source models to approximate the contextual adeptness, ethical alignment,
and deep semantic insights characteristic of their proprietary counterparts.

**Fundamentalmente, a pesquisa explora a interação entre o aumento de dados (DA) e o desenvolvimento de conhecimento (KD), ilustrando como o DA
surge como um paradigma poderoso dentro da estrutura do KD para impulsionar o desempenho dos LLMs.
Ao utilizar o DA para gerar dados de treinamento ricos em contexto e específicos para cada habilidade, o KD transcende as fronteiras tradicionais,
permitindo que modelos de código aberto se aproximem da adequação contextual, do alinhamento ético
e dos profundos insights semânticos característicos de suas contrapartes proprietárias.**

This work aims to provide an insightful guide for researchers and practitioners, offering a detailed overview
of current methodologies in knowledge distillation and proposing future research directions.
By bridging the gap between proprietary and open-source LLMs, this survey underscores the potential for more accessible,
efficient, and powerful AI solutions.

**Este trabalho visa fornecer um guia esclarecedor para pesquisadores e profissionais, oferecendo uma visão geral detalhada
das metodologias atuais em destilação de conhecimento e propondo futuras direções de pesquisa.
Ao preencher a lacuna entre LLMs proprietários e de código aberto, esta pesquisa destaca o potencial para soluções de IA mais acessíveis,
eficientes e poderosas.**

Most importantly, we firmly advocate for compliance with the legal terms that regulate the use of LLMs, ensuring ethical and lawful application of KD of LLMs.

**Mais importante ainda, defendemos firmemente o cumprimento dos termos legais que regulam o uso de LLMs, garantindo a aplicação ética e legal do KD de LLMs.**

---
### Introduction (Introdução)

In the evolving landscape of artificial intelligence (AI), proprietary1 Large Language Models (LLMs) such as GPT-3.5 Ouyang et al. (2022),
GPT-4 OpenAI et al. (2023), Gemini Team et al. (2023) and Claude2 have emerged as groundbreaking technologies,
reshaping our understanding of natural language processing (NLP). These models, characterized by their vast scale and complexity,
have unlocked new realms of possibility, from generating human-like text to offering sophisticated problem-solving capabilities.

**No cenário em evolução da inteligência artificial (IA), modelos proprietários de grande porte (LLMs)1, como GPT-3.5 Ouyang et al. (2022),
GPT-4 OpenAI et al. (2023), Gemini Team et al. (2023) e Claude2, emergiram como tecnologias inovadoras,
remodelando nossa compreensão do processamento de linguagem natural (PLN). Esses modelos, caracterizados por sua vasta escala e complexidade,
desbloquearam novos horizontes de possibilidades, desde a geração de textos semelhantes aos
humanos até o oferecimento de recursos sofisticados de resolução de problemas.**

The core significance of these LLMs lies in their emergent abilities Wei et al. (2022a, b); Xu et al. (2024a),
a phenomenon where the models display capabilities beyond their explicit training objectives,
enabling them to tackle a diverse array of tasks with remarkable proficiency.

**A importância central desses LLMs reside em suas habilidades emergentes (Wei et al. (2022a, b); Xu et al. (2024a),
um fenômeno em que os modelos demonstram capacidades que vão além de seus objetivos explícitos de treinamento,
permitindo-lhes lidar com uma gama diversificada de tarefas com proficiência notável.**

These models excel in understanding and generation, driving applications from creative generation to complex problem-solving OpenAI et al. (2023); Liang et al. (2022).
The potential of these models extends far beyond current applications, promising to revolutionize industries,
augment human creativity, and redefine our interaction with technology.

**Esses modelos se destacam em compreensão e geração, impulsionando aplicações que vão desde a geração criativa até a resolução de problemas complexos (OpenAI et al., 2023); Liang et al., 2022).
O potencial desses modelos vai muito além das aplicações atuais, prometendo revolucionar indústrias,
aumentar a criatividade humana e redefinir nossa interação com a tecnologia.**

Despite the remarkable capabilities of proprietary LLMs like GPT-4 and Gemini, they are not without their shortcomings,
particularly when viewed in light of the advantages offered by open-source models.
A significant drawback is their limited accessibility and higher cost OpenAI et al. (2023).
These proprietary models often come with substantial usage fees and restricted access,
making them less attainable for individuals and smaller organizations.

**Apesar das notáveis ​​capacidades de LLMs proprietários como GPT-4 e Gemini, eles apresentam suas deficiências,
particularmente quando vistos à luz das vantagens oferecidas por modelos de código aberto.
Uma desvantagem significativa é sua acessibilidade limitada e custo mais elevado (OpenAI et al. (2023).
Esses modelos proprietários frequentemente vêm com taxas de uso substanciais e acesso restrito,
tornando-os menos acessíveis para indivíduos e organizações menores.**

In terms of data privacy and security Wu et al. (2023a), using these proprietary LLMs frequently entails sending sensitive data to external servers,
which raises concerns about data privacy and security. This aspect is especially critical for users handling confidential information.
Moreover, the general-purpose design of proprietary LLMs, while powerful, may not always align with the specific needs of niche applications.
The constraints of accessibility, cost, and adaptability thus present significant challenges in leveraging the full potential of proprietary LLMs.

**Em termos de privacidade e segurança de dados, Wu et al. (2023a) afirmam que o uso desses LLMs proprietários frequentemente envolve o envio de dados sensíveis para servidores externos,
o que levanta preocupações sobre privacidade e segurança de dados. Esse aspecto é especialmente crítico para usuários que lidam com informações confidenciais.
Além disso, o design de uso geral dos LLMs proprietários, embora poderoso, pode nem sempre se alinhar às necessidades específicas de aplicações de nicho.
As restrições de acessibilidade, custo e adaptabilidade, portanto, apresentam desafios significativos para o aproveitamento de todo o potencial dos LLMs proprietários.**

In contrast to proprietary LLMs, open-source models like LLaMA Touvron et al. (2023) and Mistral Jiang et al. (2023a) bring several notable advantages.
One of the primary benefits of open-source models is their accessibility and adaptability.
Without the constraints of licensing fees or restrictive usage policies, these models are more readily available to a broader range of users,
from individual researchers to smaller organizations.
This openness fosters a more collaborative and inclusive AI research environment, encouraging innovation and diverse applications.
Additionally, the customizable nature of open-source LLMs allows for more tailored solutions, addressing specific needs that generic, large-scale models may not meet.

**Em contraste com os LLMs proprietários, modelos de código aberto como o LLaMA de Touvron et al. (2023) e Mistral Jiang et al. (2023a) apresentam diversas vantagens notáveis.
Um dos principais benefícios dos modelos de código aberto é sua acessibilidade e adaptabilidade.
Sem as restrições de taxas de licenciamento ou políticas de uso restritivas, esses modelos estão mais prontamente disponíveis para uma gama mais ampla de usuários,
desde pesquisadores individuais até organizações menores.
Essa abertura promove um ambiente de pesquisa em IA mais colaborativo e inclusivo, incentivando a inovação e a diversidade de aplicações.
Além disso, a natureza personalizável dos LLMs de código aberto permite soluções mais personalizadas,
atendendo a necessidades específicas que modelos genéricos de larga escala podem não atender.**

However, the open-source LLMs also have their own set of drawbacks, primarily stemming from their relatively limited scale and resources compared
to their proprietary counterparts.
One of the most significant limitations is the smaller model scale,
which often results in lower performance on real-world tasks with a bunch of instructions Zheng et al. (2023a).
These models, with fewer parameters, may struggle to capture the depth and breadth of knowledge embodied in larger models like GPT-4.

**No entanto, os LLMs de código aberto também apresentam seu próprio conjunto de desvantagens, decorrentes principalmente de sua escala e recursos relativamente limitados em comparação com suas contrapartes proprietárias.
Uma das limitações mais significativas é a escala menor do modelo,
que frequentemente resulta em desempenho inferior em tarefas do mundo real com um conjunto de instruções (Zheng et al., 2023a).
Esses modelos, com menos parâmetros, podem ter dificuldade em capturar a profundidade e a amplitude do conhecimento incorporado em modelos maiores, como o GPT-4.**

Additionally, the pre-training investment in these open-source models is typically less substantial.
This reduced investment can lead to a narrower range of pre-training data, potentially limiting the models
understanding and handling of diverse or specialized topics Liang et al. (2022); Sun et al. (2024a).

**Além disso, o investimento em pré-treinamento nesses modelos de código aberto costuma ser menos substancial.
Esse investimento reduzido pode levar a uma gama mais restrita de dados de pré-treinamento,
potencialmente limitando a compreensão e o manuseio de tópicos diversos ou especializados pelos modelos (Liang et al. (2022); Sun et al. (2024a).**

Moreover, open-source models often undergo fewer fine-tuning steps due to resource constraints.
Fine-tuning is crucial for optimizing a model’s performance for specific tasks or industries,
and the lack thereof can hinder the model’s effectiveness in specialized applications.

**Além disso, modelos de código aberto frequentemente passam por menos etapas de ajuste fino devido a restrições de recursos.
O ajuste fino é crucial para otimizar o desempenho de um modelo para tarefas ou setores específicos,
e a falta dele pode prejudicar a eficácia do modelo em aplicações especializadas.**

This limitation becomes particularly evident when these models are compared to the highly fine-tuned proprietary LLMs,
which are often tailored to excel in a wide array of complex scenarios OpenAI et al. (2023).

**Essa limitação se torna particularmente evidente quando esses modelos são comparados aos LLMs proprietários altamente ajustados,
que geralmente são adaptados para se destacar em uma ampla gama de cenários complexos (OpenAI et al., 2023).**

Primarily, recognizing the disparities between proprietary and open-source LLMs,
KD techniques have surged as a means to bridge the performance gap between these models Gou et al. (2021); Gupta and Agrawal (2022).
Knowledge distillation, in this context, involves leveraging the more advanced capabilities of leading proprietary models like GPT-4
or Gemini as a guiding framework to enhance the competencies of open-source LLMs.

**Principalmente, reconhecendo as disparidades entre LLMs proprietários e de código aberto,
as técnicas de KD surgiram como um meio de preencher a lacuna de desempenho entre esses modelos (Gou et al. (2021); Gupta e Agrawal (2022).
A destilação de conhecimento, neste contexto, envolve o aproveitamento dos recursos mais avançados dos principais modelos proprietários, como o GPT-4
ou o Gemini, como uma estrutura orientadora para aprimorar as competências dos LLMs de código aberto.**

This process is akin to transferring the ‘knowledge’ of a highly skilled teacher to a student, wherein the student (e.g., open-source LLM)
learns to mimic the performance characteristics of the teacher (e.g., proprietary LLM).
Compared to traditional knowledge distillation algorithms Gou et al. (2021), data augmentation (DA) Feng et al. (2021)
has emerged as a prevalent paradigm to achieve knowledge distillation of LLMs,
where a small seedof knowledge is used to prompt the LLM to generate more data with respect to a specific skill or domain Taori et al. (2023).

**Esse processo é semelhante à transferência do "conhecimento" de um professor altamente qualificado para um aluno, em que o aluno (por exemplo, LLM de código aberto)
aprende a imitar as características de desempenho do professor (por exemplo, LLM proprietário).
Comparado aos algoritmos tradicionais de destilação de conhecimento de Gou et al. (2021), o aumento de dados (AD) de Feng et al. (2021)
surgiu como um paradigma predominante para alcançar a destilação de conhecimento de LLMs,
onde uma pequena semente de conhecimento é usada para induzir o LLM a gerar mais dados em relação a uma habilidade ou domínio específico. Taori et al. (2023).**

Secondly, KD still retains its fundamental role in compressing LLMs, making them more efficient without significant
loss in performance.  Gu et al. (2024); Agarwal et al. (2024).
More recently, the strategy of employing open-source LLMs as teachers for their own self-improvement has emerged as a promising approach,
enhancing their capabilities significantly Yuan et al. (2024a); Chen et al. (2024a).
Figure 1 provides an illustration of these three key roles played by KD in the context of LLMs.

**Em segundo lugar, o Desenvolvimento de Conhecimento (KD) ainda mantém seu papel fundamental na compactação de LLMs, tornando-os mais eficientes sem perda significativa de desempenho. Gu et al. (2024); Agarwal et al. (2024).
Mais recentemente, a estratégia de empregar LLMs de código aberto como professores para seu próprio autoaperfeiçoamento surgiu como uma abordagem promissora,
aprimorando significativamente suas capacidades (Yuan et al. (2024a); Chen et al. (2024a).
A Figura 1 ilustra esses três papéis principais desempenhados pelo KD no contexto de LLMs.**

![image](https://github.com/user-attachments/assets/4c71a840-b6ba-4771-88a3-cd29b46eda63)

A key aspect of the knowledge distillation is the enhancement of skills such as advanced context following 
(e.g., in-context learning Huang et al. (2022a) and instruction following Taori et al. (2023)),
improved alignment with user intents (e.g., human values/principles Cui et al. (2023a),
and thinking patterns like chain-of-thought (CoT) Mukherjee et al. (2023)), and NLP task specialization (e.g., semantic understanding Ding et al. (2023a),
and code generation Chaudhary (2023)).

**Um aspecto fundamental da destilação do conhecimento é o aprimoramento de habilidades como acompanhamento avançado de contexto
(por exemplo, aprendizagem em contexto Huang et al. (2022a) e acompanhamento de instruções Taori et al. (2023)),
melhor alinhamento com as intenções do usuário (por exemplo, valores/princípios humanos Cui et al. (2023a),
e padrões de pensamento como cadeia de pensamento (CoT) Mukherjee et al. (2023)), e especialização de tarefas de PNL (por exemplo, compreensão semântica Ding et al. (2023a),
e geração de código Chaudhary (2023)).**

These skills are crucial for the wide array of applications that LLMs are expected to perform,
ranging from casual conversations to complex problem-solving in specialized domains.
For instance, in vertical domains like healthcare Wang et al. (2023a), law LAW (2023), or science Zhang et al. (2024),
where accuracy and context-specific knowledge are paramount,
knowledge distillation allows open-source models to significantly improve their performance by learning from the proprietary models
that have been extensively trained and fine-tuned in these areas.

**Essas habilidades são cruciais para a ampla gama de aplicações que se espera que os LLMs desempenhem,
desde conversas informais até a resolução de problemas complexos em domínios especializados.
Por exemplo, em domínios verticais como saúde (Wang et al., 2023a), direito (LAW, 2023) ou ciência (Zhang et al., 2024),
onde a precisão e o conhecimento específico do contexto são primordiais,
a destilação do conhecimento permite que modelos de código aberto melhorem significativamente seu desempenho, aprendendo com modelos proprietários
que foram extensivamente treinados e aprimorados nessas áreas.**

The benefits of knowledge distillation in the era of LLMs are multifaceted and transformative Gu et al. (2024).
Through a suite of distillation techniques, the gap between proprietary and open-source models is significantly narrowed Chiang et al. (2023); Xu et al. (2023a)
and even filled Zhao et al. (2023a).
This process not only streamlines computational requirements but also enhances the environmental sustainability of AI operations,
as open-source models become more proficient with lesser computational overhead.
Furthermore, knowledge distillation fosters a more accessible and equitable AI landscape,
where smaller entities and individual researchers gain access to state-of-the-art capabilities, encouraging wider participation and diversity in AI advancements.
This democratization of technology leads to more robust, versatile, and accessible AI solutions,
catalyzing innovation and growth across various industries and research domains.

**Os benefícios da destilação do conhecimento na era dos LLMs são multifacetados e transformadores (Gu et al., 2024).
Por meio de um conjunto de técnicas de destilação, a lacuna entre modelos proprietários e de código aberto é significativamente reduzida
(Chiang et al., 2023); Xu et al., 2023a)
e até mesmo preenchida (Zhao et al., 2023a).
Esse processo não apenas otimiza os requisitos computacionais, mas também aprimora a sustentabilidade ambiental das operações de IA,
à medida que os modelos de código aberto se tornam mais proficientes com menor sobrecarga computacional.
Além disso, a destilação do conhecimento promove um cenário de IA mais acessível e equitativo,
onde entidades menores e pesquisadores individuais obtêm acesso a recursos de ponta, incentivando maior participação e diversidade nos avanços da IA.
Essa democratização da tecnologia leva a soluções de IA mais robustas, versáteis e acessíveis,
catalisando inovação e crescimento em diversos setores e domínios de pesquisa.**

The escalating need for a comprehensive survey on the knowledge distillation of LLMs stems from the rapidly evolving
landscape of AI OpenAI et al. (2023); Team et al. (2023) and the increasing complexity of these models.
As AI continues to penetrate various sectors, the ability to efficiently and effectively distill knowledge
from proprietary LLMs to open-source ones becomes not just a technical aspiration but a practical necessity.

**A crescente necessidade de um levantamento abrangente sobre a destilação do conhecimento de LLMs decorre da rápida evolução do cenário da IA ​​(OpenAI et al. (2023); Team et al. (2023)) e da crescente complexidade desses modelos.
À medida que a IA continua a penetrar em diversos setores, a capacidade de destilar conhecimento de forma eficiente e eficaz
de LLMs proprietários para LLMs de código aberto torna-se não apenas uma aspiração técnica, mas uma necessidade prática.**

This need is driven by the growing demand for more accessible, cost-effective, and adaptable AI solutions that can cater to a diverse range of applications and users.
A survey in this field is vital for synthesizing the current methodologies, challenges, and breakthroughs in knowledge distillation.
It may serve as a beacon for researchers and practitioners alike, guiding them to distill complex AI capabilities into more manageable and accessible forms.
Moreover, such a survey can illuminate the path forward, identifying gaps in current techniques and proposing directions for future research.

**Essa necessidade é impulsionada pela crescente demanda por soluções de IA mais acessíveis, econômicas e adaptáveis, que possam atender a uma gama diversificada de aplicações e usuários.
Uma pesquisa nessa área é vital para sintetizar as metodologias, os desafios e os avanços atuais na destilação do conhecimento.
Ela pode servir como um guia para pesquisadores e profissionais, orientando-os a destilar capacidades complexas de IA em formas mais gerenciáveis ​​e acessíveis.
Além disso, essa pesquisa pode iluminar o caminho a seguir, identificando lacunas nas técnicas atuais e propondo direções para pesquisas futuras.**

---
### Survey Organization

The remainder of this survey is organized into several comprehensive sections,
each designed to offer a deep dive into the multifaceted aspects of knowledge distillation within the realm ofLLMs.
Following this introduction, §2 provides a foundational overview of knowledge distillation,
comparing traditional techniques with those emerging in the era of LLMs and highlighting the role of data augmentation (DA) in this context.
§3 delves into the approaches to elicit knowledge from teacher LLMs and core distillation algorithms,
examining methods from supervised fine-tuning to more complex strategies involving divergence and similarity, reinforcement learning, and ranking optimization.

**O restante desta pesquisa está organizado em várias seções abrangentes,
cada uma projetada para oferecer um mergulho profundo nos aspectos multifacetados da destilação do conhecimento no âmbito dos LLMs.
Após esta introdução, o §2 fornece uma visão geral fundamental da destilação do conhecimento,
comparando técnicas tradicionais com aquelas emergentes na era dos LLMs e destacando o papel do aumento de dados (DA) nesse contexto.
O §3 investiga as abordagens para extrair conhecimento de LLMs de professores e algoritmos de destilação essenciais,
examinando métodos que vão desde o ajuste fino supervisionado até estratégias mais complexas envolvendo divergência e similaridade,
aprendizagem por reforço e otimização de classificação.**

Then, §4 focuses on skill distillation, exploring how student models can be enhanced to improve context understanding,
alignment with user intentions, and performance across a variety of NLP tasks.
This includes discussions on natural language understanding (NLU), generation (NLG), information retrieval,
recommendation systems, and the evaluation of text generation. In §5, we venture into domain-specific vertical distillation,
showcasing how knowledge distillation techniques are applied within specialized fields such as law, healthcare, finance, and science,
illustrating the practical implications and transformative impact of these approaches.
The survey suggests open problems in §6, identifying current challenges and gaps in knowledge distillation research that offer opportunities for future work.
Finally, the conclusion and discussion in §7 synthesize the insights gained,
reflecting on the implications for the broader AI and NLP research community and proposing directions for future research.

**Em seguida, o §4 concentra-se na destilação de habilidades, explorando como os modelos de alunos podem ser aprimorados para melhorar a compreensão do contexto,
o alinhamento com as intenções do usuário e o desempenho em uma variedade de tarefas de PNL.
Isso inclui discussões sobre compreensão de linguagem natural (NLU), geração (NLG), recuperação de informações,
sistemas de recomendação e avaliação da geração de texto. No §5, nos aventuramos na destilação vertical de domínio específico,
mostrando como as técnicas de destilação de conhecimento são aplicadas em campos especializados, como direito, saúde, finanças e ciência,
ilustrando as implicações práticas e o impacto transformador dessas abordagens.
A pesquisa sugere problemas em aberto no §6, identificando desafios e lacunas atuais na pesquisa em destilação de conhecimento que oferecem
oportunidades para trabalhos futuros.
Finalmente, a conclusão e a discussão no §7 sintetizam os insights obtidos,
refletindo sobre as implicações para a comunidade mais ampla de pesquisa em IA e PNL e propondo direções para pesquisas futuras.**

Figure 2 shows an overview of this survey.
**A Figura 2 mostra uma visão geral desta pesquisa.**

![image](https://github.com/user-attachments/assets/e10c8eb6-d030-41e7-b135-0330326908a3)
