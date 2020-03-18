---
title: 'Samouczek: Wykrywanie anomalii w sprzedaży produktów'
description: Dowiedz się, jak utworzyć aplikację do wykrywania anomalii dla danych sprzedaży produktów. W tym samouczku utworzy aplikację konsoli .NET Core przy użyciu języka C# w programie Visual Studio 2019.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239992"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="64a39-104">Samouczek: Wykrywanie anomalii w sprzedaży produktów za pomocą ML.NET</span><span class="sxs-lookup"><span data-stu-id="64a39-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="64a39-105">Dowiedz się, jak utworzyć aplikację do wykrywania anomalii dla danych sprzedaży produktów.</span><span class="sxs-lookup"><span data-stu-id="64a39-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="64a39-106">Ten samouczek tworzy aplikację konsoli .NET Core przy użyciu języka C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64a39-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="64a39-107">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="64a39-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="64a39-108">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="64a39-108">Load the data</span></span>
> * <span data-ttu-id="64a39-109">Tworzenie transformacji w celu wykrywania anomalii kolec</span><span class="sxs-lookup"><span data-stu-id="64a39-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="64a39-110">Wykrywanie anomalii skokowych przy transformacji</span><span class="sxs-lookup"><span data-stu-id="64a39-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="64a39-111">Tworzenie transformacji w celu wykrywania anomalii punktu zmian</span><span class="sxs-lookup"><span data-stu-id="64a39-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="64a39-112">Wykrywanie anomalii punktu zmiany przy transformacji</span><span class="sxs-lookup"><span data-stu-id="64a39-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="64a39-113">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)</span><span class="sxs-lookup"><span data-stu-id="64a39-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64a39-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="64a39-114">Prerequisites</span></span>

* <span data-ttu-id="64a39-115">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="64a39-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="64a39-116">Zestaw danych product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="64a39-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="64a39-117">Format danych `product-sales.csv` w opiera się na zbiorze danych "Szampon sprzedaży w okresie trzech lat" pierwotnie pochodzą z DataMarket i dostarczone przez Time Series Data Library (TSDL), stworzony przez Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="64a39-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="64a39-118">"Szampon sprzedaży w okresie trzech lat" Dataset licencjonowane w ramach DataMarket Domyślna Otwarta Licencja.</span><span class="sxs-lookup"><span data-stu-id="64a39-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="64a39-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="64a39-119">Create a console application</span></span>

1. <span data-ttu-id="64a39-120">Utwórz **aplikację .NET Core Console o** nazwie "ProductSalesAnomalyDetection".</span><span class="sxs-lookup"><span data-stu-id="64a39-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="64a39-121">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="64a39-122">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="64a39-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="64a39-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="64a39-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="64a39-124">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="64a39-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="64a39-125">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="64a39-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="64a39-126">Powtórz te kroki dla **programu Microsoft.ML.TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="64a39-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="64a39-127">Dodaj następujące `using` instrukcje u góry pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="64a39-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="64a39-128">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="64a39-128">Download your data</span></span>

1. <span data-ttu-id="64a39-129">Pobierz zestaw danych i zapisz go w folderze *Data,* który został wcześniej utworzony:</span><span class="sxs-lookup"><span data-stu-id="64a39-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="64a39-130">Kliknij prawym przyciskiem myszy [*na product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) i wybierz "Zapisz link (lub target) Jako ..."</span><span class="sxs-lookup"><span data-stu-id="64a39-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="64a39-131">Upewnij się, że \*plik csv jest zapisywany w folderze \* *Dane* lub po zapisaniu go w innym miejscu, przenieś plik csv do folderu *Dane.*</span><span class="sxs-lookup"><span data-stu-id="64a39-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="64a39-132">W Eksploratorze \*rozwiązań kliknij prawym przyciskiem myszy plik csv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="64a39-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="64a39-133">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="64a39-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="64a39-134">Poniższa tabela jest podglądem \*danych z pliku csv:</span><span class="sxs-lookup"><span data-stu-id="64a39-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="64a39-135">Month</span><span class="sxs-lookup"><span data-stu-id="64a39-135">Month</span></span>  |<span data-ttu-id="64a39-136">Sprzedaż produktu</span><span class="sxs-lookup"><span data-stu-id="64a39-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="64a39-137">1-sty</span><span class="sxs-lookup"><span data-stu-id="64a39-137">1-Jan</span></span>  |    <span data-ttu-id="64a39-138">271</span><span class="sxs-lookup"><span data-stu-id="64a39-138">271</span></span>      |
|<span data-ttu-id="64a39-139">2 stycznia</span><span class="sxs-lookup"><span data-stu-id="64a39-139">2-Jan</span></span>  |    <span data-ttu-id="64a39-140">150.9</span><span class="sxs-lookup"><span data-stu-id="64a39-140">150.9</span></span>    |
|<span data-ttu-id="64a39-141">.....</span><span class="sxs-lookup"><span data-stu-id="64a39-141">.....</span></span>  |    <span data-ttu-id="64a39-142">.....</span><span class="sxs-lookup"><span data-stu-id="64a39-142">.....</span></span>    |
|<span data-ttu-id="64a39-143">1-lut</span><span class="sxs-lookup"><span data-stu-id="64a39-143">1-Feb</span></span>  |    <span data-ttu-id="64a39-144">199.3</span><span class="sxs-lookup"><span data-stu-id="64a39-144">199.3</span></span>    |
|<span data-ttu-id="64a39-145">.....</span><span class="sxs-lookup"><span data-stu-id="64a39-145">.....</span></span>  |    <span data-ttu-id="64a39-146">.....</span><span class="sxs-lookup"><span data-stu-id="64a39-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="64a39-147">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="64a39-147">Create classes and define paths</span></span>

<span data-ttu-id="64a39-148">Następnie zdefiniuj struktury danych klas wejściowych i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="64a39-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="64a39-149">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="64a39-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="64a39-150">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="64a39-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="64a39-151">W **oknie dialogowym Dodawanie nowego elementu**wybierz pozycję **Klasa** i zmień pole **Nazwa** na *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="64a39-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="64a39-152">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="64a39-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="64a39-153">Plik *ProductSalesData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="64a39-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="64a39-154">Dodaj następującą `using` instrukcję do górnej części *ProductSalesData.cs:*</span><span class="sxs-lookup"><span data-stu-id="64a39-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="64a39-155">Usuń istniejącą definicję klasy i dodaj następujący `ProductSalesData` `ProductSalesPrediction`kod, który ma dwie klasy i , do *pliku ProductSalesData.cs:*</span><span class="sxs-lookup"><span data-stu-id="64a39-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="64a39-156">`ProductSalesData`określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="64a39-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="64a39-157">[Atrybut LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny być ładowane.</span><span class="sxs-lookup"><span data-stu-id="64a39-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="64a39-158">`ProductSalesPrediction`określa klasę danych przewidywania.</span><span class="sxs-lookup"><span data-stu-id="64a39-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="64a39-159">W przypadku wykrywania anomalii przewidywanie składa się z alertu, aby wskazać, czy istnieje anomalia, wynik surowy i p-wartość.</span><span class="sxs-lookup"><span data-stu-id="64a39-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="64a39-160">Im bliżej wartość p jest 0, tym bardziej prawdopodobne anomalii wystąpił.</span><span class="sxs-lookup"><span data-stu-id="64a39-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="64a39-161">Utwórz dwa pola globalne, aby pomieścić ostatnio pobraną ścieżkę pliku zestawu danych i zapisaną ścieżkę pliku modelu:</span><span class="sxs-lookup"><span data-stu-id="64a39-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="64a39-162">`_dataPath`ma ścieżkę do zestawu danych używanego do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="64a39-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="64a39-163">`_docsize`ma liczbę rekordów w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="64a39-164">Użyjesz `_docSize` do `pvalueHistoryLength`obliczenia .</span><span class="sxs-lookup"><span data-stu-id="64a39-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="64a39-165">Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="64a39-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="64a39-166">Inicjowanie zmiennych w main</span><span class="sxs-lookup"><span data-stu-id="64a39-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="64a39-167">Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, `mlContext` aby zadeklarować i zainicjować zmienną:</span><span class="sxs-lookup"><span data-stu-id="64a39-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="64a39-168">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji `mlContext` ML.NET, a inicjowanie tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="64a39-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="64a39-169">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="64a39-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="64a39-170">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="64a39-170">Load the data</span></span>

<span data-ttu-id="64a39-171">Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="64a39-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="64a39-172">`IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="64a39-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="64a39-173">Dane mogą być ładowane z pliku tekstowego lub z innych źródeł `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.</span><span class="sxs-lookup"><span data-stu-id="64a39-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="64a39-174">Dodaj następujący kod jako następny `Main()` wiersz metody:</span><span class="sxs-lookup"><span data-stu-id="64a39-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="64a39-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku.</span><span class="sxs-lookup"><span data-stu-id="64a39-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="64a39-176">Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .</span><span class="sxs-lookup"><span data-stu-id="64a39-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="64a39-177">Wykrywanie anomalii szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="64a39-177">Time series anomaly detection</span></span>

<span data-ttu-id="64a39-178">Wykrywanie anomalii flagi nieoczekiwane lub nietypowe zdarzenia lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="64a39-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="64a39-179">Daje wskazówki, gdzie szukać problemów i pomaga odpowiedzieć na pytanie "Czy to dziwne?".</span><span class="sxs-lookup"><span data-stu-id="64a39-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Przykład wykrywania anomalii "Czy to dziwne".](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="64a39-181">Wykrywanie anomalii to proces wykrywania wartości odstających danych szeregów czasowych; punktów w danej serii czasu wprowadzania, gdzie zachowanie nie jest to, czego oczekiwano, lub "dziwne".</span><span class="sxs-lookup"><span data-stu-id="64a39-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="64a39-182">Wykrywanie anomalii może być przydatne na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="64a39-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="64a39-183">Przykład:</span><span class="sxs-lookup"><span data-stu-id="64a39-183">For instance:</span></span>

<span data-ttu-id="64a39-184">Jeśli masz samochód, możesz wiedzieć: Czy ten wskaźnik oleju jest normalny, czy też mam wyciek?</span><span class="sxs-lookup"><span data-stu-id="64a39-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="64a39-185">Jeśli monitorujesz zużycie energii, chcesz wiedzieć: Czy jest awaria?</span><span class="sxs-lookup"><span data-stu-id="64a39-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="64a39-186">Istnieją dwa typy anomalii szeregów czasowych, które można wykryć:</span><span class="sxs-lookup"><span data-stu-id="64a39-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="64a39-187">**Kolce** wskazują tymczasowe wybuchy nietypowezachowanie w systemie.</span><span class="sxs-lookup"><span data-stu-id="64a39-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="64a39-188">**Punkty zmian** wskazują początek trwałych zmian w czasie w systemie.</span><span class="sxs-lookup"><span data-stu-id="64a39-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="64a39-189">W ML.NET algorytmy wykrywania iid spike detection lub IID Change point detections nadają się do [niezależnych i identycznie rozproszonych zestawów danych.](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)</span><span class="sxs-lookup"><span data-stu-id="64a39-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="64a39-190">W przeciwieństwie do modeli w innych samouczkach, detektor anomalii szeregów czasowych przekształca się bezpośrednio na danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="64a39-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="64a39-191">Metoda `IEstimator.Fit()` nie wymaga danych szkoleniowych do produkcji transformacji.</span><span class="sxs-lookup"><span data-stu-id="64a39-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="64a39-192">Jednak musi schemat danych, który jest dostarczany przez widok danych wygenerowany `ProductSalesData`z pustej listy .</span><span class="sxs-lookup"><span data-stu-id="64a39-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="64a39-193">Będziesz analizować te same dane dotyczące sprzedaży produktów, aby wykryć skoki i punkty zmian.</span><span class="sxs-lookup"><span data-stu-id="64a39-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="64a39-194">Proces budowania i modelu szkolenia jest taki sam dla wykrywania kolców i wykrywania punktów zmiany; główną różnicą jest stosowany specyficzny algorytm wykrywania.</span><span class="sxs-lookup"><span data-stu-id="64a39-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="64a39-195">Wykrywanie kolec</span><span class="sxs-lookup"><span data-stu-id="64a39-195">Spike detection</span></span>

<span data-ttu-id="64a39-196">Celem wykrywania skoków jest zidentyfikowanie nagłych, ale tymczasowych serii, które znacznie różnią się od większości wartości danych szeregów czasowych.</span><span class="sxs-lookup"><span data-stu-id="64a39-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="64a39-197">Ważne jest, aby wykryć te podejrzane rzadkie elementy, zdarzenia lub obserwacje w odpowiednim czasie, aby zminimalizować.</span><span class="sxs-lookup"><span data-stu-id="64a39-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="64a39-198">Następujące podejście może służyć do wykrywania różnych anomalii, takich jak: awarie, cyberataki lub wirusowe treści internetowe.</span><span class="sxs-lookup"><span data-stu-id="64a39-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="64a39-199">Poniższy obraz jest przykładem skoków w zestawie danych szeregów czasowych:</span><span class="sxs-lookup"><span data-stu-id="64a39-199">The following image is an example of spikes in a time series dataset:</span></span>

![Zrzut ekranu przedstawiający dwa wykryć kolce.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="64a39-201">Dodawanie metody CreateEmptyDataView()</span><span class="sxs-lookup"><span data-stu-id="64a39-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="64a39-202">Dodaj następującą `Program.cs`metodę do:</span><span class="sxs-lookup"><span data-stu-id="64a39-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="64a39-203">Tworzy `CreateEmptyDataView()` obiekt pustego widoku danych z poprawnym schematem, `IEstimator.Fit()` który ma być używany jako dane wejściowe do metody.</span><span class="sxs-lookup"><span data-stu-id="64a39-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="64a39-204">Tworzenie metody DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="64a39-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="64a39-205">Metoda: `DetectSpike()`</span><span class="sxs-lookup"><span data-stu-id="64a39-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="64a39-206">Tworzy transformację z estymatora.</span><span class="sxs-lookup"><span data-stu-id="64a39-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="64a39-207">Wykrywa skoki na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="64a39-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="64a39-208">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="64a39-208">Displays the results.</span></span>

1. <span data-ttu-id="64a39-209">Utwórz `DetectSpike()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64a39-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="64a39-210">Użyj [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) do szkolenia modelu do wykrywania kolców.</span><span class="sxs-lookup"><span data-stu-id="64a39-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="64a39-211">Dodaj go `DetectSpike()` do metody z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64a39-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="64a39-212">Utwórz transformację wykrywania skoku, dodając następujący `DetectSpike()` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64a39-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="64a39-213">Dodaj następujący wiersz kodu, `productSales` aby przekształcić dane jako `DetectSpike()` następny wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64a39-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="64a39-214">Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do prognozowania dla wielu wierszy wejściowych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="64a39-215">Konwertuj swoje `transformedData` `IEnumerable` na silnie typizowany dla łatwiejszego wyświetlania przy użyciu [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) metody z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64a39-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="64a39-216">Utwórz wyświetloną linię <xref:System.Console.WriteLine?displayProperty=nameWithType> nagłówka przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64a39-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="64a39-217">Wyniki wykrywania skoków zostaną wyświetlone następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="64a39-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="64a39-218">`Alert`wskazuje alert skokowy dla danego punktu danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="64a39-219">`Score`jest `ProductSales` wartością dla danego punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="64a39-220">`P-Value`"P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="64a39-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="64a39-221">Im bliżej wartość p jest 0, tym bardziej prawdopodobne, punkt danych jest anomalia.</span><span class="sxs-lookup"><span data-stu-id="64a39-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="64a39-222">Użyj następującego kodu, aby `predictions` `IEnumerable` iterować i wyświetlać wyniki:</span><span class="sxs-lookup"><span data-stu-id="64a39-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="64a39-223">Dodaj wywołanie `DetectSpike()`do metody `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64a39-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="64a39-224">Wyniki wykrywania kolców</span><span class="sxs-lookup"><span data-stu-id="64a39-224">Spike detection results</span></span>

<span data-ttu-id="64a39-225">Wyniki powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="64a39-225">Your results should be similar to the following.</span></span> <span data-ttu-id="64a39-226">Podczas przetwarzania są wyświetlane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="64a39-226">During processing, messages are displayed.</span></span> <span data-ttu-id="64a39-227">Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="64a39-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="64a39-228">Niektóre komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="64a39-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="64a39-229">Wykrywanie punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="64a39-229">Change point detection</span></span>

<span data-ttu-id="64a39-230">`Change points`są trwałe zmiany w strumieniu zdarzeń szeregów czasowych dystrybucji wartości, takich jak zmiany poziomu i trendy.</span><span class="sxs-lookup"><span data-stu-id="64a39-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="64a39-231">Te trwałe zmiany trwają `spikes` znacznie dłużej niż i mogą wskazywać na katastrofalne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="64a39-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="64a39-232">`Change points`zazwyczaj nie są widoczne gołym okiem, ale mogą być wykryte w danych za pomocą metod, takich jak w poniższej metodzie.</span><span class="sxs-lookup"><span data-stu-id="64a39-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="64a39-233">Poniższy obraz jest przykładem wykrywania punktu zmiany:</span><span class="sxs-lookup"><span data-stu-id="64a39-233">The following image is an example of a change point detection:</span></span>

![Zrzut ekranu przedstawiający wykrywanie punktu zmiany.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="64a39-235">Tworzenie metody DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="64a39-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="64a39-236">Metoda `DetectChangepoint()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="64a39-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="64a39-237">Tworzy transformację z estymatora.</span><span class="sxs-lookup"><span data-stu-id="64a39-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="64a39-238">Wykrywa punkty zmian na podstawie historycznych danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="64a39-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="64a39-239">Wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="64a39-239">Displays the results.</span></span>

1. <span data-ttu-id="64a39-240">Utwórz `DetectChangepoint()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64a39-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="64a39-241">Utwórz [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) `DetectChangepoint()` w metodzie z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64a39-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="64a39-242">Podobnie jak poprzednio, utwórz transformację z estymatora, dodając następujący wiersz kodu w metodzie: `DetectChangePoint()`</span><span class="sxs-lookup"><span data-stu-id="64a39-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="64a39-243">Użyj `Transform()` metody, aby przekształcić dane, dodając `DetectChangePoint()`następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="64a39-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="64a39-244">Podobnie jak poprzednio, `transformedData` przekonwertuj swoje na silnie typizowany `IEnumerable` dla łatwiejszego `CreateEnumerable()`wyświetlania przy użyciu metody z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="64a39-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="64a39-245">Utwórz nagłówek wyświetlania z następującym kodem jako następny wiersz w metodzie: `DetectChangePoint()`</span><span class="sxs-lookup"><span data-stu-id="64a39-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="64a39-246">W wynikach wykrywania punktów zmian zostaną wyświetlone następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="64a39-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="64a39-247">`Alert`wskazuje alert punktu zmiany dla danego punktu danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="64a39-248">`Score`jest `ProductSales` wartością dla danego punktu danych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="64a39-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="64a39-249">`P-Value`"P" oznacza prawdopodobieństwo.</span><span class="sxs-lookup"><span data-stu-id="64a39-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="64a39-250">Im bliżej Wartość P jest do 0, tym bardziej prawdopodobne, punkt danych jest anomalia.</span><span class="sxs-lookup"><span data-stu-id="64a39-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="64a39-251">`Martingale value`służy do identyfikowania, jak "dziwny" jest punkt danych, na podstawie sekwencji wartości P.</span><span class="sxs-lookup"><span data-stu-id="64a39-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="64a39-252">Iteruj `predictions` `IEnumerable` i wyświetlaj wyniki za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="64a39-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="64a39-253">Dodaj następujące wywołanie `DetectChangepoint()`do `Main()` metody w metodzie:</span><span class="sxs-lookup"><span data-stu-id="64a39-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="64a39-254">Zmiana wyników wykrywania punktów</span><span class="sxs-lookup"><span data-stu-id="64a39-254">Change point detection results</span></span>

<span data-ttu-id="64a39-255">Wyniki powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="64a39-255">Your results should be similar to the following.</span></span> <span data-ttu-id="64a39-256">Podczas przetwarzania są wyświetlane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="64a39-256">During processing, messages are displayed.</span></span> <span data-ttu-id="64a39-257">Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="64a39-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="64a39-258">Niektóre wiadomości zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="64a39-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="64a39-259">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="64a39-259">Congratulations!</span></span> <span data-ttu-id="64a39-260">Teraz pomyślnie skonstruowano modele uczenia maszynowego do wykrywania skoków i anomalii punktowych zmian w danych sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="64a39-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="64a39-261">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection)</span><span class="sxs-lookup"><span data-stu-id="64a39-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="64a39-262">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="64a39-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="64a39-263">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="64a39-263">Load the data</span></span>
> * <span data-ttu-id="64a39-264">Szkolenie modelu wykrywania anomalii kolec</span><span class="sxs-lookup"><span data-stu-id="64a39-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="64a39-265">Wykrywanie anomalii kolec z uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="64a39-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="64a39-266">Szkolenie modelu wykrywania anomalii punktu zmiany</span><span class="sxs-lookup"><span data-stu-id="64a39-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="64a39-267">Wykrywanie anomalii punktu zmiany w trybie szkoleniowym</span><span class="sxs-lookup"><span data-stu-id="64a39-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="64a39-268">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="64a39-268">Next steps</span></span>

<span data-ttu-id="64a39-269">Zapoznaj się z przykładów uczenia maszynowego repozytorium GitHub do eksplorowania powody wykrywania anomalii zużycia energii.</span><span class="sxs-lookup"><span data-stu-id="64a39-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="64a39-270">dotnet/machinelearning-samples Repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="64a39-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
