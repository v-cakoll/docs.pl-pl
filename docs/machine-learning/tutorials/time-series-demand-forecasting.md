---
title: 'Poradnik: Prognoza popytu na wynajem rowerów - szeregi czasowe'
description: W tym samouczku pokazano, jak prognozować popyt na usługę wypożyczania rowerów przy użyciu analizy serii czasowych univariate i ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921256"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Samouczek: Prognozuj zapotrzebowanie na wypożyczalnię rowerów dzięki analizie szeregów czasowych i ML.NET

Dowiedz się, jak prognozować zapotrzebowanie na usługę wypożyczania rowerów przy użyciu analizy jednokierunkowych szeregów czasowych na danych przechowywanych w bazie danych programu SQL Server z ML.NET.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Ładowanie danych z bazy danych
> * Tworzenie modelu prognozowania
> * Ocena modelu prognozowania
> * Zapisywanie modelu prognozowania
> * Korzystanie z modelu prognozowania

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".

## <a name="time-series-forecasting-sample-overview"></a>Omówienie przykładowego prognozowania szeregów czasowych

Ten przykład jest **aplikacją konsoli C# .NET Core,** która prognozuje zapotrzebowanie na wypożyczanie rowerów przy użyciu algorytmu analizy serii czasowych univariate znanego jako analiza pojedynczego spektrum. Kod tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w usylenie GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

W celu uruchomienia wydajnej operacji, zarządzanie zapasami odgrywa kluczową rolę. Zbyt duża ilość produktu w magazynie oznacza, że niesprzedane produkty siedzące na półkach nie generują żadnych przychodów. Zbyt mały produkt prowadzi do utraty sprzedaży i klientów kupujących od konkurentów. Dlatego stałym pytaniem jest, jaka jest optymalna ilość zapasów, aby utrzymać się pod ręką? Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, analizując dane historyczne, identyfikując wzorce i używając tych informacji do prognozowania wartości w przyszłości.

Techniką analizowania danych użytych w tym samouczku jest analiza serii czasowych univariate. Analiza serii czasowych univariate analizuje pojedynczą obserwację numeryczną w określonym przedziale czasu, takim jak sprzedaż miesięczna.

Algorytm używany w tym samouczku jest [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA działa poprzez rozkładanie szeregów czasowych na zestaw głównych składników. Składniki te mogą być interpretowane jako części sygnału, które odpowiadają trendom, hałasowi, sezonowości i wielu innym czynnikom. Następnie te składniki są rekonstruowane i używane do prognozowania wartości jakiś czas w przyszłości.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz nową **aplikację konsoli C# .NET Core** o nazwie "BikeDemandForecasting".
1. Zainstaluj **Microsoft.ML** wersję **1.4.0** NuGet pakietu
    1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**.
    1. Zaznacz pole wyboru **Dołącz wersję wyjęcie.**
    1. Wybierz przycisk **Zainstaluj.**
    1. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.
    1. Powtórz te kroki dla **System.Data.SqlClient** w wersji **4.7.0** i **Microsoft.ML.TimeSeries** w wersji **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Przygotowywanie i rozumienie danych

1. Utwórz katalog o nazwie *Dane*.
1. Pobierz [plik bazy danych *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i zapisz go w katalogu *danych.*

> [!NOTE]
> Dane użyte w tym samouczku pochodzą z [zestawu danych udostępniania rowerów UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi i Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogodzie. Dla zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z pojedynczej kolumny liczbowej, oryginalny zestaw danych został skrócony, aby uwzględnić tylko następujące kolumny:

- **dteday**: Data obserwacji.
- **rok**: Zakodowany rok obserwacji (0=2011, 1=2012).
- **cnt**: Całkowita liczba wypożyczeń rowerów na ten dzień.

Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych programu SQL Server.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Poniżej przedstawiono próbkę danych:

| Data wynajmu | Year | TotalRentals (TotalRentals) |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz *Program.cs* plik i `using` zastąp istniejące instrukcje następującymi instrukcjami:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Utwórz klasę `ModelInput`. Poniżej `Program` klasy dodaj następujący kod.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    Klasa `ModelInput` zawiera następujące kolumny:

    - **RentalDate**: Data obserwacji.
    - **Rok**: Zakodowany rok obserwacji (0=2011, 1=2012).
    - **TotalRentals**: Całkowita liczba wypożyczeń rowerów na ten dzień.

1. Utwórz `ModelOutput` klasę poniżej `ModelInput` nowo utworzonej klasy.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Klasa `ModelOutput` zawiera następujące kolumny:

    - **ForecastedRentals**: Przewidywane wartości dla prognozowanego okresu.
    - **LowerBoundRentals**: Przewidywane wartości minimalne dla prognozowanego okresu.
    - **UpperBoundRentals**: Przewidywane wartości maksymalne dla prognozowanego okresu.

### <a name="define-paths-and-initialize-variables"></a>Definiowanie ścieżek i inicjowanie zmiennych

1. Wewnątrz `Main` metody zdefiniuj zmienne do przechowywania lokalizacji danych, parametry połączenia i gdzie zapisać uczonego modelu.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Zainicjować `mlContext` zmienną z nowym [`MLContext`](xref:Microsoft.ML.MLContext) wystąpieniem, dodając następujący `Main` wiersz do metody.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET i inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.

## <a name="load-the-data"></a>Ładowanie danych

1. Utwórz, `DatabaseLoader` który `ModelInput`ładuje rekordy typu .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Zdefiniuj kwerendę, aby załadować dane z bazy danych.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    algorytmy ML.NET oczekują, że [`Single`](xref:System.Single)dane będą typu . W związku z tym wartości liczbowe [`Real`](xref:System.Data.SqlDbType)pochodzące z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), pojedyncza wartość zmiennoprzecinkową, muszą zostać przekonwertowane na .

    Kolumny `Year` `TotalRental` i są zarówno typy liczby całkowitej w bazie danych. Korzystając `CAST` z wbudowanej funkcji, oba `Real`są rzutami na .

1. Utwórz `DatabaseSource` a, aby połączyć się z bazą danych i wykonać kwerendę.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Załaduj `IDataView`dane do pliku .

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Zestaw danych zawiera dane o wartości dwóch lat. Tylko dane z pierwszego roku są wykorzystywane do szkolenia, drugi rok jest utrzymywany w celu porównania rzeczywistych wartości z prognozą opracowaną przez model. Filtrowanie danych [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) przy użyciu transformacji.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    W pierwszym roku wybierane są `Year` tylko wartości w kolumnie `upperBound` mniejszej niż 1, ustawiając parametr na 1. I odwrotnie, dla drugiego roku wartości większe lub równe 1 `lowerBound` są wybierane przez ustawienie parametru na 1.

## <a name="define-time-series-analysis-pipeline"></a>Definiowanie potoku analizy szeregów czasowych

1. Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    Pobiera `forecastingPipeline` 365 punktów danych dla pierwszego roku i próbek lub dzieli zestaw danych szeregów czasowych na 30-dniowe (miesięczne) interwały określone w parametrze. `seriesLength` Każda z tych próbek jest analizowana przez okno tygodniowe lub 7-dniowe. Przy określaniu, co prognozowana wartość dla następnego okresu(-ów) jest, wartości z poprzednich siedmiu dni są używane do przewidywania. Model jest ustawiony na prognozowanie siedmiu okresów `horizon` w przyszłości zgodnie z definicją parametru. Ponieważ prognoza jest świadomym przypuszczeniem, nie zawsze jest w 100% dokładna. W związku z tym dobrze jest znać zakres wartości w najlepszych i najgorszych scenariuszach, zgodnie z definicją górnej i dolnej granicy. W tym przypadku poziom ufności dla dolnej i górnej granicy jest ustawiony na 95%. Poziom ufności można odpowiednio zwiększyć lub zmniejszyć. Im wyższa wartość, tym szerszy zakres jest między górną i dolną granicę, aby osiągnąć pożądany poziom zaufania.

1. Użyj [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody, aby nabyć model i dopasować `forecastingPipeline`dane do wcześniej zdefiniowanego .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Ocena modelu

Oceń, jak dobrze radzi sobie model, prognozując dane z przyszłorocznych i porównując je z rzeczywistymi wartościami.

1. Poniżej `Main` metody utwórz nową metodę `Evaluate`narzędzia o nazwie .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Wewnątrz `Evaluate` metody, prognoza danych drugiego roku przy [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) użyciu metody z uczonego modelu.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Pobierz rzeczywiste wartości z danych [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Pobierz wartości prognozy przy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) użyciu metody.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Oblicz różnicę między wartościami rzeczywistymi i prognozowymi, powszechnie określanymi jako błąd.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Zmierz wydajność, obliczając wartości Średni bezwzględny błąd i Wartość błędu kwadratowego średniego katalogu z rootem.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Aby ocenić wydajność, używane są następujące metryki:

    - **Średni błąd bezwzględny:** Mierzy, jak bliskie są prognozy do wartości rzeczywistej. Ta wartość waha się od 0 do nieskończoności. Im bliżej 0, tym lepsza jakość modelu.
    - **Root Średni kwadratowy błąd:** Podsumowuje błąd w modelu. Ta wartość waha się od 0 do nieskończoności. Im bliżej 0, tym lepsza jakość modelu.

1. Wydegowanie danych do konsoli.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Użyj `Evaluate` metody wewnątrz `Main` metody.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Zapisywanie modelu

Jeśli jesteś zadowolony z modelu, zapisz go do późniejszego wykorzystania w innych aplikacjach.

1. W `Main` metodzie utwórz plik [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)jest wygodną metodą dokonywania pojedynczych prognoz.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Zapisz model w pliku `MLModel.zip` o nazwie zgodnie z `modelPath` definicją wcześniej zdefiniowanej zmiennej. Użyj [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody, aby zapisać model.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Użyj modelu do prognozowania popytu

1. Poniżej `Evaluate` metody utwórz nową metodę `Forecast`narzędzia o nazwie .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Wewnątrz `Forecast` metody użyj [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metody prognozowania wynajmu na następne siedem dni.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Wyrównaj wartości rzeczywiste i prognozowane dla siedmiu okresów.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iterate przez dane wyjściowe prognozy i wyświetlić go na konsoli.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wewnątrz `Main` metody, wywołać `Forecast` metodę.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Uruchom aplikację. Dane wyjściowe podobne do poniższego powinny pojawić się na konsoli. W przypadku zwięzłości wyjście zostało skondensowane.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

Kontrola wartości rzeczywistych i prognozowanych pokazuje następujące relacje:

![Porównanie rzeczywiste a prognozowane](./media/time-series-demand-forecasting/forecast.png)

Podczas gdy prognozowane wartości nie przewidują dokładnej liczby wypożyczeń, zapewniają one bardziej wąski zakres wartości, który umożliwia operację optymalizacji wykorzystania zasobów.

Gratulacje! Teraz z powodzeniem skonstruowano model uczenia maszynowego szeregów czasowych, aby prognozować zapotrzebowanie na wypożyczanie rowerów.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)

## <a name="next-steps"></a>Następne kroki

- [Zadania uczenia maszynowego w ML.NET](../resources/tasks.md)
- [Zwiększanie dokładności modelu](../resources/improve-machine-learning-model-ml-net.md)
