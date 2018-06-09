---
title: Słownik uczenia maszynowego
description: Słownik terminy dotyczące uczenia maszynowego.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: 332d9e14bea165992f9f00b048286e185269ea79
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "35017286"
---
# <a name="machine-learning-glossary"></a>Machine learning słownik

Poniżej znajduje się zbiór terminy dotyczące uczenia maszynowego ważne, które są przydatne podczas tworzenia niestandardowych modeli.

## <a name="accuracy"></a>Dokładność

W [klasyfikacji](#classification), dokładność jest liczba elementów niejawnych prawidłowo podzielona przez całkowitą liczbę elementów w zestawie testów. W zakresie od 0 (najmniej dokładne) do 1 (najdokładniejszych). Dokładność jest jednym z metryki oceny wydajności modelu. Należy wziąć pod uwagę w połączeniu z [dokładności](#precision), [odwołania](#recall), i [wynik F](#f-score).

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.

## <a name="area-under-the-curve-auc"></a>Obszar krzywej (AUC)

W [klasyfikacji binarnej](#binary-classification), obliczanie metryki wartość obszarze krzywej geograficzne szybkość alarmów true (na osi y) względem szybkość fałszywych alarmów (na osi x). Dla zakresu od 0,5 (najgorszych) do 1 (najlepsze). Znany również jako obszarze krzywą ROC, tj. odbiornik charakterystyczny krzywej działania. Aby uzyskać więcej informacji, zobacz [odbiornika operacyjnego cech](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) artykuł w witrynie Wikipedia.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.

## <a name="binary-classification"></a>klasyfikacji binarnej

A [klasyfikacji](#classification) przypadek where [etykiety](#label) jest tylko jeden z dwóch klas. Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) artykuł w witrynie Wikipedia.

## <a name="classification"></a>Klasyfikacja

Gdy dane są używane do prognozowania kategorii, [nadzorowanego uczenia maszynowego](#supervised-machine-learning) klasyfikacji wywoływane jest zadanie. [Klasyfikacji binarnej](#binary-classification) odwołuje się do przewidywania tylko dwie kategorie (na przykład klasyfikacji obrazu jako obraz "kot" lub "dog"). [Wieloklasowej klasyfikacji](#multiclass-classification) odwołuje się do przewidywania wiele kategorii (na przykład przy klasyfikacji obrazu jako obraz określonych rodzaj dog).

## <a name="coefficient-of-determination"></a>Współczynnik determinacji

W [regresji](#regression), metryki oceny, która wskazuje, jak dane pasuje do modelu. W zakresie od 0 do 1. Wartość 0 oznacza, że dane są losowych lub w inny sposób nie można dopasować do modelu. Wartość 1 oznacza, że model dokładnie odpowiada danych. Jest to często określane jako r<sup>2</sup>, R<sup>2</sup>, lub r kwadrat.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.

## <a name="feature"></a>Funkcja

Właściwość mierzalnych zjawisko mierzony, zwykle (dwa razy) wartość liczbową. Wiele funkcji są określane jako **wektor funkcji** i zwykle przechowywany jako `double[]`. Funkcje zdefiniuj najważniejsze czynniki zjawisko mierzony. Aby uzyskać więcej informacji, zobacz [funkcji](https://en.wikipedia.org/wiki/Feature_(machine_learning)) artykuł w witrynie Wikipedia.

## <a name="feature-engineering"></a>Inżynieria

Funkcja engineering jest proces, który obejmuje definiowania zestawu [funkcje](#feature) i rozwoju oprogramowania, które tworzy wektory funkcji zjawisko dostępnych danych, np. wyodrębniania funkcji. Aby uzyskać więcej informacji, zobacz [Inżynieria](https://en.wikipedia.org/wiki/Feature_engineering) artykuł w witrynie Wikipedia.

## <a name="f-score"></a>Wynik F

W [klasyfikacji](#classification), metryki oceny, który równoważy [dokładności](#precision) i [odwołania](#recall).

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.

## <a name="hyperparameter"></a>Hyperparameter

Parametr algorytmu uczenia maszynowego. Przykłady obejmują liczbę drzewa, aby dowiedzieć się w lesie decyzji lub rozmiar kroku w algorytmie spadku gradientu. Wartości typu *Hyperparameters* są ustawione przed uczenia modelu i kontrolować proces parametrów funkcji prognozowania, na przykład, porównanie punktów w drzewa decyzyjnego lub obciążenia w modelu regresji liniowej . Aby uzyskać więcej informacji, zobacz [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) artykuł w witrynie Wikipedia.

## <a name="label"></a>Etykieta

Element ma być przewidzieć z modelu uczenia maszynowego. Na przykład jest rodzaj dog lub przyszłe giełdowy.

## <a name="log-loss"></a>Utrata dziennika

W [klasyfikacji](#classification), metryki oceny charakteryzuje dokładność klasyfikatora. Jest mniejsze utrata dziennika, jest dokładniejsze klasyfikatora.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.

## <a name="mean-absolute-error-mae"></a>Średni bezwzględny błąd (MAE)

W [regresji](#regression), metryki oceny jest średnią wszystkich błędów modelu, który błąd modelu odległość między przewidywane [etykiety](#label) wartość i wartość prawidłowa etykieta.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.

## <a name="model"></a>Model

Tradycyjnie parametrów funkcji prognozowania. Na przykład obciążenia w modelu regresji liniowej lub punkty podziału drzewa decyzyjnego. W ML.NET, model zawiera wszystkie informacje niezbędne do prognozowania [etykiety](#label) obiektu domeny (na przykład obraz lub tekst). Oznacza to, że modele ML.NET obejmuje kroki featurization niezbędne oraz parametrów dla funkcji prognozowania.

## <a name="multiclass-classification"></a>wieloklasowej klasyfikacji

A [klasyfikacji](#classification) przypadek where [etykiety](#label) jest jednym z co najmniej trzech klas. Aby uzyskać więcej informacji, zobacz [Wieloklasowej klasyfikacji](https://en.wikipedia.org/wiki/Multiclass_classification) artykuł w witrynie Wikipedia.

## <a name="n-gram"></a>N-gramów

Funkcja schemat wyodrębniania danych tekstowych: zmieni się w dowolnej kolejności N słowa [funkcji](#feature) wartość.

## <a name="numerical-feature-vector"></a>Wektor funkcji numerycznych

A [funkcji](#feature) wektor zawiera tylko wartości numeryczne. Jest to podobne do `double[]`.

## <a name="pipeline"></a>Potoku

Wszystkie operacje potrzeba aby dopasować modelu do zestawu danych. Potok składa się z import danych, przekształcania, featurization i uczenia kroki. Po przygotowaniu potoku zmieni się w modelu.

## <a name="precision"></a>Dokładność

W [klasyfikacji](#classification), dokładność dla klasy jest liczba elementów poprawnie przewidzieć jako należące do tej klasy podzielona przez całkowitą liczbę elementów przewidzieć jako należące do klasy.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.

## <a name="recall"></a>Odwołania

W [klasyfikacji](#classification), liczba elementów poprawnie przewidzieć jako należące do tej klasy podzielona przez całkowitą liczbę elementów, które faktycznie należą do klasy jest odwołanie do klasy.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.

## <a name="regression"></a>Regresja

A [nadzorowanego uczenia maszynowego](#supervised-machine-learning) zadań dane wyjściowe w przypadku rzeczywistych wartości, na przykład, double. Przykładami Prognozowanie cen akcji.

## <a name="relative-absolute-error"></a>Względny błąd absolutny

W [regresji](#regression), metryki oceny sumę wszystkich błędów absolutnych podzielona przez sumę odległości między poprawne [etykiety](#label) wartości i średnią wszystkich wartości etykiet Popraw.

## <a name="relative-squared-error"></a>Błąd względny średniokwadratowy

W [regresji](#regression), metryki oceny, który jest sumą wszystkich kwadrat bezwzględnych błędów podzielona przez sumę kwadratów odległości między poprawne [etykiety](#label) wartości i średnią wszystkich wartości etykiet Popraw.

## <a name="root-of-mean-squared-error-rmse"></a>Główny średniej kwadrat błąd (RMSE)

W [regresji](#regression), metryki oceny pierwiastek kwadratowy ze średniej kwadratów błędów.

Interfejs API powiązane ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.

## <a name="supervised-machine-learning"></a>Uczenie maszynowe nadzorowanym

Podklasa machine learning, w którym żądany model przewiduje etykietę danych jeszcze niewidoczne. Przykłady klasyfikacji i regresji oraz strukturalnych prognozowania. Aby uzyskać więcej informacji, zobacz [uczenia nadzorowanego](https://en.wikipedia.org/wiki/Supervised_learning) artykuł w witrynie Wikipedia.

## <a name="training"></a>Szkolenia

Proces identyfikowania [modelu](#model) dla danego szkoleniowy zestaw danych. Model liniowy oznacza to, znajdowanie wag. Drzewa obejmuje identyfikowanie punktów podziału.

## <a name="transform"></a>Transformacja

A [potoku](#pipeline) składnika przekształcenia danych. Na przykład z pliku tekstowego wektorowe liczb.

## <a name="unsupervised-machine-learning"></a>Uczenie maszynowe nienadzorowanych

Podklasa machine learning, w którym żądanego modelu znajduje ukryte (lub ukryty) struktury w danych. Przykładami klaster, modelowania tematu i zmniejszenie wymiary. Aby uzyskać więcej informacji, zobacz [uczenie nienadzorowane](https://en.wikipedia.org/wiki/Unsupervised_learning) artykuł w witrynie Wikipedia.
