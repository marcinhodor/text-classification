**Tekst pracy zostanie zamieszczony po ostatecznym zatwierdzeniu przez opiekuna projektu.**

Projekt dyplomowy zrealizowany na zakończenie studiów podyplomowych na Akademii Górniczo-Hutniczej w Krakowie na kierunku Analiza Danych - Data Science w roku akademickim 2020/2021.

Tytuł: "Praktyczne zastosowanie narzędzi przetwarzania języka naturalnego w klasyfikacji tekstu"<br>
Autor: Marcin Hodor<br>
Opiekun Projektu: dr inż. Robert Marcjan

W pracy autor opisał 4 narzędzia, wybrane spośród wielu współcześnie dostępnych klasyfikatorów tekstu i dokonał weryfikacji ich skuteczności na danych pochodzących ze zbioru o nazwie „*The 20 Newsgroups data set*” (http://qwone.com/~jason/20Newsgroups/) - zobacz poniżej informacje na temat wykorzystanych danych.

Wykorzystane narzędzia to:
- model Naiwny klasyfikator bayesowski (Naive Bayes)
- model Maszyna wektorów nośnych (Support Vector Machine)
- usługa oparta na chmurze AWS Comprehend
- algorytm BERT od Google

Kod Python użyty do eksperymentu został umieszczony w 4 notebookach z rozszerzeniem .ipynb odpowiadającym kolejnym etapom doświadczenia:

01_data_processing - import wiadomości z folderu data, czyszczenie tekstu, usuwanie *stopwords*, lematyzacja<br>
02_NB_SVM_models - implementacja modeli NB i SVM oraz ocena ich skuteczności na danych testowych<br>
03_BERT_model - implementacja modelu BERT oraz ocena jego skuteczności na danych testowych<br>
04_AWS_Comprehend - przygotowanie danych do ich użycia w usłudze AWS Comprehend, sprawdzenie trafności algorytmu poprzez porównanie przewidzianych etykiet z danymi rzeczywistymi ze zbioru testowego

W celu przetestowania zapisanego kodu na danych należy:
1. pobrać repozytorium z GitHub,
1. rozpakować dane treningowe i testowe znajdujące się w pliku data.7z w folderze data (można użyć do tego programu 7-zip - https://www.7-zip.org/download.html) tak, aby wraz z notebookami tworzyły następującą strukturę folderów:<br>

```
text-classification
└───data
│   └───20news-bydate-train
│       └───Automotive
│       └───Computers
│       │   ...
│   └───20news-bydate-test
│       └───Automotive
│       └───Computers
│       │   ...
│   └───Comprehend
│       |   predictions.jsonl
│       |   test.txt
│       |   train.csv
│
│ 01_data_processing.ipynb
│ 02_NB_SVM_models.ipynb
│ 03_BERT_model.ipynb
│ 04_AWS_Comprehend.ipynb
│ readme.md
```

W eksperymencie wykorzystano zestaw danych o nazwie „*The 20 Newsgroups data set*”, zawierający ok. 19 tysięcy wiadomości (wpisów) w języku angielskim, podzielonych na 20 grup tematycznych. Autor tego zbioru danych podzielił go na podzbiory uczący i testowy zawierające odpowiednio 10729 i 7142 wpisy. Na potrzeby doświadczenia kategorie należące do jednej, szerszej klasy zostały ze sobą połączone, natomiast grupę misc.forsale (ogłoszenia sprzedaży) usunięto ze względu na odmienny charakter wpisów od pozostałych kategorii. Tym samym liczba grup została zmniejszona z 20 do 6, tj. *Automotive*, *Computers*, *Politics*, *Religion*, *Science* oraz *Sports*. Poniższy rysunek przedstawia w jaki sposób połączono oryginalne kategorie:
```
Automotive
└───rec.autos
└───rec.motorcycles

Computers
└───comp.graphics
└───comp.os.ms-windows.misc
└───comp.sys.ibm.pc.hardware
└───comp.sys.mac.hardware
└───comp.windows.x

Politics
└───talk.politics.misc
└───talk.politics.guns
└───talk.politics.mideast

Religion
└───talk.religion.misc
└───alt.atheism
└───soc.religion.christian


Science
└───sci.crypt
└───sci.electronics
└───sci.med
└───sci.space

Sports
└───rec.sport.hockey
└───rec.sport.baseball

(misc.forsale - usunięto)
```