---
title: 'Samouczek: Przewidywanie ceny, używając algorytmu regresji'
description: W tym samouczku pokazano, jak do zbudowania modelu regresji przy użyciu strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.
author: jralexander
ms.author: johalex
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e46ab2ed9cace9d0769034356db425604f0ea06f
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063401"
---
# <a name="tutorial-predict-prices-using-a-regression-model-with-mlnet"></a><span data-ttu-id="a70df-103">Samouczek: Przewidywanie ceny za pomocą modelu regresji za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="a70df-103">Tutorial: Predict prices using a regression model with ML.NET</span></span>

<span data-ttu-id="a70df-104">W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu strukturze ML.NET do prognozowania cen, w szczególności taryf taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="a70df-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="a70df-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a70df-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a70df-106">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="a70df-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="a70df-107">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="a70df-107">Load and transform the data</span></span>
> * <span data-ttu-id="a70df-108">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="a70df-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="a70df-109">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-109">Train the model</span></span>
> * <span data-ttu-id="a70df-110">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-110">Evaluate the model</span></span>
> * <span data-ttu-id="a70df-111">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="a70df-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a70df-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a70df-112">Prerequisites</span></span>

* <span data-ttu-id="a70df-113">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="a70df-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a70df-114">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a70df-114">Create a console application</span></span>

1. <span data-ttu-id="a70df-115">Tworzenie **aplikacji konsoli .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="a70df-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="a70df-116">Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="a70df-117">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="a70df-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="a70df-118">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a70df-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a70df-119">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a70df-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="a70df-120">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="a70df-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a70df-121">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="a70df-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="a70df-122">Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="a70df-122">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="a70df-123">Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="a70df-123">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="a70df-124">Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="a70df-124">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="a70df-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a70df-125">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="a70df-126">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="a70df-126">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="a70df-127">Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="a70df-127">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="a70df-128">Przyjrzyj się każdej z kolumn.</span><span class="sxs-lookup"><span data-stu-id="a70df-128">Take a look at each of the columns.</span></span> <span data-ttu-id="a70df-129">Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="a70df-129">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="a70df-130">`label` Kolumna, która chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="a70df-130">The `label` is the column you want to predict.</span></span> <span data-ttu-id="a70df-131">Wskazywanego przez nią `Features`to dane wejściowe, nadaj model do przewidywania `Label`.</span><span class="sxs-lookup"><span data-stu-id="a70df-131">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="a70df-132">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="a70df-132">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="a70df-133">**vendor_id:** Identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="a70df-133">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="a70df-134">**rate_code:** Typ stawki podróży taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="a70df-134">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="a70df-135">**passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="a70df-135">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="a70df-136">**trip_time_in_secs:** Ilość czasu trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="a70df-136">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="a70df-137">Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż.</span><span class="sxs-lookup"><span data-stu-id="a70df-137">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="a70df-138">W tym momencie nie wiesz, jak długo podróży zajęłoby.</span><span class="sxs-lookup"><span data-stu-id="a70df-138">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="a70df-139">Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-139">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="a70df-140">**trip_distance:** Odległość wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="a70df-140">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="a70df-141">**payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="a70df-141">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="a70df-142">**fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.</span><span class="sxs-lookup"><span data-stu-id="a70df-142">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="a70df-143">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="a70df-143">Create data classes</span></span>

<span data-ttu-id="a70df-144">Tworzenie klasy dla danych wejściowych i prognozy są tym:</span><span class="sxs-lookup"><span data-stu-id="a70df-144">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="a70df-145">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a70df-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="a70df-146">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="a70df-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="a70df-147">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a70df-147">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="a70df-148">Dodaj następujący kod `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="a70df-148">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="a70df-149">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="a70df-149">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="a70df-150">`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-150">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="a70df-151">Użyj <xref:Microsoft.ML.Data.LoadColumnAttribute> atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-151">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="a70df-152">`TaxiTripFarePrediction` Klasa reprezentuje wyników.</span><span class="sxs-lookup"><span data-stu-id="a70df-152">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="a70df-153">Ma pola pojedynczego `FareAmount`, za pomocą `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowany.</span><span class="sxs-lookup"><span data-stu-id="a70df-153">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="a70df-154">W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.</span><span class="sxs-lookup"><span data-stu-id="a70df-154">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="a70df-155">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="a70df-155">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="a70df-156">Zdefiniować dane oraz model ścieżki</span><span class="sxs-lookup"><span data-stu-id="a70df-156">Define data and model paths</span></span>

<span data-ttu-id="a70df-157">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="a70df-157">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="a70df-158">Musisz utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="a70df-158">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="a70df-159">`_trainDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-159">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="a70df-160">`_testDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-160">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="a70df-161">`_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-161">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="a70df-162">Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="a70df-162">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="a70df-163">Wszystkie operacje strukturze ML.NET uruchomić w [klasy MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="a70df-163">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="a70df-164">Inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-164">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a70df-165">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a70df-165">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a70df-166">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="a70df-166">Initialize variables in Main</span></span>

<span data-ttu-id="a70df-167">Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować `mlContext` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="a70df-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="a70df-168">Dodaj następujący kod jako następnego wiersza kodu w `Main` metodę do wywołania `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-168">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="a70df-169">`Train()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a70df-169">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="a70df-170">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-170">Loads the data.</span></span>
* <span data-ttu-id="a70df-171">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="a70df-171">Extracts and transforms the data.</span></span>
* <span data-ttu-id="a70df-172">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-172">Trains the model.</span></span>
* <span data-ttu-id="a70df-173">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-173">Returns the model.</span></span>

<span data-ttu-id="a70df-174">`Train` Metoda szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-174">The `Train` method trains the model.</span></span> <span data-ttu-id="a70df-175">Tej metody Create, tuż poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a70df-175">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="a70df-176">Obciążenia i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="a70df-176">Load and transform data</span></span>

<span data-ttu-id="a70df-177">Używa strukturze ML.NET [klasy IDataView](xref:Microsoft.ML.IDataView) jako dane tabelaryczne numeryczny lub tekst opisujący sposób elastyczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="a70df-177">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="a70df-178">`IDataView` można załadować albo pliki tekstowe lub w czasie rzeczywistym (na przykład SQL bazy danych lub pliki dziennika).</span><span class="sxs-lookup"><span data-stu-id="a70df-178">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="a70df-179">Dodaj następujący kod jako pierwsza linia `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-179">Add the following code as the first line of the `LoadData()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="a70df-180">Do przewidywania taksówek taryfy podróży, możesz dodać dowolną `FareAmount` kolumna jest `Label` czy będzie przewidzieć (dane wyjściowe modelu) użyj `CopyColumnsEstimator` klasy przekształcenia do skopiowania `FareAmount`i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a70df-180">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="a70df-181">Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości liczb (`VendorIdEncoded`, `RateCodeEncoded`, i `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="a70df-181">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="a70df-182">Aby to zrobić, należy użyć [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) klasy transformacji, która przypisuje różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a70df-182">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="a70df-183">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `mlContext.Transforms.Concatenate` klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="a70df-183">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="a70df-184">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="a70df-184">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="a70df-185">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a70df-185">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="a70df-186">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="a70df-186">Choose a learning algorithm</span></span>

<span data-ttu-id="a70df-187">Ten problem dotyczy Prognozowanie taryfy podróży taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="a70df-187">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="a70df-188">Na pierwszy rzut oka może wydawać się po prostu zależą dystans.</span><span class="sxs-lookup"><span data-stu-id="a70df-188">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="a70df-189">Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="a70df-189">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="a70df-190">Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-190">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="a70df-191">Aby to zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.</span><span class="sxs-lookup"><span data-stu-id="a70df-191">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="a70df-192">Dołącz [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) zadania uczenia maszyny z definicjami przekształcania danych, dodając następujące jako następnego wiersza kodu w `Train()`:</span><span class="sxs-lookup"><span data-stu-id="a70df-192">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="a70df-193">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-193">Train the model</span></span>

<span data-ttu-id="a70df-194">Dopasuj do szkolenia modelu `dataview` i zwracają trenowanego modelu, dodając następujący wiersz kodu w `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-194">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="a70df-195">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="a70df-195">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="a70df-196">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-196">Evaluate the model</span></span>

<span data-ttu-id="a70df-197">Następnie ocenić wydajność modelu przy użyciu danych testowych do zapewniania jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a70df-197">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="a70df-198">Tworzenie `Evaluate()` metody tuż za `Train()`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a70df-198">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="a70df-199">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a70df-199">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="a70df-200">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a70df-200">Loads the test dataset.</span></span>
* <span data-ttu-id="a70df-201">Tworzy ewaluatora regresji.</span><span class="sxs-lookup"><span data-stu-id="a70df-201">Creates the regression evaluator.</span></span>
* <span data-ttu-id="a70df-202">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="a70df-202">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="a70df-203">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="a70df-203">Displays the metrics.</span></span>

<span data-ttu-id="a70df-204">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a70df-204">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="a70df-205">Obciążenia za pomocą zestawu danych testowych [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody.</span><span class="sxs-lookup"><span data-stu-id="a70df-205">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="a70df-206">Ocena modelu za pomocą tego zestawu danych w celu sprawdzenia jakości, dodając następujący kod w `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-206">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="a70df-207">Następnie przekształcić `Test` danych przez dodanie poniższego kodu `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="a70df-207">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="a70df-208">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody sprawia, że prognoz dotyczących testu wiersze danych wejściowych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-208">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="a70df-209">`RegressionContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-209">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="a70df-210">Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory regresji.</span><span class="sxs-lookup"><span data-stu-id="a70df-210">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="a70df-211">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="a70df-211">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="a70df-212">Dodaj następujący kod w następnym wierszu `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-212">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="a70df-213">Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` w testowego zestawu danych i zwraca metryki dotyczące jak działa model.</span><span class="sxs-lookup"><span data-stu-id="a70df-213">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="a70df-214">Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:</span><span class="sxs-lookup"><span data-stu-id="a70df-214">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="a70df-215">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji.</span><span class="sxs-lookup"><span data-stu-id="a70df-215">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="a70df-216">RSquared przyjmuje wartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="a70df-216">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="a70df-217">Im bliżej jego wartość jest bliższa 1, tym lepiej jest model.</span><span class="sxs-lookup"><span data-stu-id="a70df-217">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="a70df-218">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="a70df-218">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="a70df-219">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="a70df-219">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="a70df-220">Im niższa, w tym lepsze model jest.</span><span class="sxs-lookup"><span data-stu-id="a70df-220">The lower it is, the better the model is.</span></span> <span data-ttu-id="a70df-221">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="a70df-221">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="a70df-222">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="a70df-222">Use the model for predictions</span></span>

<span data-ttu-id="a70df-223">Tworzenie `TestSinglePrediction` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a70df-223">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="a70df-224">`TestSinglePrediction` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a70df-224">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="a70df-225">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a70df-225">Creates a single comment of test data.</span></span>
* <span data-ttu-id="a70df-226">Prognozuje kwota taryfy oparte na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a70df-226">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="a70df-227">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="a70df-227">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="a70df-228">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="a70df-228">Displays the predicted results.</span></span>

<span data-ttu-id="a70df-229">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a70df-229">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="a70df-230">Użyj `PredictionEngine` do prognozowania opłatę, dodając następujący kod do `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="a70df-230">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="a70df-231">[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać pojedyncze wystąpienie danych, a następnie wykonaj prognozę na nim.</span><span class="sxs-lookup"><span data-stu-id="a70df-231">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="a70df-232">Ten samouczek używa test dwustronnej tej klasy.</span><span class="sxs-lookup"><span data-stu-id="a70df-232">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="a70df-233">Później możesz dodać inne scenariusze, aby eksperymentować z modelu.</span><span class="sxs-lookup"><span data-stu-id="a70df-233">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="a70df-234">Dodaj podróży do testowania uczonego modelu prognozowania kosztu `TestSinglePrediction()` metody przez utworzenie wystąpienia `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="a70df-234">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="a70df-235">Następnie przewidzieć opłatę, w oparciu o jedno wystąpienie danych taksówek w podróży i przekazać go do `PredictionEngine` przez dodanie poniższego jako z następującymi wierszami kodu w `TestSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-235">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="a70df-236">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozowania w pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="a70df-236">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="a70df-237">Aby wyświetlić przewidywane opłacie określonego podróży, Dodaj następujący kod do `TestSinglePrediction` metody:</span><span class="sxs-lookup"><span data-stu-id="a70df-237">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="a70df-238">Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="a70df-238">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="a70df-239">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a70df-239">Congratulations!</span></span> <span data-ttu-id="a70df-240">Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="a70df-240">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="a70df-241">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="a70df-241">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a70df-242">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a70df-242">Next steps</span></span>

<span data-ttu-id="a70df-243">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a70df-243">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="a70df-244">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="a70df-244">Prepare and understand the data</span></span>
> * <span data-ttu-id="a70df-245">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="a70df-245">Create a learning pipeline</span></span>
> * <span data-ttu-id="a70df-246">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="a70df-246">Load and transform the data</span></span>
> * <span data-ttu-id="a70df-247">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="a70df-247">Choose a learning algorithm</span></span>
> * <span data-ttu-id="a70df-248">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-248">Train the model</span></span>
> * <span data-ttu-id="a70df-249">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="a70df-249">Evaluate the model</span></span>
> * <span data-ttu-id="a70df-250">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="a70df-250">Use the model for predictions</span></span>

<span data-ttu-id="a70df-251">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="a70df-251">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a70df-252">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="a70df-252">Iris clustering</span></span>](iris-clustering.md)
