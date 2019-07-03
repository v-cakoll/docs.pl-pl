---
title: Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu konstruktora modeli strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539633"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen

Dowiedz się, jak tworzyć za pomocą konstruktora modelu strukturze ML.NET [modelu regresji](../resources/glossary.md#regression) do prognozowania cen.  Aplikacji konsolowej .NET, który tworzysz w tym samouczku przewiduje taksówek opłatami na podstawie danych historycznych taryfy taksówek w Nowym Jorku.

Szablon prognozowania ceny konstruktora modelu może być używany dla dowolnych scenariuszy wymaga wartości liczbowe prognozy. Przykładowe scenariusze obejmują: lokalne Prognozowanie cen, przewidywanie zapotrzebowania i Prognozowanie sprzedaży.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotuj i zrozumieć dane
> * Wybierz scenariusz
> * Ładowanie danych
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

> [!NOTE]
> Konstruktor modelu jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje dotyczące instalacji, odwiedź stronę [Przewodnik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Tworzenie **aplikacji konsoli .NET Core** o nazwie "TaxiFarePrediction".

1. Zainstaluj **Microsoft.ML** pakietu NuGet:

    W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Zarządzaj pakietami NuGet**. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku. Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.

## <a name="prepare-and-understand-the-data"></a>Przygotuj i zrozumieć dane

1. Utwórz katalog o nazwie *danych* w projekcie mają być przechowywane pliki zestawu danych.

1. Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku. Ten zestaw danych służy do nauczanie i ocena modelu uczenia maszynowego. Ten zestaw danych pochodzi pierwotnie [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *taksówek taryfy train.csv* plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

Każdy wiersz w `taxi-fare-train.csv` zestaw danych zawiera szczegółowe informacje o wymianie danych wprowadzonych przez taksówek.

1. Otwórz **taksówek taryfy train.csv** zestawu danych

    Podany zestaw danych zawiera następujące kolumny:

    * **vendor_id:** Identyfikator dostawcy taksówek jest funkcją.
    * **rate_code:** Typ stawki podróży taksówek jest funkcją.
    * **passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.
    * **trip_time_in_secs:** Ilość czasu trwania podróży. Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż. W tym momencie nie wiesz, jak długo podróży zajęłoby. Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.
    * **trip_distance:** Odległość wyzwolenie jest funkcją.
    * **payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.
    * **fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.

`label` Kolumna, która chcesz przewidzieć. Podczas wykonywania zadania regresji, celem jest do przewidywania wartości liczbowej. W tym scenariuszu prognozowania ceny przewiduje koszt jazdy taksówek. W związku z tym **fare_amount** jest etykietą. Wskazywanego przez nią `features` to dane wejściowe, nadaj model do przewidywania `label`. W takim przypadku pozostałe kolumny są używane jako funkcje lub danych wejściowych do prognozowania kwota klasie.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

Do nauczenia modelu, należy wybrać z listy dostępnych usługi machine learning scenariuszy dostarczone przez Konstruktor modelu. W tym przypadku jest to scenariusz `Price Prediction`. Bardziej rozległe listę można znaleźć [artykuł z omówieniem konstruktora modeli](../automate-training-with-model-builder.md#scenarios).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Dodaj** > **uczenia maszynowego**.
1. W kroku scenariusza narzędzia Konstruktor modelu, wybierz *Prognozowanie cen* scenariusza.

## <a name="load-the-data"></a>Ładowanie danych

Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych programu SQL Server lub w pliku csv lub tsv pliku lokalnego. Aby uzyskać więcej informacji na temat wymagań dotyczących formatu danych, można znaleźć w następującej [łącze](../how-to-guides/install-model-builder.md#limitations).

1. W kroku danych narzędzia Konstruktor modelu, wybierz *pliku* z listy rozwijanej źródła danych.
1. Kliknij przycisk Dalej, aby *wybierz plik* pole tekstowe i użyj Eksploratora plików, przeglądania i wybierania *taksówek taryfy test.csv* w *danych* katalogu
1. Wybierz *fare_amount* w *etykiety lub kolumny Predict* listy rozwijanej i przejdź do kroku train narzędzia Konstruktor modelu.

## <a name="train-the-model"></a>Uczenie modelu

Używane do trenowania modelu prognozowania ceny w tym samouczku zadania uczenia maszynowego jest regresji. W trakcie szkolenia modelu konstruktora modeli szkolenie modeli na osobne modele przy użyciu regresji różnych algorytmów i ustawienia, aby znaleźć najlepiej działający model dla zestawu danych.

Czas wymagany do do nauczenia modelu jest proporcjonalny do ilości danych. Skorzystaj z tej tabeli jako wskazówki wybrać odpowiednią wartość `Time to train (seconds)` pola:

\* Rozmiar zestawu danych  | Typ zestawu danych       | Średni Czas do pociągu *
------------- | ------------------ | --------------
0 - 10 mb     | Liczbowe i tekstowe   | 10 s
10 - 100 mb   | Liczbowe i tekstowe   | 10 min
100 – 500 mb  | Liczbowe i tekstowe   | 30 min
500 — 1 Gb    | Liczbowe i tekstowe   | 60 min
1 Gb+         | Liczbowe i tekstowe   | 3 godziny +

1. Ponieważ plik danych szkoleniowych więcej niż 10MB, należy użyć 600 sekund (10 minut), jako wartość pozycji *czas na nauczenie (w sekundach)* .
2. Wybierz *Rozpocznij szkolenie*.

Przez cały proces szkolenia postępu dane są wyświetlane w `Progress` części kroku pociągu.

- Stan wyświetlany stan ukończenia procesu uczenia.
- Najlepsze dokładności Wyświetla dokładność najlepiej działający model znalezione przez konstruktora modeli do tej pory. Większą dokładność oznacza, że model przewiduje właściwie na danych testowych.
- Najlepszy algorytm Wyświetla nazwę algorytmu działają najlepiej wykonać znalezione przez konstruktora modeli do tej pory.
- Ostatni algorytm Wyświetla nazwę algorytmu do nauczenia modelu, ostatnio używane przez konstruktora modelu.

Po zakończeniu szkolenia, przejdź do kroku evaluate.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynik kroku szkolenia będzie jednego modelu, który ma najwyższą wydajność. W kroku evaluate narzędzia Konstruktor modelu, w sekcji danych wyjściowych będzie zawierać algorytmów używanych przez funkcję najlepiej działający model w *najlepszy Model* wpisu wraz z metrykami w *Najlepsza jakość modeli (RSquared)* . Ponadto podsumowanie tabelę zawierającą pięć modeli i ich metryki. Skorzystaj z następującego linku, aby dowiedzieć się więcej na temat [oceniania modelu metryki](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).

Jeśli nie jesteś zadowolony z metryk dokładności, niektóre łatwy sposób zwiększenia dokładności modelu i spróbuj mają zwiększyć ilość czasu do nauczenia modelu, lub Użyj większej ilości danych.

## <a name="use-the-model-for-predictions"></a>Na użytek modelu prognozy

Dwa projekty zostaną utworzone w wyniku procesu uczenia.

- TaxiFarePredictionML.ConsoleApp: Aplikacja konsoli .NET, która zawiera kod, szkolenia i użycie modelu.
- TaxiFarePredictionML.Model: Biblioteki klas .NET Standard zawierający modeli danych, które zdefiniować schemat danych wejściowych i wyjściowych modelu danych, a także utrwalonych wersję najlepiej działający model podczas szkolenia.

1. W sekcji kodu, narzędzia konstruktora modeli wybierz **dodać projekty** dodać projekty do rozwiązania.
2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu. Następnie wybierz **Dodaj > istniejący element**. Plik typu listy rozwijanej wybierz `All Files`, przejdź do *TaxiFarePredictionML.Model* projekt katalogu i wybierz `MLModel.zip` pliku. Kliknij prawym przyciskiem myszy ostatnio dodane `MLModel.zip` plik i wybierz *właściwości*. Kopiuj do katalogu wyjściowego opcji, można wybrać *Kopiuj Jeśli nowszy* z listy rozwijanej.
3. Kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu. Następnie **Dodaj > dokumentacja**. Wybierz **projektów > rozwiązania** węzła i z listy, sprawdź *TaxiFarePredictionML.Model* projektu, a następnie wybierz przycisk OK.

4. Otwórz *Program.cs* w pliku *TaxiFarePrediction* projektu.
5. Dodaj następujące instrukcje using:

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. Dodaj `ConsumeModel` metody `Program` klasy. `ConsumeModel` Utworzy `PredictionEngine` oparte na modelu wygenerowany przez konstruktora modelu do prognozowania na nowe dane i wydrukuj do konsoli.

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. Dodaj następujący kod do `Main` metody i uruchom aplikację.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    Dane wyjściowe generowane przez program powinien wyglądać podobnie jak poniższy fragment kodu:

    ```bash
    Predicted Fare: 16.82245
    ```

Jeśli musisz odwoływać się do wygenerowanego projektów w późniejszym czasie wewnątrz innego rozwiązania, możesz znaleźć je wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotuj i zrozumieć dane
> * Wybierz scenariusz
> * Ładowanie danych
> * Uczenie modelu
> * Ocena modelu
> * Na użytek modelu prognozy

Przejdź do jednej z następujących artykułów z instrukcjami, aby dowiedzieć się, jak wdrożyć model.

> [!div class="nextstepaction"]
> [Wdrażanie modelu w usłudze Azure Functions](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Wdrażanie modelu do internetowego interfejsu API](../how-to-guides/serve-model-web-api-ml-net.md)
