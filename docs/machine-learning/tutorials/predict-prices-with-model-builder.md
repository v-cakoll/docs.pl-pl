---
title: Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu konstruktora modeli strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d8c901a10c91c8a6c16ca59516b633a99785ebac
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238567"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Przewidywanie za pomocą regresji za pomocą konstruktora modelu cen

Dowiedz się, jak tworzyć model() regresji, do prognozowania cen za pomocą konstruktora modelu strukturze ML.NET.  Aplikacji konsolowej .NET, który tworzysz w tym samouczku przewiduje taksówek opłatami na podstawie danych historycznych taryfy taksówek w Nowym Jorku.

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

## <a name="prepare-and-understand-the-data"></a>Przygotuj i zrozumieć dane

1. Utwórz katalog o nazwie *danych* w projekcie mają być przechowywane pliki zestawu danych.

1. Zestaw danych używany do nauczanie i ocena modeli usługi machine learning jest pierwotnie z zestawu danych NYC TLC taksówek podróży. 

    Aby pobrać zestaw danych, przejdź do [link pobierania taksówek taryfy train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv). 
    
    Po załadowaniu strony, kliknij prawym przyciskiem myszy na stronie i wybierz **Zapisz jako**. 
    
    Użyj **Zapisz jako okno dialogowe** Aby zapisać plik w *danych* folderu utworzonego w poprzednim kroku. 
    
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *taksówek taryfy train.csv* plik i wybierz **właściwości**. W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.

Każdy wiersz w `taxi-fare-train.csv` zestaw danych zawiera szczegółowe informacje o wymianie danych wprowadzonych przez taksówek.

1. Otwórz **taksówek taryfy train.csv** zestawu danych

    Podany zestaw danych zawiera następujące kolumny:

    * **vendor_id:** Identyfikator dostawcy taksówek jest funkcją.
    * **rate_code:** Typ stawki podróży taksówek jest funkcją.
    * **passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.
    * **trip_time_in_secs:** Ilość czasu trwania podróży. 
    * **trip_distance:** Odległość wyzwolenie jest funkcją.
    * **payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.
    * **fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.

`label` Kolumna, która chcesz przewidzieć. Podczas wykonywania zadania regresji, celem jest do przewidywania wartości liczbowej. W tym scenariuszu prognozowania ceny przewiduje koszt jazdy taksówek. W związku z tym **fare_amount** jest etykietą. Wskazywanego przez nią `features` to dane wejściowe, nadaj model do przewidywania `label`. W takim przypadku pozostałe kolumny są używane jako funkcje lub danych wejściowych do prognozowania kwota klasie.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

Do nauczenia modelu, należy wybrać z listy dostępnych usługi machine learning scenariuszy dostarczone przez Konstruktor modelu. W tym przypadku jest to scenariusz `Price Prediction`. 

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu, a następnie wybierz **Dodaj** > **uczenia maszynowego**.
1. W kroku scenariusza narzędzia Konstruktor modelu, wybierz *Prognozowanie cen* scenariusza.

## <a name="load-the-data"></a>Ładowanie danych

Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych programu SQL Server lub lokalny plik w formacie csv lub tsv. 

1. W kroku danych narzędzia Konstruktor modelu, wybierz *pliku* z listy rozwijanej źródła danych.
1. Kliknij przycisk Dalej, aby *wybierz plik* pole tekstowe i użyj Eksploratora plików, przeglądania i wybierania *taksówek taryfy test.csv* w *danych* katalogu
1. Wybierz *fare_amount* w *etykiety lub kolumny Predict* listy rozwijanej i przejdź do kroku train narzędzia Konstruktor modelu.

## <a name="train-the-model"></a>Uczenie modelu

Używane do trenowania modelu prognozowania ceny w tym samouczku zadania uczenia maszynowego jest regresji. W trakcie szkolenia modelu konstruktora modeli szkolenie modeli na osobne modele przy użyciu regresji różnych algorytmów i ustawienia, aby znaleźć najlepiej działający model dla zestawu danych.

Czas wymagany do do nauczenia modelu jest proporcjonalny do ilości danych. Skorzystaj z tej tabeli jako wskazówki wybrać odpowiednią wartość `Time to train (seconds)` pola:

\* Rozmiar zestawu danych  | Typ zestawu danych       | Średni Czas do pociągu *
------------- | ------------------ | --------------
0 - 10 mb     | Liczbowe i tekstowe   | 10 s
10 - 100 mb   | Liczbowe i tekstowe   | 10-minutowy materiał
100 – 500 mb  | Liczbowe i tekstowe   | 30 minut
500 — 1 Gb    | Liczbowe i tekstowe   | 60-minutowe
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

Wynik kroku szkolenia będzie jednego modelu, który ma najwyższą wydajność. W kroku evaluate narzędzia Konstruktor modelu, w sekcji danych wyjściowych będzie zawierać algorytmów używanych przez funkcję najlepiej działający model w *najlepszy Model* wpisu wraz z metrykami w *Najlepsza jakość modeli (RSquared)* . Ponadto podsumowanie tabelę zawierającą pięć modeli i ich metryki. 

Jeśli nie jesteś zadowolony z metryk dokładności, niektóre łatwy sposób zwiększenia dokładności modelu i spróbuj mają zwiększyć ilość czasu do nauczenia modelu, lub Użyj większej ilości danych. W przeciwnym razie przejdź do kroku kodu. 

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby tworzyć prognozy

Dwa projekty zostaną utworzone w wyniku procesu uczenia.

- TaxiFarePredictionML.ConsoleApp: Aplikacja Konsolowa .NET Core, która zawiera kod, szkolenia i użycie modelu.
- TaxiFarePredictionML.Model: Biblioteki klas .NET Standard zawierający modeli danych, które zdefiniować schemat danych wejściowych i wyjściowych modelu danych, a także utrwalonych wersję najlepiej działający model podczas szkolenia.


1. W kroku kodu narzędzia Konstruktor modelu, wybierz **dodać projekty** dodać generowanych automatycznie projekty do rozwiązania.
1. Kliknij prawym przyciskiem myszy *TaxiFarePrediction* projektu. Następnie **Dodaj > dokumentacja**. Wybierz **projektów > rozwiązania** węzła i z listy, sprawdź *TaxiFarePredictionML.Model* projektu, a następnie wybierz przycisk OK.
1. Otwórz *Program.cs* w pliku *TaxiFarePrediction* projektu.
1. Dodaj następujące za pomocą instrukcji, aby odwołać się do *Microsoft.ML* pakietu NuGet i *TaxiFarePredictionML.Model* projektu:


    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. Dodaj `ConsumeModel` metody `Program` klasy. 

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

    `ConsumeModel` Będzie załadować trenowanego modelu, tworzenie [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) modelu i użyj jej do prognozowania na nowych danych.

7. Przewiduje nowe dane przy użyciu modelu, należy utworzyć nowe wystąpienie klasy `ModelInput` klasy i użyć `ConsumeModel` metody. Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych. Jest to spowodowane modelu spowoduje wygenerowanie prognoz dla niego. Dodaj następujący kod do `Main` metody i uruchom aplikację

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

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej na temat tematy wymienione w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modelu](../automate-training-with-model-builder.md#scenarios)
- [Formaty danych konstruktora modelu](../automate-training-with-model-builder.md#data-formats)
- [Regression](../resources/glossary.md#regression)
- [Metryki modelu regresji](../resources/metrics.md#metrics-for-regression)
- [Zestaw danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
