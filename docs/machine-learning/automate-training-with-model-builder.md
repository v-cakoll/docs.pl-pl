---
title: Co to jest Konstruktor modelu i jak to działa?
description: Jak korzystać z konstruktora modelu ML.NET w celu automatycznego uczenia modelu uczenia maszynowego
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777392"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co to jest Konstruktor modelu i jak to działa?

Konstruktor modelu ML.NET to intuicyjne graficzne rozszerzenie programu Visual Studio służące do kompilowania, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.

Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), aby poznać różne algorytmy uczenia maszynowego i ustawienia, które ułatwiają znalezienie tego, który najlepiej odpowiada Twojemu scenariuszowi.

Nie musisz uczyć się uczenia maszynowego, aby korzystać z konstruktora modeli. Wystarczy kilka danych i problem do rozwiązania. Konstruktor modelu generuje kod umożliwiający dodanie modelu do aplikacji .NET.

![Animacja interfejsu użytkownika rozszerzenia programu Visual Studio Builder](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="scenarios"></a>Scenariusze

W celu wygenerowania modelu uczenia maszynowego dla aplikacji można przenieść wiele różnych scenariuszy do programu model Builder.

Scenariusz to opis typu przewidywania, które chcesz wprowadzić przy użyciu danych. Na przykład:

- przewidywanie przyszłego wolumenu sprzedaży produktu na podstawie historycznych danych sprzedaży
- Klasyfikuj mową jako dodatnie lub ujemne na podstawie recenzji klienta
- Wykryj, czy transakcja bankowa jest fałszywa
- kierowanie problemów z opiniami klientów do właściwego zespołu w firmie

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Który scenariusz uczenia maszynowego jest dla mnie właściwy?

W konstruktorze modelu należy wybrać scenariusz. Typ scenariusza zależy od typu przewidywania, które próbujesz wprowadzić.

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Przewidywanie kategorii (jeśli istnieją tylko dwie kategorie)

Klasyfikacja binarna służy do kategoryzowania danych w dwóch kategoriach (tak/nie; Pass/Fail; true/false; wartość dodatnia/ujemna).

![Diagram przedstawiający przykłady klasyfikacji danych binarnych, w tym wykrywanie oszustw, łagodzenie ryzyka i osłanianie aplikacji](media/binary-classification-examples.png)

Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych tonacji opinii klientów. Jest to przykładowe zadanie uczenia maszynowego w klasyfikacji binarnej.

Jeśli scenariusz wymaga klasyfikacji do dwóch kategorii, można użyć tego szablonu z własnym zestawem danych.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Przewidywanie kategorii (jeśli istnieją trzy lub więcej kategorii)

Klasyfikacji wieloklasowej można użyć do kategoryzowania danych w trzech lub większej liczbie klas.

![Przykłady klasyfikacji wieloklasowej, w tym Klasyfikacja dokumentów i produktów, obsługa routingu biletów i problemów klientów](media/multiclass-classification-examples.png)

Klasyfikacja problemu może służyć do kategoryzowania opinii klientów (na przykład w witrynie GitHub) przy użyciu tytułu i opisu problemu. Przykładem jest zadanie uczenia maszynowego z wieloklasową klasyfikacją.

Możesz użyć szablonu klasyfikacji problemu dla danego scenariusza, jeśli chcesz podzielić dane na trzy lub więcej kategorii.

#### <a name="predict-a-number"></a>Przewidywanie liczby

Regresja służy do przewidywania liczby.

![Diagram przedstawiający przykłady regresji, takie jak prognozowanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

Funkcja prognozowania cen może służyć do przewidywania cen domu przy użyciu lokalizacji, rozmiaru i innych cech domu. Jest to przykładowe zadanie uczenia maszynowego.

Możesz użyć szablonu prognozowania cen dla danego scenariusza, jeśli chcesz prognozować wartość liczbową przy użyciu własnego zestawu danych.

#### <a name="classify-images-into-categories"></a>Klasyfikowanie obrazów do kategorii

Ten scenariusz jest specjalnym przypadkiem klasyfikacji wieloklasowej, gdzie dane wejściowe, które mają być klasyfikowane, są zestawem obrazów.

Klasyfikacja obrazu może służyć do identyfikowania obrazów różnych kategorii. Na przykład różne rodzaje terenów lub zwierząt lub wady produkcji.

Możesz użyć szablonu klasyfikacji obrazów dla danego scenariusza, jeśli masz zestaw obrazów i chcesz sklasyfikować obrazy w różnych kategoriach.

#### <a name="custom-scenario"></a>Niestandardowy scenariusz

Scenariusz niestandardowy umożliwia ręczne wybranie scenariusza.

## <a name="data"></a>Dane

Po wybraniu scenariusza Konstruktor modelu prosi o dostarczenie zestawu danych. Dane służą do uczenia, oszacowania i wyboru najlepszego modelu dla danego scenariusza.

![Diagram przedstawiający kroki konstruktora modelu](media/model-builder-steps.png)

Konstruktor modelu obsługuje zestawy danych w formatach. tsv,. csv,. txt, a także w formacie SQL Database. Jeśli masz plik txt, kolumny powinny być oddzielone `,`, `;` lub `/t`, a plik musi mieć wiersz nagłówka.

Jeśli zestaw danych zawiera obrazy, obsługiwane typy plików to `.jpg` i `.png`.

Aby uzyskać więcej informacji, zobacz [ładowanie danych szkoleniowych do konstruktora modeli](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Wybierz dane wyjściowe do przewidywania (etykieta)

Zestaw danych to tabela wierszy przykładów szkoleniowych i kolumn atrybutów. Każdy wiersz ma:

- **etykieta** (atrybut, który ma zostać przewidywalna)
- **funkcje** (atrybuty, które są używane jako dane wejściowe do przewidywania etykiet).

W przypadku scenariusza przewidywania cen dla domu funkcje mogą być następujące:

- kwadratowy materiał dla domu
- Liczba sypialniami i bathrooms
- kod pocztowy

Etykieta to historyczna cena za ten wiersz kwadratów, Bedroom i wartości łazienkowych oraz kod pocztowy.

![Tabela przedstawiająca wiersze i kolumny danych cen domu z funkcjami zawierającymi kod pocztowy pokojów i etykietę cen](media/model-builder-data.png)

### <a name="example-datasets"></a>Przykładowe zestawy danych

Jeśli nie masz jeszcze własnych danych, wypróbuj jeden z tych zestawów danych:

|Scenariusz|Zadanie ML|Dane|Etykieta|Funkcje|
|-|-|-|-|-|
|Prognoza cen|ubytk|[dane dotyczące opłat za taksówki](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Bezprzewodow|Czas podróży, odległość|
|Wykrywanie anomalii|klasyfikacja binarna|[dane sprzedaży produktu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Sprzedaż produktu|Month|
|Analiza tonacji|klasyfikacja binarna|[dane komentarzy witryny sieci Web](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etykieta (0 w przypadku wartości ujemnej tonacji, 1, gdy wartość jest dodatnia)|Komentarz, rok|
|Wykrywanie oszustw|klasyfikacja binarna|[dane karty kredytowej](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)|Kwota, v1 — v28 (funkcje anonimowe)|
|Klasyfikacja tekstu|Klasyfikacja wieloklasowa|[Dane problemu w usłudze GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Obszar|Tytuł, opis|
|Klasyfikacja obrazów|Klasyfikacja wieloklasowa|[Obrazy kwiatów](http://download.tensorflow.org/example_images/flower_photos.tgz)|Typ kwitnienia: wirujące, Dandelion, róże, przepływy, Tulips|Same dane obrazu|

## <a name="train"></a>Szkolenie

Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu pociąga za niego model.

### <a name="what-is-training"></a>Co to jest szkolenie?

Szkolenia są procesem automatycznym, dzięki któremu Konstruktor modelu uczy się, jak odpowiedzieć na pytania dla danego scenariusza. Po przeszkoleniu model może tworzyć prognozy zawierające dane wejściowe, które nie były wcześniej widoczne. Na przykład jeśli zamierzasz przewidzieć ceny domu i nowe miejsce na rynku, możesz przewidzieć cenę sprzedaży.

Ponieważ Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania podczas szkoleń.

### <a name="how-long-should-i-train-for"></a>Jak długo mam nauczyć?

Konstruktor modelu używa AutoML do eksplorowania wielu modeli, aby znaleźć najlepszy model.

Dłuższe okresy szkoleniowe umożliwiają AutoMLom Eksplorowanie więcej modeli z szerszym zakresem ustawień.

W poniższej tabeli zestawiono średni czas potrzebny do uzyskania dobrej wydajności zestawu przykładowych zestawów danych na komputerze lokalnym.

|Rozmiar zestawu danych|Średni czas uczenia|
|------------|---------------------|
|0-10 MB|10 sekund|
|10-100 MB|10 min|
|100 – 500 MB|30 minut|
|500 – 1 GB|60 min|
|1 GB +|3 godziny|

Te liczby są tylko przewodnikiem. Dokładna długość szkolenia zależy od:

- liczba funkcji (kolumn) używanych jako dane wejściowe do modelu
- Typ kolumn
- zadanie ML
- wydajność procesora, dysku i pamięci maszyny używanej na potrzeby szkolenia

## <a name="evaluate"></a>Ocena programu

Ocena to proces mierzenia, jaki jest dobry model. Konstruktor modelu korzysta z przeszkolonego modelu do tworzenia prognoz z nowymi danymi testowymi, a następnie mierzy, jak dobre są przewidywania.

Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testowy. Dane szkoleniowe (80%) służy do uczenia modelu i danych testowych (20%) jest zatrzymywany z powrotem do oszacowania modelu. 

### <a name="how-do-i-understand-my-model-performance"></a>Jak mogę zrozumieć moją wydajność modelu?

Scenariusz jest mapowany na zadanie uczenia maszynowego. Każde zadanie ML ma swój własny zestaw metryk oceny.

#### <a name="regression-for-example-price-prediction"></a>Regresja (na przykład prognozowanie cen)

Metryką domyślną dla problemów z regresją jest RSquared, wartość RSquared zakresów z zakresu od 0 do 1. 1 jest najlepszą możliwą wartością lub innymi słowy, im bliżej wartości RSquared do 1 lepiej, gdy model jest wykonywany.

Inne raportowane metryki, takie jak bezwzględne, kwadratowe straty i usługi RMS, to dodatkowe metryki, które mogą służyć do zrozumienia, jak model jest wykonywany i który jest porównywany z innymi modelami regresji.

#### <a name="binary-classification-for-example-sentiment-analysis"></a>Klasyfikacja binarna (na przykład analiza tonacji)

Domyślna Metryka dla problemów klasyfikacji jest dokładność. Dokładność definiuje proporcję poprawnych prognoz, jaką model przekracza zestaw danych testowych. Im bliżej 100% lub 1,0, tym lepiej.

Inne raportowane metryki, takie jak AUC (obszar pod krzywą), które mierzą prawdziwą dodatnią stawkę w porównaniu z fałszywą dodatnią częstotliwością, która powinna być większa niż 0,50, aby można było zaakceptować modele.

Dodatkowe metryki, takie jak F1, mogą służyć do kontrolowania równowagi między dokładnością i odwołaniem.

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a>Klasyfikacja wieloklasowa (na przykład Klasyfikacja problemu, klasyfikacja obrazu)

Metryka domyślna dla klasyfikacji wieloklasowej to Micro dokładności. Im bliżej nie jest to lepsza dokładność do 100% lub 1,0.

Kolejną ważną metryką dla klasyfikacji wieloklasowej jest dokładność makro, podobnie jak w przypadku mikrodokładności zbliżonej do 1,0. Dobrym sposobem na to, że te dwa typy dokładności są następujące:

- Mikro-dokładność: jak często bilet przychodzący jest klasyfikowany do właściwego zespołu?
- Dokładność makr: dla średniego zespołu, jak często bilet przychodzący jest poprawny dla swojego zespołu?

### <a name="more-information-on-evaluation-metrics"></a>Więcej informacji na temat metryk oceny

Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).

## <a name="improve"></a>Podnieś swoje

Jeśli Ocena wydajności modelu nie jest tak dobra, jak chcesz, możesz:

- Uczenie przez dłuższy czas. Przez automatyczny aparat uczenia maszynowego, aby wypróbować więcej algorytmów i ustawień.

- Dodaj więcej danych. Czasami ilość danych nie wystarcza do uczenia modelu uczenia maszynowego o wysokiej jakości.

- Zrównoważ dane. W przypadku zadań klasyfikacji upewnij się, że zestaw szkoleniowy jest zrównoważony w różnych kategoriach. Na przykład jeśli masz cztery klasy do 100 przykładów szkoleniowych, a dwie pierwszej klasy (tag1 i tag2) są używane do 90 rekordów, ale pozostałe dwa (tag3 i tag4) są używane tylko dla pozostałych 10 rekordów, brak zrównoważonych danych może spowodować, że model będzie niezawodny ectly predykcyjny tag3 lub tag4.

## <a name="code"></a>Kod

Po zakończeniu fazy oceny Konstruktor modelu wyprowadza plik modelu i kod, którego można użyć do dodania modelu do aplikacji. Modele ML.NET są zapisywane jako plik zip. Kod do załadowania i użycia modelu jest dodawany jako nowy projekt w rozwiązaniu. Konstruktor modelu dodaje również przykładową aplikację konsolową, którą można uruchomić, aby zobaczyć model w działaniu.

Ponadto Konstruktor modelu wyprowadza kod, który wygenerował model, dzięki czemu można zrozumieć czynności używane do generowania modelu. Możesz również użyć kodu szkolenia modelu, aby ponownie przeprowadzić uczenie modelu z nowymi danymi.

## <a name="whats-next"></a>Co dalej?

[Zainstaluj](how-to-guides/install-model-builder.md) rozszerzenie programu Visual Studio dla programu model Builder

Wypróbuj [prognozę cenową lub dowolny scenariusz regresji](tutorials/predict-prices-with-model-builder.md)
