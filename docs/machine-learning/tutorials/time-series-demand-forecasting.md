---
title: 'Samouczek: prognozowanie popytu na wypożyczenie rowerowe — seria czasu'
description: W tym samouczku pokazano, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu univariate analiz szeregów czasowych i ML.NET.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 4ea002b690de877fd6f955c05eb8235f46e0a870
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803222"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="a066a-103">Samouczek: prognozowanie popytu na usługę najmu roweru za pomocą analiz szeregów czasowych i ML.NET</span><span class="sxs-lookup"><span data-stu-id="a066a-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="a066a-104">Dowiedz się, jak prognozować zapotrzebowanie na usługę wynajmu roweru przy użyciu analizy szeregów czasowych univariate na danych przechowywanych w bazie danych SQL Server z ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a066a-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="a066a-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a066a-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a066a-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="a066a-106">Understand the problem</span></span>
> * <span data-ttu-id="a066a-107">Ładowanie danych z bazy danych</span><span class="sxs-lookup"><span data-stu-id="a066a-107">Load data from a database</span></span>
> * <span data-ttu-id="a066a-108">Tworzenie modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a066a-108">Create a forecasting model</span></span>
> * <span data-ttu-id="a066a-109">Oceń model prognozowania</span><span class="sxs-lookup"><span data-stu-id="a066a-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="a066a-110">Zapisz model prognozowania</span><span class="sxs-lookup"><span data-stu-id="a066a-110">Save a forecasting model</span></span>
> * <span data-ttu-id="a066a-111">Korzystanie z modelu prognozowania</span><span class="sxs-lookup"><span data-stu-id="a066a-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a066a-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a066a-112">Prerequisites</span></span>

- <span data-ttu-id="a066a-113">[Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a066a-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="a066a-114">Omówienie przykładu prognozowania szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="a066a-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="a066a-115">Ten przykład jest **aplikacją konsolową języka C# .NET Core** , która prognozuje zapotrzebowanie na czynsze rowerów przy użyciu univariate algorytmu analizy szeregów czasowych znanej jako analiza pojedynczego spektrum.</span><span class="sxs-lookup"><span data-stu-id="a066a-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="a066a-116">Kod dla tego przykładu można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="a066a-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="a066a-117">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="a066a-117">Understand the problem</span></span>

<span data-ttu-id="a066a-118">Aby można było uruchomić wydajną operację, zarządzanie zapasami odgrywa kluczową rolę.</span><span class="sxs-lookup"><span data-stu-id="a066a-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="a066a-119">Zbyt duża ilość produktu w magazynie oznacza niesprzedane produkty na półkach, które nie generują żadnych przychodów.</span><span class="sxs-lookup"><span data-stu-id="a066a-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="a066a-120">Zbyt niewielki produkt prowadzi do utraty sprzedaży i klientów, którzy kupują od konkurencji.</span><span class="sxs-lookup"><span data-stu-id="a066a-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="a066a-121">W związku z tym stałe pytanie to, co jest optymalną ilością zapasów do utrzymania?</span><span class="sxs-lookup"><span data-stu-id="a066a-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="a066a-122">Analiza szeregów czasowych pomaga udzielić odpowiedzi na te pytania, przeglądając dane historyczne, identyfikując wzorce i korzystając z tych informacji do prognozowania wartości jakiś czas w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a066a-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="a066a-123">Techniką analizowania danych używanych w tym samouczku jest univariate analiza szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="a066a-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="a066a-124">Univariate analiza szeregów czasowych Przyjrzyj się pojedynczej liczbie obserwacji w danym okresie w określonych odstępach czasu, takich jak sprzedaż miesięczna.</span><span class="sxs-lookup"><span data-stu-id="a066a-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="a066a-125">Algorytm używany w tym samouczku jest [analizą pojedynczego spektrum (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="a066a-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="a066a-126">Działanie SSA działa przez złożenie szeregów czasowych w zestawie składników głównych.</span><span class="sxs-lookup"><span data-stu-id="a066a-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="a066a-127">Te składniki mogą być interpretowane jako części sygnału, które odpowiadają trendom, zakłóceniom, sezonowości i wielu innym czynnikom.</span><span class="sxs-lookup"><span data-stu-id="a066a-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="a066a-128">Następnie te składniki są ponownie skonstruowane i używane do prognozowania wartości nieco czasu w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a066a-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="a066a-129">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a066a-129">Create console application</span></span>

1. <span data-ttu-id="a066a-130">Utwórz nową **aplikację konsolową w języku C# .NET Core** o nazwie "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="a066a-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="a066a-131">Zainstaluj pakiet NuGet wersji **Microsoft.ml**</span><span class="sxs-lookup"><span data-stu-id="a066a-131">Install **Microsoft.ML** version NuGet package</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. <span data-ttu-id="a066a-132">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a066a-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="a066a-133">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="a066a-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="a066a-134">Zaznacz pole wyboru **Uwzględnij wersję wstępną** .</span><span class="sxs-lookup"><span data-stu-id="a066a-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="a066a-135">Wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="a066a-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="a066a-136">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym akceptacji licencji, jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a066a-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="a066a-137">Powtórz te kroki dla elementu **System. Data. SqlClient** i **Microsoft. ml. szeregów czasowych**.</span><span class="sxs-lookup"><span data-stu-id="a066a-137">Repeat these steps for **System.Data.SqlClient** and **Microsoft.ML.TimeSeries**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a066a-138">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="a066a-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="a066a-139">Utwórz katalog o nazwie *dane*.</span><span class="sxs-lookup"><span data-stu-id="a066a-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="a066a-140">Pobierz [plik bazy danych *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) i Zapisz go w katalogu *danych* .</span><span class="sxs-lookup"><span data-stu-id="a066a-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="a066a-141">Dane używane w tym samouczku pochodzą z [zestawu danych programu UCI rower do udostępniania](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="a066a-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="a066a-142">Fanaee-T, Hadi i gama, Joao, "zdarzenie Labeling detektory kompletów i wiedza w tle", postęp w sztucznej analizie (2013): PP. 1-15, Springer Berlin Heidelberg, [link sieci Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="a066a-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="a066a-143">Oryginalny zestaw danych zawiera kilka kolumn odpowiadających sezonowości i pogoda.</span><span class="sxs-lookup"><span data-stu-id="a066a-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="a066a-144">W przypadku zwięzłości i ponieważ algorytm używany w tym samouczku wymaga tylko wartości z pojedynczej kolumny liczbowej, oryginalny zestaw danych został skrócony do uwzględnienia tylko następujących kolumn:</span><span class="sxs-lookup"><span data-stu-id="a066a-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="a066a-145">**dteday**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="a066a-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="a066a-146">**Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="a066a-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="a066a-147">**CNT**: całkowita liczba czynszów rowerów dla danego dnia.</span><span class="sxs-lookup"><span data-stu-id="a066a-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="a066a-148">Oryginalny zestaw danych jest mapowany do tabeli bazy danych z następującym schematem w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a066a-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="a066a-149">Poniżej przedstawiono przykład danych:</span><span class="sxs-lookup"><span data-stu-id="a066a-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="a066a-150">RentalDate</span><span class="sxs-lookup"><span data-stu-id="a066a-150">RentalDate</span></span> | <span data-ttu-id="a066a-151">Rok</span><span class="sxs-lookup"><span data-stu-id="a066a-151">Year</span></span> | <span data-ttu-id="a066a-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="a066a-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="a066a-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="a066a-153">1/1/2011</span></span>|<span data-ttu-id="a066a-154">0</span><span class="sxs-lookup"><span data-stu-id="a066a-154">0</span></span>|<span data-ttu-id="a066a-155">985</span><span class="sxs-lookup"><span data-stu-id="a066a-155">985</span></span>|
|<span data-ttu-id="a066a-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="a066a-156">1/2/2011</span></span>|<span data-ttu-id="a066a-157">0</span><span class="sxs-lookup"><span data-stu-id="a066a-157">0</span></span>|<span data-ttu-id="a066a-158">801</span><span class="sxs-lookup"><span data-stu-id="a066a-158">801</span></span>|
|<span data-ttu-id="a066a-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="a066a-159">1/3/2011</span></span>|<span data-ttu-id="a066a-160">0</span><span class="sxs-lookup"><span data-stu-id="a066a-160">0</span></span>|<span data-ttu-id="a066a-161">1349</span><span class="sxs-lookup"><span data-stu-id="a066a-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="a066a-162">Tworzenie klas wejściowych i wyjściowych</span><span class="sxs-lookup"><span data-stu-id="a066a-162">Create input and output classes</span></span>

1. <span data-ttu-id="a066a-163">Otwórz plik *program.cs* i Zastąp istniejące `using` instrukcje poniższymi:</span><span class="sxs-lookup"><span data-stu-id="a066a-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="a066a-164">Utwórz klasę `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="a066a-164">Create `ModelInput` class.</span></span> <span data-ttu-id="a066a-165">Poniżej `Program` klasy Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a066a-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="a066a-166">`ModelInput`Klasa zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a066a-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="a066a-167">**RentalDate**: Data obserwacji.</span><span class="sxs-lookup"><span data-stu-id="a066a-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="a066a-168">**Year**: zakodowany rok obserwacji (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="a066a-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="a066a-169">**TotalRentals**: Łączna liczba czynszów rowerów w danym dniu.</span><span class="sxs-lookup"><span data-stu-id="a066a-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="a066a-170">Utwórz `ModelOutput` klasę poniżej nowo utworzonej `ModelInput` klasy.</span><span class="sxs-lookup"><span data-stu-id="a066a-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="a066a-171">`ModelOutput`Klasa zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a066a-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="a066a-172">**ForecastedRentals**: przewidywane wartości dla przedziału czasu.</span><span class="sxs-lookup"><span data-stu-id="a066a-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="a066a-173">**LowerBoundRentals**: przewidywane wartości minimalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="a066a-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="a066a-174">**UpperBoundRentals**: przewidywane wartości maksymalne dla prognozowanego okresu.</span><span class="sxs-lookup"><span data-stu-id="a066a-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="a066a-175">Zdefiniuj ścieżki i zainicjuj zmienne</span><span class="sxs-lookup"><span data-stu-id="a066a-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="a066a-176">Wewnątrz `Main` metody Zdefiniuj zmienne do przechowywania lokalizacji danych, parametrów połączenia i miejsca, w którym ma zostać zapisany szkolony model.</span><span class="sxs-lookup"><span data-stu-id="a066a-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="a066a-177">Zainicjuj `mlContext` zmienną z nowym wystąpieniem [`MLContext`](xref:Microsoft.ML.MLContext) , dodając do metody następujący wiersz `Main` .</span><span class="sxs-lookup"><span data-stu-id="a066a-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="a066a-178">[`MLContext`](xref:Microsoft.ML.MLContext)Klasa jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie mlContext tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a066a-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a066a-179">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a066a-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a066a-180">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a066a-180">Load the data</span></span>

1. <span data-ttu-id="a066a-181">Utwórz `DatabaseLoader` ładujące rekordy typu `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="a066a-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="a066a-182">Zdefiniuj zapytanie w celu załadowania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a066a-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="a066a-183">Algorytmy ML.NET oczekują, że dane mają być typu [`Single`](xref:System.Single) .</span><span class="sxs-lookup"><span data-stu-id="a066a-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="a066a-184">W związku z tym wartości numeryczne pochodzące z bazy danych, które nie są typu [`Real`](xref:System.Data.SqlDbType) , wartości zmiennoprzecinkowej o pojedynczej precyzji, muszą być konwertowane na [`Real`](xref:System.Data.SqlDbType) .</span><span class="sxs-lookup"><span data-stu-id="a066a-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="a066a-185">`Year`Kolumny i `TotalRental` są typami całkowitymi w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a066a-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="a066a-186">Przy użyciu `CAST` funkcji wbudowanej są one rzutowane na `Real` .</span><span class="sxs-lookup"><span data-stu-id="a066a-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="a066a-187">Utwórz `DatabaseSource` połączenie, aby połączyć się z bazą danych i wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a066a-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="a066a-188">Załaduj dane do programu `IDataView` .</span><span class="sxs-lookup"><span data-stu-id="a066a-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="a066a-189">Zestaw danych zawiera dwa lata dane.</span><span class="sxs-lookup"><span data-stu-id="a066a-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="a066a-190">Tylko dane z pierwszego roku są używane na potrzeby szkoleń, drugi rok jest przetrzymywany, aby porównać rzeczywiste wartości z prognozami produkowanymi przez model.</span><span class="sxs-lookup"><span data-stu-id="a066a-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="a066a-191">Filtrowanie danych przy użyciu [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transformacji.</span><span class="sxs-lookup"><span data-stu-id="a066a-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="a066a-192">W pierwszym roku tylko wartości w `Year` kolumnie mniejszej niż 1 są wybierane przez ustawienie `upperBound` parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="a066a-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="a066a-193">Z kolei w drugim roku wartości większe niż lub równe 1 są wybierane przez ustawienie `lowerBound` parametru na 1.</span><span class="sxs-lookup"><span data-stu-id="a066a-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="a066a-194">Definiowanie potoku analizy szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="a066a-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="a066a-195">Zdefiniuj potok, który używa [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) do prognozowania wartości w zestawie danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="a066a-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="a066a-196">Program `forecastingPipeline` pobiera 365 punktów danych w pierwszym roku i próbuje lub dzieli zestaw danych szeregów czasowych na 30 dni (miesięczne) interwał określony przez `seriesLength` parametr.</span><span class="sxs-lookup"><span data-stu-id="a066a-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="a066a-197">Każdy z tych przykładów jest analizowany przez cotygodniowe lub 7-dniowe okno.</span><span class="sxs-lookup"><span data-stu-id="a066a-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="a066a-198">Podczas określania wartości prognozowanych dla następnych okresów, wartości z poprzednich siedmiu dni są używane do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="a066a-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="a066a-199">Model jest ustawiony do prognozowania siedmiu okresów w przyszłości zgodnie z definicją przez `horizon` parametr.</span><span class="sxs-lookup"><span data-stu-id="a066a-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="a066a-200">Ze względu na to, że prognoza jest świadomym zgadywaniem, nie zawsze jest poprawna 100%.</span><span class="sxs-lookup"><span data-stu-id="a066a-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="a066a-201">W związku z tym warto znać zakres wartości w scenariuszach najlepszego i najgorszego przypadku zdefiniowanej przez górną i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="a066a-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="a066a-202">W takim przypadku poziom zaufania dla dolnych i górnych granic jest ustawiony na 95%.</span><span class="sxs-lookup"><span data-stu-id="a066a-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="a066a-203">Poziom zaufania można odpowiednio zwiększyć lub zmniejszyć.</span><span class="sxs-lookup"><span data-stu-id="a066a-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="a066a-204">Im wyższa wartość, tym szerszy zakres jest między górną i dolną granicą, aby osiągnąć żądany poziom zaufania.</span><span class="sxs-lookup"><span data-stu-id="a066a-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="a066a-205">Użyj [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) metody, aby nauczyć model i dopasować dane do wcześniej zdefiniowanych `forecastingPipeline` .</span><span class="sxs-lookup"><span data-stu-id="a066a-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="a066a-206">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="a066a-206">Evaluate the model</span></span>

<span data-ttu-id="a066a-207">Oceń, jak dobrze model wykonuje, prognozowanie danych w następnym roku i porównywanie ich z wartościami rzeczywistymi.</span><span class="sxs-lookup"><span data-stu-id="a066a-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="a066a-208">Poniżej `Main` metody Utwórz nową metodę narzędzia o nazwie `Evaluate` .</span><span class="sxs-lookup"><span data-stu-id="a066a-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="a066a-209">Wewnątrz `Evaluate` metody prognozować dane drugiego roku przy użyciu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metody z przeszkolonym modelem.</span><span class="sxs-lookup"><span data-stu-id="a066a-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="a066a-210">Pobierz rzeczywiste wartości z danych przy użyciu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody.</span><span class="sxs-lookup"><span data-stu-id="a066a-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="a066a-211">Pobierz wartości prognozy przy użyciu [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody.</span><span class="sxs-lookup"><span data-stu-id="a066a-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="a066a-212">Oblicz różnicę między wartościami rzeczywistymi i prognozowanymi, często określanymi jako błąd.</span><span class="sxs-lookup"><span data-stu-id="a066a-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="a066a-213">Mierzenie wydajności przez obliczanie średniego błędu bezwzględnego i głównej średniej wartości błędu.</span><span class="sxs-lookup"><span data-stu-id="a066a-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="a066a-214">Do oceny wydajności są używane następujące metryki:</span><span class="sxs-lookup"><span data-stu-id="a066a-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="a066a-215">**Średni błąd bezwzględny**: mierzy, jak zamknięte przewidywania są rzeczywistej wartości.</span><span class="sxs-lookup"><span data-stu-id="a066a-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="a066a-216">Ta wartość mieści się w zakresie od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="a066a-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="a066a-217">Im bliżej wartości 0, tym lepiej jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="a066a-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="a066a-218">**Średni błąd oznaczający pierwiastek**: zawiera podsumowanie błędu w modelu.</span><span class="sxs-lookup"><span data-stu-id="a066a-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="a066a-219">Ta wartość mieści się w zakresie od 0 do nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="a066a-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="a066a-220">Im bliżej wartości 0, tym lepiej jakość modelu.</span><span class="sxs-lookup"><span data-stu-id="a066a-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="a066a-221">Wyprowadza metryki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a066a-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="a066a-222">Użyj `Evaluate` metody wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="a066a-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="a066a-223">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="a066a-223">Save the model</span></span>

<span data-ttu-id="a066a-224">Jeśli Twój model jest zadowalający, Zapisz go do późniejszego użycia w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="a066a-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="a066a-225">W `Main` metodzie Utwórz [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) .</span><span class="sxs-lookup"><span data-stu-id="a066a-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="a066a-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)jest wygodną metodą podejmowania pojedynczych prognoz.</span><span class="sxs-lookup"><span data-stu-id="a066a-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="a066a-227">Zapisz model w pliku o nazwie `MLModel.zip` określonej przez wcześniej zdefiniowaną `modelPath` zmienną.</span><span class="sxs-lookup"><span data-stu-id="a066a-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="a066a-228">Użyj [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) metody, aby zapisać model.</span><span class="sxs-lookup"><span data-stu-id="a066a-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="a066a-229">Użyj modelu do prognozowania popytu</span><span class="sxs-lookup"><span data-stu-id="a066a-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="a066a-230">Poniżej `Evaluate` metody Utwórz nową metodę narzędzia o nazwie `Forecast` .</span><span class="sxs-lookup"><span data-stu-id="a066a-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="a066a-231">Wewnątrz `Forecast` metody Użyj [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) metody do prognozowania czynszów w ciągu następnych siedmiu dni.</span><span class="sxs-lookup"><span data-stu-id="a066a-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="a066a-232">Wyrównaj wartości rzeczywiste i prognozy dla siedmiu okresów.</span><span class="sxs-lookup"><span data-stu-id="a066a-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="a066a-233">Wykonaj iterację w danych wyjściowych prognozy i wyświetl ją w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="a066a-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="a066a-234">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a066a-234">Run the application</span></span>

1. <span data-ttu-id="a066a-235">Wewnątrz `Main` metody Wywołaj `Forecast` metodę.</span><span class="sxs-lookup"><span data-stu-id="a066a-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="a066a-236">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="a066a-236">Run the application.</span></span> <span data-ttu-id="a066a-237">Dane wyjściowe podobne do poniższego powinny być wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="a066a-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="a066a-238">W przypadku zwięzłości dane wyjściowe zostały zagęszczone.</span><span class="sxs-lookup"><span data-stu-id="a066a-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="a066a-239">Inspekcja wartości rzeczywistych i prognozowanych przedstawia następujące relacje:</span><span class="sxs-lookup"><span data-stu-id="a066a-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Porównanie rzeczywistych i prognoz](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="a066a-241">Przewidywane wartości nie przewidywalną dokładnej liczby wynajmu, ale zapewniają bardziej wąski zakres wartości, dzięki którym można przeprowadzić operację w celu zoptymalizowania użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="a066a-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="a066a-242">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a066a-242">Congratulations!</span></span> <span data-ttu-id="a066a-243">Pomyślnie skompilowano model uczenia maszynowego w szeregach czasowych do prognozowania popytu na wypożyczenie roweru.</span><span class="sxs-lookup"><span data-stu-id="a066a-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="a066a-244">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .</span><span class="sxs-lookup"><span data-stu-id="a066a-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a066a-245">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a066a-245">Next steps</span></span>

- [<span data-ttu-id="a066a-246">Zadania uczenia maszynowego w ML.NET</span><span class="sxs-lookup"><span data-stu-id="a066a-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="a066a-247">Zwiększanie dokładności modelu</span><span class="sxs-lookup"><span data-stu-id="a066a-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
