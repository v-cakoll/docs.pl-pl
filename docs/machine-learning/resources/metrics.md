---
title: Metryki strukturze ML.NET
description: Omówienie metryk, które są używane do oceny wydajności na model w strukturze ML.NET
ms.date: 04/29/2019
author: ''
ms.openlocfilehash: 802f0a8fd32c492c8d9f89933b183802cb178cb3
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053039"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Metryki oceny model w strukturze ML.NET

## <a name="metrics-for-binary-classification"></a>Metryki dla klasyfikacji binarnej

| Metryki   |      Opis      |  Szukać |
|-----------|-----------------------|-----------|
| **Accuracy** |  [Dokładność](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) to poprawne prognoz z zestawem danych testowych. To stosunek liczby poprawne prognoz całkowitą liczbę próbek danych wejściowych. Działa to dobrze tylko w przypadku podobną liczbę próbek należących do każdej klasy.| **Bliżej 1,00, tym lepsze**. Ale 1,00 dokładnie oznacza problem związany (często: Etykieta docelowa wycieku nadmiernie dopasowane i testowania przy użyciu danych szkoleniowych). Gdy jest dane testowe niezrównoważone (gdzie większość wystąpień należą do jednej z klas), zestaw danych jest bardzo mały lub wyniki podejście 0,00 lub 1,00, a dokładność tak naprawdę nie odzwierciedla skuteczność klasyfikatora należy sprawdzić dodatkowe metryki. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) lub *powierzchni pod krzywą*: Jest to pomiar obszar pod krzywą utworzone przez sprawdzaniu true na dodatnich a fałszywie dodatnich.  |   **Bliżej 1,00, tym lepsze**. Powinien być większy niż 0,50 modelu do przyjęcia; Optymalizacja jest model przy użyciu AUC 0,50 lub mniej. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) lub *powierzchni pod krzywą krzywych Precision-Recall*: Przydatne pomiar sukcesu prognozowania, gdy klasy są bardzo imbalanced (wysoce niesymetryczne zbiory danych). |  **Bliżej 1,00, tym lepsze**. Wysoka wyniki zbliżone do wartości 1.00 show, że klasyfikatora jest zwracanie dokładne wyniki (dużej dokładności), a także zwracanie większość wszystkich wyników pozytywnych (wycofaniu wysoki). |
| **Wynik F1** | [Wynik F1](https://en.wikipedia.org/wiki/F1_score) znany także jako *równoważenia wynik F lub F-miary*. Jest harmoniczna dokładności i odwołania. Wynik F1 jest przydatne, gdy chcesz wyszukać równowagi między dokładności i odwołania.| **Bliżej 1,00, tym lepsze**.  Wynik F1 osiągnie swojej wartości najlepsze 1.00 i najgorszego wyniku w 0,00. Informuje, jak dokładne jest klasyfikatora. |

Aby uzyskać dodatkowe szczegóły dotyczące klasyfikacji binarnej metryki, przeczytaj następujące artykuły:

- [Dokładność, dokładności, odwołań lub F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Binarny klasy metryki klasyfikacji](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Relacja między Precision-Recall oraz ROC krzywych](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Metryki dla klasyfikacji wieloklasowej

| Metryki   |      Opis      |  Szukać |
|-----------|-----------------------|-----------|
| **Micro dokładności** |  [Średnia Micro dokładność](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) agreguje wkładów wszystkich klas do obliczenia średniej metryki. Jest to ułamek wystąpień poprawnie przewidzieć. Średnia micro nie przyjmuje członkostwa klasy pod uwagę. Po prostu każdej pary przykładową klasę przyczynia się jednakowo do metryki dokładności. | **Bliżej 1,00, tym lepsze**. W zadaniu klasyfikacji wieloklasowej micro dokładności jest za pośrednictwem makra dokładność Jeśli podejrzewasz, że może to być nierównowagi klasy (tj.) Możesz mieć wiele więcej przykładów dotyczących jednej klasy niż inne klasy).|
| **Dokładność — makro** | [Średnia — makro dokładność](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) jest średnia dokładności na poziomie klasy. Dokładność dla każdej klasy jest kolumną obliczaną, a dokładność — makro jest średnią te dokładności. Zasadniczo każda klasa przyczynia się jednakowo do metryki dokładności. Moduł klasy są podane weight równe jako większych klas. Metryki średnia — makro daje tymi samymi wagami do każdej klasy, niezależnie od tego, ile wystąpień przy jego użyciu zawiera klasę zestawu danych. |  **Bliżej 1,00, tym lepsze**.  Ją oblicza metryki niezależnie dla każdej klasy, a następnie pobiera średnia (dlatego traktowanie wszystkich klas równie) |
| **Log-loss**| [Logarytmicznej utraty](http://wiki.fast.ai/index.php/Log_Loss) mierzy wydajność model klasyfikacji, w których dane wejściowe prognozy są wartość prawdopodobieństwa między 0,00 i 1,00. Utraty dziennika zwiększa prawdopodobieństwo, że dostęp do przewidywanych diverges od rzeczywistej etykiety. | **Bliżej 0,00, tym lepsze**. Idealny model musi utraty dziennika 0,00. Celem naszych modeli uczenia maszynowego jest zminimalizowanie tę wartość.|
| **Zmniejszenie dziennika strat** | [Zmniejszenie logarytmicznej strat](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) może być interpretowana jako zalet klasyfikatora względem prognoz losowych.| **W zakresie od -inf i 1,00, gdzie 1,00 to doskonałe prognoz, a 0,00 wskazuje średnią prognozy**. Na przykład jeśli wartość jest równa 0.20 lub nowszej, jego mogą być interpretowane jako "prawdopodobieństwo, że prawidłowe przewidywanie wynosi 20% lepsze niż losowe zgadywania"|

Dokładność Micro ogólnie jest lepiej wyrównane z potrzebami biznesowymi prognoz uczenia Maszynowego. Chcącym jednej metryki dotyczące wybierania jakość zadanie klasyfikacji wieloklasowej zwykle należy micro dokładności.

Przykład zadanie klasyfikacji bilet pomocy technicznej: (mapuje przychodzące bilety do obsługi zespołów)

- Dokładność Micro — jak często bilet usługi w przychodzących Pobierz sklasyfikowane na odpowiedni zespół?
- Dokładność — makro — średnia zespołu, jak często jest bilet usługi w przychodzących poprawne dla swojego zespołu?

Dokładność — makro overweights małych zespołów, w tym przykładzie; małych zespołów, które pobiera tylko 10 bilety na rok traktowany jak duży zespół o 10k biletów na rok. Dokładność Micro w tym przypadku jest odwrotnie skorelowana lepiej z potrzeb biznesowych dla "czasu/zarobków można firmy Zapisz dzięki automatyzacji procesu routingu Moje biletu".

Aby uzyskać dodatkowe szczegóły dotyczące klasyfikacji wieloklasowej metryki, przeczytaj następujące artykuły:

- [Średnia Micro i makra, które dokładności, odwołania i ocena F](http://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Klasyfikacji wieloklasowej Imbalanced zestawu danych](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Metryki dotyczące regresji

| Metryki   |      Opis      |  Szukać |
|-----------|-----------------------|-----------|
| **R-kwadrat** |  [R-kwadrat (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination), lub *determinacji* reprezentuje możliwości predykcyjnego modelu jako wartość z zakresu od -inf 1,00. 1,00 oznacza, że istnieje dokładne dopasowanie i dopasowania mogą być arbitrarly niską wyniki. może być ujemna. Ocena oznacza 0,00 modelu jest zgadywania oczekiwanej wartości dla etykiety. R2 środków, jak blisko wartości danych rzeczywistych testów są przewidywane wartości. | **Bliżej 1,00, lepszą jakość**. Jednak czasami niskich wartości R-kwadrat (na przykład 0,50) może być całkowicie normalne lub wystarczające dla danego scenariusza i wysokich wartości R-kwadrat nie zawsze są dobre i się podejrzane. |
| **Utrata bezwzględne** |  [Bezwzględna utraty](https://en.wikipedia.org/wiki/Mean_absolute_error) lub *średni bezwzględny błąd (dostosowania)* mierzy się, jak blisko prognozy są rzeczywiste wyniki. Jest średnią wszystkich błędów modelu, gdzie błąd modelu jest bezwzględny odległość między wartości prognozowanej etykiety i wartość prawidłowa etykieta. Ten błąd prognozowania jest obliczana dla każdego rekordu testowego zestawu danych. Na koniec średnią wartość jest obliczana dla wszystkich zarejestrowanych bezwzględnych błędów.| **Bliżej 0,00, lepszą jakość.** Należy pamiętać, że średni bezwzględny błąd używa tej samej skali z danymi, mierzony (nie jest znormalizowana do określonego zakresu). Do dokonywania porównań między modelami dla tego samego zestawu danych lub zestaw danych o rozkład wartości podobne etykietę tylko można utraty bezwzględną, utraty Squared i utratę usługi RMS. |
| **Squared-loss** |  [Utrata Squared](https://en.wikipedia.org/wiki/Mean_squared_error) lub *oznacza kwadrat błędu (MSE)*, nazywane również *oznacza kwadrat odchylenia (MSD)*, informujący o tym, jak blisko linii regresji ma zestaw wartości danych testowych. Odbywa się to przez pobranie odległości od punktów do regresji (odległości te są błędy E) i squaring je. Squaring daje więcej wagę do większych różnice. | Zawsze jest ujemna, i **wartości bliższe 0,00 są lepsze**. W zależności od danych może być niemożliwe uzyskać bardzo małych wartości średniej kwadratów błędów.|
| **RMS-loss** |  [RMS utraty](https://en.wikipedia.org/wiki/Root-mean-square_deviation) lub *głównego oznacza kwadrat błąd (RMSE)* (nazywane również *odchylenie skuteczną, RMSD*), faktycznie mierzy różnią się przewidzieć przez model wartości i wartości obserwowane ze środowiska, które są w modelu. Utrata usługi RMS jest pierwiastek kwadratowy utraty Squared i ma te same jednostki jako etykieta, podobnie jak utrata bezwzględnymi, chociaż przyznawania ważniejsze większych różnice. Błąd głównego średniej kwadratowej jest najczęściej używany w klimatologia, prognozowania i analizę regresji do zweryfikować eksperymentalne wyniki. | Zawsze jest ujemna, i **wartości bliższe 0,00 są lepsze**. RMSD jest miarą dokładności, aby porównać prognozowania błędy różne modele dla określonego zestawu danych i nie między zestawami danych, ponieważ jest zależna od skali.|

Aby uzyskać dodatkowe szczegóły dotyczące regresji metryki, przeczytaj następujące artykuły:

- [Analizę regresji: Jak interpretować R-kwadrat i ocenić zgodność Dopasuj?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Jak interpretować R-kwadrat w analizę regresji](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [Definicja języka R-kwadrat](https://www.investopedia.com/terms/r/r-squared.asp)
- [Średni kwadrat definicji błędu](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Jakie są oznacza błąd kwadrat i błąd oznacza kwadrat główny?](https://www.vernier.com/til/1014/)
