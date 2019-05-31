---
title: W przypadku wykrycia anomalii sprzedaży, użyj strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu wykrywania anomalii sprzedaży produktu zrozumienie, jak analizować dane pod kątem klamry anomalii i zmiany punktów podejmowanie odpowiednich działań.
ms.date: 05/29/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d31765aa4ff2a0be9c4f140f33de1f5678fc7612
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423940"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a><span data-ttu-id="a8563-103">Samouczek: Na użytek strukturze ML.NET wykrywania anomalii sprzedaży produktu</span><span class="sxs-lookup"><span data-stu-id="a8563-103">Tutorial: Use ML.NET for product sales anomaly detection</span></span> 

<span data-ttu-id="a8563-104">Ten przykładowy samouczek przedstawia wykrycia anomalii w danych sprzedaży produktu podejmowanie odpowiednich działań za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2019 r.</span><span class="sxs-lookup"><span data-stu-id="a8563-104">This sample tutorial illustrates using ML.NET to detect anomalies in product sales data to take the appropriate action via a .NET Core console application using C# in Visual Studio 2019.</span></span> 

<span data-ttu-id="a8563-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a8563-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a8563-106">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a8563-106">Load the data</span></span>
> * <span data-ttu-id="a8563-107">Uczenie modelu do kolekcji wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="a8563-107">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="a8563-108">Wykrywaj anomalie kolekcji za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="a8563-108">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="a8563-109">Uczenie modelu dla zmiany punktu anomalii</span><span class="sxs-lookup"><span data-stu-id="a8563-109">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="a8563-110">Wykrywaj anomalie punktu zmiany za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="a8563-110">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="a8563-111">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="a8563-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8563-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a8563-112">Prerequisites</span></span>

* <span data-ttu-id="a8563-113">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="a8563-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="a8563-114">Zestaw danych sales.csv produktu</span><span class="sxs-lookup"><span data-stu-id="a8563-114">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="a8563-115">Dane formatu w `product-sales.csv` opiera się na zestawie danych "Szamponu sprzedaż za pośrednictwem trzech lat" pierwotnie skąd pochodzi z usługi DataMarket i udostępniane przez czas serii danych biblioteki (TSDL), utworzone przez Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="a8563-115">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="a8563-116">Zestaw danych "Szamponu sprzedaży przez trzy lata" uzyskał licencje w ramach licencji Open DataMarket domyślne.</span><span class="sxs-lookup"><span data-stu-id="a8563-116">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a8563-117">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a8563-117">Create a console application</span></span>

1. <span data-ttu-id="a8563-118">Tworzenie **aplikacji konsoli .NET Core** o nazwie "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="a8563-118">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="a8563-119">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a8563-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="a8563-120">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="a8563-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="a8563-121">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a8563-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a8563-122">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a8563-122">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="a8563-123">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="a8563-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="a8563-124">Powtórz te kroki dla **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="a8563-124">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="a8563-125">Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="a8563-125">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="a8563-126">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="a8563-126">Download your data</span></span>

1. <span data-ttu-id="a8563-127">Pobierz zestaw danych i zapisać go w celu *danych* wcześniej utworzony folder:</span><span class="sxs-lookup"><span data-stu-id="a8563-127">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="a8563-128">Kliknij prawym przyciskiem myszy [ *sales.csv produktu* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="a8563-128">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="a8563-129">Upewnij się, albo zapisać \*pliku CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*pliku CSV *danych* folderu.</span><span class="sxs-lookup"><span data-stu-id="a8563-129">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="a8563-130">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy \*pliku CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a8563-130">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="a8563-131">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="a8563-131">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="a8563-132">Poniższa tabela jest podgląd danych z usługi \*pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="a8563-132">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="a8563-133">Miesiąc</span><span class="sxs-lookup"><span data-stu-id="a8563-133">Month</span></span>  |<span data-ttu-id="a8563-134">ProductSales</span><span class="sxs-lookup"><span data-stu-id="a8563-134">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="a8563-135">1 stycznia</span><span class="sxs-lookup"><span data-stu-id="a8563-135">1-Jan</span></span>  |    <span data-ttu-id="a8563-136">271</span><span class="sxs-lookup"><span data-stu-id="a8563-136">271</span></span>      |
|<span data-ttu-id="a8563-137">2 stycznia</span><span class="sxs-lookup"><span data-stu-id="a8563-137">2-Jan</span></span>  |    <span data-ttu-id="a8563-138">150.9</span><span class="sxs-lookup"><span data-stu-id="a8563-138">150.9</span></span>    |
|<span data-ttu-id="a8563-139">.....</span><span class="sxs-lookup"><span data-stu-id="a8563-139">.....</span></span>  |    <span data-ttu-id="a8563-140">.....</span><span class="sxs-lookup"><span data-stu-id="a8563-140">.....</span></span>    |
|<span data-ttu-id="a8563-141">1-Feb</span><span class="sxs-lookup"><span data-stu-id="a8563-141">1-Feb</span></span>  |    <span data-ttu-id="a8563-142">199.3</span><span class="sxs-lookup"><span data-stu-id="a8563-142">199.3</span></span>    |
|<span data-ttu-id="a8563-143">.....</span><span class="sxs-lookup"><span data-stu-id="a8563-143">.....</span></span>  |    <span data-ttu-id="a8563-144">.....</span><span class="sxs-lookup"><span data-stu-id="a8563-144">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a8563-145">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="a8563-145">Create classes and define paths</span></span>

<span data-ttu-id="a8563-146">Następnie zdefiniuj strukturę danych wejściowych klasy.</span><span class="sxs-lookup"><span data-stu-id="a8563-146">Next, define your input class data structure.</span></span>

<span data-ttu-id="a8563-147">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="a8563-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="a8563-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a8563-148">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="a8563-149">W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="a8563-149">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="a8563-150">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a8563-150">Then, select the **Add** button.</span></span>

<span data-ttu-id="a8563-151">*ProductSalesData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="a8563-151">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a8563-152">Dodaj następujący kod `using` instrukcji na górze *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="a8563-152">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="a8563-153">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `ProductSalesData` i `ProductSalesPrediction`, *ProductSalesData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="a8563-153">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="a8563-154">`ProductSalesData` Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a8563-154">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="a8563-155">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane.</span><span class="sxs-lookup"><span data-stu-id="a8563-155">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="a8563-156">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="a8563-156">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="a8563-157">Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:</span><span class="sxs-lookup"><span data-stu-id="a8563-157">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="a8563-158">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="a8563-158">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="a8563-159">`_docsize` ma to liczba rekordów w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a8563-159">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="a8563-160">Można będzie użyć do obliczenia `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="a8563-160">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="a8563-161">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="a8563-161">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="a8563-162">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a8563-162">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a8563-163">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a8563-163">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a8563-164">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="a8563-164">Initialize variables in Main</span></span>

<span data-ttu-id="a8563-165">Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować `mlContext` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="a8563-165">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="a8563-166">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a8563-166">Load the data</span></span>

<span data-ttu-id="a8563-167">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="a8563-167">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="a8563-168">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="a8563-168">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="a8563-169">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8563-169">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="a8563-170">Dodaj następujący kod jako następnego wiersza `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-170">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="a8563-171">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="a8563-171">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="a8563-172">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="a8563-172">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="a8563-173">Zadanie ML — wykrywanie anomalii w czasie serii</span><span class="sxs-lookup"><span data-stu-id="a8563-173">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="a8563-174">Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="a8563-174">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="a8563-175">Ta funkcja zapewnia wskazówki gdzie szukać problemów i pomaga w odpowiedzi na pytanie "Jest to brzmienia?".</span><span class="sxs-lookup"><span data-stu-id="a8563-175">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Jest to nieco dziwne](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="a8563-177">Wykrywanie anomalii to proces wykrywania dane szeregów czasowych; punktów danego wejściowego szereg czasowy których zachowanie nie jest oczekiwanym lub "nieco dziwne".</span><span class="sxs-lookup"><span data-stu-id="a8563-177">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="a8563-178">Może to być przydatne na wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="a8563-178">This can be useful in lots of ways.</span></span> <span data-ttu-id="a8563-179">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a8563-179">For instance:</span></span>

<span data-ttu-id="a8563-180">Jeśli masz samochód, warto wiedzieć: Jest to przemysł miernika odczytu normalne lub masz przeciek?</span><span class="sxs-lookup"><span data-stu-id="a8563-180">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="a8563-181">Jeśli monitorujesz zużycie energii, czy chcesz wiedzieć: Występuje po awarii?</span><span class="sxs-lookup"><span data-stu-id="a8563-181">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="a8563-182">Istnieją dwa rodzaje czas serii anomalie, które mogą zostać wykryte:</span><span class="sxs-lookup"><span data-stu-id="a8563-182">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="a8563-183">**Wartości graniczne** wskazuje nietypowe zachowanie tymczasowe wzrosty w systemie.</span><span class="sxs-lookup"><span data-stu-id="a8563-183">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="a8563-184">**Punkty zmian** określenia początku trwałych zmian wraz z upływem czasu w systemie.</span><span class="sxs-lookup"><span data-stu-id="a8563-184">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="a8563-185">W strukturze ML.NET, algorytmy wykrywania kolekcji IID lub wykrywanie punktów zmiany identyfikatora IID są przystosowane do potrzeb [niezależne i identycznie rozproszonych zestawów danych](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="a8563-185">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="a8563-186">Będzie analizować te same dane sprzedaży produktu do wykrywania wzrostów i zmiany punktów.</span><span class="sxs-lookup"><span data-stu-id="a8563-186">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="a8563-187">Proces kompilowania i szkolenie modelu jest taki sam dla kolekcji wykrywania i zmiany punktu wykrywania; Główna różnica polega na algorytm wykrywania określonych.</span><span class="sxs-lookup"><span data-stu-id="a8563-187">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="a8563-188">Wykrywanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="a8563-188">Spike detection</span></span> 

<span data-ttu-id="a8563-189">Jest celem wykrywania kolekcji do identyfikowania nagłe jeszcze tymczasowe wzrosty, różniące się znacznie od większość wartości danych serii czasu.</span><span class="sxs-lookup"><span data-stu-id="a8563-189">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="a8563-190">Jest ważne wykryć te podejrzane elementów rzadkie, zdarzeń lub obserwacji w sposób terminowy minimalizowanie.</span><span class="sxs-lookup"><span data-stu-id="a8563-190">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="a8563-191">Następujące podejście może służyć do wykrywania szereg anomalie, takich jak: awarii, ataków cybernetycznych lub zawartości WWW wirusowej.</span><span class="sxs-lookup"><span data-stu-id="a8563-191">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="a8563-192">Poniższy rysunek jest przykładem skoki w zestawie danych serii czasu:</span><span class="sxs-lookup"><span data-stu-id="a8563-192">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="a8563-194">Utwórz metodę DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="a8563-194">Create the DetectSpike() method</span></span>

<span data-ttu-id="a8563-195">Dodaj następujące wywołanie do `DetectSpike()`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-195">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="a8563-196">`DetectSpike()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a8563-196">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="a8563-197">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="a8563-197">Trains the model.</span></span>
* <span data-ttu-id="a8563-198">Wykrywa skoki, na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a8563-198">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="a8563-199">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="a8563-199">Displays the results.</span></span>

<span data-ttu-id="a8563-200">Tworzenie `DetectSpike()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a8563-200">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="a8563-201">Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) do nauczenia modelu do kolekcji wykrywania.</span><span class="sxs-lookup"><span data-stu-id="a8563-201">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="a8563-202">Dodaj go do `DetectChangepoint()` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8563-202">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="a8563-203">Dopasuj do modelu `productSales` danych przez dodanie poniższego jako następnego wiersza kodu w `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-203">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="a8563-204">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="a8563-204">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="a8563-205">Dodaj następujący wiersz kodu do przekształcania `productSales` danych w następnym wierszu `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-205">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="a8563-206">W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="a8563-206">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="a8563-207">Konwertuj swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8563-207">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="a8563-208">Tworzenie za pomocą następujących wiersz nagłówka wyświetlana <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="a8563-208">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="a8563-209">Poniższe informacje będą wyświetlane w wynikach wykrywania kolekcji:</span><span class="sxs-lookup"><span data-stu-id="a8563-209">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="a8563-210">`Alert` Wskazuje alert dotyczący punktu danych w ramach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a8563-210">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="a8563-211">`Score` jest `ProductSales` wartość punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="a8563-211">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="a8563-212">`P-Value` "P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="a8563-212">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="a8563-213">Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii.</span><span class="sxs-lookup"><span data-stu-id="a8563-213">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="a8563-214">Użyj poniższego kodu, aby wykonać iterację `predictions` `IEnumerable` i wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="a8563-214">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="a8563-215">Wyniki wykrywania kolekcji</span><span class="sxs-lookup"><span data-stu-id="a8563-215">Spike detection results</span></span>

<span data-ttu-id="a8563-216">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="a8563-216">Your results should be similar to the following.</span></span> <span data-ttu-id="a8563-217">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="a8563-217">During processing, messages are displayed.</span></span> <span data-ttu-id="a8563-218">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a8563-218">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a8563-219">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="a8563-219">These have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="a8563-220">Zmiana punktu wykrywania</span><span class="sxs-lookup"><span data-stu-id="a8563-220">Change point detection</span></span>

<span data-ttu-id="a8563-221">`Change points` trwałych zmian w czas serii zdarzeń strumienia rozłożenia wartości, takich jak zmiany poziomu i trendów.</span><span class="sxs-lookup"><span data-stu-id="a8563-221">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="a8563-222">Te zmiany trwały ostatnie znacznie dłużej niż `spikes` i wskazywać, że zdarzenia krytycznego.</span><span class="sxs-lookup"><span data-stu-id="a8563-222">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="a8563-223">`Change points` nie są zwykle widoczne gołym okiem, ale może zostać wykryte w Twoich danych przy użyciu metod, takich jak następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="a8563-223">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="a8563-224">Poniższa ilustracja jest przykładem wykrywania punktu zmian:</span><span class="sxs-lookup"><span data-stu-id="a8563-224">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="a8563-226">Utwórz metodę DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="a8563-226">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="a8563-227">Dodaj następujące wywołanie do `DetectChangepoint()`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-227">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="a8563-228">`DetectChangepoint()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a8563-228">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="a8563-229">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="a8563-229">Trains the model.</span></span>
* <span data-ttu-id="a8563-230">Wykrywa, punktów zmiany na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a8563-230">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="a8563-231">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="a8563-231">Displays the results.</span></span>

<span data-ttu-id="a8563-232">Tworzenie `DetectChangepoint()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a8563-232">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="a8563-233">[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) służy do nauczenia modelu dla zmiany punktu wykrywania.</span><span class="sxs-lookup"><span data-stu-id="a8563-233">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="a8563-234">Dodaj go do `DetectChangepoint()` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8563-234">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="a8563-235">Jak poprzednio, dopasowania modelu do `productSales` danych przez dodanie poniższego jako następnego wiersza kodu w `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-235">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="a8563-236">Użyj `Transform()` metodę, aby przekształcić `Training` danych przez dodanie poniższego kodu `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="a8563-236">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="a8563-237">Tak jak wcześniej, należy przekonwertować swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu `CreateEnumerable()`metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8563-237">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="a8563-238">Utwórz nagłówek wyświetlania następującym kodem w następnym wierszu `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="a8563-238">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="a8563-239">Poniższe informacje będą wyświetlane w wynikach wykrywania punktu zmiany:</span><span class="sxs-lookup"><span data-stu-id="a8563-239">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="a8563-240">`Alert` Wskazuje alert punktu zmiany punktu danych.</span><span class="sxs-lookup"><span data-stu-id="a8563-240">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="a8563-241">`Score` jest `ProductSales` wartość punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="a8563-241">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="a8563-242">`P-Value` "P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="a8563-242">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="a8563-243">Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii.</span><span class="sxs-lookup"><span data-stu-id="a8563-243">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="a8563-244">`Martingale value` jest używany do identyfikowania, jak jest "brzmienia" punkt danych, na podstawie sekwencji wartości P.</span><span class="sxs-lookup"><span data-stu-id="a8563-244">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="a8563-245">Iteracyjne przeglądanie `predictions` `IEnumerable` i wyświetlić wyniki w następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8563-245">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="a8563-246">Zmiana punktu wykrywania wyników</span><span class="sxs-lookup"><span data-stu-id="a8563-246">Change point detection results</span></span>

<span data-ttu-id="a8563-247">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="a8563-247">Your results should be similar to the following.</span></span> <span data-ttu-id="a8563-248">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="a8563-248">During processing, messages are displayed.</span></span> <span data-ttu-id="a8563-249">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a8563-249">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a8563-250">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="a8563-250">These have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="a8563-251">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a8563-251">Congratulations!</span></span> <span data-ttu-id="a8563-252">Teraz zostały pomyślnie skompilowane modeli uczenia maszynowego do wykrywania wzrostów i zmienić punkt anomalii w danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a8563-252">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="a8563-253">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="a8563-253">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="a8563-254">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a8563-254">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a8563-255">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a8563-255">Load the data</span></span>
> * <span data-ttu-id="a8563-256">Uczenie modelu do kolekcji wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="a8563-256">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="a8563-257">Wykrywaj anomalie kolekcji za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="a8563-257">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="a8563-258">Uczenie modelu dla zmiany punktu anomalii</span><span class="sxs-lookup"><span data-stu-id="a8563-258">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="a8563-259">Wykrywaj anomalie punktu zmiany w trybie uczonego</span><span class="sxs-lookup"><span data-stu-id="a8563-259">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="a8563-260">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a8563-260">Next steps</span></span>

<span data-ttu-id="a8563-261">Zapoznaj się z repozytorium GitHub samples usługi Machine Learning można eksplorować przykładową wykrywania anomalii zużycia energii.</span><span class="sxs-lookup"><span data-stu-id="a8563-261">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a8563-262">repozytorium GitHub machinelearning-DotNet-samples</span><span class="sxs-lookup"><span data-stu-id="a8563-262">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection)
