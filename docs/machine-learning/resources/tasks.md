---
title: Zadania uczenia maszynowego
description: Zapoznaj się z różnych zadań i skojarzonych zadań, które są obsługiwane w strukturze ML.NET uczenia maszynowego.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063544"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Zadania uczenia maszynowego w strukturze ML.NET

Podczas tworzenia modelu uczenia maszynowego, należy najpierw zdefiniować, co to są licząc do osiągnięcia ze swoimi danymi. Teraz można wybrać odpowiednie uczenia zadania w danej sytuacji maszynowego. Na poniższej liście opisano różne stanowiska, zadania, których możesz korzystać z uczenia i niektórych typowych przypadków użycia.

Gdy okaże się, które zadanie działa w przypadku danego scenariusza, należy wybrać najlepszy algorytm w celu nauczenia modelu. Dostępne algorytmy są wymienione w sekcji dla każdego zadania.

## <a name="binary-classification"></a>Klasyfikacja binarna

A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania, której wystąpienia danych należy do dwóch klas (kategorie). Dane wejściowe to algorytm klasyfikacji to zestaw z etykietami przykładów, gdzie każda etykieta jest liczbą całkowitą, 0 lub 1. Dane wyjściowe to algorytm klasyfikacji binarnej jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety. Przykłady scenariuszy zastosowania Klasyfikacja binarna:

* [Opis wskaźniki nastrojów klientów usługi Twitter, komentarzy](../tutorials/sentiment-analysis.md) co "ujemny" lub "pozytywne".
* Diagnozowanie, czy pacjent ma pewne choroby, czy nie.
* Podjęciem decyzji o oznaczyć wiadomość e-mail jako "spam", czy nie.
* Określanie, czy zdjęcie zawiera dog lub owocu.

Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) artykuł w witrynie Wikipedia.

### <a name="binary-classification-trainers"></a>Klasyfikacja binarna instruktorów

Możesz uczyć model klasyfikacji binarnej, używając następujących algorytmów:

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer> 
* <xref:Microsoft.ML.Trainers.PriorTrainer> 
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a>Klasyfikacja binarna wejściami i wyjściami

Aby uzyskać najlepsze wyniki przy użyciu klasyfikacji binarnej dane szkoleniowe należy rozdzielić (czyli równy numery dane szkoleniowe pozytywne i negatywne). Brak i wartości powinny być traktowane przed szkolenia.

Etykieta wejściowych danych kolumny musi być <xref:System.Boolean>.
Funkcje wejściowe danych kolumny musi być stałym rozmiarze wektor <xref:System.Single>.

Te Instruktorzy wyświetla następujące kolumny:

| Nazwa kolumny danych wyjściowych | Typ kolumny | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieprzetworzonej oceny, która została obliczona przez model|
| `PredictedLabel` | <xref:System.Boolean> | Etykieta przewidywane, oparte na znak wyniku. Mapuje wynik ujemny `false` i mapuje wynik dodatni `true`.|

## <a name="multiclass-classification"></a>Wieloklasowej klasyfikacji

A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania klasy (kategoria) wystąpienia danych. Dane wejściowe to algorytm klasyfikacji to zestaw przykładów etykietami. Każda etykieta rozpoczyna się zwykle jako tekst. Następnie jest uruchamiany za pośrednictwem TermTransform, która konwertuje ją na typ (liczbowy) klucz. Dane wyjściowe to algorytm klasyfikacji jest klasyfikatora, które służy do prognozowania klasy nowych wystąpień bez etykiety. Przykłady scenariuszy zastosowania wieloklasowej klasyfikacji:

* Określanie rasy pies jako "Siberian Husky", "Złotego odbiorcy danych", "Poodle" itd.
* Opis filmu przegląda jako "dodatnią", "neutralne" lub "ujemny".
* Kategoryzowanie hotelu przegląda jako "Lokalizacja", "price", "czystość" itd.

Aby uzyskać więcej informacji, zobacz [klasyfikacji Wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) artykuł w witrynie Wikipedia.

>[!NOTE]
>Jeden vs wszystkich uaktualnień dowolne [uczeń klasyfikacji binarnej](#binary-classification) zajmującym się wieloklasowej zestawów danych. Więcej informacji na temat [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-trainers"></a>Instruktorzy wieloklasowej klasyfikacji

Możesz uczyć model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkolenia:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a>Klasyfikacji wieloklasowej dane wejściowe i wyjściowe

Etykieta wejściowych danych kolumny musi być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu.
Kolumna funkcji musi być wektor o stałym rozmiarze <xref:System.Single>.

Ta trainer wyświetla następujące czynności:

| Nazwa wyjściowego | Typ | Opis|
| -- | -- | -- |
| `Score` | Wektor <xref:System.Single> | Wyniki wszystkich klas. Wyższa wartość oznacza większe prawdopodobieństwo należącymi do klasy skojarzonej. Element i tym ma największą wartość, i będzie mieć indeks przewidywane etykiety. Należy pamiętać, że jest liczony od zera indeks. |
| `PredictedLabel` | [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu | Indeks przewidywane etykiety. Jeśli wartość jest i, rzeczywiste etykiety będzie kategorii i tym w typie etykiety danych wejściowych o wartości klucza. |

## <a name="regression"></a>Regresji

A [uczenia maszynowego w trybie nadzorowanym](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania wartość etykiety z zestawu powiązanych funkcji. Etykiety można rzeczywistych wartości, a nie z ograniczoną liczbą permutacji ustawiono wartości, jak Klasyfikacja zadań. Algorytmy uczenia modelu regresji zależność etykiety na jego powiązanych funkcji, aby określić, jak etykiety spowoduje to zmianę wartości, które funkcje są zróżnicowane. Dane wejściowe to algorytm regresji to zestaw przykładów z etykietami znane wartości. Dane wyjściowe to algorytm regresji jest funkcja, która służy do prognozowania wartości etykiety dla dowolnego nowego zestawu danych wejściowych funkcji. Przykłady scenariuszy zastosowania regresji:

* Prognozowanie DOM ceny na podstawie atrybutów dom, np. liczby sypialni, lokalizacji lub rozmiaru.
* Prognozowanie przyszłych cen akcji na podstawie danych historycznych i trendów na rynku bieżącego.
* Prognozowanie sprzedaży produktu, w oparciu o budżet reklamowych.

### <a name="regression-trainers"></a>Instruktorzy regresji

Możesz uczyć modelu regresji przy użyciu następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Regresja wejściami i wyjściami

Etykieta wejściowych danych kolumny musi być <xref:System.Single>.

Instruktorzy w tym celu danych wyjściowych poniżej:

| Nazwa wyjściowego | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieprzetworzone wynik, który został przewidywane według modelu |

## <a name="clustering"></a>Klastrowanie

[Nienadzorowane uczenia maszynowego](glossary.md#unsupervised-machine-learning) zadanie, które służy do grupy wystąpień danych w klastrach zawierających podobne charakterystyki. Klaster można również zidentyfikować relacji w zestawie danych, który nie może być logicznie pochodny przez obserwację przeglądania lub prosty. Dane wejściowe i wyjściowe algorytmu klastrowania zależy od metodologii wybrany. Możesz korzystać z dystrybucji, centroida — oś, łączności oraz podejścia opartego na gęstości. Strukturze ML.NET obsługuje obecnie podejście oparte na centroida — oś, przy użyciu K-średnich klastra. Scenariusze z klastrowaniem należą:

* Opis segmenty hotelu gości na podstawie nawyki i cechy hotelu wyborów.
* Identyfikowanie segmentom klientów i danymi demograficznymi ułatwiające tworzenie kampanii reklamowych docelowych.
* Kategoryzowanie spisu w oparciu metryki produkcji.

### <a name="clustering-trainer"></a>Klastrowanie instruktora

Możesz uczyć model klastrowania przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a>Klastrowanie dane wejściowe i wyjściowe

Dane wejściowe funkcji muszą być <xref:System.Single>. Etykiety nie są wymagane.

Ta trainer wyświetla następujące czynności:

| Nazwa wyjściowego | Typ | Opis|
| -- | -- | -- |
| `Score` | Wektor <xref:System.Single> | Odległości punkt danych na wszystkich klastrach centriods |
| `PredictedLabel` | [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu | Indeks najbliższego klastra przewidzieć przez model. |

## <a name="anomaly-detection"></a>Wykrywanie anomalii

To zadanie tworzy model wykrywania anomalii przy użyciu jednostki składnik Analysis (UPW). Wykrywanie anomalii oparte na analizie PCA pomaga w tworzeniu modelu w scenariuszach, gdzie jest łatwe można uzyskać danych szkoleniowych z jedną klasę, np. prawidłowe transakcje, ale trudno pobrać wystarczający przykładowe docelowe anomalii.

Technikę ustanowionych w usłudze machine learning, analizie PCA jest często używany w analizie danych poznawczych, ponieważ wewnętrzna struktura danych, co spowoduje wyświetlenie i wyjaśnia wariancji w danych. UPW polega na analizowanie danych, który zawiera wiele zmiennych. Ona szuka korelacji między zmiennych i określa kombinacja wartości, które najlepiej przechwytuje różnice w wyniki. Wartości te połączone funkcji są używane do tworzenia bardziej zwarty miejsca funkcji o nazwie głównych składników.

Wykrywanie anomalii obejmuje wiele ważne zadania w usłudze machine learning:

* Identyfikowanie transakcje, które są potencjalnie oszukańczych.
* Nauka wzorców, które wskazują, że nastąpiło włamania do sieci.
* Znajdowanie nietypowe klastrów pacjentów.
* Sprawdzanie wartości wprowadzone w systemie.

Anomalie są rzadkie zdarzenia zgodnie z definicją, może być trudne do zbierania została przeanalizowana reprezentatywna próbka danych na potrzeby modelowania. Algorytmów do tej kategorii są przeznaczone szczególnie do wyzwania core tworzenie i szkolenie modeli za pomocą imbalanced zestawów danych.

### <a name="anomaly-detection-trainer"></a>Trainer wykrywania anomalii

Możesz uczyć model wykrywania anomalii przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Wykrywanie anomalii w danych wejściowych i wyjściowych

Funkcje wejściowe muszą być wektor stałych rozmiarach <xref:System.Single>.

Ta trainer wyświetla następujące czynności:

| Nazwa wyjściowego | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Wartość nieujemną, nieograniczone wynik, który został obliczana na podstawie modelu wykrywania anomalii |

## <a name="ranking"></a>Klasyfikacja

Zadanie klasyfikacji tworzy oceniania z zestawu przykładów etykietami. Ten przykładowy zestaw składa się z grupy wystąpień, które mogą zostać ocenione przy użyciu podanych kryteriów. Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.  Oceniania jest uczony grupom rangi nowe wystąpienie z nieznanego wyniki dla każdego wystąpienia. Strukturze ML.NET klasyfikacji uczących się [klasyfikacji maszyny przedstawiono](https://en.wikipedia.org/wiki/Learning_to_rank) na podstawie.

### <a name="ranking-training-algorithms"></a>Klasyfikacja szkolenia algorytmów

Możesz uczyć model klasyfikacji, za pomocą następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a>Klasyfikacja dane wejściowe i wyjściowe

Typ danych wejściowych etykiety musi być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu lub <xref:System.Single>. Wartość etykiety określa istotność, gdzie wyższe wartości wskazują wyższe istotności. Jeśli etykieta jest [klucz](xref:Microsoft.ML.Data.KeyDataViewType) wpisz, a następnie indeks kluczy jest wartością znaczenia, gdzie najmniejszy indeks jest najmniej istotnych. Jeśli etykieta jest <xref:System.Single>, większe wartości wskazują wyższe istotności.

Dane funkcji muszą być wektor o stałym rozmiarze <xref:System.Single> i wierszy danych wejściowych grupy kolumn muszą być [klucz](xref:Microsoft.ML.Data.KeyDataViewType) typu.

Ta trainer wyświetla następujące czynności:

| Nazwa wyjściowego | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Niepowiązane wynik, który został obliczana na podstawie modelu w celu wyznaczenia prognozowania |

## <a name="recommendation"></a>Zalecenie

Zadanie zalecenie umożliwia tworzenie listy zalecanych produktów lub usług. Używa strukturze ML.NET [factorization macierzy (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [filtrowania z wykorzystaniem współpracy](https://en.wikipedia.org/wiki/Collaborative_filtering) algorytm zalecenia w przypadku produktu historycznych klasyfikacji danych w wykazie. Na przykład mieć historycznych filmu klasyfikacji danych dla użytkowników i chcesz zaleca się inne filmy, które mogą następnie obejrzyj.

### <a name="recommendation-training-algorithms"></a>Zalecenie dotyczące szkolenia algorytmów

Możesz uczyć model zaleceń przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
