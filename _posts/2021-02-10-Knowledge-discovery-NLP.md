---
layout: post
title: Knowledge Discovery using NLP
cover-img: /assets/img/nlpmain.jpg
subtitle:  Retrieving hidden inferences using linguistic regularities.
tags: [NLP, Linguistic regularites, Sklearn, pubmed, Covid-19]
image_cover : /assets/img/nlpmain.jpg
comments: true
---


## Introduction
Finding inferences from multiple resources at once has always been a difficult task. Majority of scientific knowledge is published as text, in the form of research papers. This makes it challenging to analyse it by traditional machine learning methods. In this project, we showed that biological research abstracts could be encoded as information-rich word embeddings in an unsupervised manner. We scraped 10 million research abstracts from PubMed1 and classify them as disease-related or not disease-related. We used commonlyused context-independent embeddings such as Word2Vec, FastText and GloVe for this task. Without any supervision, the embeddings were able to capture the complex relations between diseases and their related symptoms and affected organs. We present an unsupervised method to recommend symptoms and affected organs given a disease name. We also show that word embeddings constructed on domain-specific data predicted the correct symptoms and organs for the given disease with higher confidence. Our finding highlights the possibility of this method being applicable to other scientific fields beyond biology as well.

There has been extensive research done in the biomedical field domain, leading to a massive amount of papers being published over the years. Unlike most other fields like Physics, research in the biomedical domain is incremental and conducted progressively by building upon currently available knowledge. While most of these papers give inferences based on results obtained from the specific set of experiments conducted, cross-research inferences are not easy to capture without human intervention in some form or the other. In this project, we use the vast dataset of research papers as the knowledge base and find the hidden inferences which otherwise manage to skip the human congnitive ability due to the sheer quantity of papers. These hidden inferences not only confirm the currently established facts but also allow for making discoveries, or limiting the exploration field when working on finding cures to novel problems. We propose using language models to find word-level embeddings using the disease-related research papers available on PubMed as our knowledge base and using average vectors to find inferences from the embeddings created. We also perform ablation study by comparing the different language models trained and confirm the inferences gained from our model. Finally, we mention the possible reasons for the inferences gained from our model.

## Past Work
The word vectors, which are learned word representations have been found to capture meaningful syntactic and semantic regularities in a very naive and simple way (Mikolov, Yih, and Zweig 2013). These regularities are observed as constant vector offsets between a pair of words sharing a particular relationship, for example.

![Alluvial Diagram](/assets/img/nlp1.png)

These semantic regularities act as hidden patterns. These patterns can be exploited to generate novel relationships, which were not explicitly present in the training data. In Nadeem N. Rather 2017, Word2Vec was applied on MRDEF (Meta-thesaurus Definition) file from UMLS 2 (biomedical text corpus) in order to discover potential relationships. The output relationships were cross-verified against UMLS MRREL (Meta-thesaurus Relational) dataset, and 32% of the new relationships were not originally present in the UMLS MRREL dataset. The resultant relationships also included many known relationships, which the model rediscovered in an unsupervised manner.

Thus the novel relationships generated by such models can be tested to unearth hidden discoveries and implications that are out of scope for humans. Tshitoyan et al. 2019 showed that the relative positioning of metals and their oxides, from a well trained word embedding in chemistry is consistent. They also showed the same results for the relationship of metals with the lattice structure suggesting this is a property isn’t specific to metal and their oxides but is perhaps more generalizable.

## Methodology
### Dataset
PubMed is the largest repository for biomedical papers. PMID represents each paper on PubMed, and its abstract can be found at a URL which consists of the PubMed’s official URL and the paper’s PMID. Using the incremental nature of PMID, we browsed and scraped medical articles by incrementing the PMID in the URL. We utilise the python library Beautiful Soup on a Google Colab notebook for this task, which extracted the ‘Title’, ‘Abstract’ and ‘Keywords’ from each webpage’s HTML data. In total, we collected information for approximately 10 million biomedical papers. To limit the dataset to the disease-specific domain, we trained a binary classifier to distinguish the diseaserelated articles from the rest. We manually annotated 1000 disease-related and 1000 non-disease related papers. Embeddings for each article were generated using BioSent2Vec (Chen, Peng, and Lu 2019), a model pre-trained on PubMed data. The separability of the articles into disease-related and not disease-related was confirmed by Principal Component Analysis (PCA) of the generated word embeddings, as can be seen in Figure 1. These embeddings were used to train a Support Vector Classifier. Initial training results of the SVC classified close to 8 million articles as disease-related. To reduce the number of false positives, the threshold of the SVC was increased from 0.5 to 0.7, decreasing the number of disease-related papers to 6,146,920. Figure 2 illustrates the confusion matrix for the trained SVC classifier.
![Alluvial Diagram](/assets/img/nlp2.png)<br>

### Embeddings
Biomedical NLP applications have been using word embeddings to capture useful semantic properties and linguistic relationships between words using deep learning methods. To capture the context from the dataset developed, we generate word embeddings using the following three models:
- Word2Vec
- GloVe
- FastText
Embeddings from these models were generated for the disease-related papers as well as the whole set ofbiomedical papers. This is done to gauge the change in confidence obtained by using domain-specific dataset.
![Alluvial Diagram](/assets/img/nlp3.png)<br>

### Model Analysis
We utilize these contextual word embeddings to find hidden inferences. We make a custom list of diseases and use this custom list to make an average vector to be used as a representation of all diseases. We do the same process for symptoms and organs. These average vectors allow us to capture a general delineation of each category, which could be utilized for hidden information retrieval. Given a disease in our vocabulary of words, we use its words embedding to find it corresponding symptoms and also the organs that it affects. For finding symptoms of a given disease we find top ‘n’ similar words from the custom list of symptoms, to the vector predicted by the Equation 1.
![Alluvial Diagram](/assets/img/nlp4.png)<br>

where Ep is the predicted vector to be used to find top ‘n’ similar symptoms, Ed is the embeddings of the disease for which the symptoms have to be found, AvgEd is the average disease vector and AvgEs is the average symptom vector. For finding organs affected by a disease we find top ‘n’ similar words from the custom list of organs, to the vector predicted by Equation 2

![Alluvial Diagram](/assets/img/nlp5.png)<br>
where Ep is the predicted vector to be used to find top ‘n’ similar symptoms, and AvgEo is the average organ vector. To find the top ‘n’ similar words we use cosine similarity statistic between the pair of embeddings to be compared.

## Results
In order to make out dataset domain specific and filter out articles which aren’t necessarily disease related, we trained an SVC classifier with 94% accuracy. The PCA analysis on training dataset demonstrated that the data is indeed separable (disease related or not) as shown in Figure 1. The confusion matrix is illustrated in Figure 2. We also compare the 6 deep neural network based language models 3 of which are trained using Word2Vec, FastText and GloVe on filtered dataset and remaining 3 on the complete dataset. We compare the confidence scores of the model’s ability to correctly predict the corresponding symptom or organ as illustrated in Figure 3. We can see that for all 3 language models, higher confidence scores were achieved when trained on filtered dataset than on complete dataset. This is due to the ability of the language models to capture contextual information more precisely in domain specific dataset. Among 3 individual models, word2vec outperforms the FastText and GloVe by a country mile in both training scenarios. Table 1 also shows some of the examples that we tested for finding top symptoms and affected organs for a given disease.
![Alluvial Diagram](/assets/img/nlp6.png)<br>
We checked if the top 5 symptoms for Dengue occur together in a single research article. This test was done for Dengue, Acne and Jaundice with checks for symptoms and organs. We find that no single article presented all the top 5 symptoms or the organs together. Hence, our model was able to extract inferences across papers to gain knowledge about a certain disease.

[Preprint](https://preprints.jmir.org/preprint/26868) submitted to JMIR

## Novelty
Tshitoyan et al. 2019 introduced the idea of average vector but did that in a supervised manner. They used metal to metal oxide relationship to create the average vector. We instead created separate vectors for disease and symptoms and used algebra to get the average vector. This allowed us to have different list sizes of disease, organs and symptoms. Nadeem N. Rather 2017 introduce the idea of exploiting linguistic regularities to extract new information. They use biomedical data to extract relations. We employ the use of average vectors for the first time in an unsupervised manner to construct hyperdimensional knowledge-rich representation of disease, symptom and organ. And in an unsupervised manner use the relationships to extraxt information from the data. We are able to show that domain-specific data performs better in terms of capturing relationships between word embeddings, which hasn’t been shown in any of the above literature or used in previous models trained in the biomedical domain.
## Team
- Atishay Jain
- Adwit Kochar
- Udit Arora