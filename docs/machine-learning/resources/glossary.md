---
title: Glosariusz uczenia maszynowego
description: Słownik ważnych warunków uczenia maszynowego, które są przydatne podczas tworzenia niestandardowych modeli w programie ML.NET.
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 32ccb6df1cb08db45ebd25a0d1c0ea4396a6c50b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739875"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Słownik uczenia maszynowego ważnych warunków

Poniższa lista zawiera kompilację ważnych warunków uczenia maszynowego, które są przydatne podczas tworzenia niestandardowych modeli w programie ML.NET.

## <a name="accuracy"></a>Odpowiedni

W [klasyfikacji](#classification)dokładność jest liczbą poprawnie sklasyfikowanych elementów podzielona przez łączną liczbę elementów w zestawie testów. Zakresy od 0 (najmniej dokładne) do 1 (najdokładniejsze). Dokładność jest jedną z metryk oceny wydajności modelu. Należy wziąć pod uwagę w połączeniu z [dokładnością](#precision), [odwołaniem](#recall)i [wynikiem](#f-score).

## <a name="area-under-the-curve-auc"></a>Obszar pod krzywą (AUC)

W [klasyfikacji binarnej](#binary-classification), Metryka oceny, która jest wartością obszaru pod krzywą, która przedstawia prawdziwą stawkę dodatnią (na osi y) względem pozytywnej szybkości dodatniej (na osi x). Zakresy od 0,5 (najgorzej) do 1 (najlepiej). Znany również jako obszar pod krzywą ROC, tj. z krzywą charakterystyczną dla odbiornika. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [obsługi odbiornika](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) w witrynie Wikipedia.

## <a name="binary-classification"></a>Klasyfikacja binarna

Przypadek [klasyfikacji](#classification) , gdzie [etykieta](#label) jest tylko jedną z dwóch klas. Aby uzyskać więcej informacji, zobacz sekcję [klasyfikacja binarna](tasks.md#binary-classification) tematu [zadania usługi Machine Learning](tasks.md) .

## <a name="calibration"></a>Krzyw

Kalibracja jest procesem mapowania nieprzetworzonego wyniku na członkostwo klasy w przypadku klasyfikacji binarnej i wieloklasowej. Niektóre instruktorzy ML.NET mają sufiks `NonCalibrated`. Te algorytmy tworzą nieprzetworzony wynik, który następnie musi być zamapowany na prawdopodobieństwo klasy.

## <a name="catalog"></a>Wykaz

W ML.NET katalog jest kolekcją funkcji rozszerzeń pogrupowanych według wspólnego celu.

Na przykład każde zadanie uczenia maszynowego (klasyfikacja binarna, regresja, klasyfikacja itp.) ma katalog dostępnych algorytmów uczenia maszynowego (instruktorzy). Wykaz dla instruktorów klasyfikacji binarnej to: <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>Klasyfikacja

Gdy dane są używane do przewidywania kategorii, zadanie [uczenia maszynowego](#supervised-machine-learning) jest nazywane klasyfikacją. [Klasyfikacja binarna](#binary-classification) odnosi się do przewidywania tylko dwóch kategorii (na przykład klasyfikowanie obrazu jako obrazu "Cat" lub "Dog"). [Klasyfikacja wieloklasowa](#multiclass-classification) odnosi się do przewidywania wielu kategorii (na przykład podczas klasyfikowania obrazu jako obrazu konkretnej rasy Dog).

## <a name="coefficient-of-determination"></a>Współczynnik wyznaczania

W [regresji](#regression)Metryka oceny, która wskazuje, jak dobre dane pasują do modelu. Zakresy z zakresu od 0 do 1. Wartość 0 oznacza, że dane są losowo lub w przeciwnym razie nie można dopasować do modelu. Wartość 1 oznacza, że model dokładnie pasuje do danych. Jest to często określane jako r<sup>2</sup>, r<sup>2</sup>lub r-kwadrat.

## <a name="data"></a>Dane

Dane są centralne dla każdej aplikacji uczenia maszynowego. W danych ML.NET są reprezentowane przez obiekty <xref:Microsoft.ML.IDataView>. Obiekty widoku danych:

- składają się z kolumn i wierszy
- Czy opóźnieniem są oceniane, czyli ładują dane tylko wtedy, gdy operacja wywołuje ją.
- zawiera schemat definiujący typ, format i długość każdej kolumny.

## <a name="estimator"></a>Szacowania

Klasa w ML.NET implementująca interfejs <xref:Microsoft.ML.IEstimator%601>.

Szacowania to specyfikacja transformacji (transformacja przygotowywania danych i transformacja szkoleń modelu uczenia maszynowego). Szacowania można łączyć razem z potokiem transformacji. Parametry szacowania lub potoku szacowania są uzyskiwane w przypadku wywołania <xref:Microsoft.ML.IEstimator%601.Fit%2A>. Wynik <xref:Microsoft.ML.IEstimator%601.Fit%2A> jest [transformatorem](#transformer).

## <a name="extension-method"></a>Metoda rozszerzenia

Metoda .NET, która jest częścią klasy, ale jest zdefiniowana poza klasą. Pierwszy parametr metody rozszerzenia jest statycznym odwołaniem `this` do klasy, do której należy Metoda rozszerzenia.

Metody rozszerzające są szeroko używane w ML.NET do konstruowania wystąpień [szacowania](#estimator).

## <a name="feature"></a>Funkcja

Wymierna Właściwość mierzonego zjawiska, zazwyczaj wartość liczbowa (Double). Wiele funkcji jest określana jako **wektor funkcji** i zazwyczaj jest przechowywana jako `double[]`. Funkcje definiują ważne cechy mierzonego zjawiska. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [funkcji](https://en.wikipedia.org/wiki/Feature_(machine_learning)) w witrynie Wikipedia.

## <a name="feature-engineering"></a>Inżynieria funkcji

Inżynieria funkcji to proces, który obejmuje Definiowanie zestawu [funkcji](#feature) i opracowywanie oprogramowania, które generuje wektory funkcji z dostępnych danych zjawiska, czyli wyodrębniania funkcji. Aby uzyskać więcej informacji, zobacz artykuł [Inżynieria funkcji](https://en.wikipedia.org/wiki/Feature_engineering) w witrynie Wikipedia.

## <a name="f-score"></a>F-Score

W obszarze [Klasyfikacja](#classification)Metryka oceny, która równoważy [precyzję](#precision) i [odwoływanie](#recall).

## <a name="hyperparameter"></a>Hiperparametrycznego

Parametr algorytmu uczenia maszynowego. Przykłady obejmują liczbę drzew do nauczenia się w lesie decyzyjnym lub rozmiar kroku w algorytmie pochodzenie gradientu. Wartości *parametrów moje parametry* są ustawiane przed szkoleniem modelu i określają proces znajdowania parametrów funkcji przewidywania, na przykład punkty porównania w drzewie decyzyjnym lub wagi w modelu regresji liniowej. Aby uzyskać więcej informacji, zobacz artykuł z [parametrem](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) w witrynie Wikipedia.

## <a name="label"></a>Etykieta

Element do przewidywania z modelem uczenia maszynowego. Na przykład rasy Dog lub przyszłej ceny giełdowej.

## <a name="log-loss"></a>Rejestruj utratę

W [klasyfikacji](#classification), Metryka oceny, która charakteryzuje dokładność klasyfikatora. Mniejsza utrata dziennika to dokładniejszy klasyfikator.

## <a name="loss-function"></a>Funkcja strat

Funkcja strat to różnica między wartościami etykiet szkoleniowych i prognozą dokonaną przez model. Parametry modelu są szacowane przez zminimalizowanie funkcji strat.

Różnych instruktorów można skonfigurować przy użyciu różnych funkcji utraty.

## <a name="mean-absolute-error-mae"></a>Średni błąd bezwzględny (MAE)

W [regresji](#regression)Metryka oceny, która jest średnią wszystkich błędów modelu, gdzie błąd modelu to odległość między wartością [etykiety](#label) przewidywanej i poprawną wartością etykiety.

## <a name="model"></a>Model

Tradycyjnie parametry funkcji przewidywania. Na przykład wagi w modelu regresji liniowej lub punkty podziału w drzewie decyzyjnym. W programie ML.NET model zawiera wszystkie informacje niezbędne do przewidywania [etykiety](#label) obiektu domeny (na przykład obrazu lub tekstu). Oznacza to, że modele ML.NET obejmują wymagane kroki cechowania, a także parametry funkcji przewidywania.

## <a name="multiclass-classification"></a>Klasyfikacja wieloklasowa

Przypadek [klasyfikacji](#classification) , gdzie [etykieta](#label) jest jedną z trzech lub więcej klas. Aby uzyskać więcej informacji, zobacz sekcję [klasyfikacji wieloklasowego](tasks.md#multiclass-classification) tematu [zadań uczenia maszynowego](tasks.md) .

## <a name="n-gram"></a>N-gram

Schemat wyodrębniania funkcji dla danych tekstowych: każda sekwencja N wyrazów włącza wartość [funkcji](#feature) .

## <a name="normalization"></a>Normalizacja

Normalizacja to proces skalowania danych zmiennoprzecinkowych do wartości z zakresu od 0 do 1. Wiele algorytmów szkoleniowych używanych w ML.NET Wymagaj znormalizowane dane funkcji wejściowych. ML.NET zawiera serię [transformacji do normalizacji](transforms.md#normalization-and-scaling)

## <a name="numerical-feature-vector"></a>Wektor funkcji numerycznej

Wektor [funkcji](#feature) składający się tylko z wartości liczbowych. Jest to podobne do `double[]`.

## <a name="pipeline"></a>Potok

Wszystkie operacje, które są konieczne do dopasowania modelu do zestawu danych. Potok składa się z kroków importowania, przekształcania, cechowania i uczenia danych. Po przeszkoleniu potoku zostanie on przekształcony w model.

## <a name="precision"></a>Dokładność

W [klasyfikacji](#classification)precyzja dla klasy jest liczbą elementów prawidłowo przewidywanych jako należące do tej klasy podzielona przez łączną liczbę elementów przewidywanych jako należące do klasy.

## <a name="recall"></a>Odwołaj

W [klasyfikacji](#classification)odwołanie dla klasy jest liczbą elementów prawidłowo przewidywanych jako należące do tej klasy podzielona przez łączną liczbę elementów, które faktycznie należą do klasy.

## <a name="regularization"></a>Uregulowania

 Uregulowanie nakłada się na model liniowy za zbyt skomplikowany. Istnieją dwa typy uregulowania:

- $L _1 $ uregulowania zerowej wagi dla nieznaczących funkcji. Rozmiar zapisanego modelu może być mniejszy po tym typie uregulowania.
- $L _2 $ uregulowanie ogranicza zakres wagi dla nieznaczących funkcji. Jest to bardziej ogólny proces i jest mniej wrażliwy na wartości odstające.

## <a name="regression"></a>Regresji

[Nadzorowane zadanie uczenia maszynowego](#supervised-machine-learning) , gdzie wyjście jest wartością rzeczywistą, na przykład Double. Przykłady obejmują przewidywanie cen giełdowych. Aby uzyskać więcej informacji, zobacz sekcję [regresja](tasks.md#regression) w temacie [zadań uczenia maszynowego](tasks.md) .

## <a name="relative-absolute-error"></a>Względny błąd bezwzględny

W [regresji](#regression)Metryka oceny, która jest sumą wszystkich nieabsolutnych błędów podzielona przez sumę odległości między prawidłowymi wartościami [etykiet](#label) i średnią wszystkich poprawnych wartości etykiet.

## <a name="relative-squared-error"></a>Względny kwadratowy błąd

W [regresji](#regression)Metryka oceny, która jest sumą wszystkich kwadratowych błędów bezwzględnych podzielona przez sumę kwadratowych odległości między prawidłowymi wartościami [etykiet](#label) i średnią wszystkich poprawnych wartości etykiet.

## <a name="root-of-mean-squared-error-rmse"></a>Element główny średniej wartości błędu kwadratowego (RMSE)

W [regresji](#regression)Metryka oceny, która jest pierwiastek kwadratowy średniej wartości kwadratów błędów.

## <a name="scoring"></a>Zdań

Ocenianie to proces stosowania nowych danych do przeszkolonego modelu uczenia maszynowego i generowania prognoz. Ocenianie jest również znane jako inferencing. W zależności od typu modelu wynik może być wartością pierwotną, prawdopodobieństwem lub kategorią.

## <a name="supervised-machine-learning"></a>Nadzorowane Uczenie maszynowe

Podklasa uczenia maszynowego, w której żądany model przewiduje etykietę dla jeszcze niewidocznych danych. Przykłady obejmują klasyfikację, regresję i prognozowanie strukturalne. Aby uzyskać więcej informacji, zapoznaj się z artykułem [nadzorowane uczenie](https://en.wikipedia.org/wiki/Supervised_learning) w witrynie Wikipedia.

## <a name="training"></a>Szkolenia

Proces identyfikacji [modelu](#model) dla danego zestawu danych szkoleniowych. W przypadku modelu liniowego oznacza to znalezienie wag. Dla drzewa obejmuje identyfikację punktów podziału.

## <a name="transformer"></a>Funkcja

Klasa ML.NET implementująca interfejs <xref:Microsoft.ML.ITransformer>.

Transformator przekształca jeden <xref:Microsoft.ML.IDataView> w inny. Transformator jest tworzony przez szkolenie [szacowania](#estimator)lub potoku szacowania.

## <a name="unsupervised-machine-learning"></a>Nienadzorowane Uczenie maszynowe

Podklasa uczenia maszynowego, w której żądany model znajduje ukryty (lub ukryty) strukturę w danych. Przykłady obejmują klastrowanie, modelowanie tematów i zmniejszanie liczby wymiarów. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [uczenia nienadzorowanego](https://en.wikipedia.org/wiki/Unsupervised_learning) w witrynie Wikipedia.
