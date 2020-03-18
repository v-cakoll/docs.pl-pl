---
title: 'Samouczek: Przewidywanie cen za pomocą regresji za pomocą Konstruktora modeli'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET Model Builder do przewidywania cen, w szczególności, opłaty za taksówki w Nowym Jorku.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c027fe57f571c791784b0bdb7ad9503fc49daa1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187697"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Samouczek: Przewidywanie cen za pomocą regresji za pomocą Konstruktora modeli

Dowiedz się, jak używać ML.NET Model Builder do tworzenia modelu regresji do przewidywania cen.  Aplikacja konsoli .NET, który opracujesz w tym samouczku, przewiduje opłaty za przejazdtaksówką na podstawie historycznych danych taryfy taksówkowej w Nowym Jorku.

Szablon prognozowania cen konstruktora modeli może służyć dla każdego scenariusza wymagającego wartości przewidywania numerycznego. Przykładowe scenariusze to: przewidywanie cen domów, przewidywanie popytu i prognozowanie sprzedaży.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotowywanie i rozumienie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu dla prognoz

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, odwiedź [podręcznik instalacji konstruktora modeli](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację C# .NET Core Console** o nazwie "TaxiFarePrediction". Upewnij się, że **rozwiązanie i projekt w tym samym katalogu** są **zaznaczone** (VS 2019) lub **Zaznacz akcesornie utwórz katalog dla rozwiązania** (VS 2017). **checked**

## <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

1. Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać pliki zestawu danych.

1. Zestaw danych używany do szkolenia i oceny modelu uczenia maszynowego pochodzi z zestawu danych NYC TLC Taxi Trip.

    1. Aby pobrać zestaw danych, przejdź do [linku pobierania taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Po załadowaniu strony kliknij prawym przyciskiem myszy dowolne miejsce na stronie i wybierz polecenie **Zapisz jako**.

    1. Użyj **okna dialogowego Zapisz jako,** aby zapisać plik w folderze *Dane* utworzonym w poprzednim kroku.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *taxi-fare-train.csv* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.

Każdy wiersz `taxi-fare-train.csv` w zestawie danych zawiera szczegółowe informacje o podróżach taksówką.

1. Otwórz zestaw danych **taxi-fare-train.csv**

    Dostarczony zestaw danych zawiera następujące kolumny:

    - **vendor_id:** Identyfikator dostawcy taksówek jest funkcją.
    - **rate_code:** Typ stawki podróży taksówką jest cechą.
    - **passenger_count:** Liczba pasażerów w podróży jest cechą.
    - **trip_time_in_secs:** Czas podróży. Chcesz przewidzieć taryfę podróży przed zakończeniem podróży. W tym momencie nie wiesz, jak długo potrwa podróż. W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.
    - **trip_distance:** Odległość podróży jest cechą.
    - **payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.
    - **fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.

Jest `label` to kolumna, którą chcesz przewidzieć. Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej. W tym scenariuszu przewidywania cen przewidywany jest koszt przejazdu taksówką. W związku z tym **fare_amount** jest etykieta. Zidentyfikowane `features` są dane wejściowe, które dajesz modelowi przewidzieć `label`. W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty taryfy.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

Aby nabyć model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez Konstruktora modeli. W takim przypadku scenariusz `Price Prediction`jest .

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W kroku scenariusza narzędzia Konstruktor modeli wybierz scenariusz *prognozowania cen.*

## <a name="load-the-data"></a>Ładowanie danych

ProgramKonystor modeli akceptuje dane z dwóch źródeł: bazy danych programu SQL Server lub pliku lokalnego w formacie csv lub tsv.

1. W kroku danych narzędzia Konstruktor modeli wybierz pozycję *Plik* z listy rozwijanej źródła danych.
1. Wybierz przycisk obok pola *tekstowego Wybierz plik* i użyj Eksploratora plików, aby przeglądać i wybierać *taxi-fare-test.csv* w katalogu *Data*
1. Wybierz *fare_amount* z listy rozwijanej *Kolumna do przewidywania (etykieta).*
1. Rozwiń menu *rozwijane Kolumny wejściowe (Funkcje)* i usuń zaznaczenie kolumny *trip_time_in_secs,* aby wykluczyć ją jako obiekt podczas szkolenia.  Przejdź do etapu pociągu narzędzia Konstruktor modeli.

## <a name="train-the-model"></a>Uczenie modelu

Zadaniem uczenia maszynowego używanym do uczenia modelu prognozowania cen w tym samouczku jest regresja. Podczas procesu szkolenia modelu Model Builder pociągów oddzielnych modeli przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć model o najlepszej wydajności dla zestawu danych.

Czas wymagany do przeszkolenia modelu jest proporcjonalny do ilości danych. Konstruktor modeli automatycznie wybiera wartość domyślną dla **time to train (seconds)** na podstawie rozmiaru źródła danych.

1. Pozostaw wartość domyślną, jak jest dla *Time to train (sekundy),* chyba że wolisz trenować przez dłuższy czas.
2. Wybierz *pozycję Rozpocznij szkolenie*.

W trakcie całego procesu szkolenia dane `Progress` postępu są wyświetlane w sekcji etapu pociągu.

- Stan wyświetla stan ukończenia procesu szkolenia.
- Najlepsza dokładność pokazuje dokładność najlepiej działającego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model jest bardziej poprawnie przewidywany na danych testowych.
- Najlepszy algorytm wyświetla nazwę algorytmu o najlepszej wydajności, który został znaleziony do tej pory przez Konstruktora modeli.
- Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez konstruktora modelu do uczenia modelu.

Po zakończeniu szkolenia przejdź do kroku oceny.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia będzie jeden model, który miał najlepszą wydajność. W kroku oceny narzędzia Konstruktor modeli sekcja danych wyjściowych będzie zawierać algorytm używany przez model o najlepszej wydajności we wpisie *Najlepszy model* wraz z metrykami w *najlepszej jakości modelu (RSquared).* Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.

Jeśli nie jesteś zadowolony z metryk dokładności, kilka prostych sposobów, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie przejdź do kroku kodu.

## <a name="add-the-code-to-make-predictions"></a>Dodawanie kodu do prognozowania

W wyniku procesu szkoleniowego zostaną utworzone dwa projekty.

- TaxiFarePredictionML.ConsoleApp: Aplikacja .NET Core Console, która zawiera szkolenie modelu i przykładowy kod zużycia.
- TaxiFarePredictionML.Model: Biblioteka klas .NET Standard zawierająca modele danych definiujące schemat danych modelu wejściowego i wyjściowego, zapisaną `ConsumeModel` wersję modelu o najlepszej wydajności podczas szkolenia i klasę pomocnika wywoływaną do prognozowania.

1. W kroku kodu narzędzia Konstruktor modeli wybierz pozycję **Dodaj projekty,** aby dodać automatycznie wygenerowane projekty do rozwiązania.
1. Otwórz plik *Program.cs* w projekcie *TaxiFarePrediction.*
1. Dodaj następującą instrukcję, aby odwołać się do projektu *TaxiFarePredictionML.Model:*

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Aby przewidzieć nowe dane przy użyciu modelu, należy `ModelInput` utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji. Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych. Jest to spowodowane model wygeneruje przewidywanie dla niego.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. Użyj `Predict` metody z `ConsumeModel` klasy. Metoda `Predict` ładuje uczonego [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) modelu, utworzyć dla modelu i używa go do prognozowania nowych danych.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uruchom aplikację.

    Dane wyjściowe wygenerowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:

    ```bash
    Predicted Fare: 14.96086
    ```

Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotowywanie i rozumienie danych
> - Wybierz scenariusz
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu dla prognoz

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej na tematy wymienione w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenarios)
- [Regresji](../resources/glossary.md#regression)
- [Metryki modelu regresji](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [NYC TLC Taxi Trip zestaw danych](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
