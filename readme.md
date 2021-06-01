Polski / English

Projekt dyplomowy zrealizowany w czasie studiów podyplomowych na Akademii Górniczo-Hutniczej w Krakowie na kierunku Analiza Danych - Data Science w roku akademickim 2020/2021.

Tytuł: "Praktyczne zastosowanie narzędzi przetwarzania języka naturalnego w klasyfikacji tekstu"<br>
Autor: Marcin Hodor<br>
Opiekun Projektu: dr inż. Robert Marcjan

W pracy autor opisał 4 narzędzia, wybrane spośród wielu współcześnie dostępnych klasyfikatorów tekstu i dokonał weryfikacji ich skuteczności na danych pochodzących ze zbioru o nazwie „*The 20 Newsgroups data set*” (http://qwone.com/~jason/20Newsgroups/).

Wykorzystane narzędzia to:
- model Naiwny klasyfikator bayesowski (Naive Bayes)
- model Maszyna wektorów nośnych (Support Vector Machine)
- usługa oparta na chmurze AWS Comprehend
- algorytm BERT od Google

Kod Python użyty do eksperymentu został zamieszczony w 4 notebookach z rozszerzeniem .ipynb odpowiadającym kolejnym etapom doświadczenia:

1. 01_data_processing - import wiadomości z folderu "data", czyszczenie tekstu, usuwanie *stopwords*, lematyzacja
1. 02_NB_SVM_models - implementacja modeli NB i SVM oraz ocena ich skuteczności na danych testowych
1. 03_BERT_model - implementacja modelu BERT oraz ocena jego skuteczności na danych testowych
1. 04_AWS_Comprehend - przygotowanie danych do ich życia w sułudze AWS Comprehend, sprawdzenie trafności algorytmu poprzez porównaie przewidzianych etykiet z danymi rzeczywistymi ze zbioru testowego