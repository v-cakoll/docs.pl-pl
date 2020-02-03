---
title: Zadania uczenia maszynowego
description: Poznaj różne zadania uczenia maszynowego i powiązane zadania, które są obsługiwane w programie ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745100"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Zadania uczenia maszynowego w ML.NET

Zadanie uczenia maszynowego jest typem przewidywanych lub zgłaszanych wnioskami na podstawie problemu lub pytania, które jest zadawane, oraz dostępnych danych. Na przykład zadanie klasyfikacji przypisuje dane do kategorii, a zadanie klastrowania grupuje dane zgodnie z podobieństwem.

Zadania uczenia maszynowego polegają na wzorcach danych, a nie w sposób jawny.

W tym artykule opisano różne zadania uczenia maszynowego, które można wybrać w ML.NET i niektóre typowe przypadki użycia.

Po ustaleniu, które zadanie działa w danym scenariuszu, należy wybrać najlepszy algorytm do uczenia modelu. Dostępne algorytmy są wymienione w sekcji dla każdego zadania.

## <a name="binary-classification"></a>Klasyfikacja binarna

[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania, do których dwóch klas (kategorii) należy wystąpienie danych. Wejściem algorytmu klasyfikacji jest zestaw przykładowych etykiet, gdzie każda etykieta jest liczbą całkowitą równą 0 lub 1. Dane wyjściowe algorytmu klasyfikacji binarnej to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet. Przykłady scenariuszy klasyfikacji binarnej obejmują:

* [Zrozumienie tonacji komentarzy w serwisie Twitter](../tutorials/sentiment-analysis.md) jako "pozytywne" lub "negatywne".
* Diagnozowanie, czy pacjent ma określoną chorobę, czy nie.
* Podejmowanie decyzji o oznaczeniu wiadomości e-mail jako "spamu".
* Określanie, czy zdjęcie zawiera określony element, np. pies lub owoce.

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) w witrynie Wikipedia.

### <a name="binary-classification-trainers"></a>Instruktorzy klasyfikacji binarnej

Można nauczyć model klasyfikacji binarnej przy użyciu następujących algorytmów:

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

### <a name="binary-classification-inputs-and-outputs"></a>Dane wejściowe i wyjściowe klasyfikacji binarnej

Aby uzyskać najlepsze wyniki z klasyfikacją binarną, należy zrównoważyć dane szkoleniowe (to jest równa Liczba pozytywnych i negatywnych danych szkoleniowych). Brakujące wartości powinny zostać obsłużone przed szkoleniem.

Dane kolumny etykiety wejściowej muszą być <xref:System.Boolean>.
Dane w kolumnie funkcje wejściowe muszą być wektorem o stałym rozmiarze <xref:System.Single>.

Te instruktorzy wyprowadzają następujące kolumny:

| Nazwa kolumny wyjściowej | Typ kolumny | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieprzetworzony wynik, który został obliczony przez model|
| `PredictedLabel` | <xref:System.Boolean> | Przewidywana etykieta na podstawie znaku wyniku. Negatywny wynik mapy do `false` i pozytywnego wyniku mapowania do `true`.|

## <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania klasy (kategorii) wystąpienia danych. Dane wejściowe algorytmu klasyfikacji to zestaw przykładowych etykiet. Każda etykieta zwykle zaczyna się jako tekst. Następnie jest uruchamiany za pomocą TermTransform, który konwertuje go na typ klucza (liczbowy). Dane wyjściowe algorytmu klasyfikacji to klasyfikator, którego można użyć do przewidywania klasy nowych wystąpień bez etykiet. Przykładowe wieloklasowe scenariusze klasyfikacji obejmują:

* Określanie rasy Dog jako "Siberian Husky", "złota wejście metody Retriever", "POODLE" itd.
* Zrozumienie przeglądów filmów jako "pozytywnych", "neutralnych" lub "negatywnych".
* Kategoryzacja przeglądów hotelu jako "lokalizacja", "cena", "czysta" itp.

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [klasyfikacji wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) w witrynie Wikipedia.

>[!NOTE]
>Jeden a All uaktualnia każdy [kod binarny](#binary-classification) do działania w ramach wieloklasowych zestawów danych. Więcej informacji na temat witryny [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-trainers"></a>Instruktorzy klasyfikacji wieloklasowej

Można przeszkolić model klasyfikacji wieloklasowej przy użyciu następujących algorytmów szkoleniowych:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Dane wejściowe i wyjściowe klasyfikacji wieloklasowej

Dane kolumny etykiet wejściowych muszą być typu [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .
Kolumna funkcji musi być wektorem o stałym rozmiarze <xref:System.Single>.

Ta Trainer wyprowadza następujące dane:

| Nazwa wyjściowa | Typ | Opis|
| -- | -- | -- |
| `Score` | wektor <xref:System.Single> | Wyniki wszystkich klas. Wyższa wartość oznacza wyższe prawdopodobieństwo podzielenia się z klasą skojarzoną. Jeśli element i-ty ma największą wartość, przewidywany indeks etykiet będzie. Zwróć uwagę, że jest indeksem opartym na wartości zero. |
| `PredictedLabel` | Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType) | Indeks przewidywanej etykiety. Jeśli wartość jest równa i, rzeczywista etykieta będzie kategorią i, w typie etykiety wejściowej z wartościami klucza. |

## <a name="regression"></a>Regresja

[Nadzorowane zadanie uczenia maszynowego](glossary.md#supervised-machine-learning) , które jest używane do przewidywania wartości etykiety z zestawu pokrewnych funkcji. Etykieta może być dowolną wartością rzeczywistą i nie pochodzi z skończonego zestawu wartości jako zadań klasyfikacji. Algorytmy regresji modelują zależność etykiety na jej powiązanych funkcjach, aby określić, w jaki sposób etykieta zostanie zmieniona, ponieważ wartości funkcji są różne. Wejście algorytmu regresji jest zestawem przykładów z etykietami znanych wartości. Wynikiem algorytmu regresji jest funkcja, której można użyć do przewidywania wartości etykiety dla każdego nowego zestawu funkcji wejściowych. Przykłady scenariuszy regresji obejmują:

* Przewidywanie cen domu na podstawie atrybutów, takich jak liczba sypialniami, lokalizacji lub rozmiaru.
* Przewidywanie przyszłych cen giełdowych w oparciu o dane historyczne i bieżące trendy rynkowe.
* Przewidywanie sprzedaży produktu na podstawie budżetów reklamowych.

### <a name="regression-trainers"></a>Instruktorzy regresji

Model regresji można przeszkolić przy użyciu następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Dane wejściowe i wyjściowe regresji

Dane kolumny etykiety wejściowej muszą być <xref:System.Single>.

Instruktorzy dla tego zadania wyprowadzają następujące dane wyjściowe:

| Nazwa wyjściowa | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieprzetworzony wynik, który został przewidywalny przez model |

## <a name="clustering"></a>Klastrowanie

Nienadzorowane zadanie [uczenia maszynowego](glossary.md#unsupervised-machine-learning) , które jest używane do grupowania wystąpień danych w klastry zawierające podobne właściwości. Klastrowanie może również służyć do identyfikowania relacji w zestawie danych, które mogą nie być logicznie wyprowadzane przez przeglądanie lub prostą obserwację. Dane wejściowe i wyjściowe algorytmu klastrowania zależą od wybranej metodologii. Możesz skorzystać z metody dystrybucji, centroida, łączności lub opartej na gęstość. ML.NET obecnie obsługuje podejście oparte na centroida przy użyciu K-oznacza klastrowanie. Przykłady scenariuszy klastrowania obejmują:

* Zrozumienie segmentów Gości w hotelu w oparciu o nawyki i cechy charakterystyczne wyborów hotelowych.
* Identyfikowanie segmentów i demograficznych klientów w celu ułatwienia tworzenia strategicznych kampanii reklamowych.
* Kategoryzacja spisu na podstawie metryk produkcji.

### <a name="clustering-trainer"></a>Trainer klastrowania

Model klastrowania można przeszkolić przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Klastrowanie danych wejściowych i wyjściowych

Dane funkcji wejściowych muszą być <xref:System.Single>. Etykiety nie są zbędne.

Ta Trainer wyprowadza następujące dane:

| Nazwa wyjściowa | Typ | Opis|
| -- | -- | -- |
| `Score` | wektor <xref:System.Single> | Odległość danego punktu danych do wszystkich klastrów centriods |
| `PredictedLabel` | Typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType) | Indeks najbliższego klastra przewidziany przez model. |

## <a name="anomaly-detection"></a>Wykrywanie anomalii

To zadanie tworzy model wykrywania anomalii przy użyciu głównej analizy składników (PPW). Wykrywanie anomalii oparte na UPW pomaga budować model w scenariuszach, w którym można łatwo uzyskać dane szkoleniowe z jednej klasy, takie jak prawidłowe transakcje, ale trudno jest uzyskać wystarczającą liczbę próbek do dokierowanych anomalii.

Ustalona technika w uczeniu maszynowym jest często używana w analizie danych poznawczych, ponieważ ujawnia wewnętrzną strukturę danych i objaśnia wariancję danych. UPW działa przez analizowanie danych, które zawierają wiele zmiennych. Szuka korelacji między zmiennymi i określa kombinację wartości, które najlepiej przechwytuje różnice w wyników. Te połączone wartości funkcji są używane do tworzenia bardziej kompaktowego miejsca funkcji o nazwie składniki główne.

Wykrywanie anomalii obejmuje wiele ważnych zadań w usłudze Machine Learning:

* Identyfikowanie transakcji, które są potencjalnie fałszywe.
* Wzorce szkoleniowe wskazujące, że nastąpiło nieautoryzowanie sieci.
* Znajdowanie nietypowych klastrów pacjentów.
* Sprawdzanie wartości wprowadzonych w systemie.

Ponieważ anomalie są rzadkimi zdarzeniami z definicji, trudno jest zebrać reprezentatywny przykład danych do użycia podczas modelowania. Algorytmy zawarte w tej kategorii zostały szczególnie zaprojektowane w celu rozwiązywania najważniejszych wyzwań związanych z kompilowaniem i uczeniem modeli przy użyciu niezrównoważonych zestawów danych.

### <a name="anomaly-detection-trainer"></a>Trainer wykrywania anomalii

Model wykrywania anomalii można przeszkolić przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Dane wejściowe i wyjściowe wykrywania anomalii

Funkcje wejściowe muszą być wektorami o stałym rozmiarze <xref:System.Single>.

Ta Trainer wyprowadza następujące dane:

| Nazwa wyjściowa | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieujemny wynik niezwiązany, który został obliczony przez model wykrywania anomalii |
| `PredictedLabel` | <xref:System.Boolean> | Wartość true/false określająca, czy dane wejściowe są anomalią (PredictedLabel = true) czy nie (PredictedLabel = false) |

## <a name="ranking"></a>Określania

Zadanie klasyfikacji konstruuje rangę z zestawu przykładowych etykiet. Ten przykładowy zestaw składa się z grup wystąpień, które mogą być oceniane przy użyciu danego kryterium. Etykiety klasyfikacji są {0, 1, 2, 3, 4} dla każdego wystąpienia.  Ranga jest przeszkolony, aby zaklasyfikować nowe grupy wystąpień z nieznanymi wynikami dla każdego wystąpienia. ML.NET oceniające ranking są [uczeniem maszynowym](https://en.wikipedia.org/wiki/Learning_to_rank) opartym na klasyfikacji.

### <a name="ranking-training-algorithms"></a>Klasyfikowanie algorytmów szkoleniowych

Model klasyfikowania można nauczyć przy użyciu następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Klasyfikacja danych wejściowych i wyjściowych

Typ danych etykiety wejściowej musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) lub <xref:System.Single>. Wartość etykiety określa istotność, gdzie wyższe wartości wskazują wyższy poziom istotności. Jeśli etykieta jest typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) , indeks klucza jest wartością istotności, gdzie najmniejszy indeks jest najmniej istotny. Jeśli etykieta jest <xref:System.Single>, większe wartości wskazują wyższy poziom istotności.

Dane funkcji muszą być wektorem o stałym rozmiarze <xref:System.Single>, a kolumna grupy wierszy wejściowych musi być typem [klucza](xref:Microsoft.ML.Data.KeyDataViewType) .

Ta Trainer wyprowadza następujące dane:

| Nazwa wyjściowa | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Niezwiązany wynik, który został obliczony przez model w celu określenia przewidywania |

## <a name="recommendation"></a>Zalecenie

Zadanie rekomendacji umożliwia tworzenie listy zalecanych produktów lub usług. ML.NET używa [klasy Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [współpracującego algorytmu filtrowania](https://en.wikipedia.org/wiki/Collaborative_filtering) dla zaleceń w przypadku historycznych danych oceny produktu w katalogu. Na przykład masz historyczne dane klasyfikacji filmów dla użytkowników i chcesz, aby zalecać inne filmy, które mogą być obserwowane dalej.

### <a name="recommendation-training-algorithms"></a>Algorytmy szkoleniowe dotyczące rekomendacji

Możesz nauczyć model rekomendacji z następującym algorytmem:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a>Prognozowanie

Zadanie prognozowania używa ostatnich danych szeregów czasowych do prognozowania w przyszłości. Scenariusze mające zastosowanie do prognozowania obejmują Prognozowanie pogody, sezonowe przewidywania sprzedaży i konserwację predykcyjną,

### <a name="forecasting-trainers"></a>Instruktorzy prognoz

Model prognozowania można przeszkolić przy użyciu następującego algorytmu:

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
