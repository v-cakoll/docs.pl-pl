---
title: Metryki ML.NET
description: Informacje o metrykach, które są używane do oceny wydajności modelu ML.NET
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739605"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Oceń model ML.NET przy użyciu metryk

Informacje o metrykach używanych do szacowania modelu ML.NET.

Metryki oceny są specyficzne dla typu zadania uczenia maszynowego wykonywanego przez model.

Na przykład dla zadania klasyfikacji model jest oceniany przez zmierzenie, jak dobrze przewidywalna kategoria jest zgodna z rzeczywistą kategorią. W przypadku klastrowania obliczenia opierają się na tym, jak zamykane elementy klastrowane są ze sobą i ile jest rozbarwień między klastrami.

## <a name="evaluation-metrics-for-binary-classification"></a>Metryki oceny dla klasyfikacji binarnej

| Metryki   |      Opis      |  Wyszukaj |
|-----------|-----------------------|-----------|
| **Accuracy** |  [Dokładność](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) jest proporcją prawidłowych prognoz z zestawem danych testowych. Jest to stosunek liczby poprawnych prognoz do całkowitej liczby próbek wejściowych. Działa dobrze, jeśli istnieje podobna liczba próbek należących do każdej klasy.| **Im bliżej 1,00, tym lepiej**. Ale dokładnie 1,00 wskazuje na problem (często: wyciek etykiet/obiektu docelowego, nadmierne dopasowanie lub testowanie przy użyciu danych szkoleniowych). Gdy dane testowe są niezrównoważone (gdy większość wystąpień należy do jednej z klas), zestaw danych jest mały lub wyniki zbliżają się do 0,00 lub 1,00, a dokładność nie przechwytuje skuteczności klasyfikatora i należy sprawdzić dodatkowe metryki. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) lub *obszar pod krzywą* mierzy obszar pod krzywą utworzoną przez wyczyszczenie prawdziwej dodatniej stawki w porównaniu z fałszywą dodatnią częstotliwością.  |   **Im bliżej 1,00, tym lepiej**. Aby model mógł zostać akceptowalny, powinien być większy niż 0,50. Model z AUCem 0,50 lub mniej to bezwartościowe. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) lub *obszar pod krzywą krzywej odwołania z dokładnością*: użyteczna miara sukcesu w przypadku, gdy klasy są niezrównoważone (zestawy danych o wysokim stopniu skośnym). |  **Im bliżej 1,00, tym lepiej**. Wysokie wyniki zbliżone do 1,00 pokazują, że klasyfikator zwraca dokładne wyniki (wysoka precyzja), a także zwraca większość pozytywnych wyników (wysoki stopień odwołania). |
| **F1-Score** | [Wynik F1](https://en.wikipedia.org/wiki/F1_score) jest znany również jako współczynnik *f-Score lub f-Measure*. Jest to średnia harmoniczna precyzji i odwołania. Wynik F1 jest przydatny, gdy chcesz uzyskać równowagę między dokładnością a odwołaniem.| **Im bliżej 1,00, tym lepiej**.  Wynik F1 osiąga swoją najlepszą wartość w 1,00 i najgorszy wynik o godzinie 0,00. Informuje o tym, jak precyzyjnym klasyfikatorem jest. |

Aby uzyskać więcej informacji na temat metryk klasyfikacji danych binarnych, przeczytaj następujące artykuły:

- [Dokładność, precyzja, odwołanie lub F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Klasa metryk klasyfikacji binarnej](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Relacja między krzywą precyzji i odwołania ROC](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Metryki oceny dla klasyfikacji wieloklasowej

| Metryki   |      Opis      |  Wyszukaj |
|-----------|-----------------------|-----------|
| **Mikro-dokładność** |  Większość [średniej dokładności](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje wkłady wszystkich klas do obliczenia metryki średniej. Jest to ułamek przewidziany prawidłowo. Mikrośrednia nie przyjmuje przynależność klasy do konta. Zasadniczo każda para klasy próbek przyczynia się równie do metryki dokładności. | **Im bliżej 1,00, tym lepiej**. W zadaniu klasyfikacji wieloklasowej większość dokładności jest preferowana w porównaniu z dokładnością makr, jeśli podejrzewasz, że może to spowodować Niezrównoważenie klasy (tj. może istnieć wiele więcej przykładów jednej klasy niż w przypadku innych klas).|
| **Dokładność makra** | [Dokładność makra](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) jest średnią dokładnością na poziomie klasy. Jest obliczana dokładność dla każdej klasy, a dokładność makr jest średnią z tych dokładności. Zasadniczo każda klasa przyczynia się równie do metryki dokładności. Klasy mniejszości są traktowane jako takie same wagi jak większe klasy. Metryka średnia makro zapewnia taką samą wagę dla każdej klasy, niezależnie od liczby wystąpień tej klasy, w której znajduje się zestaw danych. |  **Im bliżej 1,00, tym lepiej**.  Oblicza metrykę niezależnie dla każdej klasy, a następnie pobiera średnią (dlatego jednocześnie traktowanie wszystkich klas) |
| **Dziennik — utrata**| [Strata logarytmiczna](http://wiki.fast.ai/index.php/Log_Loss) mierzy wydajność modelu klasyfikacji, gdzie dane wejściowe przewidywania to wartość prawdopodobieństwa z zakresu od 0,00 do 1,00. Utrata strat dziennika zwiększa się, ponieważ przewidywane prawdopodobieństwo rozbieżności od rzeczywistej etykiety. | **Im bliżej 0,00, tym lepiej**. Idealnym modelem będzie utratę dziennika 0,00. Celem naszych modeli uczenia maszynowego jest zminimalizowanie tej wartości.|
| **Zmniejszenie utraty dziennika** | [Obniżenie strat w postaci logarytmu](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) można interpretować jako zalety klasyfikatora w przypadku prognoz losowych.| **Zakresy od-inf i 1,00, gdzie 1,00 są idealnymi przewidywaniami, a 0,00 wskazuje na średnie przewidywania**. Na przykład jeśli wartość jest równa 0,20, może być interpretowana jako "prawdopodobieństwo poprawnego przewidywania jest 20% lepsze niż losowe zgadywanie"|

Większość dokładności jest ogólnie lepsza w zakresie potrzeb firmy dla przewidywania ML. Jeśli chcesz wybrać jedną metrykę w celu wybrania jakości zadania klasyfikacji wieloklasowej, powinna ona być zwykle z mikrodokładnością.

Przykład dla zadania klasyfikacji biletów pomocy technicznej: (mapuje bilety przychodzące do obsługi zespołów)

- Mikro-dokładność — jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?
- Dokładność makro — w przypadku średniego zespołu, jak często bilet przychodzący jest poprawny dla swojego zespołu?

Dokładność makr umożliwia przeważnie rozważenia małych zespołów w tym przykładzie. mały zespół, który pobiera tylko 10 biletów na rok, tak samo, jak duży zespół z 10 biletami rocznie. Większość dokładności w tym przypadku jest bardziej skorelowana z potrzebami biznesowymi, "ile czasu/pieniędzy może zaoszczędzić firma, automatyzując proces routingu biletów".

Aby uzyskać więcej informacji na temat metryk klasyfikacji wieloklasowej, przeczytaj następujące artykuły:

- [Funkcja mikro-and-Average z dokładnością, odwołaniem i wynikiem F-Score](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasyfikacja wieloklasowa z niezrównoważonym zestawem danych](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Metryki oceny dla regresji i rekomendacji

Zadania regresji i rekomendacji przewidują liczbę. W przypadku regresji liczba może być dowolną właściwością wyjściową, która ma wpływ na właściwości wejściowe. W przypadku rekomendacji liczba jest zwykle wartością klasyfikacji (na przykład z zakresu od 1 do 5) lub zaleceniem tak/nie (reprezentowanym odpowiednio przez 1 i 0).

| Metryki   |      Opis      |  Wyszukaj |
|----------|-----------------------|-----------|
| **R-kwadratowy** |  Oznaczenie [R-kwadratowe (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)lub *współczynnik wyznaczania* reprezentuje potęgę modelu jako wartość z przedziału od-inf do 1,00. 1,00 oznacza, że istnieje idealne dopasowanie, a dopasowanie może być niezadowalające, aby wyniki mogły być ujemne. Wynik 0,00 oznacza, że model zgadywaniu oczekiwanej wartości dla etykiety. R2 mierzy, jak zamknąć rzeczywiste wartości danych testowych do wartości przewidywanych. | **Im bliżej 1,00, tym lepsza jakość**. Niemniej jednak czasami małe wartości (na przykład 0,50) mogą być całkowicie normalne lub wystarczające dla danego scenariusza, a wysokie wartości R-kwadrat nie zawsze są dobre i są podejrzane. |
| **Bezwzględna utrata** |  [Bezwzględne](https://en.wikipedia.org/wiki/Mean_absolute_error) lub *średnie bezwzględne błędy (Mae)* mierzą, jak blisko prognoz są rzeczywiste wyniki. Jest to średnia ze wszystkich błędów modelu, gdzie błąd modelu to bezwzględna odległość między przewidywalną wartością etykiety a poprawną wartością etykiety. Ten błąd przewidywania jest obliczany dla każdego rekordu zestawu danych testowych. Na koniec wartość średnia jest obliczana dla wszystkich zarejestrowanych błędów bezwzględnych.| **Im bliżej 0,00, tym lepsza jakość.** Średni błąd bezwzględny używa takiej samej skali, jak dane są mierzone (nie jest znormalizowany do określonego zakresu). Bezwzględne, kwadratowe straty i straty RMS mogą być używane tylko w celu porównania między modelami dla tego samego zestawu danych lub zestawu danych o podobnym rozkładzie wartości etykiety. |
| **Kwadratowa strata** |  [Kwadratowy](https://en.wikipedia.org/wiki/Mean_squared_error) lub średni kwadratowy *błąd (MSE)* , nazywany również *średnim odchyleniem kwadratowym (MSD)* , informuje o tym, jak zamykasz linię regresji do zestawu wartości danych testowych, przenosząc odległości od punktów do linii regresji (te odległości są błędy E) i podniesienie je. Podniesienie zwiększa wagę do większych różnic. | Jest on zawsze nieujemny, a **wartości zbliżone do 0,00 są lepsze**. W zależności od danych może być niemożliwe uzyskanie bardzo małej wartości dla średniego błędu.|
| **RMS — utrata** |  Funkcja [RMS — utrata](https://en.wikipedia.org/wiki/Root-mean-square_deviation) lub *główna średnia kwadratowa błąd (RMSE)* (zwane także " *odchyleniem kwadratowym średniej", RMSD*), mierzy różnicę między wartościami przewidywanymi przez model i wartościami zaobserwowanymi ze środowiska, które jest modelowane. RMS-strata to pierwiastek kwadratowy z kwadratową stratą i ma te same jednostki, jak etykieta, podobnie jak w przypadku utraty absolutnej, dzięki czemu bardziej ważniejsze są większe różnice. Główny błąd średniego kwadratu jest często używany w analizie climatology, prognozowania i regresji w celu sprawdzenia doświadczalnych wyników. | Jest on zawsze nieujemny, a **wartości zbliżone do 0,00 są lepsze**. RMSD to miara dokładności, która umożliwia porównanie błędów prognozowania różnych modeli dla określonego zestawu danych, a nie między zbiorami, ponieważ jest zależne od skali.|

Aby uzyskać więcej informacji na temat metryk regresji, przeczytaj następujące artykuły:

- [Analiza regresji: jak interpretować R-kwadrat i ocenić dobry stopień dopasowania?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Sposób interpretacji języka R-kwadratowego w analizie regresji](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definicja R-kwadratowa](https://www.investopedia.com/terms/r/r-squared.asp)
- [Średnia kwadratowa definicja błędu](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co to jest błąd kwadratowy i główny błąd oznaczający pierwiastek?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Metryki oceny dla klastra

| Metryki   |      Opis      |  Wyszukaj |
|----------|-----------------------|-----------|
|**Średnia odległość**|Średnia odległość między punktami danych a centrum przypisanego do niego klastra. Średnia odległość to miara bliskości punktów danych do centroids klastra. Jest to miara, w jaki sposób "ciasne" klastra jest.|Wartości bliżej **0** są lepsze. Im bliżej średniej wartości, tym bardziej klastrowane są dane. Należy pamiętać, że ta Metryka zmniejszy się, jeśli liczba klastrów zostanie zwiększona, a w skrajnym przypadku (gdzie każdy odrębny punkt danych jest własnym klastrem) będzie równa zero.
|**Indeks Davies Bouldin**|Średni stosunek odległości między klastrami i między nimi. Im ściślejszy klaster, a inne klastry to, tym niższa wartość to.|Wartości bliżej **0** są lepsze. Klastry, które są dalej i mniej rozpraszane, spowodują lepszy wynik.|
|**Znormalizowane informacje wzajemne**|Mogą być używane, gdy dane szkoleniowe używane do uczenia modelu klastrowania są również dostarczane z etykietami prawdy (czyli klastrowanie nadzorowane). Znormalizowana Metryka informacji wzajemnych mierzy, czy podobne punkty danych są przypisane do tego samego klastra, a różne punkty danych są przypisane do różnych klastrów. Znormalizowane informacje wzajemne to wartość z zakresu od 0 do 1|Wartości bliżej **1** są lepsze|

## <a name="evaluation-metrics-for-ranking"></a>Metryki oceny na potrzeby klasyfikowania

| Metryki   |      Opis      |  Wyszukaj |
|----------|-----------------------|-----------|
|**Obniżone zyski zbiorcze**|Rabat skumulowany (DCG) jest miarą jakości rankingu. Pochodzi ona z dwóch założeń. Jeden: wysoce istotne elementy są bardziej przydatne, gdy pojawiają się wyższe w kolejności klasyfikacji. Dwie: użyteczność śledzi istotność, im wyższa wartość istotności, tym bardziej użyteczny element. Łączny zysk z rabatem jest obliczany dla konkretnej pozycji w kolejności klasyfikacji. Sumuje ocenę przydatności podzieloną przez LOGARYTM indeksu klasyfikacji do pozycji zainteresowania. Jest on obliczany przy użyciu $ \ sum_ {i = 0} ^ {p} \frac {rel_i} {\ log_ {e} {i + 1}} $ oceny przydatności są dostarczane do algorytmu szkoleniowego klasyfikacji jako etykiety prawdy. Jedna wartość DCG jest dostarczana dla każdej pozycji w tabeli klasyfikacji, dlatego nazwa otrzymuje **zyski**zbiorcze. |**Wyższe wartości są lepsze**|
|**Znormalizowane zyski skumulowane z rabatem**|Normalizacja DCG umożliwia porównywanie metryk w przypadku list klasyfikacji o różnych długościach|**Wartości bliżej 1 są lepsze**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Metryki oceny na potrzeby wykrywania anomalii

| Metryki   |      Opis      |  Wyszukaj |
|----------|-----------------------|-----------|
|**Obszar pod krzywą ROC**|Obszar pod krzywą operatora odbiornika mierzy, jak dobrze model oddziela anomalie i zwykłe punkty danych.|**Wartości bliżej 1 są lepsze**. Tylko wartości większe niż 0,5 wykazują skuteczność modelu. Wartości 0,5 lub poniżej wskazują, że model nie jest lepszy niż losowo przydzielać dane do anomalii i zwykłych kategorii|
|**Częstotliwość wykrywania z fałszywą liczbą dodatnią**|Częstotliwość wykrycia z fałszywą liczbą dodatnią jest stosunkiem liczby prawidłowo zidentyfikowanych anomalii do całkowitej liczby anomalii w zestawie testów, indeksowanych przez każdy fałszywy wynik. Oznacza to, że istnieje wartość współczynnika wykrycia z fałszywą liczbą dodatnią dla każdego elementu fałszywie dodatnich.|**Wartości bliżej 1 są lepsze**. Jeśli nie ma żadnych fałszywie dodatnich, ta wartość jest równa 1|
