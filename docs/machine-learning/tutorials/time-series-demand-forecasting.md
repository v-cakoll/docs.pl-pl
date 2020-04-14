---
title: 'Samouczek: Prognoza popytu na wynajem rowerów - szeregi czasowe'
description: W tym samouczku pokazano, jak prognozować popyt na usługę wypożyczania rowerów przy użyciu analizy szeregów czasowych unizmianowych i ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 962c40ea0536d6b6057d936cfc4b95a49ddadbf8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243287"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Samouczek: Prognoza popytu na usługi wynajmu rowerów z analizą szeregów czasowych i ML.NET

Dowiedz się, jak prognozować zapotrzebowanie na usługę wypożyczania rowerów przy użyciu analizy jednozmiennego szeregów czasowych danych przechowywanych w bazie danych programu SQL Server z ML.NET.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Ładowanie danych z bazy danych
> * Tworzenie modelu prognozowania
> * Ocena modelu prognozowania
> * Zapisywanie modelu prognozowania
> * Korzystanie z modelu prognozowania

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".

## <a name="time-series-forecasting-sample-overview"></a>Omówienie przykładu prognozowania szeregów czasowych

Ten przykład jest **C# .NET Core aplikacji konsoli,** która prognozuje popyt na wynajem rowerów przy użyciu jednozmiennego algorytmu analizy szeregów czasowych znany jako Analiza pojedynczego spektrum. Kod dla tego przykładu można znaleźć na repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w usłudze GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

Aby przeprowadzić wydajną operację, kluczową rolę odgrywa zarządzanie zapasami. Posiadanie zbyt dużej ilości produktu w magazynie oznacza, że niesprzedane produkty siedzące na półkach nie generują żadnych przychodów. Zbyt mało produktów prowadzi do utraty sprzedaży i klientów kupujących od konkurentów. W związku z tym, stałe pytanie brzmi, jaka jest optymalna ilość zapasów, aby utrzymać pod ręką? Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, analizując dane historyczne, identyfikując wzorce i używając tych informacji do prognozowania wartości przez jakiś czas w przyszłości.

Technika analizowania danych używana w tym samouczku jest jednozmienna analiza szeregów czasowych. Analiza szeregów czasowych univariate analizuje pojedynczą obserwację numeryczną w określonym przedziale czasu, takich jak sprzedaż miesięczna.

Algorytm używany w tym samouczku jest [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA działa przez rozkładanie szeregów czasowych na zestaw głównych składników. Składniki te mogą być interpretowane jako części sygnału, które odpowiadają trendom, hałasowi, sezonowości i wielu innym czynnikom. Następnie te składniki są rekonstruowane i używane do prognozowania wartości przez jakiś czas w przyszłości.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz nową **aplikację konsoli C# .NET Core** o nazwie "BikeDemandForecasting".
1. Zainstaluj **pakiet Microsoft.ML** w wersji **1.4.0** NuGet
    1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.
    1. Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**.
    1. Zaznacz pole wyboru **Dołącz wydanie wstępne.**
    1. Wybierz przycisk **Zainstaluj.**
    1. Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    1. Powtórz te kroki dla **System.Data.SqlClient** w wersji **4.7.0** i **Microsoft.ML.TimeSeries** w wersji **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Przygotowanie i zrozumienie danych

1. Tworzenie katalogu o nazwie *Data*.
1. Pobierz [plik bazy danych *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i zapisz go w katalogu *Danych.*

> [!NOTE]
> Dane użyte w tym samouczku pochodzą z [zestawu danych UCI Bike Sharing](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi i Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogodzie. Dla zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z jednej kolumny numerycznej, oryginalny zestaw danych został skondensowany, aby uwzględnić tylko następujące kolumny:

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

Poniżej przedstawiono przykład danych:

| 10.00. | Year | Całkowitarentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz *plik Program.cs* i zastąp istniejące `using` instrukcje następującymi:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Utwórz klasę `ModelInput`. Poniżej `Program` klasy dodaj następujący kod.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    Klasa `ModelInput` zawiera następujące kolumny:

    - **RentalDate**: Data obserwacji.
    - **Rok**: Zakodowany rok obserwacji (0=2011, 1=2012).
    - **TotalRentals**: Łączna liczba wypożyczeń rowerów na ten dzień.

1. Utwórz `ModelOutput` klasę poniżej nowo utworzonej `ModelInput` klasy.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Klasa `ModelOutput` zawiera następujące kolumny:

    - **Prognozowanerenty:** Przewidywane wartości dla prognozowanego okresu.
    - **LowerBoundRentals**: Przewidywane wartości minimalne dla prognozowanego okresu.
    - **UpperBoundRentals**: Przewidywane wartości maksymalne dla prognozowanego okresu.

### <a name="define-paths-and-initialize-variables"></a>Definiowanie ścieżek i inicjowanie zmiennych

1. Wewnątrz `Main` metody zdefiniuj zmienne do przechowywania lokalizacji danych, parametry połączenia i gdzie zapisać przeszkolony model.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Zainicjować `mlContext` zmienną z nowym [`MLContext`](xref:Microsoft.ML.MLContext) wystąpieniem, dodając `Main` następujący wiersz do metody.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET i inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest podobny, koncepcyjnie, do `DBContext` w entity framework.

## <a name="load-the-data"></a>Ładowanie danych

1. Utwórz, `DatabaseLoader` który ładuje rekordy typu `ModelInput`.

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Zdefiniuj kwerendę, aby załadować dane z bazy danych.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algorytmy oczekują, że dane [`Single`](xref:System.Single)będą typu. W związku z tym wartości liczbowe pochodzące [`Real`](xref:System.Data.SqlDbType)z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), pojedynczej precyzji wartości zmiennoprzecinkowej, muszą być konwertowane na .

    Kolumny `Year` `TotalRental` i kolumny są zarówno typy całkowite w bazie danych. Za `CAST` pomocą wbudowanej funkcji, są `Real`one zarówno rzutowania do .

1. Utwórz, `DatabaseSource` aby połączyć się z bazą danych i wykonać kwerendę.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Załaduj `IDataView`dane do pliku .

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Zestaw danych zawiera dane o wartości dwóch lat. Tylko dane z pierwszego roku są używane do szkolenia, drugi rok jest utrzymywany w celu porównania rzeczywistych wartości z prognozą opracowaną przez model. Filtruj dane [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) za pomocą transformacji.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    W pierwszym roku tylko wartości `Year` w kolumnie mniejszej niż `upperBound` 1 są wybierane przez ustawienie parametru na 1. Z drugiej strony w drugim roku wartości większe lub równe 1 są wybierane przez ustawienie parametru `lowerBound` na 1.

## <a name="define-time-series-analysis-pipeline"></a>Definiowanie potoku analizy szeregów czasowych

1. Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    Trwa `forecastingPipeline` 365 punktów danych dla pierwszego roku i próbki lub dzieli zestaw danych szeregów czasowych na 30-dniowe (miesięczne) interwały określone przez `seriesLength` parametr. Każda z tych próbek jest analizowana przez okno tygodniowe lub 7-dniowe. Przy określaniu, jaka jest prognozowana wartość dla następnego okresu(-ów), wartości z poprzednich siedmiu dni są używane do przewidywania. Model jest ustawiony na prognozę siedmiu okresów `horizon` w przyszłości, zgodnie z definicją parametru. Ponieważ prognoza jest świadomym przypuszczeniem, nie zawsze jest w 100% dokładna. W związku z tym dobrze jest znać zakres wartości w najlepszym i najgorszym scenariuszu, zgodnie z definicją przez górne i dolne granice. W tym przypadku poziom zaufania do dolnej i górnej granicy wynosi 95%. Poziom ufności można odpowiednio zwiększyć lub zmniejszyć. Im wyższa wartość, tym szerszy zakres znajduje się między górną i dolną granicą, aby osiągnąć pożądany poziom ufności.

1. Użyj [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody, aby wyszkolić model i `forecastingPipeline`dopasować dane do poprzednio zdefiniowanego .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Ocena modelu

Oceń, jak dobrze model działa, prognozując dane z przyszłego roku i porównując je z rzeczywistymi wartościami.

1. Poniżej `Main` metody utwórz nową `Evaluate`metodę narzędzia o nazwie .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Wewnątrz `Evaluate` metody prognozuj dane drugiego roku [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) przy użyciu metody z przeszkolonym modelem.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Pobierz rzeczywiste wartości z danych [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Pobierz wartości prognozy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Oblicz różnicę między wartościami rzeczywistymi i prognozami, powszechnie określanym jako błąd.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Zmierz wydajność, obliczając wartości Średni błąd bezwzględny i Średni błąd kwadratu głównego.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Aby ocenić wydajność, używane są następujące metryki:

    - **Średni błąd bezwzględny:** Mierzy, jak blisko prognozy są do wartości rzeczywistej. Ta wartość waha się od 0 do nieskończoności. Im bliżej 0, tym lepsza jakość modelu.
    - **Główny średni kwadratowy błąd:** Podsumowuje błąd w modelu. Ta wartość waha się od 0 do nieskończoności. Im bliżej 0, tym lepsza jakość modelu.

1. Wyśmiuj metryki do konsoli.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Użyj `Evaluate` metody wewnątrz `Main` metody.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Zapisywanie modelu

Jeśli jesteś zadowolony z modelu, zapisz go do późniejszego użycia w innych aplikacjach.

1. W `Main` metodzie utwórz plik [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)jest wygodną metodą do tworzenia pojedynczych prognoz.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Zapisz model w pliku `MLModel.zip` wywoływanym zgodnie z `modelPath` poprzednio zdefiniowaną zmienną. Użyj [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody, aby zapisać model.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Model służy do prognozowania popytu

1. Poniżej `Evaluate` metody utwórz nową `Forecast`metodę narzędzia o nazwie .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Wewnątrz `Forecast` metody użyj [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metody do prognozowania czynszów na następne siedem dni.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Wyrównaj rzeczywiste i prognozowane wartości dla siedmiu okresów.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Iteracji za pośrednictwem danych wyjściowych prognozy i wyświetlić go na konsoli.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wewnątrz `Main` metody, wywołać `Forecast` metodę.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Uruchom aplikację. Dane wyjściowe podobne do poniższego powinny pojawić się na konsoli. Dla zwięzłości, wyjście zostało skondensowane.

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

Inspekcja wartości rzeczywistych i prognozowanych pokazuje następujące relacje:

![Porównanie rzeczywiste i prognozy](./media/time-series-demand-forecasting/forecast.png)

Prognozowane wartości nie przewidują dokładnej liczby wypożyczeń, ale zapewniają węższy zakres wartości, który umożliwia operacji optymalizacji wykorzystania zasobów.

Gratulacje! Pomyślnie zbudowano model uczenia maszynowego szeregów czasowych, aby prognozować zapotrzebowanie na wypożyczenie roweru.

Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)

## <a name="next-steps"></a>Następne kroki

- [Zadania uczenia maszynowego w ML.NET](../resources/tasks.md)
- [Zwiększanie dokładności modelu](../resources/improve-machine-learning-model-ml-net.md)
