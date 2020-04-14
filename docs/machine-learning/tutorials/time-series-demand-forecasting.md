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
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="a234b-103">Samouczek: Prognoza popytu na usługi wynajmu rowerów z analizą szeregów czasowych i ML.NET</span><span class="sxs-lookup"><span data-stu-id="a234b-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="a234b-104">Dowiedz się, jak prognozować zapotrzebowanie na usługę wypożyczania rowerów przy użyciu analizy jednozmiennego szeregów czasowych danych przechowywanych w bazie danych programu SQL Server z ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a234b-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="a234b-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a234b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a234b-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="a234b-106">Understand the problem</span></span>
> * <span data-ttu-id="a234b-107">Ładowanie danych z bazy danych</span><span class="sxs-lookup"><span data-stu-id="a234b-107">Load data from a database</span></span>
> * <span data-ttu-id="a234b-108">Tworzenie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a234b-108">Create a forecasting model</span></span>
> * <span data-ttu-id="a234b-109">Ocena modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a234b-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="a234b-110">Zapisywanie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a234b-110">Save a forecasting model</span></span>
> * <span data-ttu-id="a234b-111">Korzystanie z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a234b-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a234b-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a234b-112">Prerequisites</span></span>

- <span data-ttu-id="a234b-113">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="a234b-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="a234b-114">Omówienie przykładu prognozowania szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="a234b-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="a234b-115">Ten przykład jest **C# .NET Core aplikacji konsoli,** która prognozuje popyt na wynajem rowerów przy użyciu jednozmiennego algorytmu analizy szeregów czasowych znany jako Analiza pojedynczego spektrum.</span><span class="sxs-lookup"><span data-stu-id="a234b-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="a234b-116">Kod dla tego przykładu można znaleźć na repozytorium [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="a234b-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="a234b-117">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="a234b-117">Understand the problem</span></span>

<span data-ttu-id="a234b-118">Aby przeprowadzić wydajną operację, kluczową rolę odgrywa zarządzanie zapasami.</span><span class="sxs-lookup"><span data-stu-id="a234b-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="a234b-119">Posiadanie zbyt dużej ilości produktu w magazynie oznacza, że niesprzedane produkty siedzące na półkach nie generują żadnych przychodów.</span><span class="sxs-lookup"><span data-stu-id="a234b-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="a234b-120">Zbyt mało produktów prowadzi do utraty sprzedaży i klientów kupujących od konkurentów.</span><span class="sxs-lookup"><span data-stu-id="a234b-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="a234b-121">W związku z tym, stałe pytanie brzmi, jaka jest optymalna ilość zapasów, aby utrzymać pod ręką?</span><span class="sxs-lookup"><span data-stu-id="a234b-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="a234b-122">Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, analizując dane historyczne, identyfikując wzorce i używając tych informacji do prognozowania wartości przez jakiś czas w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a234b-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="a234b-123">Technika analizowania danych używana w tym samouczku jest jednozmienna analiza szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="a234b-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="a234b-124">Analiza szeregów czasowych univariate analizuje pojedynczą obserwację numeryczną w określonym przedziale czasu, takich jak sprzedaż miesięczna.</span><span class="sxs-lookup"><span data-stu-id="a234b-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="a234b-125">Algorytm używany w tym samouczku jest [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="a234b-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="a234b-126">SSA działa przez rozkładanie szeregów czasowych na zestaw głównych składników.</span><span class="sxs-lookup"><span data-stu-id="a234b-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="a234b-127">Składniki te mogą być interpretowane jako części sygnału, które odpowiadają trendom, hałasowi, sezonowości i wielu innym czynnikom.</span><span class="sxs-lookup"><span data-stu-id="a234b-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="a234b-128">Następnie te składniki są rekonstruowane i używane do prognozowania wartości przez jakiś czas w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a234b-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="a234b-129">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a234b-129">Create console application</span></span>

1. <span data-ttu-id="a234b-130">Utwórz nową **aplikację konsoli C# .NET Core** o nazwie "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="a234b-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="a234b-131">Zainstaluj **pakiet Microsoft.ML** w wersji **1.4.0** NuGet</span><span class="sxs-lookup"><span data-stu-id="a234b-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="a234b-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a234b-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="a234b-133">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="a234b-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="a234b-134">Zaznacz pole wyboru **Dołącz wydanie wstępne.**</span><span class="sxs-lookup"><span data-stu-id="a234b-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="a234b-135">Wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="a234b-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="a234b-136">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym Akceptacja licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a234b-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="a234b-137">Powtórz te kroki dla **System.Data.SqlClient** w wersji **4.7.0** i **Microsoft.ML.TimeSeries** w wersji **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="a234b-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a234b-138">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="a234b-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="a234b-139">Tworzenie katalogu o nazwie *Data*.</span><span class="sxs-lookup"><span data-stu-id="a234b-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="a234b-140">Pobierz [plik bazy danych *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i zapisz go w katalogu *Danych.*</span><span class="sxs-lookup"><span data-stu-id="a234b-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="a234b-141">Dane użyte w tym samouczku pochodzą z [zestawu danych UCI Bike Sharing](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="a234b-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="a234b-142">Fanaee-T, Hadi i Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="a234b-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="a234b-143">Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogodzie.</span><span class="sxs-lookup"><span data-stu-id="a234b-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="a234b-144">Dla zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z jednej kolumny numerycznej, oryginalny zestaw danych został skondensowany, aby uwzględnić tylko następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a234b-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="a234b-145">**dteday**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="a234b-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="a234b-146">**rok**: Zakodowany rok obserwacji (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="a234b-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="a234b-147">**cnt**: Całkowita liczba wypożyczeń rowerów na ten dzień.</span><span class="sxs-lookup"><span data-stu-id="a234b-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="a234b-148">Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a234b-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="a234b-149">Poniżej przedstawiono przykład danych:</span><span class="sxs-lookup"><span data-stu-id="a234b-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="a234b-150">10.00.</span><span class="sxs-lookup"><span data-stu-id="a234b-150">RentalDate</span></span> | <span data-ttu-id="a234b-151">Year</span><span class="sxs-lookup"><span data-stu-id="a234b-151">Year</span></span> | <span data-ttu-id="a234b-152">Całkowitarentals</span><span class="sxs-lookup"><span data-stu-id="a234b-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="a234b-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="a234b-153">1/1/2011</span></span>|<span data-ttu-id="a234b-154">0</span><span class="sxs-lookup"><span data-stu-id="a234b-154">0</span></span>|<span data-ttu-id="a234b-155">985</span><span class="sxs-lookup"><span data-stu-id="a234b-155">985</span></span>|
|<span data-ttu-id="a234b-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="a234b-156">1/2/2011</span></span>|<span data-ttu-id="a234b-157">0</span><span class="sxs-lookup"><span data-stu-id="a234b-157">0</span></span>|<span data-ttu-id="a234b-158">801</span><span class="sxs-lookup"><span data-stu-id="a234b-158">801</span></span>|
|<span data-ttu-id="a234b-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="a234b-159">1/3/2011</span></span>|<span data-ttu-id="a234b-160">0</span><span class="sxs-lookup"><span data-stu-id="a234b-160">0</span></span>|<span data-ttu-id="a234b-161">1349</span><span class="sxs-lookup"><span data-stu-id="a234b-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="a234b-162">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="a234b-162">Create input and output classes</span></span>

1. <span data-ttu-id="a234b-163">Otwórz *plik Program.cs* i zastąp istniejące `using` instrukcje następującymi:</span><span class="sxs-lookup"><span data-stu-id="a234b-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="a234b-164">Utwórz klasę `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="a234b-164">Create `ModelInput` class.</span></span> <span data-ttu-id="a234b-165">Poniżej `Program` klasy dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a234b-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="a234b-166">Klasa `ModelInput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a234b-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="a234b-167">**RentalDate**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="a234b-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="a234b-168">**Rok**: Zakodowany rok obserwacji (0=2011, 1=2012).</span><span class="sxs-lookup"><span data-stu-id="a234b-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="a234b-169">**TotalRentals**: Łączna liczba wypożyczeń rowerów na ten dzień.</span><span class="sxs-lookup"><span data-stu-id="a234b-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="a234b-170">Utwórz `ModelOutput` klasę poniżej nowo utworzonej `ModelInput` klasy.</span><span class="sxs-lookup"><span data-stu-id="a234b-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="a234b-171">Klasa `ModelOutput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a234b-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="a234b-172">**Prognozowanerenty:** Przewidywane wartości dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="a234b-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="a234b-173">**LowerBoundRentals**: Przewidywane wartości minimalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="a234b-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="a234b-174">**UpperBoundRentals**: Przewidywane wartości maksymalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="a234b-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="a234b-175">Definiowanie ścieżek i inicjowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="a234b-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="a234b-176">Wewnątrz `Main` metody zdefiniuj zmienne do przechowywania lokalizacji danych, parametry połączenia i gdzie zapisać przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="a234b-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="a234b-177">Zainicjować `mlContext` zmienną z nowym [`MLContext`](xref:Microsoft.ML.MLContext) wystąpieniem, dodając `Main` następujący wiersz do metody.</span><span class="sxs-lookup"><span data-stu-id="a234b-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="a234b-178">Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET i inicjowanie mlContext tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a234b-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a234b-179">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="a234b-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a234b-180">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a234b-180">Load the data</span></span>

1. <span data-ttu-id="a234b-181">Utwórz, `DatabaseLoader` który ładuje rekordy typu `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="a234b-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="a234b-182">Zdefiniuj kwerendę, aby załadować dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a234b-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="a234b-183">ML.NET algorytmy oczekują, że dane [`Single`](xref:System.Single)będą typu.</span><span class="sxs-lookup"><span data-stu-id="a234b-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="a234b-184">W związku z tym wartości liczbowe pochodzące [`Real`](xref:System.Data.SqlDbType)z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), pojedynczej precyzji wartości zmiennoprzecinkowej, muszą być konwertowane na .</span><span class="sxs-lookup"><span data-stu-id="a234b-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="a234b-185">Kolumny `Year` `TotalRental` i kolumny są zarówno typy całkowite w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a234b-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="a234b-186">Za `CAST` pomocą wbudowanej funkcji, są `Real`one zarówno rzutowania do .</span><span class="sxs-lookup"><span data-stu-id="a234b-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="a234b-187">Utwórz, `DatabaseSource` aby połączyć się z bazą danych i wykonać kwerendę.</span><span class="sxs-lookup"><span data-stu-id="a234b-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="a234b-188">Załaduj `IDataView`dane do pliku .</span><span class="sxs-lookup"><span data-stu-id="a234b-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="a234b-189">Zestaw danych zawiera dane o wartości dwóch lat.</span><span class="sxs-lookup"><span data-stu-id="a234b-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="a234b-190">Tylko dane z pierwszego roku są używane do szkolenia, drugi rok jest utrzymywany w celu porównania rzeczywistych wartości z prognozą opracowaną przez model.</span><span class="sxs-lookup"><span data-stu-id="a234b-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="a234b-191">Filtruj dane [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) za pomocą transformacji.</span><span class="sxs-lookup"><span data-stu-id="a234b-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="a234b-192">W pierwszym roku tylko wartości `Year` w kolumnie mniejszej niż `upperBound` 1 są wybierane przez ustawienie parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="a234b-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="a234b-193">Z drugiej strony w drugim roku wartości większe lub równe 1 są wybierane przez ustawienie parametru `lowerBound` na 1.</span><span class="sxs-lookup"><span data-stu-id="a234b-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="a234b-194">Definiowanie potoku analizy szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="a234b-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="a234b-195">Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="a234b-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="a234b-196">Trwa `forecastingPipeline` 365 punktów danych dla pierwszego roku i próbki lub dzieli zestaw danych szeregów czasowych na 30-dniowe (miesięczne) interwały określone przez `seriesLength` parametr.</span><span class="sxs-lookup"><span data-stu-id="a234b-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="a234b-197">Każda z tych próbek jest analizowana przez okno tygodniowe lub 7-dniowe.</span><span class="sxs-lookup"><span data-stu-id="a234b-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="a234b-198">Przy określaniu, jaka jest prognozowana wartość dla następnego okresu(-ów), wartości z poprzednich siedmiu dni są używane do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="a234b-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="a234b-199">Model jest ustawiony na prognozę siedmiu okresów `horizon` w przyszłości, zgodnie z definicją parametru.</span><span class="sxs-lookup"><span data-stu-id="a234b-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="a234b-200">Ponieważ prognoza jest świadomym przypuszczeniem, nie zawsze jest w 100% dokładna.</span><span class="sxs-lookup"><span data-stu-id="a234b-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="a234b-201">W związku z tym dobrze jest znać zakres wartości w najlepszym i najgorszym scenariuszu, zgodnie z definicją przez górne i dolne granice.</span><span class="sxs-lookup"><span data-stu-id="a234b-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="a234b-202">W tym przypadku poziom zaufania do dolnej i górnej granicy wynosi 95%.</span><span class="sxs-lookup"><span data-stu-id="a234b-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="a234b-203">Poziom ufności można odpowiednio zwiększyć lub zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="a234b-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="a234b-204">Im wyższa wartość, tym szerszy zakres znajduje się między górną i dolną granicą, aby osiągnąć pożądany poziom ufności.</span><span class="sxs-lookup"><span data-stu-id="a234b-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="a234b-205">Użyj [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody, aby wyszkolić model i `forecastingPipeline`dopasować dane do poprzednio zdefiniowanego .</span><span class="sxs-lookup"><span data-stu-id="a234b-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="a234b-206">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="a234b-206">Evaluate the model</span></span>

<span data-ttu-id="a234b-207">Oceń, jak dobrze model działa, prognozując dane z przyszłego roku i porównując je z rzeczywistymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="a234b-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="a234b-208">Poniżej `Main` metody utwórz nową `Evaluate`metodę narzędzia o nazwie .</span><span class="sxs-lookup"><span data-stu-id="a234b-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="a234b-209">Wewnątrz `Evaluate` metody prognozuj dane drugiego roku [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) przy użyciu metody z przeszkolonym modelem.</span><span class="sxs-lookup"><span data-stu-id="a234b-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="a234b-210">Pobierz rzeczywiste wartości z danych [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="a234b-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="a234b-211">Pobierz wartości prognozy [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="a234b-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="a234b-212">Oblicz różnicę między wartościami rzeczywistymi i prognozami, powszechnie określanym jako błąd.</span><span class="sxs-lookup"><span data-stu-id="a234b-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="a234b-213">Zmierz wydajność, obliczając wartości Średni błąd bezwzględny i Średni błąd kwadratu głównego.</span><span class="sxs-lookup"><span data-stu-id="a234b-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="a234b-214">Aby ocenić wydajność, używane są następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="a234b-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="a234b-215">**Średni błąd bezwzględny:** Mierzy, jak blisko prognozy są do wartości rzeczywistej.</span><span class="sxs-lookup"><span data-stu-id="a234b-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="a234b-216">Ta wartość waha się od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="a234b-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="a234b-217">Im bliżej 0, tym lepsza jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="a234b-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="a234b-218">**Główny średni kwadratowy błąd:** Podsumowuje błąd w modelu.</span><span class="sxs-lookup"><span data-stu-id="a234b-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="a234b-219">Ta wartość waha się od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="a234b-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="a234b-220">Im bliżej 0, tym lepsza jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="a234b-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="a234b-221">Wyśmiuj metryki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a234b-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="a234b-222">Użyj `Evaluate` metody wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="a234b-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="a234b-223">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="a234b-223">Save the model</span></span>

<span data-ttu-id="a234b-224">Jeśli jesteś zadowolony z modelu, zapisz go do późniejszego użycia w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="a234b-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="a234b-225">W `Main` metodzie utwórz plik [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="a234b-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="a234b-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)jest wygodną metodą do tworzenia pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="a234b-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="a234b-227">Zapisz model w pliku `MLModel.zip` wywoływanym zgodnie z `modelPath` poprzednio zdefiniowaną zmienną.</span><span class="sxs-lookup"><span data-stu-id="a234b-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="a234b-228">Użyj [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody, aby zapisać model.</span><span class="sxs-lookup"><span data-stu-id="a234b-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="a234b-229">Model służy do prognozowania popytu</span><span class="sxs-lookup"><span data-stu-id="a234b-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="a234b-230">Poniżej `Evaluate` metody utwórz nową `Forecast`metodę narzędzia o nazwie .</span><span class="sxs-lookup"><span data-stu-id="a234b-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="a234b-231">Wewnątrz `Forecast` metody użyj [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metody do prognozowania czynszów na następne siedem dni.</span><span class="sxs-lookup"><span data-stu-id="a234b-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="a234b-232">Wyrównaj rzeczywiste i prognozowane wartości dla siedmiu okresów.</span><span class="sxs-lookup"><span data-stu-id="a234b-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="a234b-233">Iteracji za pośrednictwem danych wyjściowych prognozy i wyświetlić go na konsoli.</span><span class="sxs-lookup"><span data-stu-id="a234b-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="a234b-234">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a234b-234">Run the application</span></span>

1. <span data-ttu-id="a234b-235">Wewnątrz `Main` metody, wywołać `Forecast` metodę.</span><span class="sxs-lookup"><span data-stu-id="a234b-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="a234b-236">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="a234b-236">Run the application.</span></span> <span data-ttu-id="a234b-237">Dane wyjściowe podobne do poniższego powinny pojawić się na konsoli.</span><span class="sxs-lookup"><span data-stu-id="a234b-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="a234b-238">Dla zwięzłości, wyjście zostało skondensowane.</span><span class="sxs-lookup"><span data-stu-id="a234b-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="a234b-239">Inspekcja wartości rzeczywistych i prognozowanych pokazuje następujące relacje:</span><span class="sxs-lookup"><span data-stu-id="a234b-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Porównanie rzeczywiste i prognozy](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="a234b-241">Prognozowane wartości nie przewidują dokładnej liczby wypożyczeń, ale zapewniają węższy zakres wartości, który umożliwia operacji optymalizacji wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="a234b-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="a234b-242">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a234b-242">Congratulations!</span></span> <span data-ttu-id="a234b-243">Pomyślnie zbudowano model uczenia maszynowego szeregów czasowych, aby prognozować zapotrzebowanie na wypożyczenie roweru.</span><span class="sxs-lookup"><span data-stu-id="a234b-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="a234b-244">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)</span><span class="sxs-lookup"><span data-stu-id="a234b-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a234b-245">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a234b-245">Next steps</span></span>

- [<span data-ttu-id="a234b-246">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="a234b-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="a234b-247">Zwiększanie dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="a234b-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
