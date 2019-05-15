---
title: Przekształcenia danych
description: Poznaj składniki inżynierów funkcji obsługiwanych w strukturze ML.NET.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 7ea06e19b4651017079a6ae57136f033e0ce981c
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65558016"
---
# <a name="data-transformations"></a>Przekształcenia danych

Przekształcenia danych są używane do przygotowywania danych do trenowania modelu. Przekształcenia w tym przewodniku zwracają klasy, które implementują [IEstimator](xref:Microsoft.ML.IEstimator%601) interfejsu. Przekształcenia danych można łączyć w łańcuch. Każde przekształcenie oczekuje i generuje dane w określonych typach i formatach, które są określone w dokumentacji referencyjnej połączone.

Przekształcenia niektórych danych wymagają danych szkoleniowych do obliczania swoich parametrów. Na przykład: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformatora oblicza średnią i Wariancja dane szkoleniowe podczas `Fit()` operacji i używa tych parametrów w `Transform()` operacji. 

Inne przekształcenia danych nie wymagają dane szkoleniowe. Na przykład: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> wykonywać przekształcenia `Transform()` operacji bez konieczności widoczne wszystkie dane szkoleniowe podczas `Fit()` operacji.

## <a name="column-mapping-and-grouping"></a>Mapowania kolumn i grupowania

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Łączenie z co najmniej jedną kolumnę danych wejściowych w nową kolumnę danych wyjściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Kopiuj i Zmień nazwę jednej lub kilku kolumn wejściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Upuść co najmniej jedną kolumnę danych wejściowych |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Wybierz co najmniej jedną kolumnę, aby zachować dane wejściowe |

## <a name="normalization-and-scaling"></a>Normalizacja i skalowanie

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Odejmij wartość średnia (dane szkoleniowe) i dzielnikiem wariancję (dane szkoleniowe) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normalizuj w oparciu o logarytmu dane szkoleniowe |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Skalowanie wejściowe wektorów przez ich [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), gdzie p wynosi 1, 2 lub nieskończoność. Wartość domyślna to norm (odległość euklidesowa) pamięci podręcznej l2 |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Skalowanie każdej wartości w wierszu przez odjęcie średnią danych wiersza i dzielenie przez odchylenie standardowe lub l2 — normy (wiersz danych) i pomnożyć przez współczynnik skali można konfigurować (wartość domyślna 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Przypisz wartość wejściowa do indeksu bin i dzielnikiem liczba pojemników, aby wygenerować wartością zmiennoprzecinkową z zakresu od 0 do 1. Granice bin są obliczane w celu równomiernego rozkładania danych szkoleniowych przez pojemników |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Przypisz wartość wejściowa do pojemnika, w oparciu o jego korelacji z etykiet kolumn |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Możesz zmieniać skalę danych wejściowych, różnicy między minimalną i maksymalną wartość w danych szkoleniowych |

## <a name="conversions-between-data-types"></a>Konwersje między typami danych

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Konwertuj typ kolumny wejściowej na nowy typ |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Mapuj wartości do kluczy (kategorie) w oparciu o podane słownik mapowań |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Mapuj wartości do kluczy (kategorie), tworząc mapowania w danych wejściowych |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Konwertuj klucze do ich oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Przekonwertować klucze wektorów oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Przekonwertować klucze binarny wektor oryginalnych wartości |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Wartość w kolumnie wejściowej skrótu |

## <a name="text-transformations"></a>Przekształcenia tekstu

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Przekształć kolumny tekstowej w tablica liczb zmiennoprzecinkowych, znormalizowana ngrams i liczby gramów char | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Podziel tekst kolumny na poszczególnych wyrazów |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Podzielić co najmniej jeden kolumny tekstowe na wartości zmiennoprzecinkowe pojedynczych znaków w zestawie tematów |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Zmień wielkość liter, usuń znaki diakrytyczne, znaki interpunkcyjne i liczb |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Przekształć kolumny tekstowej w zbioru liczników ngrams (sekwencjami słów, kolejne)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Przekształć kolumny tekstowej w zbioru liczników ngrams wektora |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Przekształć kolumny tekstowej w wektorem liczb ngram skrótu |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Przekształć kolumny tekstowej w zbioru liczników ngram skrótu |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Usuń domyślne słowa ignorowane dla określonego języka z kolumny wejściowe |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Usuwa określone słowa ignorowane z kolumny wejściowe |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | Przekształcanie wektor wartości zmiennoprzecinkowe dokumentu (reprezentowana jako wektor wartości zmiennoprzecinkowe) w zestawie tematów |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Konwertowanie wektorów tokenów tekst na wektorów zdania przy użyciu wstępnie przeszkolonych modelu |

## <a name="image-transformations"></a>Przekształcenia obrazu

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Konwertowanie obrazu na skalę odcieni szarości |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Konwertuj wektor pikseli <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Konwertowanie z obrazu wejściowego wektorem liczb pikseli |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Ładuj obrazy z folderu do pamięci |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Zmiana rozmiaru obrazów |

## <a name="categorical-data-transformations"></a>Przekształcenia danych podzielonych na kategorie

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Konwertuj jeden lub więcej kolumn tekstowych do [hot jeden](https://en.wikipedia.org/wiki/One-hot) zakodowane wektorów |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Konwertuj jeden więcej kolumn tekstowych na bazujących na skrótach hot jeden zakodowany wektorów |

## <a name="missing-values"></a>Brak wartości

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Utwórz nową kolumnę dane wyjściowe, których wartość ma wartość true, jeśli brakuje wartości w kolumnie wejściowej |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | W przeciwnym razie utwórz nową kolumnę danych wyjściowych, którego wartość jest równa wartości domyślnej, jeśli brak wartości z kolumny wejściowej, a wartość wejściowa |

## <a name="feature-selection"></a>Wybieranie funkcji

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Wybierz funkcje, których wartości innych niż domyślne są większe niż próg |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Wybierz funkcje, od których zależy od najbardziej dane w kolumnie etykiety |

## <a name="custom-transformations"></a>Niestandardowe przekształcenia

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Przekształcanie istniejących kolumn na Zdobywaj wiedzę dzięki mapowanie zdefiniowane przez użytkownika |
