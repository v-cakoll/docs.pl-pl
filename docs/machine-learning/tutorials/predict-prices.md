---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji'
description: W tym samouczku pokazano, jak utworzyć model regresji przy użyciu ML.NET do przewidywania cen, w szczególności, New York City opłat za taksówki.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 91429383341cf718d38e636bd1d71dc25d30d20d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607974"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="4d625-103">Samouczek: Przewiduj ceny za pomocą regresji z ML.NET</span><span class="sxs-lookup"><span data-stu-id="4d625-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="4d625-104">W tym samouczku pokazano, jak utworzyć [model regresji](../resources/glossary.md#regression) przy użyciu ML.NET do przewidywania cen, w szczególności, New York City opłat za taksówki.</span><span class="sxs-lookup"><span data-stu-id="4d625-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="4d625-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4d625-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4d625-106">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="4d625-107">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-107">Load and transform the data</span></span>
> * <span data-ttu-id="4d625-108">Wybieranie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="4d625-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="4d625-109">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-109">Train the model</span></span>
> * <span data-ttu-id="4d625-110">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-110">Evaluate the model</span></span>
> * <span data-ttu-id="4d625-111">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="4d625-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d625-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4d625-112">Prerequisites</span></span>

* <span data-ttu-id="4d625-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="4d625-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4d625-114">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="4d625-114">Create a console application</span></span>

1. <span data-ttu-id="4d625-115">Utwórz **aplikację konsoli .NET** Core o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="4d625-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="4d625-116">Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać zestaw danych i pliki modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="4d625-117">Zainstaluj **pakiet nuget Microsoft.ML:**</span><span class="sxs-lookup"><span data-stu-id="4d625-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="4d625-118">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4d625-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4d625-119">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**, wybierz pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="4d625-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="4d625-120">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="4d625-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="4d625-121">Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.</span><span class="sxs-lookup"><span data-stu-id="4d625-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="4d625-122">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="4d625-123">Pobierz zestawy danych [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taxi-fare-teste.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i zapisz je w folderze *Dane* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="4d625-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="4d625-124">Używamy tych zestawów danych do uczenia modelu uczenia maszynowego, a następnie oceny dokładności modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="4d625-125">Te zestawy danych pochodzą z [zestawu danych NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="4d625-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="4d625-126">W **Eksploratorze rozwiązań** \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4d625-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="4d625-127">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="4d625-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="4d625-128">Otwórz zestaw danych **taxi-fare-train.csv** i spójrz na nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="4d625-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="4d625-129">Spójrz na każdą z kolumn.</span><span class="sxs-lookup"><span data-stu-id="4d625-129">Take a look at each of the columns.</span></span> <span data-ttu-id="4d625-130">Zrozumieć dane i zdecydować, które kolumny są **funkcje,** a które jest **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="4d625-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="4d625-131">Jest `label` to kolumna, którą chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="4d625-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="4d625-132">Zidentyfikowane `Features`są dane wejściowe, które można `Label`podać model do przewidzenia .</span><span class="sxs-lookup"><span data-stu-id="4d625-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="4d625-133">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="4d625-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="4d625-134">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="4d625-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="4d625-135">**rate_code:** Rodzaj stawki podróży taksówką jest cechą.</span><span class="sxs-lookup"><span data-stu-id="4d625-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="4d625-136">**passenger_count:** Liczba pasażerów w podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="4d625-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="4d625-137">**trip_time_in_secs:** Czas podróży trwał.</span><span class="sxs-lookup"><span data-stu-id="4d625-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="4d625-138">Chcesz przewidzieć taryfę podróży przed zakończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="4d625-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="4d625-139">W tym momencie nie wiesz, jak długo potrwa podróż.</span><span class="sxs-lookup"><span data-stu-id="4d625-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="4d625-140">W związku z tym czas podróży nie jest funkcją i wykluczysz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="4d625-141">**trip_distance:** Odległość podróży jest cechą.</span><span class="sxs-lookup"><span data-stu-id="4d625-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="4d625-142">**payment_type:** Metoda płatności (gotówka lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="4d625-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="4d625-143">**fare_amount:** Całkowita opłata za przejazd taksówką jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="4d625-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="4d625-144">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="4d625-144">Create data classes</span></span>

<span data-ttu-id="4d625-145">Tworzenie klas dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="4d625-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="4d625-146">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4d625-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="4d625-147">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="4d625-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="4d625-148">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="4d625-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="4d625-149">Dodaj następujące `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="4d625-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="4d625-150">Usuń istniejącą definicję klasy i dodaj następujący `TaxiTrip` `TaxiTripFarePrediction`kod, który ma dwie klasy i , do pliku *TaxiTrip.cs:*</span><span class="sxs-lookup"><span data-stu-id="4d625-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="4d625-151">`TaxiTrip`jest klasą danych wejściowych i zawiera definicje dla każdej kolumny zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="4d625-152">Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="4d625-153">Klasa `TaxiTripFarePrediction` reprezentuje przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="4d625-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="4d625-154">Ma jedno pole float, `FareAmount`z `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowanym atrybutem.</span><span class="sxs-lookup"><span data-stu-id="4d625-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="4d625-155">W przypadku zadania regresji **wynik** kolumna zawiera przewidywane wartości etykiet.</span><span class="sxs-lookup"><span data-stu-id="4d625-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="4d625-156">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywanie.</span><span class="sxs-lookup"><span data-stu-id="4d625-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="4d625-157">Definiowanie danych i ścieżek modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-157">Define data and model paths</span></span>

<span data-ttu-id="4d625-158">Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="4d625-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="4d625-159">Aby zapisać model, należy utworzyć trzy pola, aby przytrzymać ścieżki do plików z zestawami danych i plikiem:</span><span class="sxs-lookup"><span data-stu-id="4d625-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="4d625-160">`_trainDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="4d625-161">`_testDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="4d625-162">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="4d625-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="4d625-163">Dodaj następujący kod tuż `Main` nad metodą, aby `_textLoader` określić te ścieżki i dla zmiennej:</span><span class="sxs-lookup"><span data-stu-id="4d625-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="4d625-164">Wszystkie operacje ML.NET rozpoczynają się w [klasie MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="4d625-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="4d625-165">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4d625-166">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="4d625-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="4d625-167">Inicjowanie zmiennych w trybie Głównym</span><span class="sxs-lookup"><span data-stu-id="4d625-167">Initialize variables in Main</span></span>

<span data-ttu-id="4d625-168">Zastąp `Console.WriteLine("Hello World!")` `Main` wiersz w metodzie następującym kodem, aby zadeklarować i zainicjować zmienną: `mlContext`</span><span class="sxs-lookup"><span data-stu-id="4d625-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="4d625-169">Dodaj następujące jako następny wiersz kodu `Main` w metodzie, aby wywołać `Train` metodę:</span><span class="sxs-lookup"><span data-stu-id="4d625-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="4d625-170">Metoda `Train()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4d625-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="4d625-171">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="4d625-171">Loads the data.</span></span>
* <span data-ttu-id="4d625-172">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="4d625-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="4d625-173">Trenuje model.</span><span class="sxs-lookup"><span data-stu-id="4d625-173">Trains the model.</span></span>
* <span data-ttu-id="4d625-174">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="4d625-174">Returns the model.</span></span>

<span data-ttu-id="4d625-175">Metoda `Train` trenuje model.</span><span class="sxs-lookup"><span data-stu-id="4d625-175">The `Train` method trains the model.</span></span> <span data-ttu-id="4d625-176">Utwórz tę `Main`metodę tuż poniżej , używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4d625-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="4d625-177">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-177">Load and transform data</span></span>

<span data-ttu-id="4d625-178">ML.NET używa [IDataView klasy](xref:Microsoft.ML.IDataView) jako elastyczny, skuteczny sposób opisywania danych liczbowych lub tekstowych tabelaryczne.</span><span class="sxs-lookup"><span data-stu-id="4d625-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="4d625-179">`IDataView`można załadować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika).</span><span class="sxs-lookup"><span data-stu-id="4d625-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="4d625-180">Dodaj następujący kod jako pierwszy `Train()` wiersz metody:</span><span class="sxs-lookup"><span data-stu-id="4d625-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="4d625-181">Jak chcesz przewidzieć taryfę podróży taksówką, `FareAmount` `Label` kolumna jest, że można przewidzieć (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="4d625-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="4d625-182">Użyj `CopyColumnsEstimator` klasy transformacji, `FareAmount`aby skopiować i dodać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4d625-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="4d625-183">Algorytm, który trenuje model wymaga funkcji **liczbowych,** więc trzeba przekształcić`VendorId` `RateCode`wartości `PaymentType`danych kategorii (`VendorIdEncoded`, `RateCodeEncoded`, `PaymentTypeEncoded`i ) na liczby ( , , i ).</span><span class="sxs-lookup"><span data-stu-id="4d625-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="4d625-184">Aby to zrobić, należy użyć [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn i dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4d625-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="4d625-185">Ostatni krok w przygotowaniu danych łączy wszystkie kolumny **Features** funkcji w `mlContext.Transforms.Concatenate` features kolumny przy użyciu klasy transformacji.</span><span class="sxs-lookup"><span data-stu-id="4d625-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="4d625-186">Domyślnie algorytm uczenia się przetwarza tylko funkcje z **funkcji kolumny.**</span><span class="sxs-lookup"><span data-stu-id="4d625-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="4d625-187">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4d625-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="4d625-188">Wybieranie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="4d625-188">Choose a learning algorithm</span></span>

<span data-ttu-id="4d625-189">Ten problem polega na przewidywaniu taryfy taksówką w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="4d625-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="4d625-190">Na pierwszy rzut oka może się wydawać, że zależy to po prostu od przebytej odległości.</span><span class="sxs-lookup"><span data-stu-id="4d625-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="4d625-191">Jednak sprzedawcy taksówek w Nowym Jorku pobierają różne kwoty za inne czynniki, takie jak dodatkowi pasażerowie lub płacąc kartą kredytową zamiast gotówką.</span><span class="sxs-lookup"><span data-stu-id="4d625-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="4d625-192">Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, na podstawie innych czynników w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="4d625-193">Aby to zrobić, należy wybrać zadanie uczenia maszynowego [regresji.](../resources/glossary.md#regression)</span><span class="sxs-lookup"><span data-stu-id="4d625-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="4d625-194">Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujące `Train()`elementy jako następny wiersz kodu w:</span><span class="sxs-lookup"><span data-stu-id="4d625-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="4d625-195">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-195">Train the model</span></span>

<span data-ttu-id="4d625-196">Dopasuj model `dataview` do szkolenia i zwróć przeszkolony model, `Train()` dodając następujący wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="4d625-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="4d625-197">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda trenuje modelu przez przekształcenie zestawu danych i stosowania szkolenia.</span><span class="sxs-lookup"><span data-stu-id="4d625-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="4d625-198">Zwracacie przeszkolony model z następującym `Train()` wierszem kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="4d625-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="4d625-199">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-199">Evaluate the model</span></span>

<span data-ttu-id="4d625-200">Następnie oceń wydajność modelu za pomocą danych testowych pod kątem zapewnienia jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4d625-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="4d625-201">Utwórz `Evaluate()` metodę, `Train()`zaraz po , z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="4d625-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="4d625-202">Metoda `Evaluate` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4d625-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="4d625-203">Ładuje testowy zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-203">Loads the test dataset.</span></span>
* <span data-ttu-id="4d625-204">Tworzy oceniającego regresję.</span><span class="sxs-lookup"><span data-stu-id="4d625-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="4d625-205">Ocenia model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="4d625-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="4d625-206">Wyświetla dane.</span><span class="sxs-lookup"><span data-stu-id="4d625-206">Displays the metrics.</span></span>

<span data-ttu-id="4d625-207">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `Train` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4d625-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="4d625-208">Załaduj testowy zestaw danych przy użyciu metody [LoadFromTextFile().](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)</span><span class="sxs-lookup"><span data-stu-id="4d625-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="4d625-209">Oceń model przy użyciu tego zestawu danych jako sprawdzanie `Evaluate` jakości, dodając następujący kod w metodzie:</span><span class="sxs-lookup"><span data-stu-id="4d625-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="4d625-210">Następnie przekształć `Test` dane, `Evaluate()`dodając następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="4d625-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="4d625-211">Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) tworzy prognoz dla wierszy wejściowych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="4d625-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="4d625-212">Metoda `RegressionContext.Evaluate` oblicza metryki jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="4d625-213">Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera ogólne metryki obliczone przez oceniających regresję.</span><span class="sxs-lookup"><span data-stu-id="4d625-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="4d625-214">Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki.</span><span class="sxs-lookup"><span data-stu-id="4d625-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="4d625-215">Dodaj następujący kod jako następny `Evaluate` wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="4d625-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="4d625-216">Po ustawieniu prognozowania metoda [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości `Labels` z rzeczywistym w zestawie danych testowych i zwraca metryki dotyczące wykonywania modelu.</span><span class="sxs-lookup"><span data-stu-id="4d625-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="4d625-217">Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:</span><span class="sxs-lookup"><span data-stu-id="4d625-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="4d625-218">[RSquared](../resources/glossary.md#coefficient-of-determination) jest inny metryka oceny modeli regresji.</span><span class="sxs-lookup"><span data-stu-id="4d625-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="4d625-219">RSquared przyjmuje wartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="4d625-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="4d625-220">Im bliżej jego wartości jest 1, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="4d625-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="4d625-221">Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="4d625-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="4d625-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) jest jednym z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="4d625-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="4d625-223">Im niższy, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="4d625-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="4d625-224">Dodaj następujący kod `Evaluate` do metody, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="4d625-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="4d625-225">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="4d625-225">Use the model for predictions</span></span>

<span data-ttu-id="4d625-226">Utwórz `TestSinglePrediction` metodę, zaraz `Evaluate` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4d625-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="4d625-227">Metoda `TestSinglePrediction` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4d625-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="4d625-228">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="4d625-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="4d625-229">Prognozuje kwotę taryfy na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="4d625-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="4d625-230">Łączy dane testowe i prognozy do raportowania.</span><span class="sxs-lookup"><span data-stu-id="4d625-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="4d625-231">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="4d625-231">Displays the predicted results.</span></span>

<span data-ttu-id="4d625-232">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `Evaluate` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4d625-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="4d625-233">Użyj, `PredictionEngine` aby przewidzieć taryfę, dodając `TestSinglePrediction()`następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="4d625-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="4d625-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="4d625-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="4d625-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4d625-236">Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="4d625-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="4d625-237">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d625-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="4d625-238">Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="4d625-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="4d625-239">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="4d625-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="4d625-240">W tym samouczku używa jednej podróży testowej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="4d625-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="4d625-241">Później można dodać inne scenariusze do eksperymentowania z modelem.</span><span class="sxs-lookup"><span data-stu-id="4d625-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="4d625-242">Dodaj podróż, aby przetestować przewidywanie kosztów `TestSinglePrediction()` w metodzie przez `TaxiTrip`przeszkolony model, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="4d625-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="4d625-243">Następnie należy przewidzieć taryfę na podstawie pojedynczego wystąpienia danych podróży `PredictionEngine` taksówką i przekazać ją do, `TestSinglePrediction()` dodając następujące jako następne wiersze kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="4d625-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="4d625-244">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie na jednym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="4d625-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="4d625-245">Aby wyświetlić przewidywaną taryfę określonej podróży, dodaj `TestSinglePrediction` do metody następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4d625-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="4d625-246">Uruchom program, aby zobaczyć przewidywaną taryfę taksówek dla twojego przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="4d625-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="4d625-247">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="4d625-247">Congratulations!</span></span> <span data-ttu-id="4d625-248">Teraz udało ci się stworzyć model uczenia maszynowego do przewidywania taryf za przejazd taksówką, ocenić jego dokładność i wykorzystać go do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="4d625-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="4d625-249">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub.</span><span class="sxs-lookup"><span data-stu-id="4d625-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d625-250">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4d625-250">Next steps</span></span>

<span data-ttu-id="4d625-251">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4d625-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4d625-252">Przygotowanie i zrozumienie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="4d625-253">Tworzenie potoku nauki</span><span class="sxs-lookup"><span data-stu-id="4d625-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="4d625-254">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="4d625-254">Load and transform the data</span></span>
> * <span data-ttu-id="4d625-255">Wybieranie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="4d625-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="4d625-256">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-256">Train the model</span></span>
> * <span data-ttu-id="4d625-257">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="4d625-257">Evaluate the model</span></span>
> * <span data-ttu-id="4d625-258">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="4d625-258">Use the model for predictions</span></span>

<span data-ttu-id="4d625-259">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="4d625-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4d625-260">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="4d625-260">Iris clustering</span></span>](iris-clustering.md)
