---
title: ML.NET metryki
description: Zrozumienie metryk, które są używane do oceny wydajności modelu ML.NET
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399218"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Oceń swój model ML.NET za pomocą metryk

Zapoznaj się z metrykami używanymi do oceny modelu ML.NET.

Metryki oceny są specyficzne dla typu zadania uczenia maszynowego, które wykonuje model.

Na przykład dla zadania klasyfikacji model jest oceniany przez pomiar, jak dobrze przewidywana kategoria pasuje do rzeczywistej kategorii. A w przypadku klastrowania ocena opiera się na tym, jak blisko są elementy klastrowane do siebie i jak wiele jest separacji między klastrami.

## <a name="evaluation-metrics-for-binary-classification"></a>Metryki oceny dla klasyfikacji binarnej

| Metryki   |      Opis      |  Szukać |
|-----------|-----------------------|-----------|
| **Dokładność** |  [Dokładność](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) jest proporcją poprawnych prognoz z zestawem danych testowych. Jest to stosunek liczby prawidłowych prognoz do całkowitej liczby próbek wejściowych. Działa dobrze, jeśli istnieje podobna liczba próbek należących do każdej klasy.| **Im bliżej 1.00, tym lepiej**. Ale dokładnie 1,00 wskazuje na problem (często: wyciek etykiety/celu, nadmierne dopasowanie lub testowanie danych szkoleniowych). Gdy dane testowe są niezrównoważone (gdzie większość wystąpień należą do jednej z klas), zestaw danych jest mały lub wyniki podejście 0,00 lub 1,00, a następnie dokładność naprawdę nie przechwytywać skuteczność klasyfikatora i trzeba sprawdzić dodatkowe metryki. |
| **Auc** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) lub *Obszar pod krzywą* mierzy obszar pod krzywą, utworzony przez zamiatanie rzeczywistej dodatniej stopy w porównaniu z fałszywie dodatnim wskaźnikiem.  |   **Im bliżej 1.00, tym lepiej**. Dla akceptowalnego modelu model powinien być większy niż 0,50. Model z AUC 0,50 lub mniej jest bezwartościowy. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) lub *Obszar pod krzywą krzywej precyzyjnego przywołania*: Przydatna miara powodzenia przewidywania, gdy klasy są nierówne (wysoce skośne zestawy danych). |  **Im bliżej 1.00, tym lepiej**. Wysokie wyniki blisko 1,00 pokazują, że klasyfikator zwraca dokładne wyniki (wysoka precyzja), a także zwraca większość wszystkich pozytywnych wyników (wysokie wycofanie). |
| **Wynik F1** | [F1 wynik](https://en.wikipedia.org/wiki/F1_score) znany również jako *zrównoważony F-score lub F-measure*. Jest to harmoniczny oznacza precyzji i przypomnieć. Wynik F1 jest pomocny, gdy chcesz uzyskać równowagę między precyzją a wycofaniem.| **Im bliżej 1.00, tym lepiej**.  Wynik F1 osiąga najlepszą wartość na 1,00 i najgorszy wynik na 0,00. Informuje, jak precyzyjny jest twój klasyfikator. |

Aby uzyskać więcej informacji na temat metryki klasyfikacji binarnej przeczytać następujące artykuły:

- [Dokładność, precyzja, wycofanie lub F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Klasyfikacja binarna Metryki klasy](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Relacja między krzywymi precision-recall i ROC](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Metryki oceny dla klasyfikacji wieloklasowej

| Metryki   |      Opis      |  Szukać |
|-----------|-----------------------|-----------|
| **Mikrodokładność** |  [Mikrośrednia dokładność](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje wkład y wszystkich klas, aby obliczyć średnią metrykę. Jest to ułamek wystąpień przewidzianych poprawnie. Mikrośrednia nie uwzględnia członkostwa w klasie. Zasadniczo każda para klasy próbki przyczynia się w równym stopniu do metryki dokładności. | **Im bliżej 1.00, tym lepiej**. W wieloklasowym zadaniu klasyfikacji mikrodokładność jest korzystna niż dokładność makro, jeśli podejrzewasz, że może istnieć nierównowaga klas (tj. możesz mieć o wiele więcej przykładów jednej klasy niż innych klas).|
| **Dokładność makro** | [Średnia dokładność makro](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) to średnia dokładność na poziomie klasy. Dokładność dla każdej klasy jest obliczana, a dokładność makro jest średnią tych dokładności. Zasadniczo każda klasa przyczynia się w równym stopniu do metryki dokładności. Klasy mniejszościowe mają taką samą wagę jak większe klasy. Metryka średniej makro daje taką samą wagę każdej klasie, niezależnie od liczby wystąpień z tej klasy, które zawiera zestaw danych. |  **Im bliżej 1.00, tym lepiej**.  Oblicza metrykę niezależnie dla każdej klasy, a następnie przyjmuje średnią (w związku z tym traktując wszystkie klasy jednakowo) |
| **Utrata dziennika**| [Strata logarytmiczny](http://wiki.fast.ai/index.php/Log_Loss) mierzy wydajność modelu klasyfikacji, gdzie dane wejściowe przewidywania jest wartość prawdopodobieństwa między 0,00 i 1,00. Utrata dziennika zwiększa się, gdy przewidywane prawdopodobieństwo odbiega od rzeczywistej etykiety. | **Im bliżej 0,00, tym lepiej**. Idealny model miałby utratę log-00. Celem naszych modeli uczenia maszynowego jest zminimalizowanie tej wartości.|
| **Redukcja strat w logowaniu** | [Zmniejszenie strat logarytmicznych](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) można interpretować jako zaletę klasyfikatora nad przewidywanielos.| **Waha się od -inf i 1.00, gdzie 1.00 jest doskonałe prognozy i 0,00 wskazuje średnie prognozy**. Na przykład, jeśli wartość jest równa 0,20, może być interpretowana jako "prawdopodobieństwo prawidłowego przewidywania jest o 20% lepsze niż przypadkowe zgadywanie"|

Mikrodokładność jest na ogół lepiej dostosowana do potrzeb biznesowych prognoz ML. Jeśli chcesz wybrać pojedynczą metrykę do wyboru jakości zadania klasyfikacji wieloklasowej, zazwyczaj powinna to być mikrodokładność.

Przykład, dla zadania klasyfikacji biletów pomocy technicznej: (mapy biletów przychodzących do zespołów pomocy technicznej)

- Mikrodokładność - jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?
- Makrodokładność - dla przeciętnego zespołu, jak często bilet przychodzący jest poprawny dla ich drużyny?

Makrodokładność nadwagi małych zespołów w tym przykładzie; mały zespół, który dostaje tylko 10 biletów rocznie liczy się tak samo jak duży zespół z 10k biletów rocznie. Mikro-dokładność w tym przypadku lepiej koreluje z potrzebami biznesowymi, "ile czasu / pieniędzy firma może zaoszczędzić, automatyzując mój proces routingu biletów".

Aby uzyskać więcej informacji na temat metryki klasyfikacji wieloklasowej przeczytać następujące artykuły:

- [Mikro- i makro-średnia precyzji, przywołania i f-score](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasyfikacja wieloklasowa z zestawem danych z nierównowagą](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Metryki oceny regresji i zalecenia

Zarówno regresji i zadania rekomendacji przewidzieć liczbę. W przypadku regresji liczba może być dowolną właściwością danych wyjściowych, na którą mają wpływ właściwości wejściowe. Dla rekomendacji liczba ta jest zwykle wartością klasyfikacji (na przykład od 1 do 5) lub zaleceniem tak/nie (reprezentowanym odpowiednio przez 1 i 0).

| Metryka   |      Opis      |  Szukać |
|----------|-----------------------|-----------|
| **R-kwadrat** |  [R-kwadrat (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)lub *Współczynnik oznaczania* reprezentuje moc predykcyjną modelu jako wartość między -inf a 1,00. 1.00 oznacza, że jest idealne dopasowanie, a dopasowanie może być arbitralnie słabe, więc wyniki mogą być negatywne. Wynik 0,00 oznacza, że model odgaduje oczekiwaną wartość etykiety. R2 mierzy, jak blisko rzeczywistych wartości danych testowych są do przewidywanych wartości. | **Im bliżej 1,00, tym lepsza jakość**. Jednak czasami niskie wartości R-kwadrat (takie jak 0,50) mogą być całkowicie normalne lub wystarczająco dobre dla scenariusza, a wysokie wartości r-kwadrat nie zawsze są dobre i podejrzane. |
| **Strata bezwzględna** |  [Strata bezwzględna](https://en.wikipedia.org/wiki/Mean_absolute_error) lub *średni błąd bezwzględny (MAE)* mierzy, jak blisko są prognozy do rzeczywistych wyników. Jest to średnia wszystkich błędów modelu, gdzie błąd modelu jest bezwzględną odległością między przewidywaną wartością etykiety a poprawną wartością etykiety. Ten błąd przewidywania jest obliczany dla każdego rekordu zestawu danych testowych. Na koniec średnia wartość jest obliczana dla wszystkich zarejestrowanych błędów bezwzględnych.| **Im bliżej 0,00, tym lepsza jakość.** Średni błąd bezwzględny używa tej samej skali co mierzone dane (nie jest znormalizowany do określonego zakresu). Strata bezwzględna, kwadratowa i strata rms mogą służyć tylko do porównywania modeli dla tego samego zestawu danych lub zestawu danych o podobnej dystrybucji wartości etykiety. |
| **Strata kwadratowa** |  [Kwadratowa strata](https://en.wikipedia.org/wiki/Mean_squared_error) lub *średni kwadratowy błąd (MSE),* zwany także *średnim odchyleniem kwadratowym (MSD),* informuje, jak blisko linii regresji jest zestaw wartości danych testowych, biorąc odległości od punktów do linii regresji (te odległości są błędy E) i kwadratury je. Kwadratury dają większą wagę większym różnicom. | Zawsze jest nieujemna, a **wartości bliższe 0,00 są lepsze.** W zależności od danych może być niemożliwe uzyskanie bardzo małej wartości dla średniego błędu kwadratowego.|
| **Utrata rms** |  [Strata RMS](https://en.wikipedia.org/wiki/Root-mean-square_deviation) lub *Średni błąd kwadratowy (RMSE)* (nazywany również *odchyleniem kwadratu głównego, RMSD),* mierzy różnicę między wartościami przewidywanymi przez model a wartościami obserwowanymi z modelowanego środowiska. RMS-loss jest pierwiastek kwadratowy squared-loss i ma te same jednostki co etykieta, podobne do bezwzględnej utraty choć dając większą wagę do większych różnic. Średni błąd kwadratowy katalogu głównego jest powszechnie używany w analizie klimatologii, prognozowania i regresji w celu zweryfikowania wyników eksperymentalnych. | Zawsze jest nieujemna, a **wartości bliższe 0,00 są lepsze.** RMSD jest miarą dokładności, aby porównać błędy prognozowania różnych modeli dla określonego zestawu danych, a nie między zestawami danych, ponieważ jest zależny od skali.|

Aby uzyskać więcej informacji na temat metryki regresji, przeczytaj następujące artykuły:

- [Analiza regresji: Jak interpretować R-squared i oceny dobroci-of-Fit?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretować R-kwadrat w analizie regresji](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definicja R-kwadrat](https://www.investopedia.com/terms/r/r-squared.asp)
- [Definicja średniego kwadratu błędu](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Co to są średnie kwadratowe błąd i root średni kwadratbłędny błąd?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Metryki oceny dla klastrowania

| Metryka   |      Opis      |  Szukać |
|----------|-----------------------|-----------|
|**Średnia odległość**|Średnia odległości między punktami danych a środkiem przypisanego klastra. Średnia odległość jest miarą bliskości punktów danych do centroid klastra. Jest to miara tego, jak "ciasny" jest klaster.|Wartości bliższe **0** są lepsze. Im bliżej zera jest średnia odległość, tym bardziej klastrowane są dane. Należy jednak zauważyć, że ta metryka zmniejszy się, jeśli liczba klastrów zostanie zwiększona, a w skrajnym przypadku (gdzie każdy odrębny punkt danych jest jego własny klaster) będzie równa zero.
|**Indeks Daviesa Bouldina**|Średni stosunek odległości w obrębie klastra do odległości między klastrami. Im mocniej klastra i dalej od klastrów są, tym niższa jest ta wartość.|Wartości bliższe **0** są lepsze. Klastry, które są dalej od siebie i mniej rozproszone spowoduje lepszy wynik.|
|**Znormalizowane wzajemne informacje**|Może być używany, gdy dane szkoleniowe używane do szkolenia modelu klastrowania również pochodzi z etykietprawdy ziemi (czyli nadzorowane klastrowania). Metryka Znormalizowane wzajemne informacje mierzy, czy podobne punkty danych są przypisywane do tego samego klastra, a różne punkty danych są przypisywane do różnych klastrów. Znormalizowane wzajemne informacje to wartość z wartością z rzędu 0–1|Wartości bliżej **1** są lepsze|

## <a name="evaluation-metrics-for-ranking"></a>Wskaźniki oceny dla rankingu

| Metryka   |      Opis      |  Szukać |
|----------|-----------------------|-----------|
|**Zdyskontowane skumulowane zyski**|Zdyskontowany zysk skumulowany (DCG) jest miarą jakości rankingu. Wynika to z dwóch założeń. Po pierwsze: Bardzo istotne elementy są bardziej przydatne, gdy pojawiają się wyżej w kolejności rankingu. Po drugie: Przydatność śledzi trafność, im większe znaczenie, tym bardziej przydatny element. Zdyskontowany zysk skumulowany jest obliczany dla określonej pozycji w kolejności. Podsumowuje klasyfikację istotności podzieloną przez logarytm indeksu rankingowego do pozycji zainteresowania. Jest on obliczany przy użyciu $\sum_{i=0}^{p} \frac {rel_i} {\log_{e}{i+1}}$ Sklasyfikowania istotności są dostarczane do algorytmu szkolenia rankingowego jako etykiety prawdy naziemnej. Dla każdej pozycji w tabeli rankingowej znajduje się jedna wartość DCG, stąd nazwa Zdyskontowane **zyski**skumulowane . |**Wyższe wartości są lepsze**|
|**Znormalizowane zdyskontowane zyski skumulowane**|Normalizacja DCG umożliwia porównywanie metryki dla list rankingowych o różnych długościach|**Wartości bliżej 1 są lepsze**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Metryki oceny dla wykrywania anomalii

| Metryka   |      Opis      |  Szukać |
|----------|-----------------------|-----------|
|**Obszar pod krzywą ROC**|Obszar pod krzywą operatora odbiornika mierzy, jak dobrze model oddziela nietypowe i zwykłe punkty danych.|**Wartości bliżej 1 są lepsze**. Tylko wartości większe niż 0,5 wykazują skuteczność modelu. Wartości 0,5 lub niższe wskazują, że model nie jest lepszy niż losowo przydzielanie danych wejściowych do nietypowych i zwykłych kategorii|
|**Wskaźnik wykrywania przy liczbie fałszywych alarmów**|Wskaźnik wykrywalności przy liczbie fałszywych alarmów jest stosunkiem liczby poprawnie zidentyfikowanych anomalii do całkowitej liczby anomalii w zestawie testów, indeksowanych przez każdy fałszywy alarm. Oznacza to, że istnieje wartość dla wskaźnika wykrywania z fałszywie dodatnią liczbą dla każdego elementu fałszywie dodatniego.|**Wartości bliżej 1 są lepsze**. Jeśli nie ma fałszywych alarmów, wartość ta wynosi 1|
