---
title: 'Samouczek: Wykrywaj anomalie w sprzedaży produktu'
description: Dowiedz się, jak utworzyć aplikację wykrywania anomalii dla danych sprzedaży produktu. W tym samouczku przedstawiono tworzenie aplikacji konsolowej C# platformy .NET Core przy użyciu programu Visual Studio 2019.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e87034733b048153202bc11ab94ed7605749f60c
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331691"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="852ec-104">Samouczek: Wykrywaj anomalie w sprzedaży produktów za pomocą ML.NET</span><span class="sxs-lookup"><span data-stu-id="852ec-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="852ec-105">Dowiedz się, jak utworzyć aplikację wykrywania anomalii dla danych sprzedaży produktu.</span><span class="sxs-lookup"><span data-stu-id="852ec-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="852ec-106">W tym samouczku przedstawiono tworzenie aplikacji konsolowej C# platformy .NET Core przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="852ec-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="852ec-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="852ec-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="852ec-108">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="852ec-108">Load the data</span></span>
> * <span data-ttu-id="852ec-109">Uczenie modelu umożliwiającego przeprowadzenie wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="852ec-109">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="852ec-110">Wykrywaj anomalie wzrostu przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="852ec-110">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="852ec-111">Uczenie modelu wykrywania anomalii punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="852ec-111">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="852ec-112">Wykrywaj anomalie punktu zmiany przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="852ec-112">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="852ec-113">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .</span><span class="sxs-lookup"><span data-stu-id="852ec-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="852ec-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="852ec-114">Prerequisites</span></span>

* <span data-ttu-id="852ec-115">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ec-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="852ec-116">Zestaw danych Product-Sales. csv</span><span class="sxs-lookup"><span data-stu-id="852ec-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="852ec-117">Format danych w programie `product-sales.csv` jest oparty na zestawie danych "szampon Sales w okresie trzech lat", pierwotnie pochodzący od DataMarket i udostępnianych przez bibliotekę danych szeregów czasowych (TSDL) utworzonych przez Roba Hyndman.</span><span class="sxs-lookup"><span data-stu-id="852ec-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="852ec-118">"Szampon Sales w okresie trzech lat", który jest licencjonowany w ramach domyślnej licencji Open w ramach programu DataMarket.</span><span class="sxs-lookup"><span data-stu-id="852ec-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="852ec-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="852ec-119">Create a console application</span></span>

1. <span data-ttu-id="852ec-120">Utwórz **aplikację konsolową .NET Core** o nazwie "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="852ec-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="852ec-121">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="852ec-122">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="852ec-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="852ec-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="852ec-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="852ec-124">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, Wyszukaj pozycję **Microsoft.ml**, wybierz pakiet **v 1.0.0** na liście, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="852ec-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="852ec-125">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="852ec-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="852ec-126">Powtórz te kroki dla **Microsoft. ml. szeregów czasowych v 0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="852ec-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="852ec-127">Dodaj następujące `using` instrukcje w górnej części pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="852ec-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="852ec-128">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="852ec-128">Download your data</span></span>

1. <span data-ttu-id="852ec-129">Pobierz zestaw danych i Zapisz go w utworzonym wcześniej folderze *danych* :</span><span class="sxs-lookup"><span data-stu-id="852ec-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="852ec-130">Kliknij prawym przyciskiem myszy plik [*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."</span><span class="sxs-lookup"><span data-stu-id="852ec-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="852ec-131">Upewnij się, że plik CSV \*został zapisany w folderze *dane* lub po jego zapisaniu w \*innym miejscu Przenieś plik CSV do folderu *dane* .</span><span class="sxs-lookup"><span data-stu-id="852ec-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="852ec-132">W Eksplorator rozwiązań kliknij prawym przyciskiem \*myszy plik CSV i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="852ec-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="852ec-133">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="852ec-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="852ec-134">Poniższa tabela zawiera podgląd danych z \*pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="852ec-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="852ec-135">Bieżącym</span><span class="sxs-lookup"><span data-stu-id="852ec-135">Month</span></span>  |<span data-ttu-id="852ec-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="852ec-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="852ec-137">1 stycznia</span><span class="sxs-lookup"><span data-stu-id="852ec-137">1-Jan</span></span>  |    <span data-ttu-id="852ec-138">271</span><span class="sxs-lookup"><span data-stu-id="852ec-138">271</span></span>      |
|<span data-ttu-id="852ec-139">2-sty</span><span class="sxs-lookup"><span data-stu-id="852ec-139">2-Jan</span></span>  |    <span data-ttu-id="852ec-140">150,9</span><span class="sxs-lookup"><span data-stu-id="852ec-140">150.9</span></span>    |
|<span data-ttu-id="852ec-141">.....</span><span class="sxs-lookup"><span data-stu-id="852ec-141">.....</span></span>  |    <span data-ttu-id="852ec-142">.....</span><span class="sxs-lookup"><span data-stu-id="852ec-142">.....</span></span>    |
|<span data-ttu-id="852ec-143">1 — Luty</span><span class="sxs-lookup"><span data-stu-id="852ec-143">1-Feb</span></span>  |    <span data-ttu-id="852ec-144">199,3</span><span class="sxs-lookup"><span data-stu-id="852ec-144">199.3</span></span>    |
|<span data-ttu-id="852ec-145">.....</span><span class="sxs-lookup"><span data-stu-id="852ec-145">.....</span></span>  |    <span data-ttu-id="852ec-146">.....</span><span class="sxs-lookup"><span data-stu-id="852ec-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="852ec-147">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="852ec-147">Create classes and define paths</span></span>

<span data-ttu-id="852ec-148">Następnie zdefiniuj swoją strukturę danych klasy wejściowej.</span><span class="sxs-lookup"><span data-stu-id="852ec-148">Next, define your input class data structure.</span></span>

<span data-ttu-id="852ec-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="852ec-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="852ec-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="852ec-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="852ec-151">W **oknie dialogowym Dodaj nowy element**wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="852ec-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="852ec-152">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="852ec-152">Then, select the **Add** button.</span></span>

<span data-ttu-id="852ec-153">Plik *ProductSalesData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="852ec-153">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="852ec-154">Dodaj następującą `using` instrukcję na początku *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="852ec-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="852ec-155">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `ProductSalesData` i `ProductSalesPrediction`, do pliku *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="852ec-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="852ec-156">`ProductSalesData`Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="852ec-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="852ec-157">Atrybut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane.</span><span class="sxs-lookup"><span data-stu-id="852ec-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="852ec-158">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="852ec-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="852ec-159">Należy utworzyć dwa pola globalne do przechowywania ostatnio pobranej ścieżki pliku zestawu danych i zapisanej ścieżki pliku modelu:</span><span class="sxs-lookup"><span data-stu-id="852ec-159">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="852ec-160">`_dataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="852ec-160">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="852ec-161">`_docsize`zawiera liczbę rekordów w pliku DataSet.</span><span class="sxs-lookup"><span data-stu-id="852ec-161">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="852ec-162">Ta funkcja zostanie użyta do `pvalueHistoryLength`obliczenia.</span><span class="sxs-lookup"><span data-stu-id="852ec-162">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="852ec-163">Dodaj następujący kod do wiersza bezpośrednio powyżej metody, `Main` aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="852ec-163">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="852ec-164">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="852ec-164">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="852ec-165">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="852ec-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="852ec-166">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="852ec-166">Initialize variables in Main</span></span>

<span data-ttu-id="852ec-167">Zastąp `Main` `mlContext` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="852ec-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="852ec-168">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="852ec-168">Load the data</span></span>

<span data-ttu-id="852ec-169">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="852ec-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="852ec-170">`IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="852ec-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="852ec-171">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="852ec-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="852ec-172">Dodaj następujący kod w następnym wierszu `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="852ec-172">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="852ec-173">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="852ec-173">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="852ec-174">Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="852ec-174">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="852ec-175">"ML" — wykrywanie anomalii szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="852ec-175">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="852ec-176">Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="852ec-176">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="852ec-177">Zawiera wskazówki, gdzie szukać problemów i pomaga odpowiedzieć na pytanie "czy to brzmienia?".</span><span class="sxs-lookup"><span data-stu-id="852ec-177">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Czy ten brzmienia](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="852ec-179">Wykrywanie anomalii to proces wykrywania wartości odstających danych szeregów czasowych; wskazuje na dane wejściowe serie czasowe, w których zachowanie nie jest oczekiwane, lub "brzmienia".</span><span class="sxs-lookup"><span data-stu-id="852ec-179">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="852ec-180">Może to być przydatne na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="852ec-180">This can be useful in lots of ways.</span></span> <span data-ttu-id="852ec-181">Przykład:</span><span class="sxs-lookup"><span data-stu-id="852ec-181">For instance:</span></span>

<span data-ttu-id="852ec-182">Jeśli masz samochód, warto wiedzieć: Czy ten miernik oleju jest odczytywany w normalnym lub czy mam wyciek?</span><span class="sxs-lookup"><span data-stu-id="852ec-182">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="852ec-183">Jeśli monitorujesz zużycie mocy, warto wiedzieć: Czy wystąpił przestój?</span><span class="sxs-lookup"><span data-stu-id="852ec-183">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="852ec-184">Istnieją dwa typy anomalii szeregów czasowych, które mogą zostać wykryte:</span><span class="sxs-lookup"><span data-stu-id="852ec-184">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="852ec-185">**Skoki** wskazują tymczasowe rozerwania nietypowego zachowania w systemie.</span><span class="sxs-lookup"><span data-stu-id="852ec-185">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="852ec-186">**Punkty zmian** wskazują początek trwałych zmian w czasie w systemie.</span><span class="sxs-lookup"><span data-stu-id="852ec-186">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="852ec-187">W programie ML.NET algorytmy wykrywania i wykrywania punktu zmiany identyfikatora IID są odpowiednie dla niezależnych [i identycznie rozproszonych zestawów danych](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="852ec-187">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="852ec-188">Przeanalizujesz te same dane sprzedaży produktu w celu wykrywania skoków i punktów zmian.</span><span class="sxs-lookup"><span data-stu-id="852ec-188">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="852ec-189">Proces kompilowania i uczenia jest taki sam, jak w celu uzyskania wykrywalności i wykrywania punktów zmiany; Główną różnicą jest używany algorytm wykrywania.</span><span class="sxs-lookup"><span data-stu-id="852ec-189">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="852ec-190">Wykrywanie</span><span class="sxs-lookup"><span data-stu-id="852ec-190">Spike detection</span></span> 

<span data-ttu-id="852ec-191">Celem w zakresie wykrywania jest zidentyfikowanie nagłych obciążeń tymczasowych, które znacząco różnią się od większości wartości danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="852ec-191">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="852ec-192">Ważne jest, aby wykrywać te podejrzane rzadkie elementy, zdarzenia lub obserwacje w odpowiednim czasie, aby być zminimalizowane.</span><span class="sxs-lookup"><span data-stu-id="852ec-192">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="852ec-193">Poniższe podejście może służyć do wykrywania różnych anomalii, takich jak: awaria, ataki cybernetycznymi lub wirusowej zawartości sieci Web.</span><span class="sxs-lookup"><span data-stu-id="852ec-193">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="852ec-194">Na poniższej ilustracji przedstawiono przykład skoków w zestawie danych szeregów czasowych:</span><span class="sxs-lookup"><span data-stu-id="852ec-194">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="852ec-196">Tworzenie metody DetectSpike ()</span><span class="sxs-lookup"><span data-stu-id="852ec-196">Create the DetectSpike() method</span></span>

<span data-ttu-id="852ec-197">Dodaj następujące wywołanie do `DetectSpike()`metody jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-197">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="852ec-198">`DetectSpike()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="852ec-198">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="852ec-199">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="852ec-199">Trains the model.</span></span>
* <span data-ttu-id="852ec-200">Wykrywa skoki na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="852ec-200">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="852ec-201">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="852ec-201">Displays the results.</span></span>

<span data-ttu-id="852ec-202">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="852ec-202">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="852ec-203">Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) , aby nauczyć model na potrzeby wykrywania.</span><span class="sxs-lookup"><span data-stu-id="852ec-203">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="852ec-204">Dodaj go do `DetectSpike()` metody przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="852ec-204">Add it to the `DetectSpike()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="852ec-205">Dopasuj model do `productSales` danych, dodając następujący kod jako następny wiersz kodu `DetectSpike()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-205">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="852ec-206">Metoda [dopasowywania ()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="852ec-206">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="852ec-207">Dodaj następujący wiersz kodu, aby przekształcić `productSales` dane jako następny wiersz `DetectSpike()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-207">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="852ec-208">Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-208">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="852ec-209">Konwertuj na silnie wpisaną `IEnumerable` wartość, aby ułatwić wyświetlanie przy użyciu metody "xmlliczaln [()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) " z następującym kodem: `transformedData`</span><span class="sxs-lookup"><span data-stu-id="852ec-209">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="852ec-210">Utwórz wiersz nagłówka wyświetlanego przy użyciu następującego <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu:</span><span class="sxs-lookup"><span data-stu-id="852ec-210">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="852ec-211">Następujące informacje zostaną wyświetlone w wynikach wykrywania:</span><span class="sxs-lookup"><span data-stu-id="852ec-211">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="852ec-212">`Alert`wskazuje alert dla danego punktu danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-212">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="852ec-213">`Score``ProductSales` jest wartością dla danego punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-213">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="852ec-214">`P-Value`"P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="852ec-214">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="852ec-215">Wskazuje to, jak najprawdopodobniej ten punkt danych jest anomalią.</span><span class="sxs-lookup"><span data-stu-id="852ec-215">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="852ec-216">Użyj poniższego kodu, aby wykonać iterację `predictions` `IEnumerable` i wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="852ec-216">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="852ec-217">Skoki wyników wykrywania</span><span class="sxs-lookup"><span data-stu-id="852ec-217">Spike detection results</span></span>

<span data-ttu-id="852ec-218">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="852ec-218">Your results should be similar to the following.</span></span> <span data-ttu-id="852ec-219">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="852ec-219">During processing, messages are displayed.</span></span> <span data-ttu-id="852ec-220">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="852ec-220">You may see warnings, or processing messages.</span></span> <span data-ttu-id="852ec-221">Zostały one usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="852ec-221">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="852ec-222">Wykrywanie punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="852ec-222">Change point detection</span></span>

<span data-ttu-id="852ec-223">`Change points`są trwałymi zmianami w czasie dystrybucji strumienia zdarzeń szeregów czasowych, takich jak zmiany poziomów i trendy.</span><span class="sxs-lookup"><span data-stu-id="852ec-223">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="852ec-224">Te trwałe zmiany są ostatnie znacznie dłużej `spikes` niż i mogą wskazywać na katastrofalne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="852ec-224">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="852ec-225">`Change points`nie są zwykle widoczne dla gołym okiem, ale mogą być wykrywane w danych przy użyciu podejścia, takiego jak w poniższej metodzie.</span><span class="sxs-lookup"><span data-stu-id="852ec-225">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="852ec-226">Na poniższej ilustracji przedstawiono przykład wykrywania punktu zmiany:</span><span class="sxs-lookup"><span data-stu-id="852ec-226">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="852ec-228">Tworzenie metody DetectChangepoint ()</span><span class="sxs-lookup"><span data-stu-id="852ec-228">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="852ec-229">Dodaj następujące wywołanie do `DetectChangepoint()`metody jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-229">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="852ec-230">`DetectChangepoint()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="852ec-230">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="852ec-231">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="852ec-231">Trains the model.</span></span>
* <span data-ttu-id="852ec-232">Wykrywa punkty zmian w oparciu o dane dotyczące sprzedaży historycznej.</span><span class="sxs-lookup"><span data-stu-id="852ec-232">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="852ec-233">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="852ec-233">Displays the results.</span></span>

<span data-ttu-id="852ec-234">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `DetectChangepoint()`</span><span class="sxs-lookup"><span data-stu-id="852ec-234">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="852ec-235">[IidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) jest używany do uczenia modelu wykrywania punktu zmiany.</span><span class="sxs-lookup"><span data-stu-id="852ec-235">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="852ec-236">Dodaj go do `DetectChangepoint()` metody przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="852ec-236">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="852ec-237">Tak jak wcześniej, Dopasuj model do `productSales` danych, dodając następujący kod jako następny wiersz kodu `DetectChangePoint()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-237">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="852ec-238">Użyj metody do `Training` przekształcenia danych, dodając następujący kod do `DetectChangePoint()`: `Transform()`</span><span class="sxs-lookup"><span data-stu-id="852ec-238">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="852ec-239">Tak jak wcześniej, przekonwertuj `transformedData` na silnie wpisaną `IEnumerable` wartość, `CreateEnumerable()`aby ułatwić wyświetlanie przy użyciu metody z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="852ec-239">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="852ec-240">Utwórz nagłówek wyświetlania z następującym kodem jako następnym wierszem w `DetectChangePoint()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="852ec-240">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="852ec-241">W wynikach wykrywania punktu zmiany zostaną wyświetlone następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="852ec-241">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="852ec-242">`Alert`wskazuje alert punktu zmiany dla danego punktu danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-242">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="852ec-243">`Score``ProductSales` jest wartością dla danego punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="852ec-243">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="852ec-244">`P-Value`"P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="852ec-244">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="852ec-245">Wskazuje to, jak najprawdopodobniej ten punkt danych jest anomalią.</span><span class="sxs-lookup"><span data-stu-id="852ec-245">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="852ec-246">`Martingale value`służy do identyfikowania, jak "brzmienia" punkt danych jest oparty na sekwencji wartości P.</span><span class="sxs-lookup"><span data-stu-id="852ec-246">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="852ec-247">Wykonaj iterację i Wyświetl wyniki przy użyciu następującego kodu: `IEnumerable` `predictions`</span><span class="sxs-lookup"><span data-stu-id="852ec-247">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="852ec-248">Wyniki wykrywania punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="852ec-248">Change point detection results</span></span>

<span data-ttu-id="852ec-249">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="852ec-249">Your results should be similar to the following.</span></span> <span data-ttu-id="852ec-250">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="852ec-250">During processing, messages are displayed.</span></span> <span data-ttu-id="852ec-251">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="852ec-251">You may see warnings, or processing messages.</span></span> <span data-ttu-id="852ec-252">Zostały one usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="852ec-252">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="852ec-253">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="852ec-253">Congratulations!</span></span> <span data-ttu-id="852ec-254">Pomyślnie skompilowano modele uczenia maszynowego na potrzeby wykrywania skoków i różnic punktów zmian w danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="852ec-254">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="852ec-255">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) .</span><span class="sxs-lookup"><span data-stu-id="852ec-255">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="852ec-256">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="852ec-256">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="852ec-257">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="852ec-257">Load the data</span></span>
> * <span data-ttu-id="852ec-258">Uczenie modelu umożliwiającego przeprowadzenie wykrywania anomalii</span><span class="sxs-lookup"><span data-stu-id="852ec-258">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="852ec-259">Wykrywaj anomalie wzrostu przy użyciu przeszkolonego modelu</span><span class="sxs-lookup"><span data-stu-id="852ec-259">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="852ec-260">Uczenie modelu wykrywania anomalii punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="852ec-260">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="852ec-261">Wykryj anomalie punktu zmiany w trybie przeszkolonym</span><span class="sxs-lookup"><span data-stu-id="852ec-261">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="852ec-262">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="852ec-262">Next steps</span></span>

<span data-ttu-id="852ec-263">Zapoznaj się z repozytorium Machine Learning przykłady w witrynie GitHub, aby poznać przykład wykrywania anomalii dotyczącego zużycia mocy.</span><span class="sxs-lookup"><span data-stu-id="852ec-263">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="852ec-264">dotnet/machinelearning — przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="852ec-264">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
