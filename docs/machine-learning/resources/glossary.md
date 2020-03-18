---
title: Glosariusz uczenia maszynowego
description: Słowniczek ważnych terminów uczenia maszynowego, które są przydatne podczas tworzenia modeli niestandardowych w ML.NET.
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 32ccb6df1cb08db45ebd25a0d1c0ea4396a6c50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398938"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Słowniczek uczenia maszynowego o ważnych terminach

Poniższa lista jest kompilacją ważnych terminów uczenia maszynowego, które są przydatne podczas tworzenia modeli niestandardowych w ML.NET.

## <a name="accuracy"></a>Dokładność

W [klasyfikacji](#classification)dokładność jest liczbą prawidłowo sklasyfikowanych pozycji podzieloną przez całkowitą liczbę pozycji w zestawie testowym. Zakresy od 0 (najmniej dokładne) do 1 (najdokładniejsze). Dokładność jest jedną z metryk oceny wydajności modelu. Rozważmy to w połączeniu z [precyzją,](#precision) [wycofaniem](#recall)i [f-score.](#f-score)

## <a name="area-under-the-curve-auc"></a>Obszar pod krzywą (AUC)

W [klasyfikacji binarnej](#binary-classification)metryka oceny, która jest wartością obszaru pod krzywą, która wykreśla współczynnik dodatnich wartości true (na osi y) względem szybkości fałszywych alarmów (na osi x). Waha się od 0,5 (najgorszy) do 1 (najlepszy). Znany również jako obszar pod krzywą ROC, czyli krzywa charakterystyki działania odbiornika. Aby uzyskać więcej informacji, zobacz program [Charakterystyka obsługi odbiornika](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) na Wikipedii.

## <a name="binary-classification"></a>Klasyfikacja binarna

Przypadek [klasyfikacji,](#classification) w którym [etykieta](#label) jest tylko jedną z dwóch klas. Aby uzyskać więcej informacji, zobacz [klasyfikacja binarna](tasks.md#binary-classification) sekcji [zadania uczenia maszynowego](tasks.md) tematu.

## <a name="calibration"></a>Kalibracja

Kalibracja to proces mapowania nieprzetworzonego wyniku na członkostwo w klasie dla klasyfikacji binarnej i wieloklasowej. Niektórzy ML.NET trenerzy mają `NonCalibrated` przyrostek. Algorytmy te dają nieprzetworzony wynik, który następnie musi być mapowany na prawdopodobieństwo klasy.

## <a name="catalog"></a>Wykaz

W ML.NET katalog jest kolekcją funkcji rozszerzenia, pogrupowanych według wspólnego celu.

Na przykład każde zadanie uczenia maszynowego (klasyfikacja binarna, regresja, ranking itp.) ma katalog dostępnych algorytmów uczenia maszynowego (trenerów). Katalog dla trenerów klasyfikacji <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>binarnej to: .

## <a name="classification"></a>Klasyfikacja

Gdy dane są używane do przewidywania kategorii, nadzorowane zadanie [uczenia maszynowego](#supervised-machine-learning) jest nazywane klasyfikacją. [Klasyfikacja binarna](#binary-classification) odnosi się do przewidywania tylko dwóch kategorii (na przykład klasyfikacji obrazu jako obrazu "kota" lub "psa"). [Klasyfikacja wieloklasowa](#multiclass-classification) odnosi się do przewidywania wielu kategorii (na przykład podczas klasyfikowania obrazu jako obrazu określonej rasy psa).

## <a name="coefficient-of-determination"></a>Współczynnik oznaczalności

W [regresji](#regression), metryki oceny, która wskazuje, jak dobrze dane pasuje do modelu. Waha się od 0 do 1. Wartość 0 oznacza, że dane są losowe lub w inny sposób nie mogą być dostosowane do modelu. Wartość 1 oznacza, że model dokładnie pasuje do danych. Jest to często określane jako r<sup>2</sup>, R<sup>2</sup>, lub r-kwadrat.

## <a name="data"></a>Dane

Dane mają kluczowe znaczenie dla każdej aplikacji do uczenia maszynowego. W ML.NET dane są <xref:Microsoft.ML.IDataView> reprezentowane przez obiekty. Obiekty widoku danych:

- składa się z kolumn i wierszy
- są leniwie oceniane, to oznacza, że ładują dane tylko wtedy, gdy operacja
- zawierają schemat definiujący typ, format i długość każdej kolumny

## <a name="estimator"></a>Estymator

Klasa w ML.NET, która <xref:Microsoft.ML.IEstimator%601> implementuje interfejs.

Estymator jest specyfikacją transformacji (zarówno transformacja przygotowania danych, jak i transformacja uczenia uczenia maszynowego). Estymatory mogą być połączone ze sobą w potok przekształceń. Parametry estymatora lub potoku estymatorów są wyujane, gdy <xref:Microsoft.ML.IEstimator%601.Fit%2A> jest wywoływana. Wynikiem <xref:Microsoft.ML.IEstimator%601.Fit%2A> jest [Transformer](#transformer).

## <a name="extension-method"></a>Metoda rozszerzenia

Metoda .NET, która jest częścią klasy, ale jest zdefiniowana poza klasą. Pierwszy parametr metody rozszerzenia jest `this` statyczne odwołanie do klasy, do której należy metoda rozszerzenia.

Metody rozszerzenia są szeroko stosowane w ML.NET do konstruowania wystąpień [estymatorów](#estimator).

## <a name="feature"></a>Funkcja

Mierzalną właściwość mierzonego zjawiska, zazwyczaj wartość liczbową (podwójną). Wiele obiektów jest określanych jako **wektor funkcji** i zazwyczaj przechowywanych jako `double[]`. Cechy określają ważne cechy mierzonego zjawiska. Aby uzyskać więcej informacji, zobacz [artykuł funkcji](https://en.wikipedia.org/wiki/Feature_(machine_learning)) na Wikipedii.

## <a name="feature-engineering"></a>Inżynieria funkcji

Inżynieria funkcji to proces, który polega na zdefiniowaniu zestawu [funkcji](#feature) i opracowaniu oprogramowania, które tworzy wektory funkcji z dostępnych danych o zjawiskach, czyli ekstrakcji funkcji. Aby uzyskać więcej informacji, zobacz artykuł [inżynierii funkcji](https://en.wikipedia.org/wiki/Feature_engineering) na Wikipedii.

## <a name="f-score"></a>Wynik F

W [klasyfikacji](#classification), metryka oceny, która równoważy [precyzję](#precision) i [wycofanie](#recall).

## <a name="hyperparameter"></a>Hiperparametr

Parametr algorytmu uczenia maszynowego. Przykłady obejmują liczbę drzew do nauki w lesie decyzyjnym lub rozmiar kroku w algorytmie zejścia gradientu. Wartości *hiperparametrów* są ustawiane przed szkoleniem modelu i regulują proces znajdowania parametrów funkcji przewidywania, na przykład punktów porównania w drzewie decyzji lub wag w modelu regresji liniowej. Aby uzyskać więcej informacji, zobacz artykuł [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) na Wikipedii.

## <a name="label"></a>Label

Element, który ma być przewidywany za pomocą modelu uczenia maszynowego. Na przykład, rasa psa lub przyszłej ceny akcji.

## <a name="log-loss"></a>Utrata dziennika

W [klasyfikacji](#classification), metryki oceny, który charakteryzuje dokładność klasyfikatora. Mniejsza strata dziennika jest, tym dokładniejszy jest klasyfikator.

## <a name="loss-function"></a>Utrata, funkcja

Funkcja utraty jest różnica między wartości etykiety szkolenia i przewidywania dokonane przez model. Parametry modelu są szacowane przez zminimalizowanie funkcji strat.

Różnych trenerów można skonfigurować z różnych funkcji utraty.

## <a name="mean-absolute-error-mae"></a>Średni błąd bezwzględny (MAE)

W [regresji](#regression), metryki oceny, która jest średnia wszystkich błędów modelu, gdzie błąd modelu jest odległość między przewidywaną [wartością etykiety](#label) i poprawną wartość etykiety.

## <a name="model"></a>Model

Tradycyjnie parametry funkcji przewidywania. Na przykład wagi w modelu regresji liniowej lub punktów podziału w drzewie decyzji. W ML.NET model zawiera wszystkie informacje niezbędne do przewidywania [etykiety](#label) obiektu domeny (na przykład obrazu lub tekstu). Oznacza to, że ML.NET modele obejmują kroki featurization niezbędne, a także parametry funkcji przewidywania.

## <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

Przypadek [klasyfikacji,](#classification) w którym [etykieta](#label) jest jedną z trzech lub więcej klas. Aby uzyskać więcej informacji, zobacz [sekcję Klasyfikacja wieloklasowa](tasks.md#multiclass-classification) w temacie [Zadania uczenia maszynowego.](tasks.md)

## <a name="n-gram"></a>N-gram

Schemat wyodrębniania funkcji dla danych tekstowych: dowolna sekwencja n słów zamienia się w wartość [charakterystyczną.](#feature)

## <a name="normalization"></a>Normalizacja

Normalizacja to proces skalowania danych zmiennoprzecinkowych do wartości z wartości ami od 0 do 1. Wiele algorytmów szkoleniowych używanych w ML.NET wymagają znormalizowania danych funkcji wejściowych. ML.NET zapewnia serię [przekształceń do normalizacji](transforms.md#normalization-and-scaling)

## <a name="numerical-feature-vector"></a>Wektor operacji numerycznej

Wektor [operacji](#feature) składający się tylko z wartości liczbowych. Jest to `double[]`podobne do .

## <a name="pipeline"></a>Potok

Wszystkie operacje potrzebne do dopasowania modelu do zestawu danych. Potok składa się z importu danych, transformacji, featurization i uczenia się kroki. Po szkoleniu potoku zamienia się w model.

## <a name="precision"></a>Dokładność

W [klasyfikacji](#classification)dokładność dla klasy jest liczbą elementów poprawnie przewidywanych jako należących do tej klasy, podzielona przez całkowitą liczbę elementów przewidzianych jako należące do klasy.

## <a name="recall"></a>Kompletność

W [klasyfikacji](#classification)wycofanie dla klasy jest liczbą elementów poprawnie przewidzianych jako należące do tej klasy podzielona przez całkowitą liczbę elementów, które faktycznie należą do klasy.

## <a name="regularization"></a>Uregulowanie

 Uregulowanie karze model liniowy za zbyt skomplikowane. Istnieją dwa rodzaje uregulowania:

- $L_1$ normalizacja zeruje wagi dla nieistotnych funkcji. Rozmiar zapisanego modelu może stać się mniejszy po tego typu uregulowania.
- $L_2$ regularność minimalizuje zakres wagi dla nieistotnych obiektów. Jest to bardziej ogólny proces i jest mniej wrażliwy na wartości odstające.

## <a name="regression"></a>Regresja

Nadzorowane zadanie [uczenia maszynowego,](#supervised-machine-learning) w którym dane wyjściowe jest rzeczywistą wartością, na przykład podwójną. Przykłady obejmują przewidywanie cen akcji. Aby uzyskać więcej informacji, zobacz sekcję [Regresja](tasks.md#regression) w temacie [Zadania uczenia maszynowego.](tasks.md)

## <a name="relative-absolute-error"></a>Względny błąd bezwzględny

W [regresji](#regression), metryki oceny, która jest sumą wszystkich błędów bezwzględnych podzielona przez sumę odległości między wartościami [poprawne etykiety](#label) i średnia wszystkich prawidłowych wartości etykiet.

## <a name="relative-squared-error"></a>Względny błąd kwadratu

W [regresji](#regression), metryki oceny, która jest sumą wszystkich kwadratów bezwzględnych błędów podzielona przez sumę kwadratowych odległości między poprawnymi wartościami [etykiet](#label) i średnią wszystkich prawidłowych wartości etykiet.

## <a name="root-of-mean-squared-error-rmse"></a>Katalog główny średniego błędu kwadratowego (RMSE)

W [regresji](#regression), metryki oceny, która jest pierwiastek kwadratowy średniej kwadratów błędów.

## <a name="scoring"></a>Scoring (Ocenianie)

Ocenianie to proces stosowania nowych danych do uczonego modelu uczenia maszynowego i generowania prognoz. Punktacji jest również znany jako wnioskowanie. W zależności od typu modelu wynik może być wartością nieprzejrzystą, prawdopodobieństwem lub kategorią.

## <a name="supervised-machine-learning"></a>Nadzorowane uczenie maszynowe

Podklasa uczenia maszynowego, w której żądany model przewiduje etykietę dla jeszcze niewidocznych danych. Przykłady obejmują klasyfikacji, regresji i przewidywanie strukturalne. Aby uzyskać więcej informacji, zobacz [artykuł nadzorowany na](https://en.wikipedia.org/wiki/Supervised_learning) Wikipedii.

## <a name="training"></a>Szkolenia

Proces identyfikowania [modelu](#model) dla danego zestawu danych szkoleniowych. W przypadku modelu liniowego oznacza to znalezienie obciążek. W przypadku drzewa polega ona na identyfikowaniu punktów podziału.

## <a name="transformer"></a>Transformator

Klasa ML.NET, która <xref:Microsoft.ML.ITransformer> implementuje interfejs.

Transformator przekształca <xref:Microsoft.ML.IDataView> się jeden w drugiego. Transformator jest tworzony przez szkolenie [estymatora](#estimator)lub potoku estymatora.

## <a name="unsupervised-machine-learning"></a>Nienadzorowane uczenie maszynowe

Podklasa uczenia maszynowego, w której żądany model znajduje ukrytą (lub ukrytą) strukturę w danych. Przykłady obejmują klastrowanie, modelowanie tematów i redukcję wymiarowości. Aby uzyskać więcej informacji, zobacz artykuł [o nienadzorowanej nauce](https://en.wikipedia.org/wiki/Unsupervised_learning) na Wikipedii.
