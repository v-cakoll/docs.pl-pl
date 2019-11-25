---
title: Co to jest Konstruktor modelu i jak to działa?
description: Jak korzystać z konstruktora modelu ML.NET w celu automatycznego uczenia modelu uczenia maszynowego
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971525"
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

## <a name="choose-a-model-type"></a>Wybierz typ modelu

W konstruktorze modelu należy wybrać typ modelu uczenia maszynowego. Typ modelu zależy od tego, jakie jest prognozowanie, którą próbujesz wprowadzić.

W scenariuszach, w których jest przewidywana liczba, typ modelu uczenia maszynowego jest nazywany `regression`.

W scenariuszach, w których jest przewidywana Kategoria, typ modelu jest `classification`. Istnieją dwa typy klasyfikacji:

- gdzie dostępne są tylko 2 Kategorie: `binary classification`.
- gdzie znajdują się trzy lub więcej kategorii: `multiclass classification`.

### <a name="which-model-type-is-right-for-me"></a>Który typ modelu jest dla mnie właściwy?

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Przewidywanie kategorii (jeśli istnieją tylko dwie kategorie)

Klasyfikacja binarna służy do kategoryzowania danych w dwóch kategoriach (tak/nie; Pass/Fail; true/false; wartość dodatnia/ujemna).

![Diagram przedstawiający przykłady klasyfikacji danych binarnych, w tym wykrywanie oszustw, łagodzenie ryzyka i osłanianie aplikacji](media/binary-classification-examples.png)

Analiza tonacji może służyć do przewidywania pozytywnych lub negatywnych tonacji opinii klientów. Jest to przykładowy Typ modelu klasyfikacji binarnej.

Jeśli scenariusz wymaga klasyfikacji do dwóch kategorii, można użyć tego szablonu z własnym zestawem danych.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Przewidywanie kategorii (jeśli istnieją trzy lub więcej kategorii)

Klasyfikacji wieloklasowej można użyć do kategoryzowania danych w trzech lub większej liczbie klas.

![Przykłady klasyfikacji wieloklasowej, w tym Klasyfikacja dokumentów i produktów, obsługa routingu biletów i problemów klientów](media/multiclass-classification-examples.png)

Klasyfikacja problemu może służyć do kategoryzowania opinii klientów (na przykład w witrynie GitHub) przy użyciu tytułu i opisu problemu. Jest to przykładowy Typ modelu klasyfikacji wieloklasowej.

Możesz użyć szablonu klasyfikacji problemu dla danego scenariusza, jeśli chcesz podzielić dane na trzy lub więcej kategorii.

#### <a name="predict-a-number"></a>Przewidywanie liczby

Regresja służy do przewidywania liczby.

![Diagram przedstawiający przykłady regresji, takie jak prognozowanie cen, prognozowanie sprzedaży i konserwacja predykcyjna](media/regression-examples.png)

Funkcja prognozowania cen może służyć do przewidywania cen domu przy użyciu lokalizacji, rozmiaru i innych cech domu. Jest to przykład typu modelu regresji.

Możesz użyć szablonu prognozowania cen dla danego scenariusza, jeśli chcesz prognozować wartość liczbową przy użyciu własnego zestawu danych.

#### <a name="custom-scenario-choose-your-model-type"></a>Scenariusz niestandardowy (Wybierz typ modelu)

Niestandardowy scenariusz umożliwia ręczne wybranie typu modelu.

## <a name="data"></a>Dane

Po wybraniu typu modelu program model Builder prosi o dostarczenie zestawu danych. Dane służą do uczenia, oszacowania i wyboru najlepszego modelu dla danego scenariusza.

![Diagram przedstawiający kroki konstruktora modelu](media/model-builder-steps.png)

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

|Scenariusz|Typ modelu|Dane|Etykieta|Funkcje|
|-|-|-|-|-|
|Prognoza cen|ubytk|[dane dotyczące opłat za taksówki](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Bezprzewodow|Czas podróży, odległość|
|Wykrywanie anomalii|klasyfikacja binarna|[dane sprzedaży produktu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Sprzedaż produktu|Bieżącym|
|Analiza tonacji|klasyfikacja binarna|[dane komentarzy witryny sieci Web](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etykieta (0 w przypadku wartości ujemnej tonacji, 1, gdy wartość jest dodatnia)|Komentarz, rok|
|Wykrywanie oszustw|klasyfikacja binarna|[dane karty kredytowej](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Klasa (1 w przypadku oszustwa, 0 w przeciwnym razie)|Kwota, v1 — v28 (funkcje anonimowe)|
|Klasyfikacja tekstu|Klasyfikacja wieloklasowa|[Dane problemu w usłudze GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Obszar|Tytuł, opis|

## <a name="train"></a>trasy

Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu pociąga za niego model.

### <a name="what-is-training"></a>Co to jest szkolenie?

Szkolenia są procesem automatycznym, dzięki któremu Konstruktor modelu uczy się, jak odpowiedzieć na pytania dla danego scenariusza. Po przeszkoleniu model może tworzyć prognozy zawierające dane wejściowe, które nie były wcześniej widoczne. Na przykład jeśli zamierzasz przewidzieć ceny domu i nowe miejsce na rynku, możesz przewidzieć cenę sprzedaży.

Ponieważ Konstruktor modelu korzysta z funkcji automatycznego uczenia maszynowego (AutoML), nie wymaga żadnych danych wejściowych ani dostrajania podczas szkoleń.

## <a name="evaluate"></a>Oceny

Ocena to proces użycia przeszkolonego modelu, który umożliwia prognozowanie przy użyciu nowych danych testowych, a następnie zmierzenie, jak dobre są przewidywania.

Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testowy. Dane szkoleniowe (80%) służy do uczenia modelu i danych testowych (20%) jest zatrzymywany z powrotem do oszacowania modelu. Konstruktor modelu używa metryk, aby zmierzyć, jak dobry jest model. Określone metryki są zależne od typu modelu. Aby uzyskać więcej informacji, zobacz [metryki oceny modelu](resources/metrics.md).

## <a name="improve"></a>Przyspieszy

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
