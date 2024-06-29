<h1 align="center"> Bem vinda(o) ao Projeto - Linguagem Tóxica😊 </h1>

![Badge em Desenvolvimento](https://img.shields.io/static/v1?label=STATUS&message=CONSTRUÇÃO&color=<COLOR>)

<h1 align ="center"> Objetivo do Projeto🤔</h1>

Fruto de uma competição de Machine Learning, esse projeto tem como objetivo criar um modelo que detecta linguagem tóxica em mídias sociais. Para tal vou utilizar técnicas de NLP e machine learning para tratar os dados e treinar um modelo para tal função.


<h1 align ="center"> Compreensão do Negócio</h1>

Com redes sociais crescento e tomando espaço na vida de toda a população é importante conseguir filtrar a linguagem que muitas pessoas podem ter ao usar a internet. Uma forma criar um filtrator é criar um modelo que consegue detectar, nas mensagens de um usuário, quando ocorre
toxicidade. Tal comportamento é inaceitável em muitas redes, e necessário uma vez que sem uma barreira desta os usuários estão livres para dialogar como bem entenderem. 

   
Usarei a seguinte métrica para avaliar o modelo:
1. Acurácia - Por motivo de ter sido definido pelos criadores da competição.

<h1 align ="center"> Resumos das Etapas</h1>

<h2 align ="left"> Tratamento dos Dados</h2>

Como se trata de análise de textos, a preparação dos dados seguiu técnicas de NLP. Os tratamentos utilizados foram:


1. Colocar todas letras no diminutivo
2. Retirar pontuações e stopwords
3. Retirar acentuações
4. Aplicar Stemmização
5. Retirar valores numéricos
6. Retirar Emojis

<h2 align ="left"> Preparação dos Dados </h2>

Para iniciar com o treinamento do modelo fiz duas preparações dos dados:

1. **Bag Of Words:** Porque é uma preparação que criar muitas variáveis com apenas valores binários, esse método de preparação de dados foi utilizado para definir *Baseline* para modelo. Para tal também foi utilizado Logistic Regresion.
   
| Valor Baseline                      | 0.69             |
|-------------------------------------|-------------------|

2. **TF-IDF:** Esta é uma forma mais robusta que atribui valores diferentes para as palavras dentro de uma frase, desta forma, este é o método principal utilizado neste projete de prepação dos dados. 
  
<h2 align ="left"> Treinando o Modelo</h2>

<h3 align ="left"> Decidindo o modelo mais adequado</h3>

Para decidir qual é o mais adequado para o contexto treinei diversos modelos diferentes no seguinte passo a passo para cada modelo:

1. Obtém-se os dados preparados seguindo método TF-IDF.
2. Realiza Holdout aplicando separação de treino e teste.
3. Treina o modelo nos dados de treino por meio de validação cruzada, com 5 fatiamentos.
4. Expõe o valor médio da acurácia e o desvio padrão

Também utilizei um segundo método para fins de comparações, utilizando biblioteca *Lazypredict*. Esta biblioteca funciona treinando vários modelos e apresentando valores de métricas, no entando ela não faz o treinamento de todas bibliotecas.

No fim, os dois métodos me deram dois resultados satisfatórios para seguir para a otimização:

| Modelo                             | 
|-------------------------------------|
| LGBMClassifier                              | 
| HistGradientBoostingClassifier              | 




<h3 align ="left"> Otimização por hiperparâmetros</h3>

Para tunar os hiperparâmetros apliquei o método de SearchGridCV. Alterei os hiperparâmetros de taxa de aprendizagem, quantidade de interações, profundidade e valor mínimo de amostras para o modelo HistGradientBoostingClassifier.

Para o modelo LGBMClassifier alterei os hiperparâmetros: taxa de aprendizado, número de estimadores, profundidade, número de folhas.

O modelo *LGBMClassifier* apresentou o melhor resultado da otimização.

<h3 align ="left"> Otimização por Mudança de Threashold</h3>

Para buscar o melhor ponto de Threashold, apliquei no modelo *LGBMClassifier* o método de obteção das probabilidades e criei a condição que alterava a classificação dos textos em tóxicos e não tóxicos.
Avaliei neste caso como a acurácia alterava de acordo com a alteração do ponto de Threashold, e defini que o melhor ponto de Threashold é: **0.48**, o que significa que acima deste valor o texto é classificado como tóxico.



  

  
<h3 align ="left"> Resultados do Modelo </h3>

O modelo *LGBMClassifier* com os hiperparâmetros definido pelo GridSearchCV foi treinado com dados de treino. Fiz a predição de probabilidade dos dados de teste, e apliquei a condição do novo Threashold para classificar os dados.
Apliquei a métrica de acurácia para as predições e obtivemos seu valor que está tabelos abaixo.

| Modelo                              | Acurácia         |
|-------------------------------------|------------------|
| LGBMClassifier                      | 76%             |





<h2 align ="center"> Quais bibliotecas usei durante o projeto?</h2>

1. Pandas 🐼| Numpy | matplotlib | Seaborn |
2. NLTK | Unicode | Sklearn |Imblearn | LazyPredict | LightGBM

## Detalhes do projeto


Os dados deste projeto foram obtidos no Kaggle, para obter [clique aqui](https://www.kaggle.com/competitions/ml-olympiad-toxic-language-ptbr-detection/data)



<h2 align ="center">Autor 🚀</h2>
<a>
<img style = "border-radius: 50%;" src = https://github.com/KaueAbbe/Analise_ChurnRate/assets/68445400/bd4b5b79-4826-4d72-91e4-5fc7532ac19b width="250px;" alt=""/>

 <sub><b></b></sub></a> 

<h4> Feito com 💙 por Kaue Hermann Abbehausen 👋🏽 
<br/> 
 
 1.Cientista de Dados
 
 2. Formado em Física na Universidade Federal de Uberlândia
 
 3. Mestre em Física Estatística na Universidade de Brasília</h4>
<h4> Entre em contato por</h4>
<div align = "center"> 

 
   <a href="https://www.linkedin.com/in/kaue-abbehausen-5b1922165/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
  <a href="https://www.instagram.com/cienciaeanimacao/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href = "mailto:kaueabbehausen@hotmail.com"><img src="https://img.shields.io/badge/Microsoft_Outlook-0078D4?style=for-the-badge&logo=microsoft-outlook&logoColor=white" target="_blank"></a>
</div>
