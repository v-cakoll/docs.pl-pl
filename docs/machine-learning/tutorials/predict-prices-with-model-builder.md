---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji za pomocą Kreatora modeli'
description: W tym samouczku pokazano, jak utworzyć model regresji przy użyciu ML.NET Model Builder do przewidywania cen, w szczególności, New York City opłat za taksówki.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: 750738f8e3c65363e9996667feeccd1b84391f9f
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438241"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Samouczek: Przewidywanie cen przy użyciu regresji za pomocą Kreatora modeli

Dowiedz się, jak używać ML.NET Model Builder do tworzenia modelu regresji do przewidywania cen.  Aplikacja konsoli .NET, która została opracowyna w tym samouczku, przewiduje opłaty za taksówki na podstawie historycznych danych taryfy taksówek w Nowym Jorku.

Szablon prognozowania cen kreatora modeli może służyć do dowolnego scenariusza wymagającego wartości przewidywania liczbowego. Przykładowe scenariusze obejmują: przewidywanie cen nieruchomości, przewidywanie popytu i prognozowanie sprzedaży.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotowanie i zrozumienie danych
> - Wybieranie scenariusza
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu do prognoz

> [!NOTE]
> Kreator modeli jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

Aby uzyskać listę wymagań wstępnych i instrukcje instalacji, zapoznaj się z [podręcznikiem instalacji Kreatora modeli.](../how-to-guides/install-model-builder.md)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz **aplikację konsoli .NET Core o** nazwie "TaxiFarePrediction". Upewnij **się,** że rozwiązanie i projekt Umieść w tym samym katalogu **nie są zaznaczone** (VS 2019) lub **Sprawdź katalog** Create **dla rozwiązania** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

1. Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać pliki zestawów danych.

1. Zestaw danych używany do uczenia i oceny modelu uczenia maszynowego pochodzi z zestawu danych NYC TLC Taxi Trip.

    1. Aby pobrać zestaw danych, przejdź do linku do [pobrania taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Po załadowaniu strony kliknij prawym przyciskiem myszy dowolne miejsce na stronie i wybierz pozycję **Zapisz jako**.

    1. Użyj **okna dialogowego Zapisz jako,** aby zapisać plik w folderze *Dane* utworzonym w poprzednim kroku.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *taxi-fare-train.csv* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.

Każdy wiersz `taxi-fare-train.csv` w zestawie danych zawiera szczegóły podróży dokonywanych przez taksówkę.

1. Otwórz zestaw danych **taxi-fare-train.csv**

    Podany zestaw danych zawiera następujące kolumny:

    - **vendor_id:** Identyfikator dostawcy taksówki jest funkcją.
    - **rate_code:** Rodzaj stawki podróży taksówką jest cechą.
    - **passenger_count:** Liczba pasażerów w podróży jest cechą.
    - **trip_time_in_secs:** Czas podróży trwał. Chcesz przewidzieć taryfę podróży przed zakończeniem podróży. W tym momencie nie wiesz, jak długo potrwa podróż. W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.
    - **trip_distance:** Odległość podróży jest cechą.
    - **payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.
    - **fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.

Jest `label` to kolumna, którą chcesz przewidzieć. Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej. W tym scenariuszu przewidywania cen przewidywany jest koszt przejazdu taksówką. W związku z tym **fare_amount** jest etykietą. Zidentyfikowane `features` są dane wejściowe, które można `label`podać model do przewidzenia . W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty taryfy.

## <a name="choose-a-scenario"></a>Wybieranie scenariusza

Aby uszkolić model, należy wybrać z listy dostępnych scenariuszy uczenia maszynowego dostarczonych przez program Model Builder. W takim przypadku scenariusz `Price Prediction`jest .

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **uczenie maszynowe**.
1. W kroku scenariusza narzędzia Konstruktor modelu wybierz scenariusz *przewidywania cen.*

## <a name="load-the-data"></a>Ładowanie danych

Kreator modeli akceptuje dane z dwóch źródeł: bazy danych programu SQL Server lub pliku lokalnego w formacie csv lub tsv.

1. W kroku danych narzędzia Konstruktor modelu wybierz pozycję *Plik* z listy rozwijanej źródła danych.
1. Zaznacz przycisk obok pola *tekstowego Wybierz plik* i użyj Eksploratora plików do przeglądania i wybierz *taxi-fare-test.csv* w katalogu *Danych*
1. Wybierz *fare_amount* z *listy rozwijanej Kolumna do przewidzenia (etykieta).*
1. Rozwiń *rozwijanie kolumny wejściowej (funkcje)* i odznacz *kolumnę trip_time_in_secs,* aby wykluczyć ją jako funkcję podczas szkolenia.  Przejdź do etapu pociągu narzędzia Kreator modelu.

## <a name="train-the-model"></a>Uczenie modelu

Zadaniem uczenia maszynowego używanego do uczenia modelu przewidywania cen w tym samouczku jest regresja. Podczas procesu szkolenia modelu Model Builder trenuje oddzielne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć model o najwyższej wydajności dla zestawu danych.

Czas wymagany do szkolenia modelu jest proporcjonalny do ilości danych. Kreator modelu automatycznie wybiera wartość domyślną **dla czasu do wytrenowania (sekundy)** na podstawie rozmiaru źródła danych.

1. Pozostaw wartość domyślną, tak jak w *przypadku czasu na trening (sekundy),* chyba że wolisz trenować przez dłuższy czas.
2. Wybierz *pozycję Rozpocznij szkolenie*.

W trakcie całego procesu szkolenia dane o `Progress` postępach są wyświetlane w sekcji kroku pociągu.

- Stan wyświetla stan ukończenia procesu szkolenia.
- Najlepsza dokładność wyświetla dokładność najlepszego modelu znalezionego do tej pory przez Model Builder. Większa dokładność oznacza, że model przewidział bardziej poprawnie na danych testowych.
- Najlepszy algorytm wyświetla nazwę najlepiej działającego algorytmu wykonywanego do tej pory przez Model Builder.
- Ostatni algorytm wyświetla nazwę algorytmu ostatnio używanego przez program Model Builder do trenowania modelu.

Po zakończeniu szkolenia przejdź do kroku oceny.

## <a name="evaluate-the-model"></a>Ocena modelu

Wynikiem etapu szkolenia będzie jeden model, który miał najlepsze wyniki. W kroku oceny narzędzia Model Builder, sekcja danych wyjściowych, będzie zawierać algorytm używany przez model o najwyższej wydajności we wpisie *Najlepszy model* wraz z metrykami w najlepszej jakości *modelu (RSquared).* Ponadto tabela podsumowania zawierająca pięć najlepszych modeli i ich metryki.

Jeśli nie jesteś zadowolony z metryk dokładności, niektóre proste sposoby, aby spróbować poprawić dokładność modelu są zwiększenie czasu na szkolenie modelu lub użyć więcej danych. W przeciwnym razie przejdź do kroku kodu.

## <a name="add-the-code-to-make-predictions"></a>Dodaj kod, aby przewidywać

W wyniku procesu szkolenia zostaną utworzone dwa projekty.

- TaxiFarePredictionML.ConsoleApp: Aplikacja .NET Core Console, która zawiera kod szkolenia modelu i przykładowego użycia.
- TaxiFarePredictionML.Model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych modelu wejściowego i wyjściowego, `ConsumeModel` zapisaną wersję modelu o najwyższej skuteczności podczas szkolenia i klasę pomocniczą wywołaną do przewidywania.

1. W kroku kodu narzędzia Kreator modelu wybierz pozycję **Dodaj projekty,** aby dodać automatycznie generowane projekty do rozwiązania.
1. Otwórz plik *Program.cs* w projekcie *TaxiFarePrediction.*
1. Dodaj następującą instrukcję using, aby odwołać się do projektu *TaxiFarePredictionML.Model:*

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Aby przewidzieć na nowe dane przy użyciu modelu, `ModelInput` należy utworzyć `Main` nowe wystąpienie klasy wewnątrz metody aplikacji. Należy zauważyć, że kwota taryfy nie jest częścią danych wejściowych. Jest to spowodowane model wygeneruje przewidywanie dla niego.

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

1. Użyj `Predict` metody z `ConsumeModel` klasy. Metoda `Predict` ładuje przeszkolony model, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) utworzyć dla modelu i używa go do prognozowania na nowe dane.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uruchom aplikację.

    Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu:

    ```bash
    Predicted Fare: 14.96086
    ```

Jeśli chcesz odwołać się do wygenerowanych projektów w późniejszym czasie wewnątrz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` innego rozwiązania, można je znaleźć w katalogu.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Przygotowanie i zrozumienie danych
> - Wybieranie scenariusza
> - Ładowanie danych
> - Uczenie modelu
> - Ocena modelu
> - Użyj modelu do prognoz

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby dowiedzieć się więcej o tematach wymienionych w tym samouczku, odwiedź następujące zasoby:

- [Scenariusze konstruktora modeli](../automate-training-with-model-builder.md#scenario)
- [Regresji](../resources/glossary.md#regression)
- [Metryki modelu regresji](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [Zestaw danych NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
