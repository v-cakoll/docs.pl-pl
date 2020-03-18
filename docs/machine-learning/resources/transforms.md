---
title: Przekształcenia danych
description: Zapoznaj się z komponentami inżynierii funkcji obsługiwanymi w ML.NET.
ms.date: 04/02/2019
ms.openlocfilehash: ca410b475c556db5ad4c3862fb79755b455d6830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398924"
---
# <a name="data-transformations"></a>Przekształcenia danych

Przekształcenia danych są używane do:

- przygotowanie danych do szkolenia modelowego
- stosowanie importowanego modelu w formacie TensorFlow lub ONNX
- dane po zakończeniu procesu po przejściu przez model

Przekształcenia w tym przewodniku zwracają klasy implementują interfejs [IEstimator.](xref:Microsoft.ML.IEstimator%601) Przekształcenia danych mogą być ze sobą połączone. Każda transformacja oczekuje i generuje dane określonych typów i formatów, które są określone w połączonej dokumentacji referencyjnej.

Niektóre przekształcenia danych wymagają danych szkoleniowych do obliczania ich parametrów. Na przykład: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformator oblicza średnią i wariancję danych `Fit()` szkoleniowych podczas operacji i `Transform()` używa tych parametrów w operacji.

Inne przekształcenia danych nie wymagają danych szkoleniowych. Na przykład: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> transformacja `Transform()` może wykonać operację bez `Fit()` ujmuje żadnych danych szkoleniowych podczas operacji.

## <a name="column-mapping-and-grouping"></a>Mapowanie kolumn i grupowanie

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Łączenie jednej lub większej liczby kolumn wejściowych w nową kolumnę danych wyjściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Kopiowanie i zmienianie nazwy jednej lub większej liczby kolumn wejściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Upuść jedną lub więcej kolumn wejściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Wybierz jedną lub więcej kolumn, aby zachować z danych wejściowych |

## <a name="normalization-and-scaling"></a>Normalizacja i skalowanie

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odejmij średnią (danych szkoleniowych) i podziel przez wariancję (danych szkoleniowych) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizacja na podstawie logarytmu danych szkoleniowych |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Skaluj wektory wejściowe według ich [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), gdzie p wynosi 1, 2 lub nieskończoność. Domyślnie norma l2 (odległość euklidesowa) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Skaluj każdą wartość w wierszu, odejmując średnią danych wiersza i dziel przez odchylenie standardowe lub normę l2 (danych wiersza) i mnożyć przez konfigurowalny współczynnik skali (domyślnie 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Przypisz wartość wejściową do indeksu pojemnika i podziel przez liczbę pojemników, aby wygenerować wartość zmiennoprzecinkową z wartością od 0 do 1. Granice pojemnika są obliczane w celu równomiernego rozdzielenia danych szkoleniowych między pojemnikami |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Przypisywanie wartości wejściowej do pojemnika na podstawie jego korelacji z kolumną etykiety |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Skaluj dane wejściowe według różnicy między wartościami minimalnymi i maksymalnymi w danych szkoleniowych |

## <a name="conversions-between-data-types"></a>Konwersje między typami danych

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Konwertowanie typu kolumny wejściowej na nowy typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Mapowanie wartości na klucze (kategorie) na podstawie dostarczonego słownika mapowań |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Mapowanie wartości na klucze (kategorie), tworząc mapowanie na podstawie danych wejściowych |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Konwertowanie kluczy z powrotem na ich oryginalne wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Konwertowanie kluczy z powrotem na wektory oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Konwertowanie kluczy z powrotem na wektor binarny oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Haszuje wartość w kolumnie wejściowej |

## <a name="text-transformations"></a>Przekształcenia tekstu

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Przekształcanie kolumny tekstowej w tablicę float znormalizowanych ngramów i liczby znaków gramów |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Dzielenie jednej lub większej liczby kolumn tekstowych na pojedyncze wyrazy |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Dzielenie jednej lub większej liczby kolumn tekstowych na pojedyncze znaki unosi się nad zestawem tematów |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Zmienianie sprawy, usuwanie znaków diakrytycznych, znaków interpunkcyjnych i liczb |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Przekształcanie kolumny tekstowej w worek z limizami ngramów (sekwencje kolejnych słów)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Przekształcanie kolumny tekstowej w worek zliczeń wektora ngramów |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Przekształcanie kolumny tekstowej w wektor zliczanych ngramów zahaszowych |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Przekształć kolumnę tekstową w torbę z haszyszowe ngram liczy |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Usuwanie domyślnych słów zatrzymania dla określonego języka z kolumn wejściowych |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Usuwa określone słowa zatrzymania z kolumn wejściowych |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Przekształcanie dokumentu (reprezentowanego jako wektor pływaków) we wektoru pływaków nad zestawem tematów |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Konwertowanie wektorów tokenów tekstowych na wektory zdań przy użyciu wstępnie przeszkolonego modelu |

## <a name="image-transformations"></a>Przekształcenia obrazu

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Konwertowanie obrazu na skalę szarości |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Konwertowanie wektora pikseli na<xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Konwertowanie pikseli z obrazu wejściowego na wektor liczb |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Ładowanie obrazów z folderu do pamięci |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Zmienianie rozmiaru obrazów |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Stosuje wstępnie przeszkolony model głębokiej sieci neuronowej (DNN), aby przekształcić obraz wejściowy we wkładzie |

## <a name="categorical-data-transformations"></a>Kategoryczne przekształcenia danych

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Konwertowanie jednej lub większej liczby kolumn tekstowych na wektory zakodowane na [jednym gorącym](https://en.wikipedia.org/wiki/One-hot) |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Konwertowanie jednej lub większej liczby kolumn tekstowych na wektory zakodowane za kodowane za pomocą skrótu oparte na jednym nachyleniu |

## <a name="time-series-data-transformations"></a>Przekształcenia danych szeregów czasowych

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Wykrywanie anomalii w danych wejściowych szeregów czasowych przy użyciu algorytmu Spektral rezydualne (SR) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Wykrywanie punktów zmian w danych szeregów czasowych za pomocą analizy widma pojedynczego (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Wykrywanie punktów zmian w niezależnych i identycznie rozproszonych (IID) danych szeregów czasowych przy użyciu adaptacyjnych oszacowań gęstości jądra i wyników martingale |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Prognozowane dane szeregów czasowych przy użyciu analizy widma pojedynczego (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Wykrywanie skoków w danych szeregów czasowych za pomocą analizy widma pojedynczego (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Wykrywanie skoków w niezależnych i identycznie rozproszonych (IID) danych szeregów czasowych przy użyciu adaptacyjnych oszacowań gęstości jądra i wyników martingale |

## <a name="missing-values"></a>Brakujące wartości

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Utwórz nową kolumnę danych wyjściowych, której wartość jest true, gdy brakuje wartości w kolumnie wejściowej |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Utwórz nową kolumnę wyjściową, której wartość jest ustawiona na wartość domyślną, jeśli brakuje wartości w kolumnie wejściowej, a wartość wejściowa w przeciwnym razie |

## <a name="feature-selection"></a>Wybieranie funkcji

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Wybierz obiekty, których wartości niedomyślne są większe niż próg |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Wybierz operacje, od których dane w kolumnie etykiety są najbardziej zależne |

## <a name="feature-transformations"></a>Przekształcenia funkcji

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Mapowanie każdego wektora wejściowego na niższą przestrzeń obiektową, gdzie produkty wewnętrzne przybliżają funkcję jądra, tak aby obiekty mogły być używane jako wejścia do algorytmów liniowych |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Zmniejsz wymiary wektora operacji wejściowej, stosując algorytm analizy komponentu głównego |

## <a name="explainability-transformations"></a>Transformacje wyjaśniające

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Obliczanie wyników wkładu dla każdego elementu wektora operacji |

## <a name="calibration-transformations"></a>Przekształcenia kalibracji

| Przekształcanie | Definicja |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Przekształca nieprzetworzony wynik klasyfikatora binarnego w prawdopodobieństwo klasy przy użyciu regresji logistycznej z parametrami szacowanymi przy użyciu danych szkoleniowych |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Przekształca nieprzetworzony wynik klasy binarnego w prawdopodobieństwo klasy przy użyciu regresji logistycznej ze stałymi parametrami |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | Przekształca nieprzetworzony wynik klasyfikatora binarnego w prawdopodobieństwo klasy, przypisując wyniki do pojemników i obliczając prawdopodobieństwo na podstawie rozkładu między pojemniki |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | Przekształca nieprzetworzony wynik klasyfikatora binarnego w prawdopodobieństwo klasy, przypisując wyniki do pojemników, gdzie położenie granic i rozmiar pojemników są szacowane przy użyciu danych szkoleniowych  |

## <a name="deep-learning-transformations"></a>Transformacje uczenia głębokiego

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | Przekształcanie danych wejściowych za pomocą importowanego modelu ONNX |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | Przekształcanie danych wejściowych za pomocą importowanego modelu TensorFlow |

## <a name="custom-transformations"></a>Przekształcenia niestandardowe

| Przekształcanie | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Przekształcanie istniejących kolumn na nowe za pomocą mapowania zdefiniowanego przez użytkownika |
