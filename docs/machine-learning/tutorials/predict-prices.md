---
title: 'Samouczek: prognozowanie cen przy użyciu regresji'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 51617d14e84fa46464d7b44dbdb20afaf196924f
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957384"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="fe29b-103">Samouczek: prognozowanie cen przy użyciu regresji z ML.NET</span><span class="sxs-lookup"><span data-stu-id="fe29b-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="fe29b-104">W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu ml.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach</span><span class="sxs-lookup"><span data-stu-id="fe29b-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="fe29b-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe29b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fe29b-106">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="fe29b-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="fe29b-107">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="fe29b-107">Load and transform the data</span></span>
> * <span data-ttu-id="fe29b-108">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="fe29b-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="fe29b-109">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="fe29b-109">Train the model</span></span>
> * <span data-ttu-id="fe29b-110">Oceń model</span><span class="sxs-lookup"><span data-stu-id="fe29b-110">Evaluate the model</span></span>
> * <span data-ttu-id="fe29b-111">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="fe29b-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe29b-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fe29b-112">Prerequisites</span></span>

* <span data-ttu-id="fe29b-113">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe29b-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="fe29b-114">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="fe29b-114">Create a console application</span></span>

1. <span data-ttu-id="fe29b-115">Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="fe29b-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="fe29b-116">Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli.</span><span class="sxs-lookup"><span data-stu-id="fe29b-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="fe29b-117">Zainstaluj pakiet NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="fe29b-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="fe29b-118">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fe29b-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fe29b-119">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="fe29b-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="fe29b-120">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="fe29b-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="fe29b-121">Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="fe29b-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="fe29b-122">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="fe29b-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="fe29b-123">Pobierz zestawy danych [Taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [Taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i Zapisz je w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="fe29b-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="fe29b-124">Te zestawy danych są używane do uczenia modelu uczenia maszynowego, a następnie szacowania dokładnego modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="fe29b-125">Te zestawy danych pierwotnie pochodzą z [zestawu danych o podróży NYC TLC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="fe29b-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="fe29b-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy każdy plik @no__t -1. csv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fe29b-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="fe29b-127">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="fe29b-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="fe29b-128">Otwórz zestaw danych **Taxi-Fare-Train. csv** i sprawdź nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="fe29b-129">Zapoznaj się z każdą kolumną.</span><span class="sxs-lookup"><span data-stu-id="fe29b-129">Take a look at each of the columns.</span></span> <span data-ttu-id="fe29b-130">Zrozumienie danych i decydowanie o tym, które kolumny są **funkcjami** , a które są takie same jak **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="fe29b-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="fe29b-131">@No__t-0 to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="fe29b-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="fe29b-132">Zidentyfikowany `Features`are dane wejściowe, które dają model do przewidywania `Label`.</span><span class="sxs-lookup"><span data-stu-id="fe29b-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="fe29b-133">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="fe29b-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="fe29b-134">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="fe29b-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="fe29b-135">**rate_code:** Typ szybkości podróży z taksówką jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="fe29b-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="fe29b-136">**passenger_count:** Liczba pasażerów w podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="fe29b-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="fe29b-137">**trip_time_in_secs:** Czas trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="fe29b-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="fe29b-138">Chcesz przewidzieć przejazd podróży przed ukończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="fe29b-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="fe29b-139">W tym momencie nie wiesz, jak długo trwa podróż.</span><span class="sxs-lookup"><span data-stu-id="fe29b-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="fe29b-140">W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="fe29b-141">**trip_distance:** Odległość podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="fe29b-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="fe29b-142">**payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.</span><span class="sxs-lookup"><span data-stu-id="fe29b-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="fe29b-143">**fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.</span><span class="sxs-lookup"><span data-stu-id="fe29b-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="fe29b-144">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="fe29b-144">Create data classes</span></span>

<span data-ttu-id="fe29b-145">Utwórz klasy dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="fe29b-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="fe29b-146">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="fe29b-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="fe29b-147">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="fe29b-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="fe29b-148">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="fe29b-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="fe29b-149">Dodaj następujące dyrektywy `using` do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="fe29b-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="fe29b-150">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction` do pliku *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="fe29b-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="fe29b-151">`TaxiTrip` jest klasą danych wejściowych i zawiera definicje dla każdej z kolumn zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="fe29b-152">Użyj atrybutu <xref:Microsoft.ML.Data.LoadColumnAttribute>, aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="fe29b-153">Klasa `TaxiTripFarePrediction` reprezentuje przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="fe29b-154">Ma pojedyncze pole zmiennoprzecinkowe `FareAmount` z zastosowanym atrybutem `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fe29b-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="fe29b-155">W przypadku zadania regresji kolumna **oceny** zawiera wartości przewidywanych etykiet.</span><span class="sxs-lookup"><span data-stu-id="fe29b-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="fe29b-156">Użyj typu `float`, aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="fe29b-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="fe29b-157">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="fe29b-157">Define data and model paths</span></span>

<span data-ttu-id="fe29b-158">Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="fe29b-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="fe29b-159">Należy utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="fe29b-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="fe29b-160">`_trainDataPath` zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="fe29b-161">`_testDataPath` zawiera ścieżkę do pliku z zestawem danych używanym do szacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="fe29b-162">`_modelPath` zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="fe29b-163">Dodaj następujący kod bezpośrednio powyżej metody `Main`, aby określić te ścieżki i dla zmiennej `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="fe29b-164">Wszystkie operacje ML.NET są uruchamiane w [klasie MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="fe29b-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="fe29b-165">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fe29b-166">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fe29b-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="fe29b-167">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="fe29b-167">Initialize variables in Main</span></span>

<span data-ttu-id="fe29b-168">Zastąp wiersz `Console.WriteLine("Hello World!")` w metodzie `Main` następującym kodem, aby zadeklarować i zainicjować zmienną `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="fe29b-169">Dodaj następujący kod jako następny wiersz kodu w metodzie `Main`, aby wywołać metodę `Train`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="fe29b-170">Metoda `Train()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fe29b-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="fe29b-171">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="fe29b-171">Loads the data.</span></span>
* <span data-ttu-id="fe29b-172">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="fe29b-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="fe29b-173">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-173">Trains the model.</span></span>
* <span data-ttu-id="fe29b-174">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-174">Returns the model.</span></span>

<span data-ttu-id="fe29b-175">Metoda `Train` pociąga za model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-175">The `Train` method trains the model.</span></span> <span data-ttu-id="fe29b-176">Utwórz tę metodę tuż poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="fe29b-177">Ładowanie i Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="fe29b-177">Load and transform data</span></span>

<span data-ttu-id="fe29b-178">ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="fe29b-179">`IDataView` może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).</span><span class="sxs-lookup"><span data-stu-id="fe29b-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="fe29b-180">Dodaj następujący kod jako pierwszy wiersz metody `Train()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="fe29b-181">W miarę jak ma być przewidywana taryfa za podróż, kolumna `FareAmount` jest `Label`, który będzie przewidywalna (dane wyjściowe modelu), użyj klasy transformacji `CopyColumnsEstimator` w celu skopiowania `FareAmount` i dodania następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="fe29b-182">Algorytm, który pociąga za ten model, wymaga funkcji **liczbowych** , dlatego należy przekształcić wartości kategorii (`VendorId`, `RateCode` i `PaymentType`) na liczby (`VendorIdEncoded`, `RateCodeEncoded` i `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="fe29b-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="fe29b-183">W tym celu należy użyć klasy transformacji [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn, a następnie Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="fe29b-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="fe29b-184">Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu klasy transformacji `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="fe29b-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="fe29b-185">Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** .</span><span class="sxs-lookup"><span data-stu-id="fe29b-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="fe29b-186">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="fe29b-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="fe29b-187">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="fe29b-187">Choose a learning algorithm</span></span>

<span data-ttu-id="fe29b-188">Ten problem polega na przewidywaniu opłaty za podróż z taksówką w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="fe29b-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="fe29b-189">Na pierwszy rzut oka może wydawać się, że zależy tylko od podróży.</span><span class="sxs-lookup"><span data-stu-id="fe29b-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="fe29b-190">Jednak dostawcy taksówki w Nowym Jorku naliczane są różne kwoty dla innych czynników, takich jak dodatkowe pasażerowie lub płacisz kartą kredytową zamiast gotówki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="fe29b-191">Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, opartą na innych czynnikach w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="fe29b-192">W tym celu należy wybrać zadanie uczenia [maszynowego](../resources/glossary.md#regression) .</span><span class="sxs-lookup"><span data-stu-id="fe29b-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="fe29b-193">Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `Train()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="fe29b-194">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="fe29b-194">Train the model</span></span>

<span data-ttu-id="fe29b-195">Dopasuj model do szkolenia `dataview` i zwróć przeszkolony model, dodając następujący wiersz kodu do metody `Train()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="fe29b-196">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="fe29b-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="fe29b-197">Zwróć przeszkolony model z następującym wierszem kodu w metodzie `Train()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="fe29b-198">Oceń model</span><span class="sxs-lookup"><span data-stu-id="fe29b-198">Evaluate the model</span></span>

<span data-ttu-id="fe29b-199">Następnie Oceń wydajność modelu z danymi testowymi w celu zapewnienia jakości i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="fe29b-200">Utwórz metodę `Evaluate()` zaraz po `Train()`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="fe29b-201">Metoda `Evaluate` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fe29b-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="fe29b-202">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-202">Loads the test dataset.</span></span>
* <span data-ttu-id="fe29b-203">Tworzy ewaluatora regresji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="fe29b-204">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="fe29b-205">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-205">Displays the metrics.</span></span>

<span data-ttu-id="fe29b-206">Dodaj wywołanie do nowej metody z metody `Main` bezpośrednio w wywołaniu metody `Train` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="fe29b-207">Załaduj zestaw danych testowych przy użyciu metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .</span><span class="sxs-lookup"><span data-stu-id="fe29b-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="fe29b-208">Oceń model przy użyciu tego zestawu danych jako sprawdzenie jakości, dodając następujący kod w metodzie `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="fe29b-209">Następnie Przekształć dane `Test`, dodając następujący kod do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-209">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="fe29b-210">Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) umożliwia prognozowanie wierszy wejściowych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="fe29b-211">Metoda `RegressionContext.Evaluate` oblicza metryki jakości dla `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="fe29b-212">Zwraca obiekt <xref:Microsoft.ML.Data.RegressionMetrics>, który zawiera ogólne metryki obliczone przez oszacowania regresji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="fe29b-213">Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="fe29b-214">Dodaj następujący kod jako następny wiersz w metodzie `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="fe29b-215">Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z rzeczywistym `Labels` w testowym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="fe29b-216">Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:</span><span class="sxs-lookup"><span data-stu-id="fe29b-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="fe29b-217">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metryką oceny dla modeli regresji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="fe29b-218">RSquared przyjmuje wartości z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="fe29b-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="fe29b-219">Im bliżej wartości jest 1, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="fe29b-220">Dodaj następujący kod do metody `Evaluate`, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="fe29b-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="fe29b-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="fe29b-222">Im niższa wartość, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="fe29b-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="fe29b-223">Dodaj następujący kod do metody `Evaluate`, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="fe29b-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="fe29b-224">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="fe29b-224">Use the model for predictions</span></span>

<span data-ttu-id="fe29b-225">Utwórz metodę `TestSinglePrediction` zaraz po metodzie `Evaluate` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="fe29b-226">Metoda `TestSinglePrediction` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fe29b-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="fe29b-227">Tworzy pojedynczy komentarz dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="fe29b-228">Przewiduje wartość opłaty za przejazd na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="fe29b-229">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="fe29b-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="fe29b-230">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="fe29b-230">Displays the predicted results.</span></span>

<span data-ttu-id="fe29b-231">Dodaj wywołanie do nowej metody z metody `Main` bezpośrednio w wywołaniu metody `Evaluate` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fe29b-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="fe29b-232">Użyj `PredictionEngine` do przewidywania taryfy, dodając następujący kod do `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="fe29b-233">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-233">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="fe29b-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="fe29b-234">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="fe29b-235">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-235">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="fe29b-236">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe29b-236">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="fe29b-237">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="fe29b-237">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="fe29b-238">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="fe29b-238">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="fe29b-239">Ten samouczek używa jednej podróży testowej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="fe29b-239">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="fe29b-240">Później możesz dodać inne scenariusze, aby eksperymentować z modelem.</span><span class="sxs-lookup"><span data-stu-id="fe29b-240">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="fe29b-241">Dodaj podróż w celu przetestowania przeszkolonego modelu kosztów w metodzie `TestSinglePrediction()` przez utworzenie wystąpienia `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-241">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="fe29b-242">Następnie należy przewidzieć opłaty za pośrednictwem jednego wystąpienia danych podróży z taksówką i przekazać je do `PredictionEngine` przez dodanie następujących elementów jako następnych wierszy kodu w metodzie `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-242">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="fe29b-243">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="fe29b-243">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="fe29b-244">Aby wyświetlić przewidywaną opłatę za określoną podróż, Dodaj następujący kod do metody `TestSinglePrediction`:</span><span class="sxs-lookup"><span data-stu-id="fe29b-244">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="fe29b-245">Uruchom program, aby zobaczyć przewidywalną opłatę za taksówkę w przypadku testowym.</span><span class="sxs-lookup"><span data-stu-id="fe29b-245">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="fe29b-246">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="fe29b-246">Congratulations!</span></span> <span data-ttu-id="fe29b-247">Pomyślnie skompilowano model uczenia maszynowego na potrzeby przewidywania opłat za podróż z użyciem taksówki, oceny jego dokładności i używania go do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="fe29b-247">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="fe29b-248">Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) .</span><span class="sxs-lookup"><span data-stu-id="fe29b-248">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fe29b-249">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fe29b-249">Next steps</span></span>

<span data-ttu-id="fe29b-250">W tym samouczku przedstawiono sposób wykonywania tych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="fe29b-250">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="fe29b-251">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="fe29b-251">Prepare and understand the data</span></span>
> * <span data-ttu-id="fe29b-252">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="fe29b-252">Create a learning pipeline</span></span>
> * <span data-ttu-id="fe29b-253">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="fe29b-253">Load and transform the data</span></span>
> * <span data-ttu-id="fe29b-254">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="fe29b-254">Choose a learning algorithm</span></span>
> * <span data-ttu-id="fe29b-255">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="fe29b-255">Train the model</span></span>
> * <span data-ttu-id="fe29b-256">Oceń model</span><span class="sxs-lookup"><span data-stu-id="fe29b-256">Evaluate the model</span></span>
> * <span data-ttu-id="fe29b-257">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="fe29b-257">Use the model for predictions</span></span>

<span data-ttu-id="fe29b-258">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="fe29b-258">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fe29b-259">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="fe29b-259">Iris clustering</span></span>](iris-clustering.md)
