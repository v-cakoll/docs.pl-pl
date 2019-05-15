---
title: Jak wybrać algorytm strukturze ML.NET
description: Dowiedz się, jak wybrać algorytm strukturze ML.NET modelu uczenia maszynowego
author: natke
ms.topic: overview
ms.date: 04/20/1029
ms.openlocfilehash: d1c637437a7b285f2b66b597d616fcf39248697f
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557774"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Jak wybrać algorytm strukturze ML.NET

Dla każdego [zadań strukturze ML.NET](resources/tasks.md), istnieje wiele algorytmów szkoleń do wyboru. Co do wyboru zależy od problem próbuje rozwiązać, cechy Twoje dane i zasoby obliczeniowe i magazynowe masz dostępne. Należy pamiętać, że szkolenie modelu uczenia maszynowego jest procesem iteracyjnym. Może być konieczne wypróbować wiele algorytmów, aby znaleźć ten, który sprawdza się najlepiej.

Algorytmy działają na **funkcji**. Funkcje są wartości liczbowe obliczane na podstawie swoich danych wejściowych. Są one optymalne dane wejściowe dla algorytmów uczenia maszynowego. Przekształć nieprzetworzone dane wejściowe do funkcji za pomocą co najmniej jeden [przekształcenia danych](resources/transforms.md). Na przykład danych tekstowych jest przekształcana na zbiór liczba znaków i liczba kombinacji znaków. Gdy funkcje zostały wyodrębnione z typu danych raw, używanie przekształceń danych, ich są określane jako **neural**. Na przykład neural tekst lub dane obrazu neural.

## <a name="trainer--algorithm--task"></a>Trainer = algorytm + zadania

Algorytm jest matematycznych, który jest wykonywany w celu wygenerowania **modelu**. Różnych algorytmów, tworzyć modele o różnej charakterystyce. 

Za pomocą platformy ML.NET to ten sam algorytm można zastosować do różnych zadań. Na przykład stochastycznego spadku, skoordynowany Ascent może służyć do klasyfikacji binarnej, kontra klasyfikacji i regresji. Różnica polega na w interpretacji danych wyjściowych algorytmu do dopasowania zadania. 

Dla każdej kombinacji algorytmów lub zadania strukturze ML.NET udostępnia składnik, który wykonuje uczenie algorytmu i wykonaniu interpretacji. Te składniki są nazywane instruktorów. Na przykład <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> używa **StochasticDualCoordinatedAscent** algorytm dotyczą **regresji** zadania.

## <a name="linear-algorithms"></a>Algorytmy liniowego

Algorytmy liniowej wygenerować model, który oblicza **wyniki** z liniowej kombinacji danych wejściowych oraz zestaw **wagi**. Wagi są parametrami modelu szacowane podczas szkolenia.

Algorytmy liniowej zadziałać dla funkcji, które są [liniowo osobnych](https://en.wikipedia.org/wiki/Linear_separability).

Przed szkolenia przy użyciu liniowego algorytmu, powinny być znormalizowane funkcji. Zapobiega to jedna z funkcji mających więcej wpływu na wynik niż inne.

Ogólnie rzecz biorąc są algorytmy liniowego, skalowalne i, szybka i tania to w opracowywaniu tania do prognozowania. Skalowanie ich przez wiele funkcji i około rozmiar szkoleniowy zestaw danych.

Liniowy algorytmy wykonania wielu przebiegów w ciągu danych szkoleniowych. Jeśli zestaw danych mieści się w pamięci, następnie dodając [punktu kontrolnego w pamięci podręcznej](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) do potokiem strukturze ML.NET przed dołączeniem trainer uczyni szkolenia wykonywania szybciej.

**Instruktorzy liniowego**

|Algorytm|Właściwości|Instruktorzy|
|---------|----------|--------|
|uśrednionej perceptron|Najlepsze dla klasyfikacji tekstu|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Ascent skoordynowanego stochastycznego spadku|Dostrajanie nie jest wymagana dla wydajności dobre domyślne|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Opcja używana podczas wiele funkcji jest duży. Tworzy regresji logistycznej szkolenia statystyki, ale nie skaluje oraz AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symboliczne stochastycznego spadku gradientu|To najszybszy i najbardziej dokładna liniowej klasyfikacji binarnej instruktora. Skaluje się również przy użyciu liczba procesorów|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algorytmy drzewa decyzyjnego

Algorytmy drzewa decyzyjnego utworzyć model, który zawiera szereg decyzji: skutecznie Wykres przepływu za pomocą wartości danych.

Funkcje nie są liniowo wyodrębniona tego typu algorytmu. I funkcje nie powinny być znormalizowane, ponieważ poszczególne wartości w wektorze funkcji są używane niezależnie w podejmowaniu decyzji.

Algorytmy drzewa decyzyjnego są zazwyczaj bardzo dokładne.

Z wyjątkiem uogólniony dodatku modeli (GAMs) modele drzewa można braku explainability, gdy dużej liczby funkcji.

Algorytmy drzewa decyzyjnego zająć więcej zasobów, a nie skalowania także liniowej zrobić. Ich wykonywanie w zestawach danych, które można umieścić w pamięci.

Drzewa decyzyjnego są zespole małych drzewa, gdzie każdy drzewa ocenia dane wejściowe i przekazuje wynik do drzewa dalej do tworzenia lepszych wyników i tak dalej, gdzie każdy drzewa w zespole usprawnieniem poprzedniego.

**Instruktorzy drzewa decyzyjnego**

|Algorytm|Właściwości|Instruktorzy|
|---------|----------|--------|
|Jasny maszyny wzmocnione gradientu|Najszybszym i najbardziej dokładna instruktorów drzewa klasyfikacji binarnej. Wysoce możliwą do dostosowania|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Szybkie drzewa|Na użytek neural danych obrazu. Odporne na niezrównoważone danych. Wysoce możliwą do dostosowania | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Szybkie lasu|Skutecznie współdziała z hałas danych|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Model dodatku uogólnionego (GAM)|Najlepsze dla problemów, które wykonują dobrze z algorytmy drzewa, ale których explainability ma najwyższy priorytet|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Factorization macierzy

|Właściwości|Instruktorzy|
|----------|--------|
|Najlepsze dla rozrzedzone dane podzielone na kategorie z dużymi zestawami danych|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Algorytmy meta

Te Instruktorzy utworzyć trainer wieloklasowej z trainer binarnego. Za pomocą <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.

|Algorytm|Właściwości|Instruktorzy|
|---------|----------|--------|
|Jeden, a wszystkie|Ta wieloklasowej klasyfikatora przygotowuje jeden klasyfikator binarny dla każdej klasy, która odróżnia tę klasę od innych klas. Jest ograniczona w skalowaniu liczby klas do kategoryzowania|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Parowania sprzężenia|Ta wieloklasowej klasyfikatora przygotowuje to algorytm klasyfikacji binarnej na każdej pary klasy. Jest ograniczona w skalowaniu liczby klas, ponieważ każda kombinacja dwóch klas muszą być uczony.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-Means

|Właściwości|Instruktorzy|
|----------|--------|
|Użyj dla klastra|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Analiza głównych składników

|Właściwości|Instruktorzy|
|----------|--------|
|Używany do wykrywania anomalii|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Bayesa firmy

|Właściwości|Instruktorzy|
|----------|--------|
|Funkcje są niezależne, gdy zestaw danych szkoleniowych jest mały, należy użyć tego trainer klasyfikacji wieloklasowej.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Wcześniejsze instruktora

|Właściwości|Instruktorzy|
|----------|--------|
|Użyj tego trainer klasyfikacji binarnej do linii bazowej wydajności innych instruktorów. Zaczęła obowiązywać, metryki innych Instruktorzy powinna być lepsze niż wcześniejsze instruktora. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
