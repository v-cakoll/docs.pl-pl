---
title: 'Samouczek: prognozowanie popytu na wypożyczenie rowerowe — seria czasu'
description: W tym samouczku pokazano, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu univariate analiz szeregów czasowych i ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: e913c27c3501c4c553d7d62f948de31abb3d6f49
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740534"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Samouczek: prognozowanie popytu na usługę najmu roweru za pomocą analiz szeregów czasowych i ML.NET

Dowiedz się, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu analizy szeregów czasowych univariate na danych przechowywanych w bazie danych SQL Server z ML.NET.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
>
> * Omówienie problemu
> * Ładowanie danych z bazy danych
> * Tworzenie modelu prognozowania
> * Oceń model prognozowania
> * Zapisz model prognozowania
> * Korzystanie z modelu prognozowania

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.

## <a name="time-series-forecasting-sample-overview"></a>Omówienie przykładu prognozowania szeregów czasowych

Ten przykład to  **C# Aplikacja konsolowa platformy .NET Core** , która prognozuje zapotrzebowanie na wypożyczenie rowerów przy użyciu univariate algorytmu analizy szeregów czasowych znanej jako analiza pojedynczego spektrum. Kod dla tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w witrynie GitHub.

## <a name="understand-the-problem"></a>Omówienie problemu

Aby można było uruchomić wydajną operację, zarządzanie zapasami odgrywa kluczową rolę. Zbyt duża ilość produktu w magazynie oznacza niesprzedane produkty na półkach, które nie generują żadnych przychodów. Zbyt niewielki produkt prowadzi do utraty sprzedaży i klientów, którzy kupują od konkurencji. W związku z tym stałe pytanie to, co jest optymalną ilością zapasów do utrzymania? Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, przeglądając dane historyczne, identyfikując wzorce i korzystając z tych informacji do prognozowania wartości jakiś czas w przyszłości. 

Techniką analizowania danych używanych w tym samouczku jest univariate analiza szeregów czasowych. Univariate analiza szeregów czasowych Przyjrzyj się pojedynczej liczbie obserwacji w danym okresie w określonych odstępach czasu, takich jak sprzedaż miesięczna. 

Algorytm używany w tym samouczku jest [analizą pojedynczego spektrum (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). Działanie SSA działa przez złożenie szeregów czasowych w zestawie składników głównych. Te składniki mogą być interpretowane jako części sygnału, które odpowiadają trendom, zakłóceniom, sezonowości i wielu innym czynnikom. Następnie te składniki są ponownie skonstruowane i używane do prognozowania wartości nieco czasu w przyszłości.

## <a name="create-console-application"></a>Tworzenie aplikacji konsolowej

1. Utwórz nową  **C# aplikację konsolową .NET Core** o nazwie "BikeDemandForecasting".
1. Zainstaluj pakiet NuGet **Microsoft.ml** w wersji **1.4.0**
    1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.
    1. Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**.
    1. Zaznacz pole wyboru **Uwzględnij wersję wstępną** .
    1. Wybierz przycisk **Instaluj** .
    1. Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym akceptacji licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.
    1. Powtórz te kroki dla elementu **System. Data. SqlClient** w wersji **4.7.0** i **Microsoft. ml. szeregów czasowych** w wersji **1.4.0**.

### <a name="prepare-and-understand-the-data"></a>Przygotuj i poznanie danych

1. Utwórz katalog o nazwie *dane*.
1. Pobierz [plik bazy danych *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i Zapisz go w katalogu *danych* .

> [!NOTE]
> Dane używane w tym samouczku pochodzą z [zestawu danych programu UCI rower do udostępniania](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Fanaee-T, Hadi i gama, Joao, "zdarzenie Labeling detektory kompletów i wiedza w tle", postęp w sztucznej analizie (2013): PP. 1-15, Springer Berlin Heidelberg, [link sieci Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogoda. W przypadku zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z pojedynczej kolumny liczbowej, oryginalny zestaw danych został skrócony do uwzględnienia tylko następujących kolumn:  

- **dteday**: Data obserwacji.
- **Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).
- **CNT**: całkowita liczba czynszów rowerów dla danego dnia.

Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych SQL Server.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Poniżej przedstawiono przykład danych:

| RentalDate | Rok | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Tworzenie klas wejściowych i wyjściowych

1. Otwórz plik *program.cs* i Zastąp istniejące instrukcje `using` następującym:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Utwórz klasę `ModelInput`. Poniżej klasy `Program` Dodaj następujący kod.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    Klasa `ModelInput` zawiera następujące kolumny:

    - **RentalDate**: Data obserwacji.
    - **Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).
    - **TotalRentals**: Łączna liczba czynszów rowerów w danym dniu.

1. Utwórz klasę `ModelOutput` poniżej nowo utworzonej klasy `ModelInput`.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Klasa `ModelOutput` zawiera następujące kolumny:

    - **ForecastedRentals**: przewidywane wartości dla przedziału czasu.
    - **LowerBoundRentals**: przewidywane wartości minimalne dla prognozowanego okresu.
    - **UpperBoundRentals**: przewidywane wartości maksymalne dla prognozowanego okresu.

### <a name="define-paths-and-initialize-variables"></a>Zdefiniuj ścieżki i zainicjuj zmienne

1. Wewnątrz metody `Main` Zdefiniuj zmienne do przechowywania lokalizacji danych, parametrów połączenia i miejsca, w którym ma zostać zapisany szkolony model.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Zainicjuj zmienną `mlContext` z nowym wystąpieniem [`MLContext`](xref:Microsoft.ML.MLContext) , dodając następujący wiersz do metody `Main`.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie mlContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu. Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.

## <a name="load-the-data"></a>Ładowanie danych

1. Utwórz `DatabaseLoader` ładujące rekordy typu `ModelInput`.

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Zdefiniuj zapytanie w celu załadowania danych z bazy danych.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    Algorytmy ML.NET oczekują, że dane mają być typu [`Single`](xref:System.Single). W związku z tym wartości numeryczne pochodzące z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), wartości zmiennoprzecinkowej o pojedynczej precyzji, muszą być konwertowane na [`Real`](xref:System.Data.SqlDbType). 

    Kolumny `Year` i `TotalRental` są typami całkowitymi w bazie danych. Przy użyciu wbudowanej funkcji `CAST` są one rzutowane na `Real`.

1. Utwórz `DatabaseSource`, aby nawiązać połączenie z bazą danych i wykonać zapytanie.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Załaduj dane do `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Zestaw danych zawiera dwa lata dane. Tylko dane z pierwszego roku są używane na potrzeby szkoleń, drugi rok jest przetrzymywany, aby porównać rzeczywiste wartości z prognozami produkowanymi przez model. Filtrowanie danych przy użyciu transformacji [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) . 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    W pierwszym roku tylko wartości w `Year` kolumnie mniejsze niż 1 są wybierane przez ustawienie parametru `upperBound` na 1. Na odwrót, w drugim roku, wartości większe niż lub równe 1 są wybierane przez ustawienie parametru `lowerBound` na 1.

## <a name="define-time-series-analysis-pipeline"></a>Definiowanie potoku analizy szeregów czasowych

1. Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline` pobiera 365 punktów danych przez pierwszy rok i próbuje lub dzieli zestaw danych szeregów czasowych na 30 dni (miesięcznie), zgodnie z parametrem `seriesLength`. Każdy z tych przykładów jest analizowany przez cotygodniowe lub 7-dniowe okno. Podczas określania wartości prognozowanych dla następnych okresów, wartości z poprzednich siedmiu dni są używane do prognozowania. Model jest ustawiony na prognozowanie siedmiu okresów w przyszłości zgodnie z definicją `horizon` parametru. Ze względu na to, że prognoza jest świadomym zgadywaniem, nie zawsze jest poprawna 100%. W związku z tym warto znać zakres wartości w scenariuszach najlepszego i najgorszego przypadku zdefiniowanej przez górną i dolną granicę. W takim przypadku poziom zaufania dla dolnych i górnych granic jest ustawiony na 95%. Poziom zaufania można odpowiednio zwiększyć lub zmniejszyć. Im wyższa wartość, tym szerszy zakres jest między górną i dolną granicą, aby osiągnąć żądany poziom zaufania. 

1. Użyj metody [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) , aby nauczyć model i dopasować dane do wcześniej zdefiniowanego `forecastingPipeline`.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Oceń model

Oceń, jak dobrze model wykonuje, prognozowanie danych w następnym roku i porównywanie ich z wartościami rzeczywistymi.

1. Poniżej metody `Main` Utwórz nową metodę narzędzia o nazwie `Evaluate`.

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. Wewnątrz metody `Evaluate` prognozować dane drugiego roku przy użyciu metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) z przeszkolonym modelem.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Pobierz rzeczywiste wartości z danych za pomocą metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Pobierz wartości prognozy przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Oblicz różnicę między wartościami rzeczywistymi i prognozowanymi, często określanymi jako błąd.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Mierzenie wydajności przez obliczanie średniego błędu bezwzględnego i głównej średniej wartości błędu.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Do oceny wydajności są używane następujące metryki:

    - **Średni błąd bezwzględny**: mierzy, jak zamknięte przewidywania są rzeczywistej wartości. Ta wartość mieści się w zakresie od 0 do nieskończoności. Im bliżej wartości 0, tym lepiej jakość modelu.
    - **Średni błąd oznaczający rdzeń**: podsumowuje błąd thhe w modelu. Ta wartość mieści się w zakresie od 0 do nieskończoności. Im bliżej wartości 0, tym lepiej jakość modelu.

1. Wyprowadza metryki do konsoli.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Użyj metody `Evaluate` wewnątrz metody `Main`.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Zapisz model

Jeśli Twój model jest zadowalający, Zapisz go do późniejszego użycia w innych aplikacjach.

1. W metodzie `Main` Utwórz [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) jest wygodną metodą podejmowania pojedynczych prognoz.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Zapisz model w pliku o nazwie `MLModel.zip` jak określono przez wcześniej zdefiniowaną zmienną `modelPath`. Użyj metody [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) , aby zapisać model.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Użyj modelu do prognozowania popytu

1. Poniżej metody `Evaluate` Utwórz nową metodę narzędzia o nazwie `Forecast`.

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Wewnątrz metody `Forecast` Użyj metody [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) do prognozowania czynszów w ciągu następnych siedmiu dni.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Wyrównaj wartości rzeczywiste i prognozy dla siedmiu okresów.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Wykonaj iterację w danych wyjściowych prognozy i wyświetl ją w konsoli programu.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Uruchom aplikację

1. Wewnątrz metody `Main` Wywołaj metodę `Forecast`.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Uruchom aplikację. Dane wyjściowe podobne do poniższego powinny być wyświetlane w konsoli programu. W przypadku zwięzłości dane wyjściowe zostały zagęszczone.

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

Inspekcja wartości rzeczywistych i prognozowanych przedstawia następujące relacje:

![Porównanie rzeczywistych i prognoz](./media/time-series-demand-forecasting/forecast.png)

Przewidywane wartości nie przewidywalną dokładnej liczby wynajmu, ale zapewniają bardziej wąski zakres wartości, dzięki którym można przeprowadzić operację w celu zoptymalizowania użycia zasobów. 

Nabycia! Pomyślnie skompilowano model uczenia maszynowego w szeregach czasowych do prognozowania popytu na wypożyczenie roweru.

Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .

## <a name="next-steps"></a>Następne kroki

- [Zadania uczenia maszynowego w ML.NET](../resources/tasks.md)
- [Popraw dokładność modelu](../resources/improve-machine-learning-model-ml-net.md)
