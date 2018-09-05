---
title: Przekształcenia danych
description: Eksploruj obsługiwane w strukturze ML.NET przekształcenia danych.
ms.date: 08/08/2018
author: jralexander
ms.author: johalex
ms.openlocfilehash: 3c483f4a263052eb15435775a47f514893eee049
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519398"
---
# <a name="data-transforms"></a>Przekształcenia danych

Poniższe tabele zawierają informacje na temat wszystkich przekształceń danych obsługiwane w strukturze ML.NET (Wybierz dane, przekształcenie typu, aby przejść do odpowiedniej tabeli):

* [Podzielone na kategorie](#categorical)
* [Combiners i segregators](#combiners-and-segregators)
* [Wybieranie funkcji](#feature-selection)
* [Featurizers](#featurizers)
* [Etykieta analizy](#label-parsing)
* [Brak wartości](#missing-values)
* [Normalizacja](#normalization)
* [Filtry wierszy](#row-filters)
* [Schemat](#schema)
* [Przetwarzanie tekstu i cechowania](#text-processing-and-featurization)
* [Różne](#miscellaneous)

> [!NOTE]
> Strukturze ML.NET jest obecnie dostępna w wersji zapoznawczej. Nie wszystkie przekształcenia danych są obecnie obsługiwane. Aby przesłać żądanie dla niektórych transformacji, otwórz problem w [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) repozytorium GitHub.

## <a name="categorical"></a>Podzielone na kategorie

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CategoricalHashOneHotVectorizer> | Koduje podzielonych na kategorie zmiennej z kodowaniem bazujących na skrótach. |
| <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer> | Koduje podzielonych na kategorie zmiennej z kodowaniem hot jeden, oparte na słownik terminów. |

## <a name="combiners-and-segregators"></a>Combiners i segregators

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CombinerByContiguousGroupId> | Grupy wartości skalarnej kolumny do wektora na podstawie identyfikatora grupy ciągłych. |
| <xref:Microsoft.ML.Transforms.FeatureCombiner> | Łączy wszystkie funkcje w jedną funkcję kolumny. |
| <xref:Microsoft.ML.Transforms.ManyHeterogeneousModelCombiner> | Łączy sekwencja TransformModels i PredictorModel do pojedynczego PredictorModel. |
| <xref:Microsoft.ML.Transforms.ModelCombiner> | Łączy ze sobą ciąg TransformModels w jednym modelu. |
| <xref:Microsoft.ML.Transforms.Segregator> | Rozgrupowuje wektor kolumn na sekwencje wierszy; odwrotność Przekształcanie grupy. |
| <xref:Microsoft.ML.Transforms.TwoHeterogeneousModelCombiner> | Łączy TransformModel i PredictorModel w jednym PredictorModel. |

## <a name="feature-selection"></a>Wybieranie funkcji

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByCount> | Wybiera miejsc, w których liczbę wartości innych niż domyślne jest większa lub równa wartości progowej. |
| <xref:Microsoft.ML.Transforms.FeatureSelectorByMutualInformation> | Wybiera miejsc top k we wszystkich określonych kolumn uporządkowane według ich wzajemne informacji z kolumną etykiety. |

## <a name="featurizers"></a>Featurizers

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.HashConverter> | Konwertuje wartości w kolumnie wartości skrótów. Ta transformacja akceptuje zarówno liczbowe i tekstowe dane wejściowe, zarówno pojedynczych, jak i wartości wektorowych kolumn. |
| <xref:Microsoft.ML.Transforms.TreeLeafFeaturizer> | Szkolenie modeli zespołu drzewa lub ładuje go z pliku, a następnie mapuje wektor funkcji numerycznych do trzech danych wyjściowych: 1. Wektor zawierający poszczególne drzewa wyników zespołu drzewa. 2. Wektor, wskazując pozostawia, które wektor funkcji znajduje się w zespole drzewa. 3. Wektor, wskazując ścieżek, które wektor funkcji znajduje się w zespole drzewa. Jeśli określono zarówno w plikach modelu, jak i trainer wektora użyje pliku modelu. Jeśli nie podano wektora będzie wytrenuj model FastTree domyślne. Aby obsługiwać klucza etykiety, to uczenia modelu regresji kierunku ich opcjonalnie cieniowania indeksów. |

## <a name="label-parsing"></a>Etykieta analizy

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Dictionarizer> | Konwertuje wprowadzanie wartości (wyrazy, liczby itp.) do indeksowania w słowniku. |
| <xref:Microsoft.ML.Transforms.LabelColumnKeyBooleanConverter> | Przekształca etykietę do klucza lub wartość logiczna (jeśli jest to konieczne), zapewnienie odpowiedniej klasyfikacji. |
| <xref:Microsoft.ML.Transforms.LabelIndicator> | Używane przez OVA remapper etykiety. |
| <xref:Microsoft.ML.Transforms.LabelToFloatConverter> | Przekształca etykiety na typ zmiennoprzecinkowy, zapewnienie odpowiedniej dla regresji. |
| <xref:Microsoft.ML.Transforms.PredictedLabelColumnOriginalValueConverter> | Przekształca kolumny przewidywane etykiety do ich oryginalnych wartości, chyba że jest on typu wartość logiczna. |

## <a name="missing-values"></a>Brak wartości

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueHandler> | Obsługiwać brakujące wartości, zastępując wartość domyślna lub wartość średnią/min/max (dla tylko kolumny nietekstową). Opcjonalnie można połączyć kolumną wskaźnik, jeśli typ kolumny wejściowej jest wartością liczbową. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicator> | Utwórz kolumnę dane wyjściowe z taką samą liczbę miejsc, jako kolumna danych wejściowych, których dane wyjściowe ma wartość true, jeśli brak wartości w kolumnie wejściowej. |
| <xref:Microsoft.ML.Transforms.MissingValuesDropper> | Usuwa NAs z kolumny wektora. |
| <xref:Microsoft.ML.Transforms.MissingValuesRowDropper> | Filtry na poziomie wierszy, które zawierają brakujące wartości. |
| <xref:Microsoft.ML.Transforms.MissingValueSubstitutor> | Utwórz kolumnę wyjściową tego samego typu i rozmiaru kolumny wejściowej, w którym brakuje wartości są zastępowane wartość domyślna lub wartość średnią/min/max (dla tylko kolumny nietekstową). |

## <a name="normalization"></a>Normalizacja

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BinNormalizer> | Wartości są przypisywane do pojemniki equidensity i wartość jest mapowany do jego bin_number / number_of_bins. |
| <xref:Microsoft.ML.Transforms.ConditionalNormalizer> | Normalizuj kolumn, tylko, jeśli jest to konieczne. |
| <xref:Microsoft.ML.Transforms.GlobalContrastNormalizer> | Wykonuje normalizacji kontrast globalne wartości wejściowe: Y = (s * X - min) / D, których s skalowania, M to średnia i D-L2 norm lub odchylenia standardowego. | 
| <xref:Microsoft.ML.Transforms.LogMeanVarianceNormalizer> | Normalizuje danych na podstawie obliczona średnia i Wariancja logarytmu danych. |
| <xref:Microsoft.ML.Transforms.LpNormalizer> | Normalizuj wektorów (wiersze) indywidualnie przez podczas ponownego skalowania ich do normy jednostki (L2, L1 lub LInf). Wykonuje następujące operacje na wektor X: Y = (X - min) / D, gdzie M to średnia i D to L2 norm, L1 norm lub LInf norm. |
| <xref:Microsoft.ML.Transforms.MeanVarianceNormalizer> | Normalizuje danych na podstawie obliczona średnia i wariancja danych. |
| <xref:Microsoft.ML.Transforms.MinMaxNormalizer> | Normalizuje danych na podstawie obserwacji minimalne i maksymalne wartości danych. |
| <xref:Microsoft.ML.Transforms.SupervisedBinNormalizer> | Podobnie jak <xref:Microsoft.ML.Transforms.BinNormalizer>, ale oblicza pojemników, w oparciu o korelacji z kolumną etykiety, nie equidensity. Nowa wartość jest bin_number / number_of_bins. |

## <a name="row-filters"></a>Filtry wierszy

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowRangeFilter> | Filtrowanie widoku danych dla kolumny typu Single, Double lub klucza (ciągły). Przechowuje wartości, które należą do zakresu określonej minimalnej/maksymalnej. NaNs zawsze są odfiltrowywane. Jeśli dane wejściowe są typu klucza, minimalny/maksymalny są traktowane jako wartości procentowe liczby wartości. |
| <xref:Microsoft.ML.Transforms.RowSkipAndTakeFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy na opcjonalne przesunięcie. Może służyć do implementowania stronicowania danych. |
| <xref:Microsoft.ML.Transforms.RowSkipFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy przez pominięcie liczbę wierszy. |
| <xref:Microsoft.ML.Transforms.RowTakeFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy, wykonując N pierwszych wierszy. |

## <a name="schema"></a>Schemat

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnConcatenator> | Łączy dwie kolumny tego samego typu elementu. |
| <xref:Microsoft.ML.Transforms.ColumnCopier> | Duplikaty kolumny z zestawu danych.|
| <xref:Microsoft.ML.Transforms.ColumnDropper> | Porzuca kolumn z zestawu danych. |
| <xref:Microsoft.ML.Transforms.ColumnSelector> | Wybiera zestaw kolumn i usunięcie wszystkich innych. |
| <xref:Microsoft.ML.Transforms.ColumnTypeConverter> | Konwertuje kolumny do innego typu, przy użyciu standardowych konwersji. |
| <xref:Microsoft.ML.Transforms.KeyToTextConverter> | KeyToValueTransform korzysta z metadanych KeyValues do mapowania klucza indeksów odpowiednie wartości w metadanych KeyValues. |
| <xref:Microsoft.ML.Transforms.NGramTranslator> | Tworzy zbiór liczników ngrams (sekwencji kolejnych wartości o długości 1-n) w przypadku danego wektora kluczy. Robi to, tworząc słownika ngrams i za pomocą identyfikatora w słowniku jako indeks w zbiorze. | 
| <xref:Microsoft.ML.Transforms.OptionalColumnCreator> | Jeśli kolumna źródłowa nie istnieje po deserializacji, Utwórz kolumnę z prawej typu i domyślne wartości. |

## <a name="text-processing-and-featurization"></a>Przetwarzanie tekstu i cechowania

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CharacterTokenizer> | Tokenizator zorientowane na znak, jeżeli tekst jest uważany za sekwencji znaków. |
| <xref:Microsoft.ML.Transforms.TextFeaturizer> | Przekształcenia Włącza kolekcję dokumenty tekstowe do wektorów liczbowych. Wektory funkcji są znormalizowane liczby ngrams (program word i/lub znak) w danym tokenami tekstu. |
| <xref:Microsoft.ML.Transforms.TextToKeyConverter> | Konwertuje wprowadzanie wartości (wyrazy, liczby itp.) do indeksowania w słowniku. |
| <xref:Microsoft.ML.Transforms.WordEmbeddings> | Przekształcenia konwertuje wektorów tokenów tekst na liczbowe wektorów przy użyciu wstępnie przeszkolonych modelu. Aby uzyskać więcej informacji na temat technika, zobacz [osadzania Word](https://en.wikipedia.org/wiki/Word_embedding) strony Wikipedii. |
| <xref:Microsoft.ML.Transforms.WordTokenizer> | Dane wejściowe tej transformacji jest tekst, a wynik jest wektorem tekstu zawierające słowa (tokeny) w oryginalny tekst. Separator jest miejsce, ale można określić inny znak (lub wielu znaków). |

## <a name="miscellaneous"></a>Różne

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ApproximateBootstrapSampler> | Określenie w przybliżeniu ładowania początkowego pobierania próbek. |
| <xref:Microsoft.ML.Transforms.BinaryPredictionScoreColumnsRenamer> | Do przewidywania binarne zmienia nazwę PredictedLabel oraz wynik kolumn, aby zawierał on nazwę klasy dodatnią.|
| <xref:Microsoft.ML.Transforms.DataCache> | Zapisuje w pamięci podręcznej przy użyciu opcji określonego pamięci podręcznej. |
| <xref:Microsoft.ML.Transforms.DatasetScorer> | Ocenia zestawu danych z modeli predykcyjnych. |
| <xref:Microsoft.ML.Transforms.DatasetTransformScorer> | Ocenia zestawu danych za pomocą modelu transformacji. |
| <xref:Microsoft.ML.Transforms.NoOperation> | Nic nie robi. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Dodaje kolumnę o wygenerowanego numeru sekwencji. |
| <xref:Microsoft.ML.Transforms.ScoreColumnSelector> | Wybiera tylko ostatnia ocena kolumny i dodatkowe kolumny określone w argumenty. |
| <xref:Microsoft.ML.Transforms.Scorer> | Włącza modeli predykcyjnych w transformacji model analizy biznesowej. |
| <xref:Microsoft.ML.Transforms.SentimentAnalyzer> | Używa modelu wstępnie przetrenowane opinii, aby oceniać ciągów wejściowych. |
| <xref:Microsoft.ML.Transforms.TrainTestDatasetSplitter> | Dzieli dane ustawia zestaw danych na szkolenie i testowanie. |
