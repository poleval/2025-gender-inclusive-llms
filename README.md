# Gender-inclusive LLMs for Polish

👩🏻‍🏫 [Alina Wróblewska](https://www.linkedin.com/in/alina-wroblewska-phd-b22055357)

## 👋 Introduction

Polish is a grammatical gender language in which all nouns inherently encode gender markers as an integral part of the grammatical system. For example, *śliwka* [a plum] is feminine, *jabłko* [an apple] is neutral, whereas *pomidor* [a tomato] is masculine. All adjectives and verbs associated with a noun must match the noun's grammatical gender. Additionally, personal nouns have distinct feminine, e.g., *nauczycielka* [a teacher<sub>fem</sub>] and masculine forms, e.g., *nauczyciel* [a teacher<sub>masc</sub>]. While feminine personal nouns typically denote female individuals or groups of females, masculine personal nouns refer not only to male individuals or male groups but also to mixed-gender groups and even females, a phenomenon known as the generic masculine, e.g., *niemiecka polityk Ursula von der Leyen* [German<sub>fem</sub> politician<sub>masc</sub> Ursula<sub>fem</sub> von der Leyen].

Although the grammatical system of Polish allows for naming individuals according to their natural gender (i.e., female or male), standard Polish remains heavily masculine-centric. This is reflected in a strong dominance of masculine expressions over feminine ones, which may be interpreted as reinforcing gender bias and exclusion. 

One social consequence of this linguistic system is that current large language models (LLMs) trained on Polish texts inherit and reinforce masculine bias, generating gender-imbalanced outputs. As LLMs become increasingly integrated into communication, translation, and content generation systems, ensuring their outputs reflect gender inclusivity is crucial, particularly in gender-rich languages like Polish.

The dominance of masculine expressions over feminine ones in a language is a form of gender discrimination ([GEC](https://edoc.coe.int/en/gender-equality/6947-gender-equality-glossary.html),  [GNL-EU](https://www.europarl.europa.eu/cmsdata/151780/GNL_Guidelines_EN.pdf)). Acknowledging the harmful effects of sexist language, the Council of Europe encourages its member states to eliminate sexism from language and to adopt practices that support gender equality. In line with this recommendation, we introduce a task focused on developing gender-inclusive LLMs for Polish.

<p align="center">
<img src="https://github.com/poleval/2025-gender-inclusive-llms/blob/main/pictures/gender-equality.png" alt="gender_inclusive_language" width="100"/>
</p>

<p align="center">
✨<b>Make the world more equal! Join the gender-inclusive challenge!</b>
</p>



## 💡 Task description

### Task objective

The task aims to raise community awareness of gender inequalities in Polish and to develop LLMs capable of generating grammatically correct and gender-aware language across various contexts. Participants are challenged to embed gender inclusivity as a core feature of LLMs, offering a solution to mitigating gender bias in Polish language generation. By advancing gender-inclusive LLMs, this shared task contributes to broader efforts to promote gender equality through language, highlighting the potential of AI to facilitate more inclusive and equitable communication.


### Specification

Each submitted gender-inclusive LLM will be evaluated on two tasks:

> 🅰️ **gender-inclusive proofreading** — transforming a text passage written in standard Polish into its gender-inclusive version.
> 
> 🅱️ **Gender-sensitive Polish⇄English translation** — translating a text passage written in gender-inclusive Polish into English or an English text passage into a gender-inclusive Polish translation.

📦 **Data:** Inclusive Polish Instruction Set (**IPIS**) is made available to all participants.

💹 **Working phase:** Using the *train* and *dev* subsets of the IPIS dataset, participants are expected to enhance **open-source LLMs** to ensure gender inclusivity.

✅ **Testing phase:** Using the *test* subset of the IPIS dataset, submitted outputs of gender-inclusive LLMs will be evaluated in the PolEval system.

*️⃣ **System prompt:** The system prompts with **gender-inclusive guidelines** based on Wróblewska et al. (2025) are available in the task repository. Participants are encouraged to apply the provided system prompts during training and inference. 

⚠️ While modifications to the system prompt and alternative uses of the IPIS dataset, such as for data augmentation, are permitted, these must align with the task requirements and principles of fair competition.


### Task constraints

1. Participants are permitted to use **publicly available** pretrained language models, including both Polish-specific and multilingual models.
2. The use of **proprietary** or **closed-source** LLMs is prohibited.
3. The *training* and *development* subsets of the IPIS dataset may be used freely for any task-related purpose, including but not limited to LLM instruction-tuning, fine-tuning, and data augmentation. 
4. Participants may use **publicly accessible** linguistic resources, such as Polish corpora, lexical databases, knowledge graphs, and other structured data resources.
5. All external resources and models used for developing a gender-inclusive LLM must be clearly documented in the final submission, including appropriate bibliographic references and/or direct URLs.
6. The use of non-public datasets, tools, or models is strictly forbidden.
7. It is prohibited to input any portion of the IPIS dataset — whether training or development instances — into proprietary LLMs (e.g. ChatGPT, Claude) for any reason, including data augmentation.
8. Each team is allowed to submit a maximum of three runs per task.
9. Participants are expected to prepare a short article, describing their solution with enough details to allow replication of the research.


## 📦 IPIS dataset

**Inclusive Polish Instruction Set** (Wróblewska and Żuk, 2025) is a collection of instructions designed to improve the gender sensitivity and inclusiveness of LLMs in the Polish language scenario. The IPIS dataset is built on a gender-inclusive text corpus manually annotated in the [PLLuM project](https://pllum.org.pl).


### IPIS format

🅰️ **Subtask**

Each IPIS-proofreading sample consists of three main components:

1. **user prompt** (```prompt```) — a specification of the given task,
2. **input text passage** (```source```) — a text passage requiring a gender-inclusive proofreading,
3. **desired output** (```target```) — the expected response corresponding to the user instruction and input text passage. This serves as the ground truth for evaluating and optimising LLM's predictions.
    

```
{'source_resource_id': 'nlprepl-nkjp1m-dev',
 'ipis_id': 'IPIS_proofreading_dev_2143',
 'prompt': 'Przeredaguj tekst w standardowym języku polskim, aby nie zawierał treści krzywdzących i wykluczających. Tekst źródłowy: ',
 'source': 'W 24-osobowym składzie sędziowskim znalazło się 8 Polaków, pianistów i pedagogów. W przypadku własnych uczniów nie będą mieli prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.',
 'target': 'W 24-osobowym składzie sędziowskim znalazło się 8 Pol*aków/ek, pianist*ów/ek i pedago*gów/żek. W przypadku własnych ucz*niów/ennic nie będą mi*eli/ały prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.',
 'messages': [{'content': 'Przeredaguj tekst w standardowym języku polskim, aby nie zawierał treści krzywdzących i wykluczających. Tekst źródłowy: W 24-osobowym składzie sędziowskim znalazło się 8 Polaków, pianistów i pedagogów. W przypadku własnych uczniów nie będą mieli prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.', 'role': 'user'}, {'content': 'W 24-osobowym składzie sędziowskim znalazło się 8 Pol*aków/ek, pianist*ów/ek i pedago*gów/żek. W przypadku własnych ucz*niów/ennic nie będą mi*eli/ały prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.', 'role': 'assistant'}],
 'normalised_target': null}
```

🅱️ **Subtask**

Each IPIS-translation sample consists of three main components and lanugage specifications:

1. **user prompt** (```prompt```) — a specification of the given task,
2. **input text passage** (```source```) — a text passage to translate,
3. **desired output** (```target```) — an expected translation in standard English or gender-inclusive Polish. This serves as the ground truth for evaluating and optimising LLM's predictions,
4. ```prompt_language``` — the language of ```prompt``` (either EN or PL)
5. ```source_language``` — the language of a passage to translate, either inclusive Polish (PL) or standard English (EN)
6. ```target_language``` — the language of a reference translation, either standard English (EN) or gender-inclusive Polish (PL)

```
{"source_resource_id": "EU_Karta_Praw_Podstawowych",
"ipis_id": "IPIS_translation_dev_117",
"prompt": "Translate into inclusive Polish. Text to translate: ",
"source": "Article 28\nRight of collective bargaining and action\nWorkers and employers, or their respective organisations, have, in accordance with Union law and national laws and practices, the right to negotiate and conclude collective agreements at the appropriate levels and, in cases of conflicts of interest, to take collective action to defend their interests, including strike action.",
"target": "Artykuł 28\nPrawo do rokowań i działań zbiorowych\nPracownic*y/e i pracodaw*cy/czynie, lub ich odpowiednie organizacje, mają, zgodnie z prawem Unii oraz ustawodawstwami i praktykami krajowymi, prawo do negocjowania i zawierania układów zbiorowych pracy na odpowiednich poziomach oraz do podejmowania, w przypadkach konfliktu interesów, działań zbiorowych, w tym strajku, w obronie swoich interesów.",
"prompt_language": "EN",
"source_language": "EN",
"target_language": "PL",
"messages": [{"content": "Translate into inclusive Polish. Text to translate: Article 28\nRight of collective bargaining and action\nWorkers and employers, or their respective organisations, have, in accordance with Union law and national laws and practices, the right to negotiate and conclude collective agreements at the appropriate levels and, in cases of conflicts of interest, to take collective action to defend their interests, including strike action.", "role": "user"}, {"content": "Artykuł 28\nPrawo do rokowań i działań zbiorowych\nPracownic*y/e i pracodaw*cy/czynie, lub ich odpowiednie organizacje, mają, zgodnie z prawem Unii oraz ustawodawstwami i praktykami krajowymi, prawo do negocjowania i zawierania układów zbiorowych pracy na odpowiednich poziomach oraz do podejmowania, w przypadkach konfliktu interesów, działań zbiorowych, w tym strajku, w obronie swoich interesów.", "role": "assistant"}]}
```

### IPIS size

🅰️ **Subtask**

The **gender-inclusive proofreading** *test*, *dev* and *train* subsets consist of 5278, 2732 and 23,532 instances, respectively. All IPIS test, dev and train subsets are balanced for the ratio of gender-inclusive transformations.
 
🅱️ **Subtask**

The **gender-sensitive translation** *test* and *train* subsets consist of 760 and 1728 instances, respectively. 


## ⚖️ Evaluation

### Methodology

🅱️ **Subtask**

To evaluate the ability of the gender-inclusive LLM to process and generate gender-inclusive Polish in the Polish⇄English translation scenario, its outcomes are compared against gold standard test instances and ranked using the primary metric:

*  *chrF* ([Popović, 2015](https://aclanthology.org/W15-3049.pdf))

The translation quality is additionally evaluated with two secondary metrics:

*  *chrF++*
*  *BLEU* ([Papieni et al., 2002](https://aclanthology.org/P02-1040.pdf)).

🅰️ **Subtask**

To evaluate the ability of the gender-inclusive LLM to generate gender-inclusive language, its outcomes are compared against gold standard test instances. The normalised LLM-generated texts are evaluated with the primary metric:

* *F<sub>1</sub>-measure* (see [Normalisation procedure](#procedure) for details how to normalise LLMs' outputs). 

The textual quality of LLM-proofread passages is additionally evaluated using automatic secondary metrics:

* *chrF* and *chrF++* ([Popović, 2015](https://aclanthology.org/W15-3049.pdf))
* *BLEU* ([Papieni et al., 2002](https://aclanthology.org/P02-1040.pdf)).

### <a name="procedure"></a>Normalisation procedure
Various gender-inclusive alternatives are possible, e.g. for *posłowie* [deputies]:

> posłanki i posłowie
> 
> posłowie i posłanki
> 
> posłowie/posłanki
> 
> posłanki/posłowie
> 
> posł*owie/anki

For evaluation, the gender-inclusive ```generated_target``` samples should be normalised. The normalisation process consists in expanding all occurrences of gender-inclusive expressions, especially those containing slashes or gender stars (asterisks), into their full masculine and feminine forms and then filtering out predefined stop words (i.e. punctuation marks, subordinating and coordinating conjunctions). For normalisation steps, we use [Lambo](https://gitlab.clarin-pl.eu/syntactic-tools/lambo) (Przybyła, 2022) for tokenisation and [Combo](https://gitlab.clarin-pl.eu/syntactic-tools/combo) ([Klimaszewski and Wróblewska, 2021](https://aclanthology.org/2021.emnlp-demo.7)) for part-of-speech tagging.

⚠️ A Python script for normalisation is included in the task repository.

### Baseline and SOTA

The baseline corresponds to the best off-the-shelf LLM (-default). The state of the art corresponds to the best LLM instruction-tuned on the IPIS train subset (-tuned) and possibly guided by a system prompt in Polish (-pl) or English (-en). We have tested multilingual models [Llama-8B](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct), [Mistral-7B](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.2) and [Mistral-Nemo](https://huggingface.co/mistralai/Mistral-Nemo-Instruct-2407), and Polish-specific models [Bielik-7B](https://huggingface.co/speakleash/Bielik-7B-Instruct-v0.1), [Llama-PLLuM-8B](https://huggingface.co/CYFRAGOVPL/Llama-PLLuM-8B-chat), [Bielik-11B](https://huggingface.co/speakleash/Bielik-11B-v2.3-Instruct) and [PLLuM-12B](https://huggingface.co/CYFRAGOVPL/PLLuM-12B-nc-chat). The detailed scores are in Wróblewska and Żuk (2025).


🅰️ **Subtask**

<table>
    <thead>
        <tr>
        	  <th colspan="2">LLM</th>
            <th>precision</th>
            <th>recall</th>
            <th><b>F<sub>1</sub></b></th>
            <th>BLEU</th>
            <th>chrF</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        	  <td><b>Baseline</b></td>
            <td><b>PLLuM-12B-default-pl</b></td>
            <td>2.56</td>
            <td>6.28</td>
            <td>3.64</td>
            <td>63.59</td>
            <td>82.74</td>
        </tr>
        <tr>
        	  <td><b>SOTA</b></td>
            <td><b>Bielik-11B-tuned</b></td>
            <td>63.93</td>
            <td>56.26</td>
            <td>59.85</td>
            <td>95.22</td>
            <td>97.81</td>
        </tr>
     </tbody>
</table>

🅱️ **Subtask**

<table>
    <thead>
        <tr>
        	  <th colspan="2">LLM</th>
        	  <th>BLEU</th>
            <th>chrF</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        	  <td><b>Baseline<sub>PL-to-EN</sub></b></td>
            <td><b>Mistral-Nemo-12B-default</b></td>
            <td>53.68</td>
            <td>75.35</td>
        </tr>
        <tr>
        	  <td><b>SOTA<sub>PL-to-EN</sub></b></td>
            <td><b>Bielik-12B-tuned-en</b></td>
            <td>57.55</td>
            <td>78.03</td>
        </tr>
        <tr>
        	  <td><b>Baseline<sub>EN-to-PL</sub></b></td>
            <td><b>Bielik-12B-default</b></td>
            <td>41.49</td>
            <td>71.78</td>
        </tr>
        <tr>
        	  <td><b>SOTA<sub>EN-to-PL</sub></b></td>
            <td><b>Bielik-11B-fewshot-en</b></td>
            <td>43.02</td>
            <td>72.46</td>
        </tr>
     </tbody>
</table>


## 🚀 Submission

🅰️ **Subtask**

Test instances provided to participants in the testing phase will have the following structure:

```
{'source_resource_id': 'example-test',
 'ipis_id': 'IPIS_proofreading_test_X',
 'prompt': 'Przeredaguj tekst napisany w standardowym języku polskim, aby nie zawierał treści krzywdzących i wykluczających. Tekst źródłowy: ',
 'source': 'W 24-osobowym składzie sędziowskim znalazło się 8 Polaków, pianistów i pedagogów. W przypadku własnych uczniów nie będą mieli prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.',
 'target': null,
 'normalised_target': null}
```

JSON test instances submitted by participants must include the following fields: 

* ```ipis_id``` with the original IPIS ID
* ```generated_target``` with a text passage proofread by the participating LLM
* ```normalised_target``` containing its normalised form

```
{'ipis_id': 'IPIS_proofreading_test_X',
'generated_target': 'W 24-osobowym składzie sędziowskim znalazło się 8 Pol*aków/ek, pianist*ów/ek i pedago*gów/żek. W przypadku własnych ucz*niów/ennic nie będą mi*eli/ały prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.',
 'normalised_target': ['w', '24-osobowym', 'składzie', 'sędziowskim', 'znalazło', 'się', '8', 'polaków', 'polek', 'pianistów', 'pianistek', 'pedagogów', 'pedagożek', 'w', 'przypadku', 'własnych', 'uczniów', 'uczennic', 'nie', 'będą', 'mieli', 'miały', 'prawa', 'głosu', 'pojawią', 'się', 'też', 'm.in', 'laureat', 'nagrody', 'za', 'najlepsze', 'nagranie', 'roku', 'chopinowskiego', 'emanuel', 'ax', 'rosyjska', 'pianistka', 'reprezentująca', 'usa', 'bella', 'davidovich']}
```

⚠️ For normalisation, we recommend using a Python normalisation script included in the task repository. 

🅱️ **Subtask**


Test instances provided to participants in the testing phase will have the following structure:

```
{'source_resource_id': 'example-test',
 'ipis_id': 'IPIS_translation_test_X',
 'prompt': 'Translate the text from Polish to English:',
 'source': 'W 24-osobowym składzie sędziowskim znalazło się 8 Pol*aków/ek, pianist*ów/ek i pedago*gów/żek. W przypadku własnych ucz*niów/ennic nie będą mi*eli/ały prawa głosu. Pojawią się też m.in. laureat nagrody za najlepsze nagranie Roku Chopinowskiego - Emanuel Ax i rosyjska pianistka reprezentująca USA - Bella Davidovich.',
 'target': null,
 'prompt_language': 'EN',
 'source_language': 'PL',
 'target_language': 'EN'}
```


JSON test instances submitted by participants must include the following fields:

* ```ipis_id``` with the original IPIS ID
* ```generated_target``` with a text passage translated by the participating LLM

```
{'ipis_id': 'IPIS_translation_test_X',
 'generated_target': 'Among the 24-member jury are 8 Poles — pianists and educators. They will not be allowed to vote for their students. There are also, among others, Emanuel Ax, the winner of the award for the best recording of the Chopin Year, and Bella Davidovich, a Russian-born pianist representing the USA.'}
```

### Submission components for both subtasks
1. A ```.jsonl``` file containing a list of instances, each formatted as a JSON object.
2. A link to the gender-inclusive LLM participating in this task.
3. Names, emails and institutional affiliations of all team members.


## 📚 References

* Alina Wróblewska and Bartosz Żuk (2025). [*Integrating gender inclusivity into large language models via instruction tuning*](https://arxiv.org/pdf/2508.18466). Arxiv.
* Alina Wróblewska, Martyna Lewandowska, Aleksandra Tomaszewska, Karol Saputa and Maciej Ogrodniczuk (2025). [*Koncepcja form równościowych z asteryskiem inkluzywnym*](https://doi.org/10.31286/JP.001040), Język Polski CV(2), p. 97—118.
