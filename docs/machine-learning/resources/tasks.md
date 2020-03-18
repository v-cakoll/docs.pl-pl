---
title: Zadania uczenia maszynowego
description: Zapoznaj się z różnymi zadaniami uczenia maszynowego i skojarzonymi zadaniami obsługiwanymi w ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399204"
---
# <a name="machine-learning-tasks-in-mlnet"></a>Zadania uczenia maszynowego w ML.NET

Zadanie uczenia maszynowego jest typem prognozowania lub wnioskowania, na podstawie problemu lub pytania, które jest zadawane i dostępnych danych. Na przykład zadanie klasyfikacji przypisuje dane do kategorii, a zadania klastrowania grupują dane zgodnie z podobieństwem.

Zadania uczenia maszynowego polegać na wzorce w danych, a nie jawnie zaprogramowane.

W tym artykule opisano różne zadania uczenia maszynowego, które można wybrać w ML.NET i niektórych typowych przypadkach użycia.

Po podjęciu decyzji, które zadanie działa dla twojego scenariusza, musisz wybrać najlepszy algorytm do uczenia modelu. Dostępne algorytmy są wymienione w sekcji dla każdego zadania.

## <a name="binary-classification"></a>Klasyfikacja binarna

Nadzorowane zadanie [uczenia maszynowego,](glossary.md#supervised-machine-learning) które służy do przewidywania, które z dwóch klas (kategorii) należy do wystąpienia danych. Dane wejściowe algorytmu klasyfikacji jest zestaw oznaczonych przykładów, gdzie każda etykieta jest liczbą całkowitą 0 lub 1. Dane wyjściowe algorytmu klasyfikacji binarnej jest klasyfikatorem, którego można użyć do przewidywania klasy nowych wystąpień bez etykiety. Przykłady scenariuszy klasyfikacji binarnej obejmują:

* [Zrozumienie sentymentu komentarzy na Twitterze](../tutorials/sentiment-analysis.md) jako "pozytywnych" lub "negatywnych".
* Diagnozowanie, czy pacjent ma pewną chorobę, czy nie.
* Podejmowanie decyzji o oznaczenie wiadomości e-mail jako "spam" lub nie.
* Określanie, czy zdjęcie zawiera określony przedmiot, czy nie, takie jak pies lub owoc.

Aby uzyskać więcej informacji, zobacz artykuł [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) na Wikipedii.

### <a name="binary-classification-trainers"></a>Trenerzy klasyfikacji binarnej

Model klasyfikacji binarnej można nabyć przy użyciu następujących algorytmów:

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

Aby uzyskać najlepsze wyniki w klasyfikacji binarnej, dane szkoleniowe powinny być zrównoważone (czyli równej liczby pozytywnych i negatywnych danych szkoleniowych). Brakujące wartości powinny być obsługiwane przed szkoleniem.

Dane kolumny etykiety <xref:System.Boolean>wejściowej muszą być .
Dane kolumnowe funkcji wejściowych muszą <xref:System.Single>być wektorem o stałym rozmiarze .

Te trenerzy wyprowadzają następujące kolumny:

| Nazwa kolumny wyjściowej | Typ kolumny | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Surowy wynik obliczony przez model|
| `PredictedLabel` | <xref:System.Boolean> | Przewidywana etykieta na podstawie znaku wyniku. Negatywny wynik mapuje i `false` pozytywny `true`wynik mapuje do .|

## <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które służy do przewidywania klasy (kategorii) wystąpienia danych. Dane wejściowe algorytmu klasyfikacji jest zestaw oznaczonych przykładów. Każda etykieta zwykle zaczyna się jako tekst. Następnie jest uruchamiany przez TermTransform, który konwertuje go do typu Klucz (numeryczny). Dane wyjściowe algorytmu klasyfikacji jest klasyfikatorem, którego można użyć do przewidywania klasy nowych wystąpień bez etykiety. Przykłady wieloklasowych scenariuszy klasyfikacji obejmują:

* Określenie rasy psa jako "Syberyjskiego Husky", "Golden Retriever", "Pudel", itp.
* Zrozumienie recenzji filmów jako "pozytywnych", "neutralnych" lub "negatywnych".
* Kategoryzowanie recenzji hoteli jako "lokalizacja", "cena", "czystość" itp.

Aby uzyskać więcej informacji, zobacz artykuł [klasyfikacji wieloklasowej](https://en.wikipedia.org/wiki/Multiclass_classification) na Wikipedii.

>[!NOTE]
>Jeden vs wszystkie uaktualnia dowolnego [uczącego się klasyfikacji binarnej](#binary-classification) do działania na wieloklasowych zestawów danych. Więcej informacji na temathttps://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)[Wikipedia] ( .

### <a name="multiclass-classification-trainers"></a>Trenerzy klasyfikacji wieloklasowej

Można nabyć wieloklasowy model klasyfikacji przy użyciu następujących algorytmów szkoleniowych:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Wieloklasowe wejścia i wyjścia klasyfikacji

Dane kolumny etykiety wejściowej muszą być [typu klucza.](xref:Microsoft.ML.Data.KeyDataViewType)
Kolumna operacji musi być wektorem o stałym rozmiarze <xref:System.Single>.

Ten trener wyprowadza następujące elementy:

| Nazwa wyjścia | Typ | Opis|
| -- | -- | -- |
| `Score` | Wektor<xref:System.Single> | Wyniki wszystkich klas. Wyższa wartość oznacza większe prawdopodobieństwo wpadki do skojarzonej klasy. Jeśli i-th element ma największą wartość, indeks emanujący etykietą przewidywaną będzie i. Należy pamiętać, że i jest indeksem zerowym. |
| `PredictedLabel` | typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType) | Indeks przewidywanej etykiety. Jeśli jego wartość jest i, rzeczywista etykieta będzie i-ty kategorii w typie etykiety wejściowej wartości klucza. |

## <a name="regression"></a>Regresja

[Nadzorowane](glossary.md#supervised-machine-learning) zadanie uczenia maszynowego, które służy do przewidywania wartości etykiety z zestawu powiązanych funkcji. Etykieta może mieć dowolną wartość rzeczywistą i nie pochodzi od skończonego zestawu wartości, jak w zadaniach klasyfikacji. Algorytmy regresji modelu zależności etykiety na jego powiązanych funkcji, aby określić, jak etykieta zmieni się jako wartości funkcji są zróżnicowane. Dane wejściowe algorytmu regresji jest zestaw przykładów z etykietami znanych wartości. Dane wyjściowe algorytmu regresji jest funkcją, której można użyć do przewidywania wartości etykiety dla każdego nowego zestawu funkcji wejściowych. Przykłady scenariuszy regresji obejmują:

* Przewidywanie cen domów na podstawie atrybutów domu, takich jak liczba sypialni, lokalizacja lub rozmiar.
* Przewidywanie przyszłych cen akcji na podstawie danych historycznych i aktualnych trendów rynkowych.
* Przewidywanie sprzedaży produktu na podstawie budżetów reklamowych.

### <a name="regression-trainers"></a>Trenerzy regresji

Model regresji można nabyć przy użyciu następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Wejścia i wyjścia regresji

Dane kolumny etykiety <xref:System.Single>wejściowej muszą być .

Trenerzy dla tego zadania wyprowadzają następujące wyniki:

| Nazwa wyjścia | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Surowy wynik, który został przepowiedziany przez model |

## <a name="clustering"></a>Klastrowanie

Nienadzorowane zadanie [uczenia maszynowego,](glossary.md#unsupervised-machine-learning) które jest używane do grupowania wystąpień danych w klastry, które zawierają podobne właściwości. Klastrowanie może być również używany do identyfikowania relacji w zestawie danych, które mogą nie logicznie pochodzić przez przeglądanie lub prostą obserwację. Dane wejściowe i wyjściowe algorytmu klastrowania zależą od wybranej metodologii. Można przyjąć podejście oparte na dystrybucji, centroidach, łączności lub gęstości. ML.NET obecnie obsługuje podejście oparte na centroidach przy użyciu klastrowania K-Means. Przykłady scenariuszy klastrowania obejmują:

* Zrozumienie segmentów gości hotelowych na podstawie nawyków i cech hotelowych.
* Identyfikowanie segmentów klientów i danych demograficznych w celu tworzenia ukierunkowanych kampanii reklamowych.
* Kategoryzowanie zapasów na podstawie danych produkcyjnych.

### <a name="clustering-trainer"></a>Trener klastrów

Model klastrowania można nabyć przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Klastrowanie wejść i wyjść

Dane wejściowe funkcji <xref:System.Single>muszą być . Etykiety nie są potrzebne.

Ten trener wyprowadza następujące elementy:

| Nazwa wyjścia | Typ | Opis|
| -- | -- | -- |
| `Score` | wektor<xref:System.Single> | Odległości danych wskazują na centriody wszystkich klastrów |
| `PredictedLabel` | typ [klucza](xref:Microsoft.ML.Data.KeyDataViewType) | Najbliższy indeks klastra przewidywane przez model. |

## <a name="anomaly-detection"></a>Wykrywanie anomalii

To zadanie tworzy model wykrywania anomalii przy użyciu analizy składników głównych (PCA). Wykrywanie anomalii opartych na pca pomaga utworzyć model w scenariuszach, w których jest łatwe do uzyskania danych szkoleniowych z jednej klasy, takich jak prawidłowe transakcje, ale trudno uzyskać wystarczające przykłady docelowych anomalii.

Ustalona technika uczenia maszynowego, PCA jest często używany w analizie danych badawczych, ponieważ ujawnia wewnętrzną strukturę danych i wyjaśnia wariancję w danych. PcA działa poprzez analizowanie danych, które zawiera wiele zmiennych. Szuka korelacji między zmiennymi i określa kombinację wartości, która najlepiej przechwytuje różnice w wynikach. Te połączone wartości operacji są używane do tworzenia bardziej kompaktowej przestrzeni obiektowej zwanej głównymi komponentami.

Wykrywanie anomalii obejmuje wiele ważnych zadań w uczeniu maszynowym:

* Identyfikowanie transakcji, które mogą być fałszywe.
* Wzorce uczenia się, które wskazują, że doszło do włamania do sieci.
* Znalezienie nieprawidłowych skupisk pacjentów.
* Sprawdzanie wartości wprowadzonych do systemu.

Ponieważ anomalie są rzadkie zdarzenia z definicji, może być trudne do zebrania reprezentatywnej próbki danych do użycia do modelowania. Algorytmy zawarte w tej kategorii zostały specjalnie zaprojektowane, aby sprostać podstawowym wyzwaniom związanym z tworzeniem i szkoleniem modeli przy użyciu niezrównoważonych zestawów danych.

### <a name="anomaly-detection-trainer"></a>Trener wykrywania anomalii

Model wykrywania anomalii można nabyć przy użyciu następującego algorytmu:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Wejścia i wyjścia wykrywania anomalii

Operacje wejściowe muszą być wektorem o stałym rozmiarze <xref:System.Single>.

Ten trener wyprowadza następujące elementy:

| Nazwa wyjścia | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Nieujemna, nieograniczona ocena obliczona przez model wykrywania anomalii |
| `PredictedLabel` | <xref:System.Boolean> | Wartość prawda/fałsz reprezentująca, czy dane wejściowe są anomalią (PredictedLabel=true), czy nie (PredictedLabel=false) |

## <a name="ranking"></a>Ranking

Zadanie klasyfikacji konstruuje ranker z zestawu oznaczonych przykładów. Ten przykładowy zestaw składa się z grup wystąpień, które mogą być oceniane przy danych kryteriach. Etykiety rankingu to { 0, 1, 2, 3, 4 } dla każdego wystąpienia.  Ranker jest przeszkolony do rangi nowych grup wystąpień z nieznanych wyników dla każdego wystąpienia. ML.NET rankingu uczących się są [machine learned rankingu](https://en.wikipedia.org/wiki/Learning_to_rank) oparte.

### <a name="ranking-training-algorithms"></a>Ranking algorytmów szkoleniowych

Model klasyfikacji można nabyć za pomocą następujących algorytmów:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Ranking danych wejściowych i wyjściowych

Typ danych etykiety wejściowej <xref:System.Single>musi być [typem klucza](xref:Microsoft.ML.Data.KeyDataViewType) lub . Wartość etykiety określa trafność, gdzie wyższe wartości wskazują na większą trafność. Jeśli etykieta jest typem [klucza,](xref:Microsoft.ML.Data.KeyDataViewType) indeks klucza jest wartością istotności, gdzie najmniejszy indeks jest najmniej odpowiedni. Jeśli etykieta <xref:System.Single>jest , większe wartości wskazują na większą trafność.

Dane obiektu muszą być wektorem o stałym rozmiarze, a kolumna grupy wierszy wejściowych <xref:System.Single> musi być [typem klucza.](xref:Microsoft.ML.Data.KeyDataViewType)

Ten trener wyprowadza następujące elementy:

| Nazwa wyjścia | Typ | Opis|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Wynik bez ograniczeń, który został obliczony przez model w celu określenia |

## <a name="recommendation"></a>Zalecenie

Zadanie rekomendacji umożliwia tworzenie listy zalecanych produktów lub usług. ML.NET używa [matrycy faktoryzację (MF),](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)algorytm [filtrowania współpracy](https://en.wikipedia.org/wiki/Collaborative_filtering) dla zaleceń, gdy masz historyczne dane klasyfikacji produktów w katalogu. Na przykład masz historyczne dane klasyfikacji filmów dla użytkowników i chcesz polecić inne filmy, które prawdopodobnie będą oglądać dalej.

### <a name="recommendation-training-algorithms"></a>Algorytmy szkolenia rekomendacji

Można nabyć model rekomendacji z następującym algorytmem:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a>Prognozowanie

Zadanie prognozowania używać danych z poprzednich szeregów czasowych do prognozowania przyszłego zachowania. Scenariusze mające zastosowanie do prognozowania obejmują prognozowanie pogody, sezonowe prognozy sprzedaży i konserwację predykcyjna,

### <a name="forecasting-trainers"></a>Trenerzy prognozowania

Model prognozowania można nabyć za pomocą następującego algorytmu:

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
