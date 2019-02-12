---
title: Usługi Machine learning — słownik w strukturze ML.NET
description: Słownik ważne terminy dotyczące uczenia maszynowego, które są przydatne podczas tworzenia niestandardowych modeli w strukturze ML.NET.
ms.custom: seodec18
ms.date: 12/20/2018
ms.openlocfilehash: 3dfa17e9264bf913465adb63ce0a90a9d196e617
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092439"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Machine learning słownik terminów ważne

Poniższa lista jest kompilacja terminy dotyczące uczenia maszynowego ważne, które są przydatne podczas tworzenia niestandardowych modeli w strukturze ML.NET.

## <a name="accuracy"></a>dokładność

W [klasyfikacji](#classification), dokładności jest liczba elementów poprawnie sklasyfikowane podzielona przez całkowitą liczbę elementów w zestawie testów. Z zakresu od 0 (co najmniej z dokładnością) do 1 (najdokładniejszych). Dokładność jest jedną z metryk oceny wydajności modelu. Należy wziąć pod uwagę w połączeniu z [dokładności](#precision), [odwołania](#recall), i [wynik F](#f-score).

## <a name="area-under-the-curve-auc"></a>Powierzchni pod krzywą (AUC)

W [klasyfikacji binarnej](#binary-classification), metryki oceny, która jest wartością powierzchni pod krzywą geograficzne współczynnik prawdziwie dodatnie (na osi y) względem współczynnik wyników fałszywie dodatnich (na osi x). Dla zakresu od 0,5 (najgorzej) do 1 (najlepszą). Nazywane również obszarze krzywej ROC, czyli odbiorcy cech krzywej działania. Aby uzyskać więcej informacji, zobacz [Receiver operating cechy](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) artykuł w witrynie Wikipedia.

## <a name="binary-classification"></a>Klasyfikacja binarna

A [klasyfikacji](#classification) zamierzone, gdzie [etykiety](#label) jest tylko jeden z dwóch klas. Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](tasks.md#binary-classification) części [zadania uczenia maszynowego](tasks.md) tematu.

## <a name="classification"></a>Klasyfikacja

Gdy dane są używane do prognozowania kategorię, [uczenia maszynowego w trybie nadzorowanym](#supervised-machine-learning) zadania nosi nazwę klasyfikacji. [Klasyfikacja binarna](#binary-classification) odwołuje się do przewidywania tylko dwóm kategoriom (na przykład klasyfikowania obrazów jako obraz dog lub cat). [Klasyfikacji wieloklasowej](#multiclass-classification) odwołuje się do przewidywania wielu kategorii (na przykład podczas klasyfikowania obrazów jako obraz określonych rasy pies).

## <a name="coefficient-of-determination"></a>Determinacji

W [regresji](#regression), metryki oceny, która wskazuje, jak dobrze pasuje do modelu danych. Z zakresu od 0 do 1. Wartość 0 oznacza, że dane są losowych lub w inny sposób nie można dopasować do modelu. Wartość 1 oznacza, że model dokładnie pasują do danych. To jest często nazywany r<sup>2</sup>, R<sup>2</sup>, lub r kwadrat.

## <a name="feature"></a>Funkcja

Właściwość mierzalne zjawisko mierzony, zazwyczaj (podwójny) wartość liczbową. Wiele funkcji są określane jako **wektor funkcji** i zazwyczaj przechowywane jako `double[]`. Funkcje definiują istotne cechy zjawisko mierzony. Aby uzyskać więcej informacji, zobacz [funkcji](https://en.wikipedia.org/wiki/Feature_(machine_learning)) artykuł w witrynie Wikipedia.

## <a name="feature-engineering"></a>Inżynieria funkcji

Inżynieria funkcji to proces, który obejmuje zdefiniowanie zestawu [funkcji](#feature) i opracowywania oprogramowania, które tworzy wektorów funkcji z danych dostępnych zjawiskiem, czyli wyodrębniania funkcji. Aby uzyskać więcej informacji, zobacz [Inżynieria funkcji](https://en.wikipedia.org/wiki/Feature_engineering) artykuł w witrynie Wikipedia.

## <a name="f-score"></a>F-score

W [klasyfikacji](#classification), metryki oceny, która równoważy [dokładności](#precision) i [odwołania](#recall).

## <a name="hyperparameter"></a>Hiperparametrycznego

Parametr algorytmu uczenia maszynowego. Przykłady obejmują liczbę drzewa, aby dowiedzieć się więcej w las decyzyjny lub rozmiar kroku w algorytmie spadku gradientu. Wartości typu *Hiperparametrów* są ustawiane przed uczenia modelu i określają sposób proces wyszukiwania tych parametrów w funkcji prognozowania, na przykład porównanie wskazuje drzewa decyzyjnego lub obciążenia w modelu regresji liniowej . Aby uzyskać więcej informacji, zobacz [Hiperparametrycznego](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) artykuł w witrynie Wikipedia.

## <a name="label"></a>Etykieta

Element można przewidzieć przy użyciu modelu uczenia maszynowego. Na przykład rasy dog lub przyszłe cena akcji.

## <a name="log-loss"></a>Utrata dziennika

W [klasyfikacji](#classification), metryki oceny, który charakteryzuje dokładność klasyfikatora. Jest mniejsze utrata dziennika, jest bardziej precyzyjne klasyfikatora.

## <a name="mean-absolute-error-mae"></a>Średni bezwzględny błąd (dostosowania)

W [regresji](#regression), metryki oceny średnią wszystkich błędów modelu, w których jest błąd modelu odległość między przewidywane [etykiety](#label) i wartością prawidłowa etykieta.

## <a name="model"></a>Model

Tradycyjnie parametry funkcji prognozowania. Na przykład obciążenia w modelu regresji liniowej lub punkty podziału drzewa decyzyjnego. W strukturze ML.NET, model zawiera wszystkie informacje niezbędne do prognozowania [etykiety](#label) obiektu domeny (na przykład obraz lub tekst). Oznacza to, że modele strukturze ML.NET zawierają niezbędne oraz parametry funkcji prognozowania czynności cechowania.

## <a name="multiclass-classification"></a>Wieloklasowej klasyfikacji

A [klasyfikacji](#classification) zamierzone, gdzie [etykiety](#label) jest jednym z trzech lub więcej klas. Aby uzyskać więcej informacji, zobacz [klasyfikacji Wieloklasowej](tasks.md#multiclass-classification) części [zadania uczenia maszynowego](tasks.md) tematu.

## <a name="n-gram"></a>N-gram

Funkcja wyodrębniania schemat danych tekstowych: dowolnej sekwencji wyrazów N jest przekształcany [funkcji](#feature) wartość.

## <a name="numerical-feature-vector"></a>Wektor liczbowych

A [funkcji](#feature) wektor składający się tylko z wartości liczbowe. Jest to podobne do `double[]`.

## <a name="pipeline"></a>Potok

Wszystkie operacje wymagane do dopasowania modelu do zestawu danych. Potok składa się z importowania danych, przekształcania, cechowania i nauki kroki. Po przygotowaniu potoku zmieni się w modelu.

## <a name="precision"></a>Dokładność

W [klasyfikacji](#classification), dokładność dla klasy jest liczba elementów, poprawnie przewidzieć jako należące do tej klasy podzielona przez całkowitą liczbę elementów, które przewiduje jako należące do tej klasy.

## <a name="recall"></a>Odwołaj

W [klasyfikacji](#classification), odwołania do klasy jest liczba elementów, poprawnie przewidzieć jako należące do tej klasy podzielona przez całkowitą liczbę elementów, które faktycznie należą do klasy.

## <a name="regression"></a>Regresji

A [uczenia maszynowego w trybie nadzorowanym](#supervised-machine-learning) zadań, której dane wyjściowe jest wartością rzeczywistą, na przykład, double. Przykłady obejmują Prognozowanie cen akcji. Aby uzyskać więcej informacji, zobacz [regresji](tasks.md#regression) części [zadania uczenia maszynowego](tasks.md) tematu.

## <a name="relative-absolute-error"></a>Względny błąd absolutny

W [regresji](#regression), metryki oceny, która jest sumą wszystkich błędów absolutnych podzielona przez sumę odległości między poprawne [etykiety](#label) wartości i średnią wszystkich Popraw wartości etykiety.

## <a name="relative-squared-error"></a>Względny błąd kwadrat

W [regresji](#regression), metryki oceny, która jest sumą wszystkich kwadrat błędów absolutnych i podzielona przez suma kwadratów odległości między poprawne [etykiety](#label) wartości i średnią wszystkich Popraw wartości etykiety.

## <a name="root-of-mean-squared-error-rmse"></a>Główny średniej kwadrat błąd (RMSE)

W [regresji](#regression), metryki oceny pierwiastek kwadratowy ze średniej kwadratów błędów.

## <a name="supervised-machine-learning"></a>Uczenie maszynowe nadzorowanych

Podklasa klasy usługi machine learning, w którym żądany model przewiduje etykiety danych, ale niewidzianych. Przykłady obejmują klasyfikacji, regresji i ze strukturą prognozy. Aby uzyskać więcej informacji, zobacz [uczenia nadzorowanego](https://en.wikipedia.org/wiki/Supervised_learning) artykuł w witrynie Wikipedia.

## <a name="training"></a>Szkolenia

Proces identyfikowania [modelu](#model) dla danego szkoleniowy zestaw danych. Dla modelu liniowego oznacza to, znajdowanie wag. Dla drzewa obejmuje to identyfikowanie punktów podziału.

## <a name="transform"></a>Transformacja

A [potoku](#pipeline) składnika, który przekształca dane. Na przykład z pliku tekstowego do wektor numerów.

## <a name="unsupervised-machine-learning"></a>Uczenie maszynowe nienadzorowanych

Podklasa klasy usługi machine learning, w którym żądany model znajduje struktury ukryty (lub ukrytego) w danych. Przykłady obejmują klastrowania, modelowanie tematu i wymiarowości. Aby uzyskać więcej informacji, zobacz [uczenie nienadzorowane](https://en.wikipedia.org/wiki/Unsupervised_learning) artykuł w witrynie Wikipedia.
