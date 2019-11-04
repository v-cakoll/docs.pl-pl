---
title: 'Samouczek: prognozowanie cen przy użyciu regresji z konstruktorem modelu'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu konstruktora modelu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f5010f944dba007e24d3c0e22d4e339f9ed0522a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459187"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Samouczek: prognozowanie cen przy użyciu regresji z konstruktorem modelu

Dowiedz się, jak za pomocą konstruktora modeli ML.NET utworzyć model regresji do przewidywania cen.  Aplikacja konsolowa platformy .NET, którą opracowujesz w tym samouczku, przewiduje opłaty za taksówkę w oparciu o historyczne dane dotyczące opłat za taksówkę w Nowym Jorku.

Szablon prognozowania cen konstruktora modeli może być używany w każdym scenariuszu wymagającym wartości prognozowanych liczbowych. Przykładowe scenariusze obejmują: prognozowanie cen domu, prognozowanie popytu i prognozowanie sprzedaży.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
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

    1. Aby pobrać zestaw danych, przejdź do [linku pobierania Taxi-Fare-Train. csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).

    1. Gdy strona zostanie załadowana, kliknij prawym przyciskiem myszy w dowolnym miejscu na stronie i wybierz polecenie **Zapisz jako**.

    1. Użyj **okna dialogowego Zapisz jako** , aby zapisać plik w folderze *danych* utworzonym w poprzednim kroku.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Taxi-Fare-Train. csv* i wybierz polecenie **Właściwości**. W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.

Każdy wiersz w zestawie danych `taxi-fare-train.csv` zawiera szczegółowe informacje o podróży dokonywanych przez taksówkę.

1. Otwórz zestaw danych **Taxi-Fare-Train. csv**

    Podany zestaw danych zawiera następujące kolumny:

    - **vendor_id:** Identyfikator dostawcy taksówki jest funkcją.
    - **rate_code:** Typ szybkości podróży z taksówką jest funkcją.
    - **passenger_count:** Liczba pasażerów w podróży to funkcja.
    - **trip_time_in_secs:** Czas trwania podróży. Chcesz przewidzieć przejazd podróży przed ukończeniem podróży. W tym momencie nie wiesz, jak długo trwa podróż. W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.
    - **trip_distance:** Odległość podróży to funkcja.
    - **payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.
    - **fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.

`label` to kolumna, która ma zostać przewidywalna. Podczas wykonywania zadania regresji celem jest przewidywanie wartości liczbowej. W tym scenariuszu prognozowania cen jest przewidywany koszt najazdy z taksówką. W związku z tym **fare_amount** jest etykietą. Określone `features` to dane wejściowe, które umożliwiają modelowi prognozowanie `label`. W takim przypadku pozostałe kolumny z wyjątkiem **trip_time_in_secs** są używane jako funkcje lub dane wejściowe do przewidywania kwoty opłat.

## <a name="choose-a-scenario"></a>Wybierz scenariusz

Aby szkolić model, musisz wybrać z listy dostępnych scenariuszy uczenia maszynowego udostępnianych przez konstruktora modelu. W takim przypadku scenariusz jest `Price Prediction`.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *TaxiFarePrediction* i wybierz polecenie **Dodaj** > **Machine Learning**.
1. W kroku scenariusz narzędzia model Builder wybierz opcję scenariusz *prognozowania cen* .

## <a name="load-the-data"></a>Ładowanie danych

Konstruktor modelu akceptuje dane z dwóch źródeł, bazy danych SQL Server lub pliku lokalnego w formacie CSV lub TSV.

1. W kroku dane narzędzia model Builder wybierz pozycję *plik* z listy rozwijanej Źródło danych.
1. Wybierz przycisk obok pola tekstowego *Wybierz plik* i Użyj Eksploratora plików do przeglądania i wybierania *Taxi-Fare-test. csv* w katalogu *danych*
1. Wybierz pozycję *fare_amount* w *kolumnie do przewidywania (etykieta)* listy rozwijanej.
1. Rozwiń listę rozwijaną *kolumny wejściowe (funkcje)* i usuń zaznaczenie kolumny *trip_time_in_secs* , aby wykluczyć ją jako funkcję podczas szkolenia.  Przejdź do kroku uczenia narzędzia model Builder.

## <a name="train-the-model"></a>Uczenie modelu

Zadanie uczenia maszynowego używane do uczenia modelu prognozowania cen w tym samouczku to regresja. W trakcie procesu szkolenia modelu, Konstruktor modelu pociąga za siebie różne modele przy użyciu różnych algorytmów regresji i ustawień, aby znaleźć najlepszy model dla zestawu danych.

Czas wymagany przez model do uczenia jest proporcjonalny do ilości danych. Konstruktor modelu automatycznie wybiera wartość domyślną dla **czasu do uczenia (w sekundach)** na podstawie rozmiaru źródła danych.

1. Pozostaw wartość domyślną jako *czas do uczenia (w sekundach)* , chyba że wolisz dłużej uczenie się przez dłuższy czas.
2. Wybierz pozycję *Rozpocznij szkolenie*.

W trakcie całego procesu szkolenia dane o postępie są wyświetlane w sekcji `Progress` kroku uczenie.

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

- TaxiFarePredictionML. ConsoleApp: Aplikacja konsolowa platformy .NET Core, która zawiera model szkoleń i przykładowego kodu zużycia.
- TaxiFarePredictionML. model: Biblioteka klas .NET Standard zawierająca modele danych, które definiują schemat danych wejściowych i wyjściowych, zapisana wersja modelu najlepszego przebiegu podczas uczenia i klasy pomocnika o nazwie `ConsumeModel` do prognozowania.

1. W kroku Code narzędzia model Builder wybierz pozycję **Dodaj projekty** , aby dodać automatycznie generowane projekty do rozwiązania.
1. Otwórz plik *program.cs* w projekcie *TaxiFarePrediction* .
1. Dodaj następującą instrukcję using, aby odwołać się do projektu *TaxiFarePredictionML. model* :

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Aby przeprowadzić prognozowanie nowych danych przy użyciu modelu, Utwórz nowe wystąpienie klasy `ModelInput` w ramach metody `Main` aplikacji. Zwróć uwagę, że opłata za opłaty nie jest częścią danych wejściowych. Dzieje się tak, ponieważ model generuje dla niego prognozę. 

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

1. Użyj metody `Predict` z klasy `ConsumeModel`. Metoda `Predict` ładuje przeszkolony model, tworzy [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dla modelu i używa go do prognozowania nowych danych. 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uruchom aplikację.

    Dane wyjściowe generowane przez program powinny wyglądać podobnie do poniższego fragmentu kodu:

    ```bash
    Predicted Fare: 14.96086
    ```

Jeśli musisz odwoływać się do wygenerowanych projektów w późniejszym czasie w innym rozwiązaniu, możesz je znaleźć w katalogu `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób wykonywania tych instrukcji:
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
- [Ubytk](../resources/glossary.md#regression)
- [Metryki modelu regresji](../resources/metrics.md#metrics-for-regression)
- [Zestaw danych podróży NYC TLC](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
