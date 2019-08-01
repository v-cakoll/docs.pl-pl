---
title: Przekształcenia danych
description: Poznaj składniki inżynierii funkcji obsługiwane w programie ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: cbcdef5b8f5f6334d5545f100976347ade9ee6fd
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671873"
---
# <a name="data-transformations"></a>Przekształcenia danych

Przekształcenia danych są używane do:
- Przygotowywanie danych do szkolenia modelu
- stosowanie zaimportowanego modelu w formacie TensorFlow lub ONNX
- dane po zakończeniu procesu po przekazaniu ich przez model

Przekształcenia w tym przewodniku zwracają klasy implementujące interfejs [IEstimator](xref:Microsoft.ML.IEstimator%601) . Przekształcenia danych można łączyć ze sobą. Każda transformacja oczekuje i tworzy dane określonych typów i formatów, które są określone w połączonej dokumentacji referencyjnej.

Niektóre przekształcenia danych wymagają danych szkoleniowych do obliczenia ich parametrów. Na przykład: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformator oblicza średnią i wariancję danych szkoleniowych `Fit()` podczas operacji i `Transform()` używa tych parametrów w operacji. 

Inne przekształcenia danych nie wymagają danych szkoleniowych. Na przykład: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformacja może `Transform()` wykonać operację bez zaobserwować `Fit()` żadnych danych szkoleniowych podczas operacji.

## <a name="column-mapping-and-grouping"></a>Mapowanie i grupowanie kolumn

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Łączenie co najmniej jednej kolumny wejściowej w nową kolumnę wyjściową |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Kopiuj i Zmień nazwę co najmniej jednej kolumny wejściowej |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Upuść co najmniej jedną kolumnę wejściową |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Wybierz co najmniej jedną kolumnę, która ma być zachowana z danych wejściowych |

## <a name="normalization-and-scaling"></a>Normalizacja i skalowanie

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odejmij średnią (dane szkoleniowe) i Podziel się przez wariancję (danych szkoleniowych) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizowanie na podstawie logarytmu danych szkoleniowych |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Skaluj wektory wejściowe według ich [standardu LP](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), gdzie p ma 1, 2 lub nieskończoność. Wartość domyślna to L2 (Euclidean Distance) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Skaluj każdą wartość w wierszu, odejmując średnią z danych wiersza i dzieląc ją przez wartość odchylenia standardowego lub L2 (w danych wiersza), i pomnóż przez konfigurowalny współczynnik skalowania (domyślnie 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Przypisz wartość wejściową do indeksu bin i Podziel ją na liczbę pojemników, aby utworzyć wartość zmiennoprzecinkową z zakresu od 0 do 1. Granice pojemnika są obliczane w celu równomiernego dystrybuowania danych szkoleniowych między pojemnikami |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Przypisz wartość wejściową do pojemnika na podstawie jego korelacji z kolumną etykieta |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Skalowanie danych wejściowych według różnicy między wartościami minimalnymi i maksymalnymi w danych szkoleniowych |

## <a name="conversions-between-data-types"></a>Konwersje między typami danych

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Konwertuj typ kolumny wejściowej na nowy typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Mapuj wartości do kluczy (kategorii) na podstawie podanego słownika mapowań |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Mapuj wartości do kluczy (kategorii) przez utworzenie mapowania na podstawie danych wejściowych |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Konwertuj klucze z powrotem na ich oryginalne wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Konwertuj klucze z powrotem do wektorów oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Konwertuj klucze z powrotem do binarnego wektora oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Mieszanie wartości w kolumnie wejściowej |

## <a name="text-transformations"></a>Przekształcenia tekstu

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Przekształcanie kolumny tekstowej w tablicę zmiennoprzecinkową znormalizowanych ngrams i liczby char-Grams | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Dzielenie jednej lub więcej kolumn tekstowych na pojedyncze słowa |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Dzielenie jednej lub więcej kolumn tekstowych na pojedyncze znaki zmiennoprzecinkowe w zestawie tematów |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Zmień wielkość liter, Usuń znaki diakrytyczne, znaki interpunkcyjne i cyfry |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Przekształcanie kolumny tekstowej w zbiór liczb ngrams (sekwencje kolejnych wyrazów)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Przekształcanie kolumny tekstowej w zbiór liczb wektorów ngrams |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Przekształcanie kolumny tekstowej w wektor ngramych liczników |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Przekształcanie kolumny tekstowej w zbiór ngramych liczników skrótów |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Usuń domyślne słowa zatrzymywania dla określonego języka z kolumn wejściowych |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Usuwa określone słowa Stop z kolumn wejściowych |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | Przekształcanie dokumentu (reprezentowanego jako wektory elementów zmiennoprzecinkowych) do wektora zmiennoprzecinkowego na zestawie tematów |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Konwertowanie wektorów tokenów tekstowych na wektory zdania przy użyciu modelu wstępnie nauczonego |

## <a name="image-transformations"></a>Przekształcenia obrazu

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Konwertuj obraz na skalę odcieni szarooci |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Konwertuj wektor pikseli na<xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Konwersja pikseli z obrazu wejściowego do wektora liczb |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Ładowanie obrazów z folderu do pamięci |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Zmień rozmiar obrazów |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage*> | Stosuje wstępnie szkolony model głębokiej sieci neuronowychowej (DNN) do przekształcania obrazu wejściowego w wektor funkcji |

## <a name="categorical-data-transformations"></a>Kategorii przekształcenia danych

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Konwertowanie jednej lub więcej kolumn tekstowych na [jednostronicowe](https://en.wikipedia.org/wiki/One-hot) wektory kodowane |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Konwertowanie jednej lub większej liczby kolumn tekstowych na oparte na skrótach wektory kodowane z jednym gorącą |

## <a name="time-series-data-transformations"></a>Przekształcenia danych szeregów czasowych

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn*> | Wykrywaj anomalie w wejściowych danych szeregów czasowych przy użyciu algorytmu widma resztkowa (SR) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa*> | Wykrywanie punktów zmian w danych szeregów czasowych przy użyciu analizy szerokiego spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint*> | Wykrywanie punktów zmiany w niezależnych i identycznie dystrybuowanych (IID) danych szeregów czasowych przy użyciu funkcji oceny gęstości jądra i oceny Martingale |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*> | Prognozowanie danych szeregów czasowych przy użyciu analizy szerokiego spektrum (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa*> | Wykrywanie skoków w danych szeregów czasowych przy użyciu analizy wielowartościowej (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike*> | Wykrywanie skoków w niezależnych i identycznie dystrybuowanych danych szeregów czasowych (IID) przy użyciu dostosowanych ocen gęstości jądra i Martingale |

## <a name="missing-values"></a>Brakujące wartości

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Tworzenie nowej logicznej kolumny danych wyjściowych, która ma wartość true, jeśli brakuje wartości w kolumnie wejściowej |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | Utwórz nową kolumnę wyjściową, wartość, dla której jest ustawiona wartość domyślna, jeśli brak wartości w kolumnie wejściowej, a wartość wejściowa w przeciwnym razie |

## <a name="feature-selection"></a>Wybór funkcji

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Wybierz funkcje, których wartości inne niż domyślne są większe niż wartość progowa |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Wybierz funkcje, na których dane w kolumnie etykieta są najbardziej zależne |

## <a name="feature-transformations"></a>Przekształcenia funkcji

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap*> | Mapuj każdy wektor wejściowy na dolne miejsce funkcji, gdzie wewnętrzne produkty przybliżą funkcję jądra, dzięki czemu funkcje mogą być używane jako dane wejściowe w algorytmach liniowych |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents*> | Zmniejsz wymiary wektora funkcji wejściowych, stosując algorytm analizy składników głównych |

## <a name="explainability-transformations"></a>Przekształcenia objaśniające

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution*> | Oblicz wyniki udziału dla każdego elementu wektora funkcji |

## <a name="calibration-transformations"></a>Przekształcenia kalibracji

| Transformacja | Definicja |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Przekształca nieprzetworzony wynik klasyfikatora danych binarnych na prawdopodobieństwo klasy przy użyciu regresji logistycznej z parametrami szacowanymi przy użyciu danych szkoleniowych |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Przekształca nieprzetworzony wynik klasyfikatora danych binarnych na prawdopodobieństwo klasy przy użyciu regresji logistycznej ze stałymi parametrami |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive*> | Przekształca dane wynikowe klasyfikatora binarnego na prawdopodobieństwo klasy przez przypisanie wyników do pojemników oraz Obliczanie prawdopodobieństwa na podstawie rozkładu między pojemnikami |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic*> | Przekształca nieprzetworzony wynik klasyfikatora danych binarnych na prawdopodobieństwo klasy przez przypisanie wyników do pojemników, gdzie pozycja granic i rozmiar pojemników są szacowane przy użyciu danych szkoleniowych.  |

## <a name="deep-learning-transformations"></a>Przekształcenie głębokie uczenia

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*> | Przekształcanie danych wejściowych z zaimportowanym modelem ONNX |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel*> | Przekształcanie danych wejściowych z zaimportowanym modelem TensorFlow |

## <a name="custom-transformations"></a>Przekształcenia niestandardowe

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Przekształcanie istniejących kolumn na nowe przy użyciu mapowania zdefiniowanego przez użytkownika |
