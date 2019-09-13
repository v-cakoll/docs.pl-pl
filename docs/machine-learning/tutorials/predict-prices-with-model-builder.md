---
title: Przewidywanie cen przy użyciu regresji z konstruktorem modelu
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu konstruktora modelu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bc1dacdad436cc5384bca4bbce224acc18d69201
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929431"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Przewidywanie cen przy użyciu regresji z konstruktorem modelu

Dowiedz się, jak za pomocą konstruktora modeli ML.NET utworzyć model regresji () w celu przewidywania cen.  Aplikacja konsolowa platformy .NET, którą opracowujesz w tym samouczku, przewiduje opłaty za taksówkę w oparciu o historyczne dane dotyczące opłat za taksówkę w Nowym Jorku.

Szablon prognozowania cen konstruktora modeli może być używany w każdym scenariuszu wymagającym wartości prognozowanych liczbowych. Przykładowe scenariusze obejmują: prognozowanie cen domu, prognozowanie popytu i prognozowanie sprzedaży.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotuj i poznanie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Oceń model
> - Używanie modelu dla prognoz

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

Listę wymagań wstępnych i instrukcji instalacji można znaleźć w [podręczniku instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".

## <a name="prepare-and-understand-the-data"></a>Przygotuj i poznanie danych

1. Utwórz katalog o nazwie *dane* w projekcie, aby przechowywać pliki zestawu danych.

1. Zestaw danych służący do uczenia i oszacowania modelu uczenia maszynowego jest pierwotnie z zestawu danych o podróży NYC TLC.

    Aby pobrać zestaw danych, przejdź do linku [pobierania Taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    Gdy strona zostanie załadowana, kliknij prawym przyciskiem myszy w dowolnym miejscu na stronie i wybierz polecenie **Zapisz jako**.

    Użyj **okna dialogowego Zapisz jako** , aby zapisać plik w folderze *danych* utworzonym w poprzednim kroku.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Taxi-Fare-Train. csv* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

Każdy wiersz w `taxi-fare-train.csv` zestawie danych zawiera szczegółowe informacje o podróży dokonywanych przez taksówkę.

1. Otwórz zestaw danych **Taxi-Fare-Train. csv**

    Podany zestaw danych zawiera następujące kolumny:

    - **vendor_id:** Identyfikator dostawcy taksówki jest funkcją.
    - **rate_code:** Typ szybkości podróży z taksówką jest funkcją.
    - **passenger_count:** Liczba pasażerów w podróży to funkcja.
    - **trip_time_in_secs:** Czas trwania podróży.
    - **trip_distance:** Odległość podróży to funkcja.
    - **payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.
    - **fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.

`label` Jest to kolumna, która ma zostać przewidywalna. Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej. W tym scenariuszu prognozowania cen jest przewidywany koszt najazdy z taksówką. W związku z tym **fare_amount** jest etykietą. Identyfikowane `features` są dane wejściowe, które dają model do `label`przewidywania. W takim przypadku pozostałe kolumny są używane jako funkcje lub dane wejściowe do przewidywania kwoty opłat.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu. W tym przypadku scenariuszem jest `Price Prediction`.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* , a następnie wybierz pozycję **Dodaj** > **Machine Learning**.
1. W kroku scenariusz narzędzia model Builder wybierz opcję scenariusz prognozowania *cen* .

## <a name="load-the-data"></a>Ładowanie danych

Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub pliku lokalnego w formacie CSV lub TSV.

1. W kroku dane narzędzia model Builder wybierz pozycję *plik* z listy rozwijanej Źródło danych.
1. Wybierz przycisk obok pola tekstowego *Wybierz plik* i Użyj Eksploratora plików do przeglądania i wybierania *Taxi-Fare-test. csv* w katalogu *danych*
1. Wybierz *fare_amount* w *etykiecie lub kolumnie do przewidywania* rozwijania i przejdź do kroku uczenia narzędzia model Builder.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu prognozowania cen w tym samouczku to regresja. W trakcie procesu szkolenia modelu, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć najlepszy model dla zestawu danych.

Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych. Użyj tego wykresu jako wskazówek, aby wybrać odpowiednią wartość dla `Time to train (seconds)` pola:

\* Rozmiar zestawu danych  | Typ zestawu danych       | Średni Czas trwania uczenia *
------------- | ------------------ | --------------
0-10 MB     | Wartości numeryczne i tekstowe   | 10 sekund
10-100 MB   | Wartości numeryczne i tekstowe   | 10 min
100 – 500 MB  | Wartości numeryczne i tekstowe   | 30 minut
500 – 1 GB    | Wartości numeryczne i tekstowe   | 60 min
1 Gb+         | Wartości numeryczne i tekstowe   | 3 godziny +

1. Ponieważ plik danych szkoleniowych jest większy niż 10 MB, użyj 600 sekund (10 minut) jako wartości *czasu do uczenia (w sekundach)* .
2. Wybierz pozycję *Rozpocznij szkolenie*.

W trakcie całego procesu szkolenia dane o postępie są wyświetlane `Progress` w sekcji kroku uczenie.

- Stan przedstawia stan zakończenia procesu szkolenia.
- Najlepsza dokładność przedstawia dokładność najlepszego modelu, który został znaleziony przez konstruktora modelu do tej pory. Większa dokładność oznacza, że model przewidywalno dokładniej na danych testowych.
- Najlepszym algorytmem jest wyświetlana nazwa najlepszego wykonywania algorytmu, który został wykonany przez konstruktora modelu do tej pory.
- Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.

Po zakończeniu szkolenia przejdź do kroku szacowania.

## <a name="evaluate-the-model"></a>Oceń model

Wynikiem kroku szkolenia będzie jeden model, który miał najlepszą wydajność. W kroku szacowania narzędzia model Builder sekcja Output będzie zawierać algorytm używany przez model najlepszego wykonywania w najlepszym wpisie *modelu* oraz metryki w *najlepszej jakości modelu (RSquared)* . Ponadto tabela podsumowująca zawierająca pięć najważniejszych modeli i ich metryki.

Jeśli Twoje metryki dokładności nie są zadowalające, niektóre proste sposoby wypróbowania i poprawienia dokładności modelu mają na celu zwiększenie ilości czasu na nauczenie modelu lub użycie większej ilości danych. W przeciwnym razie przejdź do kroku kodu.

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby tworzyć przewidywania

W wyniku procesu szkolenia zostaną utworzone dwa projekty.

- TaxiFarePredictionML.ConsoleApp: Aplikacja konsolowa platformy .NET Core, która zawiera model szkolenia i kod zużycia.
- TaxiFarePredictionML. model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych, a także utrwalaną wersję najlepszego modelu podczas uczenia.

1. W kroku Code narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.
1. Kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* . Następnie **Dodaj odwołanie >** . Wybierz węzeł **projekty > rozwiązaniu** i z listy Sprawdź projekt *TaxiFarePredictionML. model* i wybierz przycisk OK.
1. Otwórz plik *program.cs* w projekcie *TaxiFarePrediction* .
1. Dodaj następujące instrukcje using, aby odwołać się do pakietu NuGet *Microsoft.ml* i projektu *TaxiFarePredictionML. model* :

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. `ConsumeModel` Dodaj metodę`Program` do klasy.

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

    Program załaduje szkolony model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) utworzy dla modelu i użyje go do prognozowania nowych danych. `ConsumeModel`

1. Aby przeprowadzić prognozowanie nowych danych przy użyciu modelu, Utwórz nowe wystąpienie `ModelInput` klasy i `ConsumeModel` Użyj metody. Zwróć uwagę, że opłata za opłaty nie jest częścią danych wejściowych. Dzieje się tak, ponieważ model generuje dla niego prognozę. Dodaj następujący kod do `Main` metody i uruchom aplikację

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

    Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:

    ```bash
    Predicted Fare: 16.82245
    ```

Jeśli musisz odwoływać się do wygenerowanych projektów w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotuj i poznanie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Oceń model
> - Używanie modelu dla prognoz

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej na temat tematów wymienionych w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modelu](../automate-training-with-model-builder.md#scenarios)
- [Regression](../resources/glossary.md#regression)
- [Metryki modelu regresji](../resources/metrics.md#metrics-for-regression)
- [Zestaw danych podróży NYC TLC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
