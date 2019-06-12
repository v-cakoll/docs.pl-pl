---
title: 'Samouczek: Wykrywanie anomalii w — sprzedaż produktów'
description: Dowiedz się, jak utworzyć aplikację wykrywania anomalii do danych sprzedaży produktu. Ten samouczek tworzy, używając aplikacji konsoli .NET Core C# w programie Visual Studio 2019 r.
ms.date: 06/11/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 6ea5adf79a17bb10ddea676eaea483c2cf627d82
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026048"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="1fb76-104">Samouczek: Wykrywanie anomalii w — sprzedaż produktów za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="1fb76-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="1fb76-105">Dowiedz się, jak utworzyć aplikację wykrywania anomalii do danych sprzedaży produktu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="1fb76-106">Ten samouczek tworzy, używając aplikacji konsoli .NET Core C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1fb76-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="1fb76-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1fb76-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="1fb76-108">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1fb76-108">Load the data</span></span>
> * <span data-ttu-id="1fb76-109">Uczenie modelu do kolekcji wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="1fb76-109">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="1fb76-110">Wykrywaj anomalie kolekcji za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="1fb76-110">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="1fb76-111">Uczenie modelu dla zmiany punktu anomalii</span><span class="sxs-lookup"><span data-stu-id="1fb76-111">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="1fb76-112">Wykrywaj anomalie punktu zmiany za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="1fb76-112">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="1fb76-113">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="1fb76-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1fb76-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1fb76-114">Prerequisites</span></span>

* <span data-ttu-id="1fb76-115">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="1fb76-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="1fb76-116">Zestaw danych sales.csv produktu</span><span class="sxs-lookup"><span data-stu-id="1fb76-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="1fb76-117">Dane formatu w `product-sales.csv` opiera się na zestawie danych "Szamponu sprzedaż za pośrednictwem trzech lat" pierwotnie skąd pochodzi z usługi DataMarket i udostępniane przez czas serii danych biblioteki (TSDL), utworzone przez Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="1fb76-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="1fb76-118">Zestaw danych "Szamponu sprzedaży przez trzy lata" uzyskał licencje w ramach licencji Open DataMarket domyślne.</span><span class="sxs-lookup"><span data-stu-id="1fb76-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="1fb76-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="1fb76-119">Create a console application</span></span>

1. <span data-ttu-id="1fb76-120">Tworzenie **aplikacji konsoli .NET Core** o nazwie "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="1fb76-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="1fb76-121">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="1fb76-122">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="1fb76-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1fb76-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1fb76-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1fb76-124">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1fb76-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="1fb76-125">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="1fb76-126">Powtórz te kroki dla **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="1fb76-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="1fb76-127">Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="1fb76-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="1fb76-128">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="1fb76-128">Download your data</span></span>

1. <span data-ttu-id="1fb76-129">Pobierz zestaw danych i zapisać go w celu *danych* wcześniej utworzony folder:</span><span class="sxs-lookup"><span data-stu-id="1fb76-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="1fb76-130">Kliknij prawym przyciskiem myszy [ *sales.csv produktu* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="1fb76-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="1fb76-131">Upewnij się, albo zapisać \*pliku CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*pliku CSV *danych* folderu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="1fb76-132">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy \*pliku CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1fb76-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="1fb76-133">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="1fb76-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="1fb76-134">Poniższa tabela jest podgląd danych z usługi \*pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="1fb76-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="1fb76-135">Miesiąc</span><span class="sxs-lookup"><span data-stu-id="1fb76-135">Month</span></span>  |<span data-ttu-id="1fb76-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="1fb76-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="1fb76-137">1 stycznia</span><span class="sxs-lookup"><span data-stu-id="1fb76-137">1-Jan</span></span>  |    <span data-ttu-id="1fb76-138">271</span><span class="sxs-lookup"><span data-stu-id="1fb76-138">271</span></span>      |
|<span data-ttu-id="1fb76-139">2 stycznia</span><span class="sxs-lookup"><span data-stu-id="1fb76-139">2-Jan</span></span>  |    <span data-ttu-id="1fb76-140">150.9</span><span class="sxs-lookup"><span data-stu-id="1fb76-140">150.9</span></span>    |
|<span data-ttu-id="1fb76-141">.....</span><span class="sxs-lookup"><span data-stu-id="1fb76-141">.....</span></span>  |    <span data-ttu-id="1fb76-142">.....</span><span class="sxs-lookup"><span data-stu-id="1fb76-142">.....</span></span>    |
|<span data-ttu-id="1fb76-143">1-Feb</span><span class="sxs-lookup"><span data-stu-id="1fb76-143">1-Feb</span></span>  |    <span data-ttu-id="1fb76-144">199.3</span><span class="sxs-lookup"><span data-stu-id="1fb76-144">199.3</span></span>    |
|<span data-ttu-id="1fb76-145">.....</span><span class="sxs-lookup"><span data-stu-id="1fb76-145">.....</span></span>  |    <span data-ttu-id="1fb76-146">.....</span><span class="sxs-lookup"><span data-stu-id="1fb76-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="1fb76-147">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="1fb76-147">Create classes and define paths</span></span>

<span data-ttu-id="1fb76-148">Następnie zdefiniuj strukturę danych wejściowych klasy.</span><span class="sxs-lookup"><span data-stu-id="1fb76-148">Next, define your input class data structure.</span></span>

<span data-ttu-id="1fb76-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="1fb76-150">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="1fb76-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="1fb76-151">W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="1fb76-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="1fb76-152">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1fb76-152">Then, select the **Add** button.</span></span>

<span data-ttu-id="1fb76-153">*ProductSalesData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-153">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="1fb76-154">Dodaj następujący kod `using` instrukcji na górze *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="1fb76-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="1fb76-155">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `ProductSalesData` i `ProductSalesPrediction`, *ProductSalesData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="1fb76-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="1fb76-156">`ProductSalesData` Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="1fb76-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane.</span><span class="sxs-lookup"><span data-stu-id="1fb76-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="1fb76-158">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="1fb76-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="1fb76-159">Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-159">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="1fb76-160">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-160">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="1fb76-161">`_docsize` ma to liczba rekordów w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-161">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="1fb76-162">Można będzie użyć do obliczenia `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="1fb76-162">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="1fb76-163">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="1fb76-163">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="1fb76-164">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-164">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="1fb76-165">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1fb76-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="1fb76-166">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="1fb76-166">Initialize variables in Main</span></span>

<span data-ttu-id="1fb76-167">Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować `mlContext` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="1fb76-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="1fb76-168">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1fb76-168">Load the data</span></span>

<span data-ttu-id="1fb76-169">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="1fb76-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="1fb76-170">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="1fb76-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="1fb76-171">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="1fb76-172">Dodaj następujący kod jako następnego wiersza `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-172">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="1fb76-173">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="1fb76-173">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="1fb76-174">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="1fb76-174">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="1fb76-175">Zadanie ML — wykrywanie anomalii w czasie serii</span><span class="sxs-lookup"><span data-stu-id="1fb76-175">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="1fb76-176">Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="1fb76-176">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="1fb76-177">Ta funkcja zapewnia wskazówki gdzie szukać problemów i pomaga w odpowiedzi na pytanie "Jest to brzmienia?".</span><span class="sxs-lookup"><span data-stu-id="1fb76-177">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Jest to nieco dziwne](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="1fb76-179">Wykrywanie anomalii to proces wykrywania dane szeregów czasowych; punktów danego wejściowego szereg czasowy których zachowanie nie jest oczekiwanym lub "nieco dziwne".</span><span class="sxs-lookup"><span data-stu-id="1fb76-179">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="1fb76-180">Może to być przydatne na wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="1fb76-180">This can be useful in lots of ways.</span></span> <span data-ttu-id="1fb76-181">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1fb76-181">For instance:</span></span>

<span data-ttu-id="1fb76-182">Jeśli masz samochód, warto wiedzieć: Jest to przemysł miernika odczytu normalne lub masz przeciek?</span><span class="sxs-lookup"><span data-stu-id="1fb76-182">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="1fb76-183">Jeśli monitorujesz zużycie energii, czy chcesz wiedzieć: Występuje po awarii?</span><span class="sxs-lookup"><span data-stu-id="1fb76-183">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="1fb76-184">Istnieją dwa rodzaje czas serii anomalie, które mogą zostać wykryte:</span><span class="sxs-lookup"><span data-stu-id="1fb76-184">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="1fb76-185">**Wartości graniczne** wskazuje nietypowe zachowanie tymczasowe wzrosty w systemie.</span><span class="sxs-lookup"><span data-stu-id="1fb76-185">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="1fb76-186">**Punkty zmian** określenia początku trwałych zmian wraz z upływem czasu w systemie.</span><span class="sxs-lookup"><span data-stu-id="1fb76-186">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="1fb76-187">W strukturze ML.NET, algorytmy wykrywania kolekcji IID lub wykrywanie punktów zmiany identyfikatora IID są przystosowane do potrzeb [niezależne i identycznie rozproszonych zestawów danych](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="1fb76-187">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="1fb76-188">Będzie analizować te same dane sprzedaży produktu do wykrywania wzrostów i zmiany punktów.</span><span class="sxs-lookup"><span data-stu-id="1fb76-188">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="1fb76-189">Proces kompilowania i szkolenie modelu jest taki sam dla kolekcji wykrywania i zmiany punktu wykrywania; Główna różnica polega na algorytm wykrywania określonych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-189">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="1fb76-190">Wykrywanie kolekcji</span><span class="sxs-lookup"><span data-stu-id="1fb76-190">Spike detection</span></span> 

<span data-ttu-id="1fb76-191">Jest celem wykrywania kolekcji do identyfikowania nagłe jeszcze tymczasowe wzrosty, różniące się znacznie od większość wartości danych serii czasu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-191">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="1fb76-192">Jest ważne wykryć te podejrzane elementów rzadkie, zdarzeń lub obserwacji w sposób terminowy minimalizowanie.</span><span class="sxs-lookup"><span data-stu-id="1fb76-192">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="1fb76-193">Następujące podejście może służyć do wykrywania szereg anomalie, takich jak: awarii, ataków cybernetycznych lub zawartości WWW wirusowej.</span><span class="sxs-lookup"><span data-stu-id="1fb76-193">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="1fb76-194">Poniższy rysunek jest przykładem skoki w zestawie danych serii czasu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-194">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="1fb76-196">Utwórz metodę DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="1fb76-196">Create the DetectSpike() method</span></span>

<span data-ttu-id="1fb76-197">Dodaj następujące wywołanie do `DetectSpike()`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-197">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="1fb76-198">`DetectSpike()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="1fb76-198">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="1fb76-199">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-199">Trains the model.</span></span>
* <span data-ttu-id="1fb76-200">Wykrywa skoki, na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="1fb76-200">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="1fb76-201">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="1fb76-201">Displays the results.</span></span>

<span data-ttu-id="1fb76-202">Tworzenie `DetectSpike()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-202">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="1fb76-203">Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) do nauczenia modelu do kolekcji wykrywania.</span><span class="sxs-lookup"><span data-stu-id="1fb76-203">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="1fb76-204">Dodaj go do `DetectChangepoint()` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fb76-204">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="1fb76-205">Dopasuj do modelu `productSales` danych przez dodanie poniższego jako następnego wiersza kodu w `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-205">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="1fb76-206">[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="1fb76-206">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="1fb76-207">Dodaj następujący wiersz kodu do przekształcania `productSales` danych w następnym wierszu `DetectSpike()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-207">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="1fb76-208">W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="1fb76-208">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="1fb76-209">Konwertuj swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fb76-209">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="1fb76-210">Tworzenie za pomocą następujących wiersz nagłówka wyświetlana <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-210">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="1fb76-211">Poniższe informacje będą wyświetlane w wynikach wykrywania kolekcji:</span><span class="sxs-lookup"><span data-stu-id="1fb76-211">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="1fb76-212">`Alert` Wskazuje alert dotyczący punktu danych w ramach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1fb76-212">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="1fb76-213">`Score` jest `ProductSales` wartość punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-213">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="1fb76-214">`P-Value` "P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="1fb76-214">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="1fb76-215">Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii.</span><span class="sxs-lookup"><span data-stu-id="1fb76-215">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="1fb76-216">Użyj poniższego kodu, aby wykonać iterację `predictions` `IEnumerable` i wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="1fb76-216">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="1fb76-217">Wyniki wykrywania kolekcji</span><span class="sxs-lookup"><span data-stu-id="1fb76-217">Spike detection results</span></span>

<span data-ttu-id="1fb76-218">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="1fb76-218">Your results should be similar to the following.</span></span> <span data-ttu-id="1fb76-219">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="1fb76-219">During processing, messages are displayed.</span></span> <span data-ttu-id="1fb76-220">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="1fb76-220">You may see warnings, or processing messages.</span></span> <span data-ttu-id="1fb76-221">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="1fb76-221">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="1fb76-222">Zmiana punktu wykrywania</span><span class="sxs-lookup"><span data-stu-id="1fb76-222">Change point detection</span></span>

<span data-ttu-id="1fb76-223">`Change points` trwałych zmian w czas serii zdarzeń strumienia rozłożenia wartości, takich jak zmiany poziomu i trendów.</span><span class="sxs-lookup"><span data-stu-id="1fb76-223">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="1fb76-224">Te zmiany trwały ostatnie znacznie dłużej niż `spikes` i wskazywać, że zdarzenia krytycznego.</span><span class="sxs-lookup"><span data-stu-id="1fb76-224">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="1fb76-225">`Change points` nie są zwykle widoczne gołym okiem, ale może zostać wykryte w Twoich danych przy użyciu metod, takich jak następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="1fb76-225">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="1fb76-226">Poniższa ilustracja jest przykładem wykrywania punktu zmian:</span><span class="sxs-lookup"><span data-stu-id="1fb76-226">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="1fb76-228">Utwórz metodę DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="1fb76-228">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="1fb76-229">Dodaj następujące wywołanie do `DetectChangepoint()`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-229">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="1fb76-230">`DetectChangepoint()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="1fb76-230">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="1fb76-231">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="1fb76-231">Trains the model.</span></span>
* <span data-ttu-id="1fb76-232">Wykrywa, punktów zmiany na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="1fb76-232">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="1fb76-233">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="1fb76-233">Displays the results.</span></span>

<span data-ttu-id="1fb76-234">Tworzenie `DetectChangepoint()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1fb76-234">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="1fb76-235">[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) służy do nauczenia modelu dla zmiany punktu wykrywania.</span><span class="sxs-lookup"><span data-stu-id="1fb76-235">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="1fb76-236">Dodaj go do `DetectChangepoint()` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fb76-236">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="1fb76-237">Jak poprzednio, dopasowania modelu do `productSales` danych przez dodanie poniższego jako następnego wiersza kodu w `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-237">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="1fb76-238">Użyj `Transform()` metodę, aby przekształcić `Training` danych przez dodanie poniższego kodu `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="1fb76-238">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="1fb76-239">Tak jak wcześniej, należy przekonwertować swoje `transformedData` do silnie typizowanego `IEnumerable` dla łatwiejsze wyświetlania przy użyciu `CreateEnumerable()`metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fb76-239">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="1fb76-240">Utwórz nagłówek wyświetlania następującym kodem w następnym wierszu `DetectChangePoint()` metody:</span><span class="sxs-lookup"><span data-stu-id="1fb76-240">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="1fb76-241">Poniższe informacje będą wyświetlane w wynikach wykrywania punktu zmiany:</span><span class="sxs-lookup"><span data-stu-id="1fb76-241">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="1fb76-242">`Alert` Wskazuje alert punktu zmiany punktu danych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-242">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="1fb76-243">`Score` jest `ProductSales` wartość punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="1fb76-243">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="1fb76-244">`P-Value` "P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="1fb76-244">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="1fb76-245">Oznacza to, jakie jest prawdopodobieństwo, ten punkt danych anomalii.</span><span class="sxs-lookup"><span data-stu-id="1fb76-245">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="1fb76-246">`Martingale value` jest używany do identyfikowania, jak jest "brzmienia" punkt danych, na podstawie sekwencji wartości P.</span><span class="sxs-lookup"><span data-stu-id="1fb76-246">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="1fb76-247">Iteracyjne przeglądanie `predictions` `IEnumerable` i wyświetlić wyniki w następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fb76-247">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="1fb76-248">Zmiana punktu wykrywania wyników</span><span class="sxs-lookup"><span data-stu-id="1fb76-248">Change point detection results</span></span>

<span data-ttu-id="1fb76-249">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="1fb76-249">Your results should be similar to the following.</span></span> <span data-ttu-id="1fb76-250">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="1fb76-250">During processing, messages are displayed.</span></span> <span data-ttu-id="1fb76-251">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="1fb76-251">You may see warnings, or processing messages.</span></span> <span data-ttu-id="1fb76-252">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="1fb76-252">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="1fb76-253">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="1fb76-253">Congratulations!</span></span> <span data-ttu-id="1fb76-254">Teraz zostały pomyślnie skompilowane modeli uczenia maszynowego do wykrywania wzrostów i zmienić punkt anomalii w danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="1fb76-254">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="1fb76-255">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="1fb76-255">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="1fb76-256">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1fb76-256">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="1fb76-257">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="1fb76-257">Load the data</span></span>
> * <span data-ttu-id="1fb76-258">Uczenie modelu do kolekcji wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="1fb76-258">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="1fb76-259">Wykrywaj anomalie kolekcji za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="1fb76-259">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="1fb76-260">Uczenie modelu dla zmiany punktu anomalii</span><span class="sxs-lookup"><span data-stu-id="1fb76-260">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="1fb76-261">Wykrywaj anomalie punktu zmiany w trybie uczonego</span><span class="sxs-lookup"><span data-stu-id="1fb76-261">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="1fb76-262">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1fb76-262">Next steps</span></span>

<span data-ttu-id="1fb76-263">Zapoznaj się z repozytorium GitHub samples usługi Machine Learning można eksplorować przykładową wykrywania anomalii zużycia energii.</span><span class="sxs-lookup"><span data-stu-id="1fb76-263">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="1fb76-264">repozytorium GitHub machinelearning-DotNet-samples</span><span class="sxs-lookup"><span data-stu-id="1fb76-264">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
