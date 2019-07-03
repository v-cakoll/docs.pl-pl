---
title: Co to jest konstruktor modelu i jak to działa?
description: Jak automatycznie szkolenie modelu uczenia maszynowego za pomocą konstruktora modeli strukturze ML.NET
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6049db79753986544de18faebfd047aa190af153
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539802"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Co to jest konstruktor modelu i jak to działa?

Konstruktor modelu strukturze ML.NET jest łatwy do zrozumienia graficzny rozszerzenie programu Visual Studio do tworzenia, uczenia i wdrażania niestandardowych modeli uczenia maszynowego.

Konstruktor modelu używa automatycznych usługi machine learning (AutoML) do eksplorowania algorytmów uczenia maszynowego różnych i ustawienia, aby pomóc w znalezieniu taki, który najlepiej odpowiada Twojemu scenariuszowi.

Machine learning wiedzy na temat za pomocą konstruktora modelu nie jest konieczne. To wszystko, czego potrzebujesz, niektórych danych i rozwiązać problem. Konstruktor modelu generuje kod, aby dodać model do aplikacji platformy .NET.

![Model animacji interfejsu użytkownika rozszerzenia konstruktora programu Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Konstruktor modelu jest obecnie w wersji zapoznawczej.

## <a name="scenarios"></a>Scenariusze

Wiele różnych scenariuszy może doprowadzić do konstruktora modelu, aby wygenerować model aplikacji uczenia maszynowego.

Scenariusz znajduje się opis typu prognozowania, który chcesz, aby na podstawie posiadanych danych. Na przykład:
- przewidywanie przyszłych produktów wielkość sprzedaży na podstawie historycznych danych sprzedaży
- klasyfikowanie tonacji, jak dodatnie lub ujemne, przeglądy wykonywane przez klientów w oparciu
- wykrywa, czy transakcji bankowych jest fałszywe
- problemy z opinii klientów trasy do właściwego zespołu w firmie

W Konstruktorze modelu należy zamapować scenariusza na [zadań strukturze ML.NET](resources/tasks.md). Można użyć konstruktora modelu dla **regresji** (prognozowanie liczby) i **klasyfikacji** (przewidywania kategorii).

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Scenariusze, które machine learning jest dla mnie odpowiednia?

Konstruktor modelu jest dostarczany z szablonów na potrzeby analizy tonacji, Klasyfikacja problemu, prognozowanie cen i scenariusze dostosowywania. Te szablony może służyć jako punkt początkowy dla określonego scenariusza strukturze ML.NET.

#### <a name="sentiment-analysis-binary-classification"></a>Analiza tonacji (klasyfikacja binarna)

Analiza tonacji może służyć do prognozowania dodatnie lub ujemne tonacji opinii klientów. To przykład zadania klasyfikacji binarnej.

Klasyfikacja binarna jest używany do skategoryzowania danych na dwie klasy (tak/nie; Powodzenie/niepowodzenie; PRAWDA/FAŁSZ plus/minus). Może służyć do odpowiedzi na pytania takie jak:

- Jest to spamu poczty e-mail? (wykrywanie spam)
- Które kandydaci mogą kwalifikować się do członkostwa? (sortowanie aplikacji)
- Konta, które nie mogą płacić faktur na czas? (Ograniczanie ryzyka)
- Ta transakcja karty kredytowej jest fałszywe? (wykrywanie oszustw)

Jeśli dany scenariusz wymaga klasyfikacji na dwie kategorie, możesz użyć tego szablonu, za pomocą własnego zestawu danych.

#### <a name="issue-classification-multiclass-classification"></a>Klasyfikacja problemów (klasyfikacja wieloklasowa)

Klasyfikacja problemu może służyć do klasyfikowania problemów opinii (na przykład w serwisie GitHub) klientów przy użyciu problem tytuł i opis. To przykład zadania klasyfikacji wieloklasowej.

Klasyfikacji wieloklasowej może służyć do klasyfikowania danych do co najmniej trzech klas. Może służyć do odpowiedzi na pytania takie jak:

- Do działu, które należy kierować bilet pomocy technicznej? (Obsługa biletu routing)
- Co to jest priorytet problemu klienta? (priorytetyzacji problem klienta)
- Jakiej kategorii czy należy produkt? (klasyfikacja produktu)
- Jakiego typu dokumentu? (klasyfikacja dokumentu/wiadomości e-mail)

Aby skategoryzować dane na co najmniej trzy kategorie, można użyć szablonu klasyfikacji problemu dla danego scenariusza.

#### <a name="price-prediction-regression"></a>Przewidywanie cen (regresja)

Prognozowanie cen może służyć do prognozowania cen DOM przy użyciu umiejscowienie, rozmiar i inne cechy domu. To przykład zadania regresji.

Regresja służy do prognozowania liczby. Może służyć do odpowiedzi na pytania takie jak:

- Jakie ceny domu sprzedaż dla? (Prognozowanie cen)
- Po czas, jaki element mechanicznych będzie wymagała konserwacji? (konserwacji predykcyjnej)
- Co to jest wilgotności w tym osuszacz? (monitorowanie komputera)
- Jaka będzie całkowitej sprzedaży rocznej dla tego regionu? (prognozowania sprzedaży)

Jeśli chcesz przewidzieć wartość liczbową z własnego zestawu danych, można użyć szablonu prognozowania ceny dla danego scenariusza.

#### <a name="custom-scenario-choose-your-task"></a>Scenariusz niestandardowe (Wybierz zadanie)

Scenariusz niestandardowy można wybrać własne zadanie. Wybierz scenariusz, który jest najbardziej odpowiednie dla danego problemu.

Scenariusz niestandardowy można wybrać własne zadania uczenia maszynowego. W szablonach poprzedniego zadania uczenia maszynowego został naprawiony do scenariusza: klasyfikacji binarnej, wieloklasowej klasyfikacji lub regresji. W tym szablonie można zadania uczenia Maszynowego, które chcesz użyć na podstawie posiadanych danych.

## <a name="data"></a>Dane

Po zamapowaniu scenariusza na zadanie, Konstruktor modelu prosi o podanie zestawu danych. Dane są używane do uczenie, ocenę i wybrać najlepszy model dla danego scenariusza. Należy również wybrać danych wyjściowych, który chcesz przewidzieć.

### <a name="choose-the-output-to-predict-label"></a>Wybierz dane wyjściowe do przewidywania (etykieta)

Zestaw danych jest tabela wierszy przykłady szkolenia i kolumny atrybutów. Każdy wiersz zawiera:
- **etykiety** (atrybut, który chcesz przewidzieć)
- **Funkcje** (atrybutów, które są używane jako dane wejściowe do prognozowania etykiety).

W scenariuszu Prognozowanie cen DOM funkcji może być:
- liczba metrów kwadratowych z domu
- liczby sypialni i łazienki
- Kod pocztowy

Etykieta jest ceny historyczne domu dla tego wiersza, kwadratowy wartości nagrań z monitorowania, sypialni i łazienkowe i kod pocztowy.

![Tabelę przedstawiającą wierszy i kolumn w domu danych dotyczących cen za pomocą funkcji, składająca się kod pocztowy pokojów wielkości i ceny etykiety](media/model-builder-data.png)

### <a name="data-formats"></a>Formaty danych

Konstruktor modelu umieszcza następujące ograniczenia dotyczące danych:

- Dane muszą być przechowywane w pliku (pliku CSV lub tsv wiersza nagłówka) lub w bazie danych programu SQL server.
- Limit 1 GB na zestaw danych szkoleniowych
- Program SQL server jest objęta limitem 100 000 wierszy na potrzeby szkolenia
- Dane z programu SQL server są kopiowane z serwera, na maszynę lokalną przed szkolenia

### <a name="example-datasets"></a>Przykładowe zestawy danych

Jeśli nie masz jeszcze własnych danych, wypróbuj jedną z tych zestawów danych:

|Scenariusz|Zadania uczenia Maszynowego|Dane|Etykieta|Funkcje|
|-|-|-|-|-|
|Prognozowanie cen|Regresji|[danych taksówek w klasie](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Taryfy|Czas obiegu, odległości|
|Wykrywanie anomalii|Klasyfikacja binarna|[dane dotyczące sprzedaży produktu](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|— Sprzedaż produktów|Miesiąc|
|Analiza tonacji|Klasyfikacja binarna|[dane komentarz witryny sieci Web](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|Etykieta (0 po negatywną tonację, 1, gdy dodatni)|Komentarz, rok|
|Wykrywanie oszustw|Klasyfikacja binarna|[dane kart kredytowych](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Klasy (1, gdy jest to fałszywe, w przeciwnym razie 0)|Czas, w wersji 1-V28 (funkcje anonimowe)|
|Klasyfikacji tekstu|Wieloklasowej klasyfikacji|[Dane problem usługi GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Obszar|Tytuł, opis|

## <a name="train"></a>Szkolenie

Po wybraniu scenariusza, danych i etykiety, Konstruktor modelu przygotowuje modelu.

### <a name="what-is-training"></a>Co to jest szkolenia?

Szkolenie jest procesu automatycznego za pomocą którego konstruktora modeli nauczy modelu jak odpowiedzieć na pytania dla danego scenariusza. Po przeszkolonych, model może tworzyć prognozy przy użyciu danych wejściowych, które nie został wcześniej zauważony. Na przykład czy Prognozowanie cen dom i nowy dom znajduje się na rynku, może przewidzieć jej miesięczna cena sprzedaży.

Ponieważ Konstruktor modelu używa automatycznych usługi machine learning (AutoML), nie wymaga żadnych danych wejściowych lub dostosowywania od użytkownika podczas szkolenia.

### <a name="how-long-should-i-train-for"></a>Jak długo należy szkolenie dla?

Możesz podać czasu szkoleń. Ogólnie rzecz biorąc szkolenia dłużej daje bardziej precyzyjne modelu. Więcej czasu na szkolenie jest również wymagane, w miarę zwiększania rozmiaru zestawu danych szkoleniowych. W poniższej tabeli przedstawiono wskazówki czasu szkolenia dla zestawów danych o zwiększenie rozmiaru.

Rozmiar zestawu danych  | Typ zestawu danych       | Średni Czas na nauczenie
------------- | ------------------ | --------------
0 - 10 mb     | Liczbowe i tekstowe   | 10 s
10 - 100 mb   | Liczbowe i tekstowe   | 10 min
100 – 500 mb  | Liczbowe i tekstowe   | 30 min
500 — 1 Gb    | Liczbowe i tekstowe   | 60 min
1 Gb+         | Liczbowe i tekstowe   | 3 godziny +

Dokładny czas na nauczenie również zależy od:

- Typ kolumny oznacza to tekst programu vs liczbowe
- typ tworzonego zadania uczenia maszyny (regresji lub klasyfikacji)
- Liczba wierszy, używane na potrzeby szkolenia
- Liczba kolumn funkcji używane na potrzeby szkolenia

Konstruktor modelu przetestowano w skali od 1 TB pojemności zestawu danych, ale tworzenie wysokiej jakości model dla tego rozmiaru zestawu danych może zająć maksymalnie cztery dni!

## <a name="evaluate"></a>Oceń

Ocena jest proces za pomocą uczonego modelu do prognozowania z nowymi danymi testu, a następnie pomiaru jak dobre prognozy są.

Konstruktor modelu dzieli dane szkoleniowe na zestaw szkoleniowy i zestaw testów. Dane szkoleniowe (80%) Służy do nauczenia modelu, a dane testowe (20%) jest wstrzymywane do oceny modelu.  Metryki używane do oceny, zależą od zadania uczenia Maszynowego. Aby uzyskać więcej informacji, zobacz [model metryk oceny](resources/metrics.md).

### <a name="sentiment-analysis-binary-classification"></a>Analiza tonacji (klasyfikacja binarna)

Metryka domyślna Klasyfikacja binarna problemów jest **dokładność**. Dokładność definiuje część poprawne prognozy modelu sprawia, że za pośrednictwem zestawu danych testowych. **Bliżej 100%, tym lepiej jest**.

Inne metryki zgłaszane, takie jak AUC (powierzchni pod krzywą), czyli miary stawkę dodatnią wartość true, a fałszywie dodatnich, powinien być większy niż 0,50 dla modeli do przyjęcia.

Dodatkowe metryki, takie jak ocena F1 może służyć do kontrolowania równowagę między precyzji (wskaźnik poprawne prognozy do całkowitej prognozy tej klasy) oraz odwołania (część poprawne prognozy do całkowitej rzeczywiste elementy członkowskie tej klasy).

### <a name="issue-classification-multiclass-classification"></a>Klasyfikacja problemów (klasyfikacja wieloklasowa)

Metryka domyślnej dla klasyfikacji wieloklasowej problemów jest **wczesnych dokładność**. **Bliżej 100%, tym lepiej jest**.

W przypadku problemów, których data dzieli się na wielu klas istnieją dwa rodzaje dokładność:

- Operacje Micro dokładność: ułamek prognoz, które są prawidłowe we wszystkich wystąpieniach. W tym scenariuszu klasyfikacji problemu micro dokładności jest część przychodzące problemy, które zostaną przypisane do odpowiedniej kategorii.
- Dokładność makra: średni dokładności na poziomie klasy. W tym scenariuszu klasyfikacji problemu dokładności jest mierzona dla każdej kategorii, a następnie są uśredniane dokładności kategorii. Dla tej metryki dla wszystkich klas są podane weight równe. W przypadku zestawów danych doskonale o zrównoważonym obciążeniu (jeśli istnieje taka sama liczba przykłady wystąpienia każdej kategorii), micro dokładności i dokładność makra są takie same.

### <a name="price-prediction-regression"></a>Przewidywanie cen (regresja)

Metryka domyślnej dla problemów regresji jest **RSquared**. 1 jest najlepsze możliwe wartości. Im bliżej RSquared jest 1, tym lepiej modelu.

Inne metryki zgłoszony, takie jak utrata bezwzględną, kwadrat straty, i utratę usługi RMS może służyć do zrozumienia modelu i porównaj je z innymi modelami regresji.

## <a name="improve"></a>Poprawa

Jeśli model ocenę wydajności nie jest tak dobre, jak ma to być, możesz:

* Szkolenie na dłuższy okres czasu. Za pomocą więcej czasu, aparat learning automatycznych maszyny do wypróbowania więcej algorytmów i ustawienia.

* Dodawanie większej ilości danych. Czasami ilość danych nie jest wystarczające do nauczenia modelu uczenia maszynowego wysokiej jakości.

* Saldo danych. Klasyfikacja zadań upewnij się, że zestaw szkoleniowy jest równoważone w kategorii. Na przykład, jeśli ma cztery klasy 100 przykłady szkolenia i dwie klasy pierwszy (tag1 i tag2) są używane do 90 rekordy, ale inne dwóch (tag3 i tag4) są używane tylko w pozostałych 10 rekordów, Brak danych o zrównoważonym obciążeniu może spowodować, że model można mieć trudności z loro ectly przewidzieć tag3 lub tag4.

## <a name="code"></a>Kod

Po fazie oceny konstruktora modeli danych wyjściowych pliku modelu i kodu, który służy do dodawania modelu do aplikacji. Modele strukturze ML.NET są zapisywane jako plik zip. Kod, aby załadować i użyć modelu zostanie dodany jako nowy projekt w rozwiązaniu. Konstruktor modelu dodaje również przykładową aplikację konsoli można uruchomić, aby wyświetlić model w akcji.

Ponadto konstruktora modeli generuje kod, który wygenerował modelu, tak aby mogli zrozumieć kroki używane do generowania modelu. Kod szkolenie modelu umożliwia także ponowne szkolenie modelu za pomocą nowych danych.

## <a name="whats-next"></a>Co dalej?

Spróbuj [Prognozowanie cen lub dowolnego scenariusza regresji](tutorials/predict-prices-with-model-builder.md)
