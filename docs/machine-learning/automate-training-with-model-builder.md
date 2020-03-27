---
title: Co to jest Kreator modeli i jak działa?
description: Jak automatycznie szkolić model uczenia maszynowego za pomocą ML.NET Programu Model Builder
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344768"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co to jest Kreator modeli i jak działa?

ML.NET Model Builder to intuicyjne graficzne rozszerzenie programu Visual Studio do tworzenia, szkolenia i wdrażania niestandardowych modeli uczenia maszynowego.

Kreator modeli używa automatycznego uczenia maszynowego (AutoML) do eksplorowania różnych algorytmów i ustawień uczenia maszynowego, aby ułatwić znalezienie tego, który najlepiej odpowiada twojemu scenariuszowi.

Nie potrzebujesz wiedzy specjalistycznej w zakresie uczenia maszynowego, aby korzystać z kreatora modeli. Wszystko, czego potrzebujesz, to dane i problem do rozwiązania. Kreator modeli generuje kod, aby dodać model do aplikacji .NET.

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio programu Model Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Kreator modeli jest obecnie w wersji zapoznawczej.

## <a name="scenario"></a>Scenariusz

Można przynieść wiele różnych scenariuszy do konstruktora modelu, aby wygenerować model uczenia maszynowego dla aplikacji.

Scenariusz to opis typu prognozowania, które chcesz wprowadzić przy użyciu danych. Przykład:

- przewidywanie przyszłej wielkości sprzedaży produktu na podstawie historycznych danych o sprzedaży
- klasyfikowanie nastrojów jako pozytywnych lub negatywnych na podstawie opinii klientów
- wykrywanie, czy transakcja bankowa jest oszukańcza
- rozsyłanie problemów z opiniami klientów do właściwego zespołu w firmie

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Który scenariusz uczenia maszynowego jest dla mnie odpowiedni?

W Kreatorze modeli należy wybrać scenariusz. Typ scenariusza zależy od tego, jaki typ prognozowania próbujesz zrobić.

#### <a name="text-classification"></a>Klasyfikacja tekstu

Klasyfikacja służy do kategoryzowanie danych na kategorie.

![Diagram przedstawiający przykłady klasyfikacji binarnej, w tym wykrywanie oszustw, ograniczanie ryzyka i monitorowanie aplikacji](media/binary-classification-examples.png)

![Przykłady klasyfikacji wieloklasowej, w tym klasyfikacja dokumentów i produktów, routing biletów pomocy technicznej i ustalanie priorytetów problemów klientów](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>Przewidywanie wartości

Regresja jest używana do przewidywania liczb.

![Diagram przedstawiający przykłady regresji, takie jak przewidywanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

#### <a name="image-classification"></a>Klasyfikacja obrazów

Klasyfikacja obrazów może służyć do identyfikowania obrazów różnych kategorii. Na przykład różne rodzaje terenu lub zwierząt lub wady produkcyjne.

Można użyć scenariusza klasyfikacji obrazów, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy do różnych kategorii.

#### <a name="recommendation"></a>Zalecenie

Scenariusz rekomendacji przewiduje listę sugerowanych elementów dla określonego użytkownika, na podstawie tego, jak podobne są ich polubienia i antypatie do innych użytkowników".

Możesz użyć scenariusza rekomendacji, gdy masz zestaw użytkowników i zestaw "produktów", takich jak produkty do zakupu, filmy, książki lub programy telewizyjne, wraz z zestawem "ocen" tych produktów przez użytkowników.

## <a name="environment"></a>Środowisko

Model uczenia maszynowego można trenować lokalnie na komputerze lub w chmurze na platformie Azure.

Podczas szkolenia lokalnego, pracujesz w ramach ograniczeń zasobów komputera (procesora CPU, pamięci i dysku). Podczas szkolenia w chmurze, można skalować zasoby w górę, aby spełnić wymagania scenariusza, szczególnie dla dużych zestawów danych.

Szkolenie lokalne jest obsługiwane dla wszystkich scenariuszy.

Szkolenie platformy Azure jest obsługiwane dla klasyfikacji obrazów.

## <a name="data"></a>Dane

Po wybraniu scenariusza Kreator modelu prosi o podanie zestawu danych. Dane są używane do szkolenia, oceny i wybierz najlepszy model dla scenariusza.

![Diagram przedstawiający kroki Konstruktora modeli](media/model-builder-steps.png)

Program Model Builder obsługuje zestawy danych w formatach .tsv, csv, .txt, a także w formacie bazy danych SQL. Jeśli masz plik txt, kolumny powinny być `,`oddzielone `/t` lub, `;` a plik musi mieć wiersz nagłówka.

Jeśli zestaw danych składa się z obrazów, obsługiwane `.jpg` `.png`typy plików są i .

Aby uzyskać więcej informacji, zobacz [Ładowanie danych szkoleniowych do kreatora modeli](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Wybierz dane wyjściowe do przewidzenia (etykieta)

Zestaw danych to tabela wierszy przykładów treningu i kolumn atrybutów. Każdy wiersz ma:

- **etykieta** (atrybut, który chcesz przewidzieć)
- **funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiety).

W przypadku scenariusza przewidywania ceny domu funkcje mogą być:

- kwadratowy materiał z domu
- liczba sypialni i łazienek
- kod pocztowy

Etykieta jest historyczną ceną domu dla tego rzędu kwadratowych materiałów, sypialni i wartości łazienki i kodu pocztowego.

![Tabela przedstawiająca wiersze i kolumny danych o cenie domu z funkcjami składającymi się z kodu pocztowego pokoi wielkości i etykiety cenowej](media/model-builder-data.png)

### <a name="example-datasets"></a>Przykładowe zestawy danych

Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z następujących zestawów danych:

|Scenariusz|Przykład|Dane|Label|Funkcje|
|-|-|-|-|-|
|Klasyfikacja|Przewidywanie anomalii sprzedaży|[dane dotyczące sprzedaży produktów](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Sprzedaż produktów|Month|
||Przewidywanie nastrojów komentarzy na stronie internetowej|[dane dotyczące komentarzy do witryny](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etykieta (0, gdy negatywne nastroje, 1, gdy dodatnie)|Komentarz, Rok|
||Przewidywanie nieuczciwych transakcji kartą kredytową|[dane karty kredytowej](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Klasa (1, gdy oszukańcze, 0 w przeciwnym razie)|Kwota, V1-V28 (funkcje zanonimizowane)|
||Przewidywanie typu problemu w repozytorium Usługi GitHub|[Dane o problemie z githubem](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Obszar|Tytuł, Opis|
|Przewidywanie wartości|Przewiduj cenę taryfy taksówek|[dane dotyczące taryfy taksówek](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Taryfy|Czas podróży, odległość|
|Klasyfikacja obrazów|Przewidywanie kategorii problemu|[obrazy kwiatów](http://download.tensorflow.org/example_images/flower_photos.tgz)|Rodzaj kwiatu: stokrotka, mniszek lekarski, róże, słoneczniki, tulipany|Same dane obrazu|
|Zalecenie|Przewiduj filmy, które komuś się spodobają|[oceny filmów](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|Użytkownicy, Filmy|Klasyfikacje|

## <a name="train"></a>Szkolenie

Po wybraniu scenariusza, danych i etykiety, Model Builder trenuje modelu.

### <a name="what-is-training"></a>Co to jest szkolenie?

Szkolenie to automatyczny proces, w którym kreator modelu uczy modelu, jak odpowiedzieć na pytania dotyczące scenariusza. Po przeszkoleniu modelu można dokonać prognoz z danych wejściowych, które nie widział wcześniej. Na przykład, jeśli przewidujesz ceny domów i nowy dom pojawia się na rynku, możesz przewidzieć jego cenę sprzedaży.

Ponieważ program Model Builder używa automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania od ciebie podczas szkolenia.

### <a name="how-long-should-i-train-for"></a>Jak długo powinienem trenować?

Kreator modeli używa automl do eksplorowania wielu modeli, aby znaleźć model o najlepszej wydajności.

Dłuższe okresy treningowe umożliwiają automl eksplorowanie większej liczby modeli z szerszym zakresem ustawień.

W poniższej tabeli podsumowano średni czas wykonania pakietu przykładowych zestawów danych na komputerze lokalnym.

|Rozmiar zestawu danych|Średni czas szkolenia|
|------------|---------------------|
|0 - 10 MB|10 sek.|
|10 - 100 MB|10 min.|
|100 - 500 MB|30 min.|
|500 - 1 GB|60 min.|
|1 GB+|3+ godzin|

Te liczby są tylko przewodnikiem. Dokładna długość szkolenia zależy od:

- liczba obiektów (kolumn) używanych jako dane wejściowe do modelu
- typ kolumn
- zadanie ML
- wydajność procesora, dysku i pamięci urządzenia używanego do treningu

## <a name="evaluate"></a>Evaluate

Ocena to proces pomiaru, jak dobry jest Twój model. Kreator modeli używa uczonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są prognozy.

Kreator modeli dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testów. Dane szkoleniowe (80%) służy do szkolenia modelu i danych testowych (20%) zostanie wstrzymana w celu oceny modelu.

### <a name="how-do-i-understand-my-model-performance"></a>Jak zrozumieć wydajność modelu?

Scenariusz mapuje zadanie uczenia maszynowego. Każde zadanie uczenia maszynowego ma swój własny zestaw metryk oceny.

#### <a name="value-prediction"></a>Przewidywanie wartości

Domyślną metryką problemów z przewidywaniem wartości jest RSquared, wartość RSquared waha się od 0 do 1. 1 jest najlepszą możliwą wartością lub innymi słowy im bliżej wartości RSquared do 1, tym lepszy model wykonuje.

Inne metryki zgłaszane, takie jak bezwzględna strata, strata kwadratowa i strata usługi RMS to dodatkowe metryki, których można użyć do zrozumienia działania modelu i porównania go z innymi modelami przewidywania wartości.

#### <a name="classification-2-categories"></a>Klasyfikacja (2 kategorie)

Domyślną metryką problemów z klasyfikacją jest dokładność. Dokładność definiuje proporcję poprawnych prognoz, które model tworzy za pomocą zestawu danych testowych. Im bliżej 100% lub 1,0 tym lepiej.

Inne zgłaszane wskaźniki, takie jak AUC (Obszar pod krzywą), który mierzy rzeczywistą dodatnią stopę w porównaniu z fałszywie dodatnim wskaźnikiem powinny być większe niż 0,50 dla modeli, które mają być dopuszczalne.

Dodatkowe metryki, takie jak wynik F1 może służyć do kontrolowania równowagi między Precision i Recall.

#### <a name="classification-3-categories"></a>Klasyfikacja (3+ kategorie)

Domyślną metryką dla klasyfikacji wieloklasowej jest mikrodyskość. Im bliżej mikrodemy do 100% lub 1,0, tym lepiej.

Inną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobna do mikrodyskności im bliżej 1.0, tym lepiej. Dobrym sposobem na zastanowienie się nad tymi dwoma typami dokładności jest:

- Mikrodyskłańca: Jak często przychodzący bilet jest klasyfikowany do właściwego zespołu?
- Makrodność: Jak często bilet przychodzący jest poprawny dla swojej drużyny?

### <a name="more-information-on-evaluation-metrics"></a>Więcej informacji na temat wskaźników oceny

Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).

## <a name="improve"></a>Poprawić

Jeśli wynik wydajności modelu nie jest tak dobry, jak chcesz, możesz:

- Trenuj przez dłuższy czas. Z więcej czasu, zautomatyzowany aparat uczenia maszynowego eksperymenty z więcej algorytmów i ustawień.

- Dodaj więcej danych. Czasami ilość danych nie jest wystarczająca do przeszkolenia modelu uczenia maszynowego wysokiej jakości.

- Zrównoważyć swoje dane. W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony między kategoriami. Na przykład, jeśli masz cztery klasy dla 100 przykładów treningu, a dwie pierwsze klasy (tag1 i tag2) są używane dla 90 rekordów, ale pozostałe dwie (tag3 i tag4) są używane tylko w pozostałych 10 rekordach, brak zrównoważonych danych może spowodować, że model będzie miał problemy z poprawnie przewidzieć tag3 lub tag4.

## <a name="code"></a>Code

Po fazie oceny Program Model Builder wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji. ML.NET modele są zapisywane jako plik zip. Kod do ładowania i używania modelu jest dodawany jako nowy projekt w rozwiązaniu. Kreator modeli dodaje również przykładową aplikację konsoli, którą można uruchomić, aby wyświetlić model w działaniu.

Ponadto Program Model Builder wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć kroki używane do generowania modelu. Można również użyć kodu szkolenia modelu do ponownego przeszkolenia modelu z nowymi danymi.

## <a name="whats-next"></a>Co dalej?

[Instalowanie](how-to-guides/install-model-builder.md) rozszerzenia programu Visual Studio programu Builder

Wypróbuj [przewidywanie cen lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)
