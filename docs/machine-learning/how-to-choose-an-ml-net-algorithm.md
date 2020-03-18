---
title: Jak wybrać algorytm ML.NET
description: Dowiedz się, jak wybrać algorytm ML.NET dla modelu uczenia maszynowego
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 0fed33203c02303e37e47f548e08ec131eeb1c77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739998"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>Jak wybrać algorytm ML.NET

Dla każdego [zadania ML.NET](resources/tasks.md)istnieje wiele algorytmów szkoleniowych do wyboru. Który z nich wybrać zależy od problemu, który próbujesz rozwiązać, charakterystyki danych i zasobów obliczeniowych i magazynowych, które mają dostępne. Należy pamiętać, że szkolenie modelu uczenia maszynowego jest procesem iteracyjnym. Może być konieczne wypróbowanie wielu algorytmów, aby znaleźć ten, który działa najlepiej.

Algorytmy działają na **funkcjach**. Funkcje są wartościami liczbowymi obliczonymi na podstawie danych wejściowych. Są to optymalne dane wejściowe dla algorytmów uczenia maszynowego. Przekształć surowe dane wejściowe w funkcje przy użyciu jednej lub większej [liczby przekształceń danych.](resources/transforms.md) Na przykład dane tekstowe są przekształcane w zestaw liczby wyrazów i kombinacji wyrazów. Po wyodrębnieniu funkcji z typu danych pierwotnych przy użyciu przekształceń danych, są one określane jako **featurized**. Na przykład featurized tekst lub featurized danych obrazu.

## <a name="trainer--algorithm--task"></a>Trener = Algorytm + Zadanie

Algorytm jest matematyka, która jest wykonywana w celu uzyskania **modelu**. Różne algorytmy tworzą modele o różnych cechach.

W ML.NET ten sam algorytm można zastosować do różnych zadań. Na przykład Stochastic Dual Skoordynowane Wynurzenie może służyć do klasyfikacji binarnej, klasyfikacji wieloklasowej i regresji. Różnica polega na tym, jak dane wyjściowe algorytmu są interpretowane w celu dopasowania zadania.

Dla każdej kombinacji algorytmu/zadania ML.NET zawiera składnik, który wykonuje algorytm szkolenia i wykonuje interpretację. Składniki te nazywane są trenerami. Na przykład <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> używa **StochasticDualCoordinatedAscent** algorytmstosowany do **regresji** zadania.

## <a name="linear-algorithms"></a>Algorytmy liniowe

Algorytmy liniowe tworzą model, który oblicza **wyniki** na podstawie liniowej kombinacji danych wejściowych i zestawu **wag.** Wagi są parametrami modelu szacowanymi podczas treningu.

Algorytmy liniowe działają dobrze dla funkcji, które są [liniowo rozdzielne.](https://en.wikipedia.org/wiki/Linear_separability)

Przed treningiem z algorytmem liniowym funkcje powinny zostać znormalizowane. Zapobiega to jednej funkcji mającej większy wpływ na wynik niż inne.

Ogólnie algorytmy liniowe są skalowalne i szybkie, tanie do pociągu, tanie do przewidzenia. Skalują się one według liczby funkcji i w przybliżeniu według rozmiaru zestawu danych szkoleniowych.

Algorytmy liniowe sprawiają, że wiele przebiegów nad danymi treningowymi. Jeśli zestaw danych pasuje do pamięci, a następnie dodanie [punktu kontrolnego pamięci podręcznej](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) do potoku ML.NET przed dołączania trenera, spowoduje, że szkolenie będzie działać szybciej.

**Trenerzy liniowi**

|Algorytm|Właściwości|Trenerzy|
|---------|----------|--------|
|Uśredniona perceptron|Najlepsze do klasyfikacji tekstu|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stochastic dual skoordynowane wznoszenie|Dostrajanie nie jest potrzebne do uzyskania dobrej domyślnej wydajności|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS (angielski)|Użyj, gdy liczba obiektów jest duża. Tworzy statystyki szkolenia regresji logistycznej, ale nie skaluje się tak dobrze, jak AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Symboliczne zejście gradientu stochastycznego|Najszybszy i najdokładniejszy liniowy trener klasyfikacji binarnej. Skaluje się dobrze z liczbą procesorów|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Algorytmy drzewa decyzyjnego

Algorytmy drzewa decyzyjnego utworzyć model, który zawiera szereg decyzji: skutecznie schemat blokowy za pośrednictwem wartości danych.

Funkcje nie muszą być liniowo rozdzielne, aby użyć tego typu algorytmu. A funkcje nie muszą być znormalizowane, ponieważ poszczególne wartości wektora operacji są używane niezależnie w procesie decyzyjnym.

Algorytmy drzewa decyzyjnego są na ogół bardzo dokładne.

Z wyjątkiem uogólnionych modeli dodatków (GAMs), modele drzewa może brak wyjaśnienia, gdy liczba funkcji jest duża.

Algorytmy drzewa decyzyjnego zajmują więcej zasobów i nie skalują się tak dobrze, jak algorytmy liniowe. Działają one dobrze na zestawy danych, które mogą pasować do pamięci.

Wzmocnione drzewa decyzyjne są zespołem małych drzew, gdzie każde drzewo ocenia dane wejściowe i przekazuje wynik do następnego drzewa, aby uzyskać lepszy wynik itd., gdzie każde drzewo w zespole poprawia się w stosunku do poprzedniego.

**Trenerzy drzewa decyzyjnego**

|Algorytm|Właściwości|Trenerzy|
|---------|----------|--------|
|Maszyna wzmocniona gradientem światła|Najszybszy i najdokładniejszy z binarnych trenerów drzewa klasyfikacji. Wysoce przestrajalny|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Szybkie drzewo|Służy do featurized danych obrazu. Odporne na niezrównoważone dane. Wysoce przestrajalny | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Szybki las|Działa dobrze z hałaśliwymi danymi|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Uogólniony model addytywny (GAM)|Najlepsze rozwiązanie problemów, które sprawdzają się w algorytmach drzewa, ale gdzie objaśnienie jest priorytetem|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Faktoryzacja macierzy

|Właściwości|Trenerzy|
|----------|--------|
|Najlepsze dla rzadkich danych kategorycznych z dużymi zestawami danych|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algorytmy

Trenerzy ci tworzą wieloklasowego trenera od trenera binarnego. Używać <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>z <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>, , .

|Algorytm|Właściwości|Trenerzy|
|---------|----------|--------|
|Jeden kontra wszystkie|Ten wieloklasowy klasyfikator trenuje jeden klasyfikator binarny dla każdej klasy, który odróżnia tę klasę od wszystkich innych klas. Jest ograniczona w skali przez liczbę klas do kategoryzowania|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Sprzęgło parowe|Ten wieloklasowy klasyfikator trenuje algorytm klasyfikacji binarnej na każdej parze klas. Jest ograniczona w skali przez liczbę klas, jak każda kombinacja dwóch klas musi być przeszkolony.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>Środki K

|Właściwości|Trenerzy|
|----------|--------|
|Służy do klastrowania|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Analiza głównych składników

|Właściwości|Trenerzy|
|----------|--------|
|Służy do wykrywania anomalii|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Prosty algorytm Bayesa

|Właściwości|Trenerzy|
|----------|--------|
|Użyj tego wieloklasowego trenera klasyfikacji, gdy funkcje są niezależne, a zestaw danych szkolenia jest mały.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Poprzedni trener

|Właściwości|Trenerzy|
|----------|--------|
|Użyj tego trenera klasyfikacji binarnej do linii bazowej wydajności innych trenerów. Aby być skutecznym, wskaźniki innych trenerów powinny być lepsze niż poprzedni trener. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
