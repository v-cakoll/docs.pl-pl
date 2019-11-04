---
title: 'Samouczek: prognozowanie popytu na wypożyczenie rowerowe — seria czasu'
description: W tym samouczku pokazano, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu univariate analiz szeregów czasowych i ML.NET.
ms.date: 10/31/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: f30aac5f8467c2410e9008bafea3cf35af3f4e2a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425640"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="233c3-103">Samouczek: prognozowanie popytu na usługę najmu roweru za pomocą analiz szeregów czasowych i ML.NET</span><span class="sxs-lookup"><span data-stu-id="233c3-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="233c3-104">Dowiedz się, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu analizy szeregów czasowych univariate na danych przechowywanych w bazie danych SQL Server z ML.NET.</span><span class="sxs-lookup"><span data-stu-id="233c3-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="233c3-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="233c3-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="233c3-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="233c3-106">Understand the problem</span></span>
> * <span data-ttu-id="233c3-107">Ładowanie danych z bazy danych</span><span class="sxs-lookup"><span data-stu-id="233c3-107">Load data from a database</span></span>
> * <span data-ttu-id="233c3-108">Tworzenie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="233c3-108">Create a forecasting model</span></span>
> * <span data-ttu-id="233c3-109">Oceń model prognozowania</span><span class="sxs-lookup"><span data-stu-id="233c3-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="233c3-110">Zapisz model prognozowania</span><span class="sxs-lookup"><span data-stu-id="233c3-110">Save a forecasting model</span></span>
> * <span data-ttu-id="233c3-111">Korzystanie z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="233c3-111">Use a forecasting model</span></span>

> [!NOTE]
> <span data-ttu-id="233c3-112">W tym samouczku jest stosowana wersja zapoznawcza programu DatabaseLoader.</span><span class="sxs-lookup"><span data-stu-id="233c3-112">This tutorial uses a preview version of DatabaseLoader.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="233c3-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="233c3-113">Prerequisites</span></span>

- <span data-ttu-id="233c3-114">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="233c3-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="233c3-115">Omówienie przykładu prognozowania szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="233c3-115">Time series forecasting sample overview</span></span>

<span data-ttu-id="233c3-116">Ten przykład to  **C# Aplikacja konsolowa platformy .NET Core** , która prognozuje zapotrzebowanie na wypożyczenie rowerów przy użyciu univariate algorytmu analizy szeregów czasowych znanej jako analiza pojedynczego spektrum.</span><span class="sxs-lookup"><span data-stu-id="233c3-116">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="233c3-117">Kod dla tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="233c3-117">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="233c3-118">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="233c3-118">Understand the problem</span></span>

<span data-ttu-id="233c3-119">Aby można było uruchomić wydajną operację, zarządzanie zapasami odgrywa kluczową rolę.</span><span class="sxs-lookup"><span data-stu-id="233c3-119">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="233c3-120">Zbyt duża ilość produktu w magazynie oznacza niesprzedane produkty na półkach, które nie generują żadnych przychodów.</span><span class="sxs-lookup"><span data-stu-id="233c3-120">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="233c3-121">Zbyt niewielki produkt prowadzi do utraty sprzedaży i klientów, którzy kupują od konkurencji.</span><span class="sxs-lookup"><span data-stu-id="233c3-121">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="233c3-122">W związku z tym stałe pytanie to, co jest optymalną ilością zapasów do utrzymania?</span><span class="sxs-lookup"><span data-stu-id="233c3-122">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="233c3-123">Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, przeglądając dane historyczne, identyfikując wzorce i korzystając z tych informacji do prognozowania wartości jakiś czas w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="233c3-123">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span> 

<span data-ttu-id="233c3-124">Techniką analizowania danych używanych w tym samouczku jest univariate analiza szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="233c3-124">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="233c3-125">Univariate analiza szeregów czasowych Przyjrzyj się pojedynczej liczbie obserwacji w danym okresie w określonych odstępach czasu, takich jak sprzedaż miesięczna.</span><span class="sxs-lookup"><span data-stu-id="233c3-125">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span> 

<span data-ttu-id="233c3-126">Algorytm używany w tym samouczku jest [analizą pojedynczego spektrum (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="233c3-126">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="233c3-127">Działanie SSA działa przez złożenie szeregów czasowych w zestawie składników głównych.</span><span class="sxs-lookup"><span data-stu-id="233c3-127">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="233c3-128">Te składniki mogą być interpretowane jako części sygnału, które odpowiadają trendom, zakłóceniom, sezonowości i wielu innym czynnikom.</span><span class="sxs-lookup"><span data-stu-id="233c3-128">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="233c3-129">Następnie te składniki są ponownie skonstruowane i używane do prognozowania wartości nieco czasu w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="233c3-129">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="233c3-130">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="233c3-130">Create console application</span></span>

1. <span data-ttu-id="233c3-131">Utwórz nową  **C# aplikację konsolową .NET Core** o nazwie "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="233c3-131">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="233c3-132">Zainstaluj pakiet NuGet **Microsoft.ml** w wersji **1.4.0-preview2**</span><span class="sxs-lookup"><span data-stu-id="233c3-132">Install **Microsoft.ML** version **1.4.0-preview2** NuGet package</span></span>
    1. <span data-ttu-id="233c3-133">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="233c3-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="233c3-134">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="233c3-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="233c3-135">Zaznacz pole wyboru **Uwzględnij wersję wstępną** .</span><span class="sxs-lookup"><span data-stu-id="233c3-135">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="233c3-136">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="233c3-136">Select the **Install** button.</span></span>
    1. <span data-ttu-id="233c3-137">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym akceptacji licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="233c3-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="233c3-138">Powtórz te kroki dla elementu **System. Data. SqlClient** w wersji **4.7.0**, **Microsoft. ml. wersja eksperymentalna** **0.16.0-preview2**i **Microsoft. ml. szeregów czasowych** wersja **1.4.0-preview2**.</span><span class="sxs-lookup"><span data-stu-id="233c3-138">Repeat these steps for **System.Data.SqlClient** version **4.7.0**, **Microsoft.ML.Experimental** version **0.16.0-preview2**, and **Microsoft.ML.TimeSeries** version **1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="233c3-139">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="233c3-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="233c3-140">Utwórz katalog o nazwie *dane*.</span><span class="sxs-lookup"><span data-stu-id="233c3-140">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="233c3-141">Pobierz [plik bazy danych *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i Zapisz go w katalogu *danych* .</span><span class="sxs-lookup"><span data-stu-id="233c3-141">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="233c3-142">Dane używane w tym samouczku pochodzą z [zestawu danych programu UCI rower do udostępniania](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="233c3-142">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="233c3-143">Fanaee-T, Hadi i gama, Joao, "zdarzenie Labeling detektory kompletów i wiedza w tle", postęp w sztucznej analizie (2013): PP. 1-15, Springer Berlin Heidelberg, [link sieci Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="233c3-143">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="233c3-144">Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogoda.</span><span class="sxs-lookup"><span data-stu-id="233c3-144">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="233c3-145">W przypadku zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z pojedynczej kolumny liczbowej, oryginalny zestaw danych został skrócony do uwzględnienia tylko następujących kolumn:</span><span class="sxs-lookup"><span data-stu-id="233c3-145">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>  

- <span data-ttu-id="233c3-146">**dteday**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="233c3-146">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="233c3-147">**Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="233c3-147">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="233c3-148">**CNT**: całkowita liczba czynszów rowerów dla danego dnia.</span><span class="sxs-lookup"><span data-stu-id="233c3-148">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="233c3-149">Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="233c3-149">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="233c3-150">Poniżej przedstawiono przykład danych:</span><span class="sxs-lookup"><span data-stu-id="233c3-150">The following is a sample of the data:</span></span>

| <span data-ttu-id="233c3-151">RentalDate</span><span class="sxs-lookup"><span data-stu-id="233c3-151">RentalDate</span></span> | <span data-ttu-id="233c3-152">Rok</span><span class="sxs-lookup"><span data-stu-id="233c3-152">Year</span></span> | <span data-ttu-id="233c3-153">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="233c3-153">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="233c3-154">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="233c3-154">1/1/2011</span></span>|<span data-ttu-id="233c3-155">0</span><span class="sxs-lookup"><span data-stu-id="233c3-155">0</span></span>|<span data-ttu-id="233c3-156">985</span><span class="sxs-lookup"><span data-stu-id="233c3-156">985</span></span>|
|<span data-ttu-id="233c3-157">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="233c3-157">1/2/2011</span></span>|<span data-ttu-id="233c3-158">0</span><span class="sxs-lookup"><span data-stu-id="233c3-158">0</span></span>|<span data-ttu-id="233c3-159">801</span><span class="sxs-lookup"><span data-stu-id="233c3-159">801</span></span>|
|<span data-ttu-id="233c3-160">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="233c3-160">1/3/2011</span></span>|<span data-ttu-id="233c3-161">0</span><span class="sxs-lookup"><span data-stu-id="233c3-161">0</span></span>|<span data-ttu-id="233c3-162">1349</span><span class="sxs-lookup"><span data-stu-id="233c3-162">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="233c3-163">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="233c3-163">Create input and output classes</span></span>

1. <span data-ttu-id="233c3-164">Otwórz plik *program.cs* i Zastąp istniejące instrukcje `using` następującym:</span><span class="sxs-lookup"><span data-stu-id="233c3-164">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="233c3-165">Utwórz klasę `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="233c3-165">Create `ModelInput` class.</span></span> <span data-ttu-id="233c3-166">Poniżej klasy `Program` Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="233c3-166">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]    

    <span data-ttu-id="233c3-167">Klasa `ModelInput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="233c3-167">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="233c3-168">**RentalDate**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="233c3-168">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="233c3-169">**Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="233c3-169">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="233c3-170">**TotalRentals**: Łączna liczba czynszów rowerów w danym dniu.</span><span class="sxs-lookup"><span data-stu-id="233c3-170">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="233c3-171">Utwórz klasę `ModelOutput` poniżej nowo utworzonej klasy `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="233c3-171">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="233c3-172">Klasa `ModelOutput` zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="233c3-172">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="233c3-173">**ForecastedRentals**: przewidywane wartości dla przedziału czasu.</span><span class="sxs-lookup"><span data-stu-id="233c3-173">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="233c3-174">**LowerBoundRentals**: przewidywane wartości minimalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="233c3-174">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="233c3-175">**UpperBoundRentals**: przewidywane wartości maksymalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="233c3-175">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="233c3-176">Zdefiniuj ścieżki i zainicjuj zmienne</span><span class="sxs-lookup"><span data-stu-id="233c3-176">Define paths and initialize variables</span></span>

1. <span data-ttu-id="233c3-177">Wewnątrz metody `Main` Zdefiniuj zmienne do przechowywania lokalizacji danych, parametrów połączenia i miejsca, w którym ma zostać zapisany szkolony model.</span><span class="sxs-lookup"><span data-stu-id="233c3-177">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="233c3-178">Zainicjuj zmienną `mlContext` z nowym wystąpieniem [`MLContext`](xref:Microsoft.ML.MLContext) , dodając następujący wiersz do metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="233c3-178">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="233c3-179">Klasa [`MLContext`](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie mlContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="233c3-179">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="233c3-180">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="233c3-180">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="233c3-181">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="233c3-181">Load the data</span></span>

1. <span data-ttu-id="233c3-182">Utwórz `DatabaseLoader` ładujące rekordy typu `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="233c3-182">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="233c3-183">Zdefiniuj zapytanie w celu załadowania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="233c3-183">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="233c3-184">Algorytmy ML.NET oczekują, że dane mają być typu [`Single`](xref:System.Single).</span><span class="sxs-lookup"><span data-stu-id="233c3-184">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="233c3-185">W związku z tym wartości numeryczne pochodzące z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType), wartości zmiennoprzecinkowej o pojedynczej precyzji, muszą być konwertowane na [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="233c3-185">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> 

    <span data-ttu-id="233c3-186">Kolumny `Year` i `TotalRental` są typami całkowitymi w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="233c3-186">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="233c3-187">Przy użyciu wbudowanej funkcji `CAST` są one rzutowane na `Real`.</span><span class="sxs-lookup"><span data-stu-id="233c3-187">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="233c3-188">Utwórz `DatabaseSource`, aby nawiązać połączenie z bazą danych i wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="233c3-188">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="233c3-189">Załaduj dane do `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="233c3-189">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="233c3-190">Zestaw danych zawiera dwa lata dane.</span><span class="sxs-lookup"><span data-stu-id="233c3-190">The dataset contains two years worth of data.</span></span> <span data-ttu-id="233c3-191">Tylko dane z pierwszego roku są używane na potrzeby szkoleń, drugi rok jest przetrzymywany, aby porównać rzeczywiste wartości z prognozami produkowanymi przez model.</span><span class="sxs-lookup"><span data-stu-id="233c3-191">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="233c3-192">Filtrowanie danych przy użyciu transformacji [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) .</span><span class="sxs-lookup"><span data-stu-id="233c3-192">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span> 

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="233c3-193">W pierwszym roku tylko wartości w `Year` kolumnie mniejsze niż 1 są wybierane przez ustawienie parametru `upperBound` na 1.</span><span class="sxs-lookup"><span data-stu-id="233c3-193">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="233c3-194">Na odwrót, w drugim roku, wartości większe niż lub równe 1 są wybierane przez ustawienie parametru `lowerBound` na 1.</span><span class="sxs-lookup"><span data-stu-id="233c3-194">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="233c3-195">Definiowanie potoku analizy szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="233c3-195">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="233c3-196">Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="233c3-196">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="233c3-197">`forecastingPipeline` pobiera 365 punktów danych przez pierwszy rok i próbuje lub dzieli zestaw danych szeregów czasowych na 30 dni (miesięcznie), zgodnie z parametrem `seriesLength`.</span><span class="sxs-lookup"><span data-stu-id="233c3-197">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="233c3-198">Każdy z tych przykładów jest analizowany przez cotygodniowe lub 7-dniowe okno.</span><span class="sxs-lookup"><span data-stu-id="233c3-198">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="233c3-199">Podczas określania wartości prognozowanych dla następnych okresów, wartości z poprzednich siedmiu dni są używane do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="233c3-199">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="233c3-200">Model jest ustawiony na prognozowanie siedmiu okresów w przyszłości zgodnie z definicją `horizon` parametru.</span><span class="sxs-lookup"><span data-stu-id="233c3-200">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="233c3-201">Ze względu na to, że prognoza jest świadomym zgadywaniem, nie zawsze jest poprawna 100%.</span><span class="sxs-lookup"><span data-stu-id="233c3-201">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="233c3-202">W związku z tym warto znać zakres wartości w scenariuszach najlepszego i najgorszego przypadku zdefiniowanej przez górną i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="233c3-202">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="233c3-203">W takim przypadku poziom zaufania dla dolnych i górnych granic jest ustawiony na 95%.</span><span class="sxs-lookup"><span data-stu-id="233c3-203">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="233c3-204">Poziom zaufania można odpowiednio zwiększyć lub zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="233c3-204">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="233c3-205">Im wyższa wartość, tym szerszy zakres jest między górną i dolną granicą, aby osiągnąć żądany poziom zaufania.</span><span class="sxs-lookup"><span data-stu-id="233c3-205">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span> 

1. <span data-ttu-id="233c3-206">Użyj metody [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) , aby nauczyć model i dopasować dane do wcześniej zdefiniowanego `forecastingPipeline`.</span><span class="sxs-lookup"><span data-stu-id="233c3-206">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="233c3-207">Oceń model</span><span class="sxs-lookup"><span data-stu-id="233c3-207">Evaluate the model</span></span>

<span data-ttu-id="233c3-208">Oceń, jak dobrze model wykonuje, prognozowanie danych w następnym roku i porównywanie ich z wartościami rzeczywistymi.</span><span class="sxs-lookup"><span data-stu-id="233c3-208">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="233c3-209">Poniżej metody `Main` Utwórz nową metodę narzędzia o nazwie `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="233c3-209">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {
        
    }
    ```

1. <span data-ttu-id="233c3-210">Wewnątrz metody `Evaluate` prognozować dane drugiego roku przy użyciu metody [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) z przeszkolonym modelem.</span><span class="sxs-lookup"><span data-stu-id="233c3-210">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="233c3-211">Pobierz rzeczywiste wartości z danych za pomocą metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="233c3-211">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="233c3-212">Pobierz wartości prognozy przy użyciu metody [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="233c3-212">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="233c3-213">Oblicz różnicę między wartościami rzeczywistymi i prognozowanymi, często określanymi jako błąd.</span><span class="sxs-lookup"><span data-stu-id="233c3-213">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="233c3-214">Mierzenie wydajności przez obliczanie średniego błędu bezwzględnego i głównej średniej wartości błędu.</span><span class="sxs-lookup"><span data-stu-id="233c3-214">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="233c3-215">Do oceny wydajności są używane następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="233c3-215">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="233c3-216">**Średni błąd bezwzględny**: mierzy, jak zamknięte przewidywania są rzeczywistej wartości.</span><span class="sxs-lookup"><span data-stu-id="233c3-216">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="233c3-217">Ta wartość mieści się w zakresie od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="233c3-217">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="233c3-218">Im bliżej wartości 0, tym lepiej jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="233c3-218">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="233c3-219">**Średni błąd oznaczający rdzeń**: podsumowuje błąd thhe w modelu.</span><span class="sxs-lookup"><span data-stu-id="233c3-219">**Root Mean Squared Error**: Summarizes thhe error in the model.</span></span> <span data-ttu-id="233c3-220">Ta wartość mieści się w zakresie od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="233c3-220">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="233c3-221">Im bliżej wartości 0, tym lepiej jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="233c3-221">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="233c3-222">Wyprowadza metryki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="233c3-222">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="233c3-223">Użyj metody `Evaluate` wewnątrz metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="233c3-223">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="233c3-224">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="233c3-224">Save the model</span></span>

<span data-ttu-id="233c3-225">Jeśli Twój model jest zadowalający, Zapisz go do późniejszego użycia w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="233c3-225">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="233c3-226">W metodzie `Main` Utwórz [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="233c3-226">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="233c3-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) jest wygodną metodą podejmowania pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="233c3-227">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="233c3-228">Zapisz model w pliku o nazwie `MLModel.zip` jak określono przez wcześniej zdefiniowaną zmienną `modelPath`.</span><span class="sxs-lookup"><span data-stu-id="233c3-228">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="233c3-229">Użyj metody [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) , aby zapisać model.</span><span class="sxs-lookup"><span data-stu-id="233c3-229">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="233c3-230">Użyj modelu do prognozowania popytu</span><span class="sxs-lookup"><span data-stu-id="233c3-230">Use the model to forecast demand</span></span>

1. <span data-ttu-id="233c3-231">Poniżej metody `Evaluate` Utwórz nową metodę narzędzia o nazwie `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="233c3-231">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="233c3-232">Wewnątrz metody `Forecast` Użyj metody [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) do prognozowania czynszów w ciągu następnych siedmiu dni.</span><span class="sxs-lookup"><span data-stu-id="233c3-232">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="233c3-233">Wyrównaj wartości rzeczywiste i prognozy dla siedmiu okresów.</span><span class="sxs-lookup"><span data-stu-id="233c3-233">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="233c3-234">Wykonaj iterację w danych wyjściowych prognozy i wyświetl ją w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="233c3-234">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="233c3-235">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="233c3-235">Run the application</span></span>

1. <span data-ttu-id="233c3-236">Wewnątrz metody `Main` Wywołaj metodę `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="233c3-236">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="233c3-237">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="233c3-237">Run the application.</span></span> <span data-ttu-id="233c3-238">Dane wyjściowe podobne do poniższego powinny być wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="233c3-238">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="233c3-239">W przypadku zwięzłości dane wyjściowe zostały zagęszczone.</span><span class="sxs-lookup"><span data-stu-id="233c3-239">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="233c3-240">Inspekcja wartości rzeczywistych i prognozowanych przedstawia następujące relacje:</span><span class="sxs-lookup"><span data-stu-id="233c3-240">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Porównanie rzeczywistych i prognoz](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="233c3-242">Przewidywane wartości nie przewidywalną dokładnej liczby wynajmu, ale zapewniają bardziej wąski zakres wartości, dzięki którym można przeprowadzić operację w celu zoptymalizowania użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="233c3-242">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span> 

<span data-ttu-id="233c3-243">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="233c3-243">Congratulations!</span></span> <span data-ttu-id="233c3-244">Pomyślnie skompilowano model uczenia maszynowego w szeregach czasowych do prognozowania popytu na wypożyczenie roweru.</span><span class="sxs-lookup"><span data-stu-id="233c3-244">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="233c3-245">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .</span><span class="sxs-lookup"><span data-stu-id="233c3-245">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="233c3-246">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="233c3-246">Next steps</span></span>

- [<span data-ttu-id="233c3-247">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="233c3-247">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="233c3-248">Popraw dokładność modelu</span><span class="sxs-lookup"><span data-stu-id="233c3-248">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
