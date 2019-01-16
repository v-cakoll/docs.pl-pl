---
title: Przekształcenia danych - strukturze ML.NET uczenia maszynowego
description: Poznaj składniki inżynierów funkcji obsługiwanych w strukturze ML.NET.
author: JRAlexander
ms.custom: seodec18
ms.date: 01/14/2019
ms.openlocfilehash: ebcbcc56eeb7c3caf7350e6c4bfd53997582652e
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307503"
---
# <a name="machine-learning-data-transforms---mlnet"></a>Przekształcenia danych - strukturze ML.NET uczenia maszynowego

Poniższe tabele zawierają informacje na temat wszystkich przekształceń danych obsługiwane w strukturze ML.NET.

> [!NOTE]
> Strukturze ML.NET jest obecnie dostępna w wersji zapoznawczej. Nie wszystkie przekształcenia danych są obecnie obsługiwane. Aby przesłać żądanie dla niektórych transformacji, otwórz problem w [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) repozytorium GitHub.

## <a name="combiners-and-segregators"></a>Combiners i segregators

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | Grupy wartości skalarnej kolumny do wektora na podstawie identyfikatora grupy ciągłych. |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | Kolumny wektor UN-groups na sekwencje odwrotność transformacji grupy wierszy. |

## <a name="conversions"></a>Konwersje 

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | Skróty pojedynczy cenionym kolumn lub vector kolumn. W kolumnach wektor wyznacza wartość skrótu każdego miejsca oddzielnie. Można wyznaczania wartości skrótu wartości tekstowych lub wartości klucza. |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | Konwertuje wiele wartości w kolumnie wartości skrótów. Ta transformacja akceptuje zarówno liczbowe i tekstowe dane wejściowe, zarówno pojedynczych, jak i wartości wektorowych kolumn. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | Konwertuje klucz na kolumnę binarne wektora. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | Korzysta z metadanych KeyValues do mapowania klucza indeksów odpowiednie wartości w metadanych KeyValues. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | Konwertuje klucz na kolumnę wektora. |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | Zmiany podstawowy typ kolumny pod warunkiem, że można przekonwertować typu. |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | Konwertuje wprowadzanie wartości (wyrazy, liczby itp.) do indeksowania w słowniku. |


## <a name="deep-learning"></a>Uczenie głębokie

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Dostarcza dane do istniejącego modelu ONNX i zwraca wynik (Prognozowane). |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Można oceniać za pomocą wstępnie przetrenowane TensorFlow modelu lub ponowne szkolenie modelu TensorFlow. |

## <a name="feature-extraction"></a>Funkcja wyodrębniania

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | Usuwa określony wykaz słowa ignorowane, porównując poszczególne tokeny (porównanie bez uwzględniania wielkości liter) w celu Stop-słowa.| 
| <xref:Microsoft.ML.ImageAnalytics.ImageGrayscaleTransform> | Trwa co najmniej jedną kolumnę ImageType i konwertuje je na odcienie szarości reprezentacja tego samego obrazu.|
| <xref:Microsoft.ML.ImageAnalytics.ImageLoaderTransform> | Trwa co najmniej jedną kolumnę ReadOnlyMemory i ładuje je jako ImageType. |
| <xref:Microsoft.ML.ImageAnalytics.ImagePixelExtractorTransform> | Trwa co najmniej jedną kolumnę ImageType i konwertuje je do reprezentacji wektora.|
| <xref:Microsoft.ML.ImageAnalytics.ImageResizerTransform> | Trwa co najmniej jedną kolumnę ImageType i zmienia rozmiar je do podanej wysokości i szerokości.|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | Implementuje LightLDA, z implementacją z najnowocześniejszych ukrytego Bayesian alokacji.|
| <xref:Microsoft.ML.Transforms.LoadTransform> | Ładuje określone przekształcenia z pliku określonego modelu. Zezwala na przekształcenia "selekcjonowania" z łańcucha serializacji lub zastosowanie wstępnie przeszkolonych transformacji do widoku danych różnych (ale nadal zgodny). |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | Tworzy zbiór liczników ngrams (sekwencji kolejnych wartości o długości 1-n) w przypadku danego wektora kluczy. Robi to, tworząc słownika ngrams i za pomocą identyfikatora w słowniku jako indeks w zbiorze. | 
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | Jest przekształcany kolekcja tekstowych tokenami (wektor ReadOnlyMemory) lub wektorów klucze wektorów liczbowych. Wektory funkcji są liczby ngrams (sekwencji kolejnych tokenów - słowa lub klucze - o długości 1-n). | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | Włącza kolekcji tokenami tekstu (wektor ReadOnlyMemory) do wektorów liczbowych, za pomocą wyznaczania wartości skrótu. | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | Tworzy zbiór liczników ngrams (sekwencji kolejnych wyrazów o długości 1-n) w danego tekstu. | 
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | Konwertuje wartość podzielonych na kategorie na tablicę wskaźnika przez tworzenie słownika kategorie na podstawie danych i za pomocą identyfikatora w słowniku jako indeks w tablicy |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | Oblicza projekcji wektor funkcji na podobszar niski rangi. |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | Używa modelu wstępnie przetrenowane opinii, aby oceniać ciągów wejściowych. |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | Usuwa listy specyficzny dla języka słowa ignorowane (najbardziej popularne wyrazy) porównując Stop-słowa oddzielne tokeny (porównanie bez uwzględniania wielkości liter). |
| <xref:Microsoft.ML.Transforms.Categorical.TermLookupTransformer> | Mapuje kolumn wartości tekstowych na nowe kolumny przy użyciu mapy zestawu danych, dostępne za pośrednictwem jego argumenty. |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | Tworzy zbiór liczników ngrams (sekwencji następujących po sobie słowa) w danego tekstu. Robi to, tworząc słownika ngrams i za pomocą identyfikatora w słowniku jako indeks w zbiorze. |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | Tworzy zbiór liczników ngrams (sekwencji kolejnych wyrazów o długości 1-n) w danego tekstu. Robi to przez tworzenie skrótów każdego ngram i przy użyciu wartości skrótu jako indeks w zbiorze. |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | Dzieli tekst na przy użyciu znaków separatora słów. |


## <a name="image-model-featurizers"></a>Featurizers modelu obrazu

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | Jest to metoda rozszerzenia ma być używany z <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> aby można było używać pretrained [AlexNet](https://en.wikipedia.org/wiki/AlexNet) modelu. NuGet zawierający to rozszerzenie jest gwarantowana dołączenie pliku modelu binarnego. | 
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | Jest to metoda rozszerzenia ma być używany z <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> używania pretrained modelu ResNet18. NuGet zawierający to rozszerzenie jest gwarantowana dołączenie pliku modelu binarnego. |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | Jest to metoda rozszerzenia ma być używany z <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> używać pretrained ResNet50model. NuGet zawierający to rozszerzenie jest gwarantowana dołączenie pliku modelu binarnego. |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | Jest to metoda rozszerzenia ma być używany z <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> używania pretrained modelu ResNet101. NuGet zawierający to rozszerzenie jest gwarantowana dołączenie pliku modelu binarnego. |

## <a name="label-parsing"></a>Etykieta analizy

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  Konwertuje etykiety. |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | Ponownie mapuje wieloklasowej etykiety na binarne wartość True, False etykiet, głównie do użytku z OVA.|

## <a name="missing-values"></a>Brak wartości

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | Brak wartości z kolumn spadnie. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | Tworzy kolumnę dane wyjściowe z taką samą liczbę miejsc, jako kolumna danych wejściowych, których dane wyjściowe ma wartość true, jeśli brak wartości w kolumnie wejściowej. |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | Obsługiwać brakujące wartości, zastępując wartość domyślna lub wartość średnią/min/max (dla tylko kolumny nietekstową). |

## <a name="normalization"></a>Normalizacja

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | Przekształcanie normalizacji LP-Norm (wektor/row-wise). |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | Oblicza średnią i wariancji dla kolumny cenionym wektora. Śledzi bieżącego średnią i M2 (suma kwadratów różnic wartości od średniej), liczba NaNs i liczbę elementów różna od zera. |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | Oblicza średnią i wariancji dla kolumny cenionym wektora. Śledzi bieżącego średnią i M2 (suma kwadratów różnic wartości od średniej), liczba NaNs i liczbę elementów różna od zera. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | Śledzi min, max, liczby wartości rozrzedzonych (vCount) i liczbę wywołań ProcessValue() (trainCount) w kolumnie cenionym wektora. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxSngAggregator> | Śledzi min, max, liczby wartości rozrzedzonych (vCount) i liczbę wywołań ProcessValue() (trainCount) w kolumnie cenionym wektora. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | Standaryzuje zakresów funkcji. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |Standaryzuje zakresów funkcji. |

## <a name="onnx"></a>Onnx

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Wyniki wstępnie szkolone modele ONNX korzystających z ONNX standardowa wersja 1.2 |

## <a name="preprocessing"></a>Przetwarzanie wstępne
| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | Przybliża bootstrap próbkowania przy użyciu metody próbkowania Poissona. |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | Generuje losową Fouriera funkcji. |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Tokenizator zorientowane na znak, jeżeli tekst jest uważany za sekwencji znaków. |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | Optymalizacja Simplfies, aby ułatwić identyfikowanie wagi. |

## <a name="row-filters"></a>Filtry wierszy

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | Przesuwa kursor losowego podjął próbę przy użyciu puli daną liczbę wierszy.  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy przez pominięcie liczbę wierszy. |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy na opcjonalne przesunięcie. Może służyć do implementowania stronicowania danych. Po utworzeniu za pomocą SkipTakeFilter.SkipArguments zachowuje się jak `SkipFilter`.
| <xref:Microsoft.ML.Transforms.TakeFilter> | Umożliwia ograniczenie danych wejściowych do podzestawu wierszy, wykonując N pierwszych wierszy. |


## <a name="schema"></a>Schemat

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | Duplikaty kolumny z zestawu danych.|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | Wybiera zestaw kolumn, aby usunąć lub zachować te dane z danym danych wejściowych. |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | Porzuca miejsc z kolumn.|
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | Tworzy nową kolumnę z określonymi wartościami typu i domyślne. |
| <xref:Microsoft.ML.Transforms.RangeFilter> | Filtrowanie widoku danych dla kolumny typu Single, Double lub klucza (ciągły). Przechowuje wartości, które należą do zakresu określonej minimalnej/maksymalnej. NaNs zawsze są odfiltrowywane. Jeśli dane wejściowe są typu klucza, minimalny/maksymalny są traktowane jako wartości procentowe liczby wartości. |

## <a name="tensorflow"></a>TensorFlow

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Albo wyniki za pomocą wstępnie przetrenowane TensorFlow modelu retrains modelu TensorFlow. |

## <a name="text-processing-and-featurization"></a>Przetwarzanie tekstu i cechowania

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | Transformacja normalizacji tekstu, która umożliwia normalizowanie wielkości liter, usuwając znaki diakrytyczne, znaki interpunkcyjne i/lub cyfry. Transformacja działa na wprowadzanie tekstu, a także wektor tokenów/tekstu (wektor ReadOnlyMemory). |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Tokenizator zorientowane na znak, jeżeli tekst jest uważany za sekwencji znaków. |

## <a name="time-series"></a>Szeregów czasowych

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesProcessing.ExponentialAverageTransform> | Przyjmuje średnią ważoną wartości: ExpAvg(y_t) = a * y_t + (1-a) * ExpAvg(y_(t-1)). |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidChangePointDetector> | Implementuje przekształcenie zmiany punktu wykrywacz dla i.i.d. Sekwencja (losowej próbki) na podstawie adaptacyjne jądra gęstość szacowania i martingales. |
| <xref:Microsoft.ML.TimeSeriesProcessing.IidSpikeDetector> | Implementuje wykrywacz kolekcji przekształcania dla i.i.d. Sekwencja (losowej próbki) oparte na szacowania gęstość adaptacyjne jądra. |
| <xref:Microsoft.ML.TimeSeriesProcessing.MovingAverageTransform> | Zawiera średnią ważoną wartości okna przewijania. |
| <xref:Microsoft.ML.TimeSeriesProcessing.PercentileThresholdTransform> | Określa, czy bieżąca wartość szeregów czasowych należy do przewijania percentyl największe wartości okna. |
| <xref:Microsoft.ML.TimeSeriesProcessing.PValueTransform> | Oblicza serię, bieżąca wartość empirycznej p wartość na podstawie innych wartości w ramach przesuwającego się okna. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SlidingWindowTransform> | Generuje przesuwającego się okna w szeregu czasowym typu Single. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaChangePointDetector> | Implementuje przekształcenia wykrywanie zmiany punktu oparte na pojedynczej o szerokim zakresie funkcji modelowania w szeregu czasowym. |
| <xref:Microsoft.ML.TimeSeriesProcessing.SsaSpikeDetector> | Implementuje przekształcenie wykrywacz kolekcji oparte na pojedynczej o szerokim zakresie funkcji modelowania w szeregu czasowym. |

## <a name="miscellaneous"></a>Różne

| Transformacja | Definicja |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | Tworzy DataTransform złożonego. |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | Generuje dodatkowe kolumny podanego `IDataView`. Go nie zmieniają się liczba wierszy, są widoczne w wyniku aplikacji przez użytkownika funkcji do każdego wiersza danych wejściowych.|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | Dodaje kolumnę o wygenerowanego numeru sekwencji. |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | Tworzy kolumny o identyfikatorze kursora w kolumnie. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Generuje losową liczbę. |
| <xref:Microsoft.ML.Transforms.ScoringTransformer> | Łączy informacje z wielu modeli predykcyjnych, aby wygenerować nowy model w potoku za pomocą wyniki z już uczonego modelu. |
