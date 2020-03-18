---
title: Co to jest Model Builder i jak działa?
description: Jak używać ML.NET Model Builder do automatycznego uczenia modelu uczenia maszynowego
ms.date: 01/07/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: cff4601843ec9ca7201ea7dbdbfbcfa18f50e46e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399225"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co to jest Model Builder i jak działa?

ML.NET Model Builder to intuicyjne graficzne rozszerzenie programu Visual Studio do tworzenia, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.

Program Model Builder używa automatycznego uczenia maszynowego (AutoML) do eksplorowania różnych algorytmów i ustawień uczenia maszynowego, aby ułatwić znalezienie tego, który najlepiej pasuje do twojego scenariusza.

Nie potrzebujesz wiedzy o uczeniu maszynowym, aby korzystać z modelu Konstruktora. Wszystko, czego potrzebujesz, to niektóre dane i problem do rozwiązania. Konstruktor modeli generuje kod, aby dodać model do aplikacji .NET.

![Animacja interfejsu użytkownika rozszerzenia programu Model Builder Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="scenarios"></a>Scenariusze

Można przynieść wiele różnych scenariuszy do konstruktora modeli, aby wygenerować model uczenia maszynowego dla aplikacji.

Scenariusz jest opistypu przewidywania, które chcesz zrobić przy użyciu danych. Przykład:

- przewidywanie przyszłej wielkości sprzedaży produktów na podstawie historycznych danych sprzedaży
- klasyfikować nastroje jako pozytywne lub negatywne na podstawie opinii klientów
- wykryć, czy transakcja bankowa jest oszukańcza
- kierowanie problemów z opiniami klientów do właściwego zespołu w twojej firmie

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Który scenariusz uczenia maszynowego jest dla mnie odpowiedni?

W Konstruktorze modeli należy wybrać scenariusz. Typ scenariusza zależy od typu przewidywania, który próbujesz zrobić.

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Przewidywanie kategorii (gdy istnieją tylko dwie kategorie)

Klasyfikacja binarna służy do kategoryzowania danych na dwie kategorie (tak/nie; pass/fail; true/false; positive/negative).

![Diagram przedstawiający przykłady klasyfikacji binarnej, w tym wykrywanie oszustw, ograniczanie ryzyka i sprawdzanie aplikacji](media/binary-classification-examples.png)

Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych nastrojów opinii klientów. Jest to przykład zadania uczenia maszynowego klasyfikacji binarnej.

Jeśli scenariusz wymaga klasyfikacji na dwie kategorie, można użyć tego szablonu z własnym zestawem danych.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Przewidywanie kategorii (gdy istnieją trzy lub więcej kategorii)

Klasyfikacja wieloklasowa może służyć do kategoryzowania danych na trzy lub więcej klas.

![Przykłady klasyfikacji wieloklasowej, w tym klasyfikacji dokumentów i produktów, routingu biletów pomocy technicznej i priorytetyzacji problemów klienta](media/multiclass-classification-examples.png)

Klasyfikacja problemów może służyć do kategoryzowania opinii klientów (na przykład w usłudze GitHub) problemów przy użyciu tytułu i opisu problemu. Jest to przykład wieloklasowego zadania uczenia maszynowego klasyfikacji.

Szablon klasyfikacji problemów dla scenariusza można użyć, jeśli chcesz podzielić dane na trzy lub więcej kategorii.

#### <a name="predict-a-number"></a>Przewidywanie liczby

Regresja służy do przewidywania liczb.

![Diagram przedstawiający przykłady regresji, takie jak przewidywanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

Przewidywanie cen może służyć do przewidywania cen domów za pomocą lokalizacji, wielkości i innych cech domu. Jest to przykład zadania uczenia maszynowego regresji.

Można użyć szablonu prognozowania cen dla scenariusza, jeśli chcesz przewidzieć wartość liczbową z własnego zestawu danych.

#### <a name="classify-images-into-categories"></a>Klasyfikowanie obrazów na kategorie

Ten scenariusz jest szczególnym przypadkiem klasyfikacji wieloklasowej, gdzie dane wejściowe, które mają być kategoryzowane jest zestaw obrazów.

Klasyfikacja obrazów może służyć do identyfikowania obrazów różnych kategorii. Na przykład różne rodzaje terenu lub zwierząt lub wady produkcyjne.

Można użyć szablonu klasyfikacji obrazów dla scenariusza, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy na różne kategorie.

#### <a name="custom-scenario"></a>Scenariusz niestandardowy

Scenariusz niestandardowy umożliwia ręczne wybranie scenariusza.

## <a name="data"></a>Dane

Po wybraniu scenariusza Konstruktor modeli prosi o podanie zestawu danych. Dane są używane do uczenia, oceny i wybrać najlepszy model dla scenariusza.

![Diagram przedstawiający kroki konstruktora modeli](media/model-builder-steps.png)

Program Model Builder obsługuje zestawy danych w formatach .tsv, csv, .txt, a także w formacie bazy danych SQL. Jeśli masz plik txt, kolumny powinny `,`być `;` `/t` oddzielone , a plik musi mieć wiersz nagłówka.

Jeśli zestaw danych składa się z obrazów, obsługiwane `.jpg` `.png`typy plików są i .

Aby uzyskać więcej informacji, zobacz [Ładowanie danych szkoleniowych do konstruktora modeli](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Wybierz dane wyjściowe do przewidzenia (etykieta)

Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów. Każdy wiersz ma:

- **etykieta** (atrybut, który chcesz przewidzieć)
- **(atrybuty,** które są używane jako dane wejściowe do przewidywania etykiety).

W scenariuszu prognozowania ceny domu funkcje mogą być następujące:

- kwadratowy materiał filmowy domu
- liczba sypialni i łazienek
- kod pocztowy

Etykieta jest historyczna cena domu dla tego rzędu kwadratowych materiału, sypialni i wartości łazienki i kodu pocztowego.

![Tabela przedstawiająca wiersze i kolumny danych o cenach domów z funkcjami składającymi się z kodu pocztowego pokoi i etykiety cenowej](media/model-builder-data.png)

### <a name="example-datasets"></a>Przykładowe zestawy danych

Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z następujących zestawów danych:

|Scenariusz|Zadanie ML|Dane|Label|Funkcje|
|-|-|-|-|-|
|Przewidywanie cen|Regresji|[dane dotyczące opłat za przejazd taksówką](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Taryfy|Czas podróży, odległość|
|Wykrywanie anomalii|klasyfikacja binarna|[dane o sprzedaży produktów](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Sprzedaż produktów|Month|
|Analiza tonacji|klasyfikacja binarna|[dane komentarza strony internetowej](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etykieta (0, gdy negatywne nastroje, 1, gdy dodatnie)|Komentarz, Rok|
|Wykrywanie oszustw|klasyfikacja binarna|[dane karty kredytowej](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)|Kwota, V1-V28 (funkcje zanonimizowane)|
|Klasyfikacja tekstu|klasyfikacja wieloklasowa|[Dane o problemach usługi GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Obszar|Tytuł, Opis|
|Klasyfikacja obrazów|klasyfikacja wieloklasowa|[Kwiaty obrazy](http://download.tensorflow.org/example_images/flower_photos.tgz)|Rodzaj kwiatu: stokrotka, mniszek lekarski, róże, słoneczniki, tulipany|Same dane obrazu|

## <a name="train"></a>Szkolenie

Po wybraniu scenariusza, danych i etykiety Konstruktor modeli szkoli model.

### <a name="what-is-training"></a>Co to jest szkolenie?

Szkolenie to automatyczny proces, za pomocą którego model Konstruktor nauczy model, jak odpowiadać na pytania dotyczące scenariusza. Po przeszkoleniu model może przewidywać dane wejściowe, których wcześniej nie widział. Na przykład, jeśli przewidujesz ceny domów i nowy dom wchodzi na rynek, możesz przewidzieć jego cenę sprzedaży.

Ponieważ Model Konstruktor używa automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani strojenia od ciebie podczas szkolenia.

### <a name="how-long-should-i-train-for"></a>Jak długo powinienem trenować?

Model Konstruktor używa automl do eksplorowania wielu modeli, aby znaleźć najlepszy model.

Dłuższe okresy treningowe umożliwiają automl eksplorowanie większej liczby modeli z szerszym zakresem ustawień.

W poniższej tabeli podsumowano średni czas, który został umówiony na uzyskanie dobrej wydajności dla zestawu przykładowych zestawów danych na komputerze lokalnym.

|Rozmiar zestawu danych|Średni czas szkolenia|
|------------|---------------------|
|0 - 10 MB|10 sek.|
|10 - 100 MB|10 min.|
|100 - 500 MB|30 min.|
|500 - 1 GB|60 min.|
|1 GB+|3+ godzin|

Liczby te są tylko przewodnikiem. Dokładna długość szkolenia zależy od:

- liczba obiektów (kolumn) używanych jako dane wejściowe do modelu
- typ kolumn
- zadanie ML
- wydajność procesora, dysku i pamięci urządzenia używanego do szkolenia

## <a name="evaluate"></a>Evaluate

Ocena to proces pomiaru, jak dobry jest twój model. Konstruktor modeli używa uczonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są prognozy.

Konstruktor modeli dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testów. Dane szkoleniowe (80%) służy do szkolenia modelu i danych testowych (20%) jest wstrzymywana do oceny modelu.

### <a name="how-do-i-understand-my-model-performance"></a>Jak zrozumieć wydajność modelu?

Scenariusz jest mapowany do zadania uczenia maszynowego. Każde zadanie ml ma swój własny zestaw metryk oceny.

#### <a name="regression-for-example-price-prediction"></a>Regresja (na przykład przewidywanie cen)

Domyślną metryką dla problemów z regresją jest RSquared, wartość RSquared waha się od 0 do 1. 1 jest najlepszą możliwą wartością lub innymi słowy, im bliżej wartości RSquared do 1, tym lepiej radzi sobie twój model.

Inne metryki zgłaszane, takie jak strata bezwzględna, kwadratowa strata i strata rms są dodatkowe metryki, które mogą służyć do zrozumienia, jak model działa i porównanie go z innymi modelami regresji.

#### <a name="binary-classification-for-example-sentiment-analysis"></a>Klasyfikacja binarna (na przykład analiza tonacji)

Domyślną metryką problemów z klasyfikacją jest dokładność. Dokładność definiuje proporcję poprawnych prognoz modelu jest wykonywanie za pomocą zestawu danych testowych. Im bliżej 100% lub 1,0, tym lepiej.

Inne zgłoszone wskaźniki, takie jak AUC (Obszar pod krzywą), który mierzy rzeczywistą dodatnią szybkość w porównaniu z fałszywie dodatnim wskaźnikiem, powinny być większe niż 0,50, aby modele były akceptowalne.

Dodatkowe metryki, takie jak wynik F1 może służyć do kontrolowania równowagi między precyzji i odwołania.

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a>Klasyfikacja wieloklasowa (na przykład klasyfikacja wydania, klasyfikacja obrazów)

Domyślną metryką dla klasyfikacji wieloklasowej jest Mikrodokładność. Im bliżej Mikro dokładności do 100% lub 1,0, tym lepiej.

Inną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobna do mikrodokładności im bliżej 1.0, tym lepiej. Dobrym sposobem myślenia o tych dwóch rodzajach dokładności jest:

- Mikrodokładność: Jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?
- Makrodokładność: Jak często bilet przychodzący jest prawidłowy dla ich drużyny?

### <a name="more-information-on-evaluation-metrics"></a>Więcej informacji na temat wskaźników oceny

Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).

## <a name="improve"></a>Poprawić

Jeśli wynik wydajności modelu nie jest tak dobry, jak chcesz, możesz:

- Trenuj przez dłuższy czas. Z więcej czasu, aparat automatycznego uczenia maszynowego, aby wypróbować więcej algorytmów i ustawień.

- Dodaj więcej danych. Czasami ilość danych nie jest wystarczająca do nauczenia modelu uczenia maszynowego wysokiej jakości.

- Zrównoważ swoje dane. W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach. Na przykład jeśli masz cztery klasy na 100 przykładów szkolenia, a dwie pierwsze klasy (tag1 i tag2) są używane dla 90 rekordów, ale pozostałe dwie (tag3 i tag4) są używane tylko w pozostałych 10 rekordach, brak zrównoważonych danych może spowodować, że model będzie miał problemy z poprawnie przewidzieć tag3 lub tag4.

## <a name="code"></a>Code

Po fazie oceny Konstruktor modeli generuje plik modelu i kod, którego można użyć do dodania modelu do aplikacji. ML.NET modele są zapisywane jako plik zip. Kod do załadowania i używania modelu jest dodawany jako nowy projekt w rozwiązaniu. Konstruktor modeli dodaje również przykładową aplikację konsoli, którą można uruchomić, aby zobaczyć model w działaniu.

Ponadto Konstruktor modeli generuje kod, który wygenerował model, dzięki czemu można zrozumieć kroki używane do generowania modelu. Można również użyć kodu szkolenia modelu do ponownego uczenia modelu z nowymi danymi.

## <a name="whats-next"></a>Co dalej?

[Instalowanie](how-to-guides/install-model-builder.md) rozszerzenia programu Visual Studio dla konstruktora modeli

[Wypróbuj prognozę cen lub scenariusz regresji](tutorials/predict-prices-with-model-builder.md)
