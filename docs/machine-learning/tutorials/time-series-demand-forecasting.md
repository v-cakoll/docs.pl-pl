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
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="7315f-103">Samouczek: Prognozuj zapotrzebowanie na wypożyczalnię rowerów dzięki analizie szeregów czasowych i ML.NET</span><span class="sxs-lookup"><span data-stu-id="7315f-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="7315f-104">Dowiedz się, jak prognozować zapotrzebowanie na usługę wypożyczania rowerów przy użyciu analizy jednokierunkowych szeregów czasowych na danych przechowywanych w bazie danych programu SQL Server z ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7315f-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="7315f-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7315f-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7315f-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="7315f-106">Understand the problem</span></span>
> * <span data-ttu-id="7315f-107">Ładowanie danych z bazy danych</span><span class="sxs-lookup"><span data-stu-id="7315f-107">Load data from a database</span></span>
> * <span data-ttu-id="7315f-108">Tworzenie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="7315f-108">Create a forecasting model</span></span>
> * <span data-ttu-id="7315f-109">Ocena modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="7315f-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="7315f-110">Zapisywanie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="7315f-110">Save a forecasting model</span></span>
> * <span data-ttu-id="7315f-111">Korzystanie z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="7315f-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7315f-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7315f-112">Prerequisites</span></span>

- <span data-ttu-id="7315f-113">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="7315f-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="7315f-114">Omówienie przykładowego prognozowania szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="7315f-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="7315f-115">Ten przykład jest **aplikacją konsoli C# .NET Core,** która prognozuje zapotrzebowanie na wypożyczanie rowerów przy użyciu algorytmu analizy serii czasowych univariate znanego jako analiza pojedynczego spektrum.</span><span class="sxs-lookup"><span data-stu-id="7315f-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="7315f-116">Kod tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w usylenie GitHub.</span><span class="sxs-lookup"><span data-stu-id="7315f-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="7315f-117">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="7315f-117">Understand the problem</span></span>

<span data-ttu-id="7315f-118">W celu uruchomienia wydajnej operacji, zarządzanie zapasami odgrywa kluczową rolę.</span><span class="sxs-lookup"><span data-stu-id="7315f-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="7315f-119">Zbyt duża ilość produktu w magazynie oznacza, że niesprzedane produkty siedzące na półkach nie generują żadnych przychodów.</span><span class="sxs-lookup"><span data-stu-id="7315f-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="7315f-120">Zbyt mały produkt prowadzi do utraty sprzedaży i klientów kupujących od konkurentów.</span><span class="sxs-lookup"><span data-stu-id="7315f-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="7315f-121">Dlatego stałym pytaniem jest, jaka jest optymalna ilość zapasów, aby utrzymać się pod ręką?</span><span class="sxs-lookup"><span data-stu-id="7315f-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="7315f-122">Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, analizując dane historyczne, identyfikując wzorce i używając tych informacji do prognozowania wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7315f-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="7315f-123">Techniką analizowania danych użytych w tym samouczku jest analiza serii czasowych univariate.</span><span class="sxs-lookup"><span data-stu-id="7315f-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="7315f-124">Analiza serii czasowych univariate analizuje pojedynczą obserwację numeryczną w określonym przedziale czasu, takim jak sprzedaż miesięczna.</span><span class="sxs-lookup"><span data-stu-id="7315f-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="7315f-125">Algorytm używany w tym samouczku jest [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="7315f-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="7315f-126">SSA działa poprzez rozkładanie szeregów czasowych na zestaw głównych składników.</span><span class="sxs-lookup"><span data-stu-id="7315f-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="7315f-127">Składniki te mogą być interpretowane jako części sygnału, które odpowiadają trendom, hałasowi, sezonowości i wielu innym czynnikom.</span><span class="sxs-lookup"><span data-stu-id="7315f-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="7315f-128">Następnie te składniki są rekonstruowane i używane do prognozowania wartości jakiś czas w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7315f-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="7315f-129">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="7315f-129">Create console application</span></span>

1. <span data-ttu-id="7315f-130">Utwórz nową **aplikację konsoli C# .NET Core** o nazwie "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="7315f-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="7315f-131">Zainstaluj **Microsoft.ML** wersję **1.4.0** NuGet pakietu</span><span class="sxs-lookup"><span data-stu-id="7315f-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="7315f-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7315f-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="7315f-133">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="7315f-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="7315f-134">Zaznacz pole wyboru **Dołącz wersję wyjęcie.**</span><span class="sxs-lookup"><span data-stu-id="7315f-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="7315f-135">Wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="7315f-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="7315f-136">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="7315f-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="7315f-137">Powtórz te kroki dla **System.Data.SqlClient** w wersji **4.7.0** i **Microsoft.ML.TimeSeries** w wersji **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="7315f-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="7315f-138">Przygotowywanie i rozumienie danych</span><span class="sxs-lookup"><span data-stu-id="7315f-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="7315f-139">Utwórz katalog o nazwie *Dane*.</span><span class="sxs-lookup"><span data-stu-id="7315f-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="7315f-140">Pobierz [plik bazy danych *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i zapisz go w katalogu *danych.*</span><span class="sxs-lookup"><span data-stu-id="7315f-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="7315f-141">Dane użyte w tym samouczku pochodzą z [zestawu danych udostępniania rowerów UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="7315f-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="7315f-142">Fanaee-T, Hadi i Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="7315f-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="7315f-143">Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogodzie.</span><span class="sxs-lookup"><span data-stu-id="7315f-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="7315f-144">Dla zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z pojedynczej kolumny liczbowej, oryginalny zestaw danych został skrócony, aby uwzględnić tylko następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="7315f-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="7315f-145">**dteday**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="7315f-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="7315f-146">**rok**: Zakodowany rok obserwacji (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="7315f-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="7315f-147">**cnt**: Całkowita liczba wypożyczeń rowerów na ten dzień.</span><span class="sxs-lookup"><span data-stu-id="7315f-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="7315f-148">Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7315f-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="7315f-149">Poniżej przedstawiono próbkę danych:</span><span class="sxs-lookup"><span data-stu-id="7315f-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="7315f-150">Data wynajmu</span><span class="sxs-lookup"><span data-stu-id="7315f-150">RentalDate</span></span> | <span data-ttu-id="7315f-151">Year</span><span class="sxs-lookup"><span data-stu-id="7315f-151">Year</span></span> | <span data-ttu-id="7315f-152">TotalRentals (TotalRentals)</span><span class="sxs-lookup"><span data-stu-id="7315f-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="7315f-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="7315f-153">1/1/2011</span></span>|<span data-ttu-id="7315f-154">0</span><span class="sxs-lookup"><span data-stu-id="7315f-154">0</span></span>|<span data-ttu-id="7315f-155">985</span><span class="sxs-lookup"><span data-stu-id="7315f-155">985</span></span>|
|<span data-ttu-id="7315f-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="7315f-156">1/2/2011</span></span>|<span data-ttu-id="7315f-157">0</span><span class="sxs-lookup"><span data-stu-id="7315f-157">0</span></span>|<span data-ttu-id="7315f-158">801</span><span class="sxs-lookup"><span data-stu-id="7315f-158">801</span></span>|
|<span data-ttu-id="7315f-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="7315f-159">1/3/2011</span></span>|<span data-ttu-id="7315f-160">0</span><span class="sxs-lookup"><span data-stu-id="7315f-160">0</span></span>|<span data-ttu-id="7315f-161">1349</span><span class="sxs-lookup"><span data-stu-id="7315f-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="7315f-162">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="7315f-162">Create input and output classes</span></span>

1. <span data-ttu-id="7315f-163">Otwórz *Program.cs* plik i `using` zastąp istniejące instrukcje następującymi instrukcjami:</span><span class="sxs-lookup"><span data-stu-id="7315f-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="7315f-164">Utwórz klasę `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="7315f-164">Create `ModelInput` class.</span></span> <span data-ttu-id="7315f-165">Poniżej `Program` klasy dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="7315f-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="7315f-166">Klasa `ModelInput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="7315f-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="7315f-167">**RentalDate**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="7315f-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="7315f-168">**Rok**: Zakodowany rok obserwacji (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="7315f-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="7315f-169">**TotalRentals**: Całkowita liczba wypożyczeń rowerów na ten dzień.</span><span class="sxs-lookup"><span data-stu-id="7315f-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="7315f-170">Utwórz `ModelOutput` klasę poniżej `ModelInput` nowo utworzonej klasy.</span><span class="sxs-lookup"><span data-stu-id="7315f-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="7315f-171">Klasa `ModelOutput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="7315f-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="7315f-172">**ForecastedRentals**: Przewidywane wartości dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="7315f-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="7315f-173">**LowerBoundRentals**: Przewidywane wartości minimalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="7315f-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="7315f-174">**UpperBoundRentals**: Przewidywane wartości maksymalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="7315f-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="7315f-175">Definiowanie ścieżek i inicjowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="7315f-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="7315f-176">Wewnątrz `Main` metody zdefiniuj zmienne do przechowywania lokalizacji danych, parametry połączenia i gdzie zapisać uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="7315f-177">Zainicjować `mlContext` zmienną z nowym [`MLContext`](xref:Microsoft.ML.MLContext) wystąpieniem, dodając następujący `Main` wiersz do metody.</span><span class="sxs-lookup"><span data-stu-id="7315f-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="7315f-178">Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET i inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7315f-179">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="7315f-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7315f-180">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="7315f-180">Load the data</span></span>

1. <span data-ttu-id="7315f-181">Utwórz, `DatabaseLoader` który `ModelInput`ładuje rekordy typu .</span><span class="sxs-lookup"><span data-stu-id="7315f-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="7315f-182">Zdefiniuj kwerendę, aby załadować dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7315f-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="7315f-183">algorytmy ML.NET oczekują, że [`Single`](xref:System.Single)dane będą typu .</span><span class="sxs-lookup"><span data-stu-id="7315f-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="7315f-184">W związku z tym wartości liczbowe [`Real`](xref:System.Data.SqlDbType)pochodzące z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), pojedyncza wartość zmiennoprzecinkową, muszą zostać przekonwertowane na .</span><span class="sxs-lookup"><span data-stu-id="7315f-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="7315f-185">Kolumny `Year` `TotalRental` i są zarówno typy liczby całkowitej w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7315f-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="7315f-186">Korzystając `CAST` z wbudowanej funkcji, oba `Real`są rzutami na .</span><span class="sxs-lookup"><span data-stu-id="7315f-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="7315f-187">Utwórz `DatabaseSource` a, aby połączyć się z bazą danych i wykonać kwerendę.</span><span class="sxs-lookup"><span data-stu-id="7315f-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="7315f-188">Załaduj `IDataView`dane do pliku .</span><span class="sxs-lookup"><span data-stu-id="7315f-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="7315f-189">Zestaw danych zawiera dane o wartości dwóch lat.</span><span class="sxs-lookup"><span data-stu-id="7315f-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="7315f-190">Tylko dane z pierwszego roku są wykorzystywane do szkolenia, drugi rok jest utrzymywany w celu porównania rzeczywistych wartości z prognozą opracowaną przez model.</span><span class="sxs-lookup"><span data-stu-id="7315f-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="7315f-191">Filtrowanie danych [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) przy użyciu transformacji.</span><span class="sxs-lookup"><span data-stu-id="7315f-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="7315f-192">W pierwszym roku wybierane są `Year` tylko wartości w kolumnie `upperBound` mniejszej niż 1, ustawiając parametr na 1.</span><span class="sxs-lookup"><span data-stu-id="7315f-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="7315f-193">I odwrotnie, dla drugiego roku wartości większe lub równe 1 `lowerBound` są wybierane przez ustawienie parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="7315f-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="7315f-194">Definiowanie potoku analizy szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="7315f-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="7315f-195">Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="7315f-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="7315f-196">Pobiera `forecastingPipeline` 365 punktów danych dla pierwszego roku i próbek lub dzieli zestaw danych szeregów czasowych na 30-dniowe (miesięczne) interwały określone w parametrze. `seriesLength`</span><span class="sxs-lookup"><span data-stu-id="7315f-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="7315f-197">Każda z tych próbek jest analizowana przez okno tygodniowe lub 7-dniowe.</span><span class="sxs-lookup"><span data-stu-id="7315f-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="7315f-198">Przy określaniu, co prognozowana wartość dla następnego okresu(-ów) jest, wartości z poprzednich siedmiu dni są używane do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="7315f-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="7315f-199">Model jest ustawiony na prognozowanie siedmiu okresów `horizon` w przyszłości zgodnie z definicją parametru.</span><span class="sxs-lookup"><span data-stu-id="7315f-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="7315f-200">Ponieważ prognoza jest świadomym przypuszczeniem, nie zawsze jest w 100% dokładna.</span><span class="sxs-lookup"><span data-stu-id="7315f-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="7315f-201">W związku z tym dobrze jest znać zakres wartości w najlepszych i najgorszych scenariuszach, zgodnie z definicją górnej i dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="7315f-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="7315f-202">W tym przypadku poziom ufności dla dolnej i górnej granicy jest ustawiony na 95%.</span><span class="sxs-lookup"><span data-stu-id="7315f-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="7315f-203">Poziom ufności można odpowiednio zwiększyć lub zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="7315f-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="7315f-204">Im wyższa wartość, tym szerszy zakres jest między górną i dolną granicę, aby osiągnąć pożądany poziom zaufania.</span><span class="sxs-lookup"><span data-stu-id="7315f-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="7315f-205">Użyj [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody, aby nabyć model i dopasować `forecastingPipeline`dane do wcześniej zdefiniowanego .</span><span class="sxs-lookup"><span data-stu-id="7315f-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="7315f-206">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="7315f-206">Evaluate the model</span></span>

<span data-ttu-id="7315f-207">Oceń, jak dobrze radzi sobie model, prognozując dane z przyszłorocznych i porównując je z rzeczywistymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="7315f-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="7315f-208">Poniżej `Main` metody utwórz nową metodę `Evaluate`narzędzia o nazwie .</span><span class="sxs-lookup"><span data-stu-id="7315f-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="7315f-209">Wewnątrz `Evaluate` metody, prognoza danych drugiego roku przy [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) użyciu metody z uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="7315f-210">Pobierz rzeczywiste wartości z danych [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="7315f-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="7315f-211">Pobierz wartości prognozy przy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="7315f-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="7315f-212">Oblicz różnicę między wartościami rzeczywistymi i prognozowymi, powszechnie określanymi jako błąd.</span><span class="sxs-lookup"><span data-stu-id="7315f-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="7315f-213">Zmierz wydajność, obliczając wartości Średni bezwzględny błąd i Wartość błędu kwadratowego średniego katalogu z rootem.</span><span class="sxs-lookup"><span data-stu-id="7315f-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="7315f-214">Aby ocenić wydajność, używane są następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="7315f-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="7315f-215">**Średni błąd bezwzględny:** Mierzy, jak bliskie są prognozy do wartości rzeczywistej.</span><span class="sxs-lookup"><span data-stu-id="7315f-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="7315f-216">Ta wartość waha się od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="7315f-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="7315f-217">Im bliżej 0, tym lepsza jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="7315f-218">**Root Średni kwadratowy błąd:** Podsumowuje błąd w modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="7315f-219">Ta wartość waha się od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="7315f-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="7315f-220">Im bliżej 0, tym lepsza jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="7315f-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="7315f-221">Wydegowanie danych do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7315f-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="7315f-222">Użyj `Evaluate` metody wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7315f-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="7315f-223">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="7315f-223">Save the model</span></span>

<span data-ttu-id="7315f-224">Jeśli jesteś zadowolony z modelu, zapisz go do późniejszego wykorzystania w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="7315f-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="7315f-225">W `Main` metodzie utwórz plik [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="7315f-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="7315f-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)jest wygodną metodą dokonywania pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="7315f-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="7315f-227">Zapisz model w pliku `MLModel.zip` o nazwie zgodnie z `modelPath` definicją wcześniej zdefiniowanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7315f-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="7315f-228">Użyj [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody, aby zapisać model.</span><span class="sxs-lookup"><span data-stu-id="7315f-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="7315f-229">Użyj modelu do prognozowania popytu</span><span class="sxs-lookup"><span data-stu-id="7315f-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="7315f-230">Poniżej `Evaluate` metody utwórz nową metodę `Forecast`narzędzia o nazwie .</span><span class="sxs-lookup"><span data-stu-id="7315f-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="7315f-231">Wewnątrz `Forecast` metody użyj [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metody prognozowania wynajmu na następne siedem dni.</span><span class="sxs-lookup"><span data-stu-id="7315f-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="7315f-232">Wyrównaj wartości rzeczywiste i prognozowane dla siedmiu okresów.</span><span class="sxs-lookup"><span data-stu-id="7315f-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="7315f-233">Iterate przez dane wyjściowe prognozy i wyświetlić go na konsoli.</span><span class="sxs-lookup"><span data-stu-id="7315f-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="7315f-234">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7315f-234">Run the application</span></span>

1. <span data-ttu-id="7315f-235">Wewnątrz `Main` metody, wywołać `Forecast` metodę.</span><span class="sxs-lookup"><span data-stu-id="7315f-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="7315f-236">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="7315f-236">Run the application.</span></span> <span data-ttu-id="7315f-237">Dane wyjściowe podobne do poniższego powinny pojawić się na konsoli.</span><span class="sxs-lookup"><span data-stu-id="7315f-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="7315f-238">W przypadku zwięzłości wyjście zostało skondensowane.</span><span class="sxs-lookup"><span data-stu-id="7315f-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="7315f-239">Kontrola wartości rzeczywistych i prognozowanych pokazuje następujące relacje:</span><span class="sxs-lookup"><span data-stu-id="7315f-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Porównanie rzeczywiste a prognozowane](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="7315f-241">Podczas gdy prognozowane wartości nie przewidują dokładnej liczby wypożyczeń, zapewniają one bardziej wąski zakres wartości, który umożliwia operację optymalizacji wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="7315f-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="7315f-242">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="7315f-242">Congratulations!</span></span> <span data-ttu-id="7315f-243">Teraz z powodzeniem skonstruowano model uczenia maszynowego szeregów czasowych, aby prognozować zapotrzebowanie na wypożyczanie rowerów.</span><span class="sxs-lookup"><span data-stu-id="7315f-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="7315f-244">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)</span><span class="sxs-lookup"><span data-stu-id="7315f-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7315f-245">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7315f-245">Next steps</span></span>

- [<span data-ttu-id="7315f-246">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="7315f-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="7315f-247">Zwiększanie dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="7315f-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
