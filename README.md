# CORD-19
COVID-19 Open Research Dataset Challenge - NLP data analysis

https://www.kaggle.com/datasets/allen-institute-for-ai/CORD-19-research-challenge

In collaboration with: Reshma Kelkar (https://github.com/Reshma-34)

## Objective
#### To perform topic modeling on research articles
The project aims to derive insights from the research papers related to Covid-19. This set of notebooks provides a data mining process with the help of LDA (Latent Derichlet Analysis). This process parses thousands of research papers and builds topic models that can summarize the content of a research paper in a few biologically relevant keywords. The LDA model can also be used to compare and group similar research articles based on the identified keywords and topics. One of the applications of such grouping is narrowing down the search space with automated topic modeling.<br>
While the current focus is on Covid-19 research articles, this set of notebooks can be used to parse any collection of documents to build topic models.

## Usage

Topic modeling can satisfy user's requirement to get papers related to various topics such as drugs, immune response, vaccines, antivirals, matabolic pathways etc.<br>
The example given at the end of this file shows various topics and interpretation of the visualization for documents in terms of those topics.

#### How to run the pipiline?
1. Run 1.abstrac_entity_vectorization.ipynb<br>
2. Run 2.fulltext_external-keywords.ipynb<br>
3. Run 3.lda_visualization.ipynb<br>

NOTES:
Specific instructions and comments are written in the individual notebooks.<br>
Intermediate outputs will be stored in the same folder. Outputs from latest run are provided, which may be used as inputs to save time.<br>


#### Steps involved in the pipeline:

A) Scientific entity recognition of abstract section of the research articles using SciSpacy en_core_sci_lg model.<br>

B) Identification of scientific keywords (obtained from external databases, given below) in the full text of research articles.<br>

C) Perform Latent Dirichlet allocation (LDA) on the combined set of entities recognised from abstracts and keywords from external databases.<br>

D) Visualization LDA results:<br>
   We propose to visualize the importance of topics in a selected document and the broadness of topics in a single chart.<br>
   
   We use a bubble chart as follows.<br>

   1. X-axis shows top N topics for a chosen document.<br>
   2. Y-axis denotes how much importance of the topic in the document.<br>
      (Higher the y-value, more the importance of the topic in this document.)<br>
   3. Radius of the bubble denotes in how many other documents this topic is important.<br>
      The importance can be set using a threshold.<br>
      (Larger the radius, higher chances of finding a similar document. Or, smaller the radius, more unique is the document.)<br>

#### Data sources
Research article data is taken from https://pages.semanticscholar.org/coronavirus-research<br>
(Also available on Kaggle- https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge)<br>

External databases used for deriving keywords:<br>
Disease Database: http://www.diseasesdatabase.com/<br>
	Categories of keywords fetched from the Disease Database are as follows.<br>
	1. arthropods<br>
	2. autoimmuneDiseases<br>
	3. bacteria<br>
	4. orthopedicConditions<br>
	5. symptomsAndSigns<br>
	6. viruses<br>

Kegg Medicus: https://www.genome.jp/kegg/medicus.html<br>
	Categories of keywords fetched from the Kegg Medicus are as follows.<br>
	1. disease<br>
	2. drug<br>
	3. network<br>

#### Example
Saved model file name: 3.lda_visualization_nTopics10.pkl<br>
NOTE: All intermediate output files are also provided.<br>

Topics obtained from an example run with n_topics=10 (represented by top 10 contributing entities):<br>

[(0,  
  '0.074*"cell" + 0.056*"infection" + 0.041*"response" + 0.027*"immune" + '  
  '0.023*"mouse" + 0.021*"expression" + 0.018*"effect" + 0.018*"symptom" + '  
  '0.017*"treatment" + 0.016*"increase"'),  
 (1,  
  '0.058*"vaccine" + 0.050*"day" + 0.050*"antibody" + 0.042*"strain" + '  
  '0.024*"serum" + 0.023*"pedv" + 0.021*"animal" + 0.018*"porcine" + '  
  '0.018*"pig" + 0.018*"group"'),  
 (2,  
  '0.049*"protein" + 0.047*"virus" + 0.027*"cell" + 0.026*"viral" + '
  '0.024*"rna" + 0.023*"gene" + 0.020*"host" + 0.016*"sequence" + '
  '0.013*"replication" + 0.013*"human"'),
 (3,
  '0.034*"drug" + 0.023*"hepatitis c" + 0.021*"domain" + 0.017*"ethanol" + '
  '0.016*"hepatitis c virus" + 0.015*"glucose" + 0.015*"calcium" + '
  '0.015*"compound" + 0.014*"rosin" + 0.014*"serine"'),
 (4,
  '0.083*"disease" + 0.063*"health" + 0.034*"population" + 0.033*"infectious" '
  '+ 0.029*"public" + 0.028*"country" + 0.026*"human" + 0.023*"pandemic" + '
  '0.022*"risk" + 0.020*"global"'),
 (5,
  '0.045*"model" + 0.044*"covid" + 0.042*"19" + 0.030*"study" + 0.030*"datum" '
  '+ 0.023*"analysis" + 0.020*"epidemic" + 0.018*"method" + 0.018*"level" + '
  '0.017*"preprint"'),
 (6,
  '0.019*"severe acute respiratory syndrome" + 0.017*"pain" + '
  '0.011*"tuberculosis" + 0.011*"oxygen" + 0.009*"measles" + '
  '0.009*"respiratory syncytial virus" + 0.008*"staphylococcus aureus" + '
  '0.008*"respiratory distress" + 0.007*"rash" + 0.007*"wine"'),
 (7,
  '0.071*"virus" + 0.042*"infection" + 0.032*"respiratory" + 0.028*"influenza" '
  '+ 0.027*"viral" + 0.023*"positive" + 0.023*"pcr" + 0.019*"sample" + '
  '0.017*"study" + 0.017*"human"'),
 (8,
  '0.064*"sars" + 0.061*"patient" + 0.059*"cov" + 0.039*"case" + '
  '0.022*"infection" + 0.020*"severe" + 0.020*"coronavirus" + '
  '0.020*"transmission" + 0.019*"respiratory" + 0.015*"acute"'),
 (9,
  '0.079*"assay" + 0.056*"detection" + 0.050*"test" + 0.042*"diagnostic" + '
  '0.041*"sensitivity" + 0.037*"sample" + 0.035*"specificity" + 0.028*"dna" + '
  '0.027*"testing" + 0.024*"cat"')]

#### Visualization
Please see images<br>
doc2.png:<br>
Bubble chart for document id 2- The topic 5 is important in document 2. The radius of the corresponding bubble is considerably small.<br>
This means that document 2 might be unique in terms of topic 5. I.e. it is less likely to find other documents talking about this topic.<br>

doc3459.png:<br>
Bubble chart for document id 3459- The topic 6 seems to be important in this document. But the radius of the corresponding bubble is<br>
quite large. This means that it might be very likely to find other documents that talk about the same topic (topic 6).<br>


