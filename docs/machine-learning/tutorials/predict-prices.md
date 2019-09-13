---
title: 'Samouczek: Przewidywanie cen przy użyciu regresji'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: c9bf91ce5188a512524337f981366040ec09f6f6
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929449"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="2638e-103">Samouczek: Przewidywanie cen przy użyciu regresji z ML.NET</span><span class="sxs-lookup"><span data-stu-id="2638e-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="2638e-104">W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu ml.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach</span><span class="sxs-lookup"><span data-stu-id="2638e-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="2638e-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2638e-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2638e-106">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2638e-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="2638e-107">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="2638e-107">Load and transform the data</span></span>
> * <span data-ttu-id="2638e-108">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2638e-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2638e-109">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2638e-109">Train the model</span></span>
> * <span data-ttu-id="2638e-110">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2638e-110">Evaluate the model</span></span>
> * <span data-ttu-id="2638e-111">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2638e-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2638e-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2638e-112">Prerequisites</span></span>

* <span data-ttu-id="2638e-113">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2638e-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2638e-114">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="2638e-114">Create a console application</span></span>

1. <span data-ttu-id="2638e-115">Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="2638e-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="2638e-116">Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli.</span><span class="sxs-lookup"><span data-stu-id="2638e-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="2638e-117">Zainstaluj pakiet NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="2638e-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="2638e-118">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2638e-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2638e-119">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="2638e-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2638e-120">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="2638e-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="2638e-121">Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="2638e-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2638e-122">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2638e-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="2638e-123">Pobierz zestawy danych [Taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [Taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i Zapisz je w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="2638e-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="2638e-124">Te zestawy danych są używane do uczenia modelu uczenia maszynowego, a następnie szacowania dokładnego modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="2638e-125">Te zestawy danych pierwotnie pochodzą z [zestawu danych o podróży NYC TLC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="2638e-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="2638e-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy każdy z \*plików CSV i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2638e-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="2638e-127">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="2638e-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="2638e-128">Otwórz zestaw danych **Taxi-Fare-Train. csv** i sprawdź nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="2638e-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="2638e-129">Zapoznaj się z każdą kolumną.</span><span class="sxs-lookup"><span data-stu-id="2638e-129">Take a look at each of the columns.</span></span> <span data-ttu-id="2638e-130">Zrozumienie danych i decydowanie o tym, które kolumny są **funkcjami** , a które są takie same jak **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="2638e-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="2638e-131">`label` Jest to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="2638e-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="2638e-132">Identyfikowane `Features`są dane wejściowe, które dają model do `Label`przewidywania.</span><span class="sxs-lookup"><span data-stu-id="2638e-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="2638e-133">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="2638e-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="2638e-134">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="2638e-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="2638e-135">**rate_code:** Typ szybkości podróży z taksówką jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="2638e-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="2638e-136">**passenger_count:** Liczba pasażerów w podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2638e-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="2638e-137">**trip_time_in_secs:** Czas trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="2638e-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="2638e-138">Chcesz przewidzieć przejazd podróży przed ukończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="2638e-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="2638e-139">W tym momencie nie wiesz, jak długo trwa podróż.</span><span class="sxs-lookup"><span data-stu-id="2638e-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="2638e-140">W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="2638e-141">**trip_distance:** Odległość podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2638e-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="2638e-142">**payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2638e-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="2638e-143">**fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.</span><span class="sxs-lookup"><span data-stu-id="2638e-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="2638e-144">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="2638e-144">Create data classes</span></span>

<span data-ttu-id="2638e-145">Utwórz klasy dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="2638e-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="2638e-146">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="2638e-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2638e-147">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="2638e-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="2638e-148">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="2638e-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2638e-149">Dodaj następujące `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="2638e-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="2638e-150">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do pliku *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="2638e-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="2638e-151">`TaxiTrip`jest klasą danych wejściowych i zawiera definicje dla każdej z kolumn zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="2638e-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="2638e-152">Użyj atrybutu <xref:Microsoft.ML.Data.LoadColumnAttribute> , aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="2638e-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="2638e-153">`TaxiTripFarePrediction` Klasa reprezentuje przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="2638e-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="2638e-154">Ma pojedyncze pole `FareAmount`zmiennoprzecinkowe, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> z zastosowanym atrybutem.</span><span class="sxs-lookup"><span data-stu-id="2638e-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="2638e-155">W przypadku zadania regresji kolumna **oceny** zawiera wartości przewidywanych etykiet.</span><span class="sxs-lookup"><span data-stu-id="2638e-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="2638e-156">Użyj typu `float` , aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="2638e-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="2638e-157">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="2638e-157">Define data and model paths</span></span>

<span data-ttu-id="2638e-158">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2638e-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="2638e-159">Należy utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="2638e-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="2638e-160">`_trainDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="2638e-161">`_testDataPath`zawiera ścieżkę do pliku z zestawem danych używanym do szacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="2638e-162">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="2638e-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="2638e-163">Dodaj następujący kod bezpośrednio powyżej `Main` metody, aby określić te ścieżki i `_textLoader` dla zmiennej:</span><span class="sxs-lookup"><span data-stu-id="2638e-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="2638e-164">Wszystkie operacje ML.NET są uruchamiane w [klasie MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="2638e-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="2638e-165">Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2638e-166">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2638e-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2638e-167">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="2638e-167">Initialize variables in Main</span></span>

<span data-ttu-id="2638e-168">Zastąp `Main` `mlContext` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="2638e-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="2638e-169">Dodaj następujący kod jako następny wiersz kodu w `Main` metodzie, aby `Train` wywołać metodę:</span><span class="sxs-lookup"><span data-stu-id="2638e-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="2638e-170">`Train()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2638e-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="2638e-171">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="2638e-171">Loads the data.</span></span>
* <span data-ttu-id="2638e-172">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="2638e-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="2638e-173">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="2638e-173">Trains the model.</span></span>
* <span data-ttu-id="2638e-174">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="2638e-174">Returns the model.</span></span>

<span data-ttu-id="2638e-175">`Train` Metoda pociąga za niego model.</span><span class="sxs-lookup"><span data-stu-id="2638e-175">The `Train` method trains the model.</span></span> <span data-ttu-id="2638e-176">Utwórz tę metodę tuż poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2638e-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="2638e-177">Ładowanie i Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="2638e-177">Load and transform data</span></span>

<span data-ttu-id="2638e-178">ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2638e-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="2638e-179">`IDataView`może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).</span><span class="sxs-lookup"><span data-stu-id="2638e-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="2638e-180">Dodaj następujący kod jako pierwszy wiersz `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="2638e-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="2638e-181">W miarę jak ma być przewidywana taryfa za podróż `FareAmount` , kolumna `Label` jest przewidywalna (dane wyjściowe modelu), użyj `CopyColumnsEstimator` klasy transformacji do skopiowania `FareAmount`i dodania następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2638e-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="2638e-182">Algorytm, który pociąga za ten model, wymaga funkcji **liczbowych** , dlatego należy przekształcić wartości`VendorId`danych `RateCode`kategorii ( `PaymentType`, i) na liczby`VendorIdEncoded`( `RateCodeEncoded`, i `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="2638e-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="2638e-183">W tym celu należy użyć klasy transformacji [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn, a następnie Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2638e-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="2638e-184">Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu `mlContext.Transforms.Concatenate` klasy transformacji.</span><span class="sxs-lookup"><span data-stu-id="2638e-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="2638e-185">Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** .</span><span class="sxs-lookup"><span data-stu-id="2638e-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="2638e-186">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2638e-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="2638e-187">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2638e-187">Choose a learning algorithm</span></span>

<span data-ttu-id="2638e-188">Ten problem polega na przewidywaniu opłaty za podróż z taksówką w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="2638e-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="2638e-189">Na pierwszy rzut oka może wydawać się, że zależy tylko od podróży.</span><span class="sxs-lookup"><span data-stu-id="2638e-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="2638e-190">Jednak dostawcy taksówki w Nowym Jorku naliczane są różne kwoty dla innych czynników, takich jak dodatkowe pasażerowie lub płacisz kartą kredytową zamiast gotówki.</span><span class="sxs-lookup"><span data-stu-id="2638e-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="2638e-191">Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, opartą na innych czynnikach w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="2638e-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="2638e-192">W tym celu należy wybrać zadanie uczenia [maszynowego](../resources/glossary.md#regression) .</span><span class="sxs-lookup"><span data-stu-id="2638e-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="2638e-193">Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `Train()`:</span><span class="sxs-lookup"><span data-stu-id="2638e-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="2638e-194">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2638e-194">Train the model</span></span>

<span data-ttu-id="2638e-195">Dopasuj model do szkolenia `dataview` i zwróć przeszkolony model, dodając następujący wiersz kodu `Train()` do metody:</span><span class="sxs-lookup"><span data-stu-id="2638e-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="2638e-196">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="2638e-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="2638e-197">Zwróć przeszkolony model z następującym wierszem kodu w `Train()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="2638e-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="2638e-198">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2638e-198">Evaluate the model</span></span>

<span data-ttu-id="2638e-199">Następnie Oceń wydajność modelu z danymi testowymi w celu zapewnienia jakości i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="2638e-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="2638e-200">Utwórz metodę, tuż po `Train()`, przy użyciu następującego kodu: `Evaluate()`</span><span class="sxs-lookup"><span data-stu-id="2638e-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="2638e-201">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2638e-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="2638e-202">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2638e-202">Loads the test dataset.</span></span>
* <span data-ttu-id="2638e-203">Tworzy ewaluatora regresji.</span><span class="sxs-lookup"><span data-stu-id="2638e-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="2638e-204">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="2638e-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="2638e-205">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="2638e-205">Displays the metrics.</span></span>

<span data-ttu-id="2638e-206">Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `Train` pod wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2638e-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="2638e-207">Załaduj zestaw danych testowych przy użyciu metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .</span><span class="sxs-lookup"><span data-stu-id="2638e-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="2638e-208">Oceń model przy użyciu tego zestawu danych jako sprawdzenie jakości, dodając następujący kod w `Evaluate` metodzie:</span><span class="sxs-lookup"><span data-stu-id="2638e-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="2638e-209">Następnie Przekształć `Test` dane, dodając następujący kod do `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="2638e-209">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="2638e-210">Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) umożliwia prognozowanie wierszy wejściowych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2638e-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="2638e-211">Metoda oblicza metryki jakości `PredictionModel` dla użycia określonego zestawu danych. `RegressionContext.Evaluate`</span><span class="sxs-lookup"><span data-stu-id="2638e-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="2638e-212">Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera ogólne metryki obliczone przez oszacowania regresji.</span><span class="sxs-lookup"><span data-stu-id="2638e-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="2638e-213">Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki.</span><span class="sxs-lookup"><span data-stu-id="2638e-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="2638e-214">Dodaj następujący kod w następnym wierszu `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="2638e-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="2638e-215">Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowanym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.</span><span class="sxs-lookup"><span data-stu-id="2638e-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="2638e-216">Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:</span><span class="sxs-lookup"><span data-stu-id="2638e-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="2638e-217">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metryką oceny dla modeli regresji.</span><span class="sxs-lookup"><span data-stu-id="2638e-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="2638e-218">RSquared przyjmuje wartości z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2638e-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="2638e-219">Im bliżej wartości jest 1, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="2638e-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="2638e-220">Dodaj następujący kod do `Evaluate` metody, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="2638e-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="2638e-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="2638e-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="2638e-222">Im niższa wartość, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="2638e-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="2638e-223">Dodaj następujący kod do `Evaluate` metody, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="2638e-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="2638e-224">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2638e-224">Use the model for predictions</span></span>

<span data-ttu-id="2638e-225">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Evaluate` `TestSinglePrediction`</span><span class="sxs-lookup"><span data-stu-id="2638e-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="2638e-226">`TestSinglePrediction` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2638e-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="2638e-227">Tworzy pojedynczy komentarz dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2638e-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="2638e-228">Przewiduje wartość opłaty za przejazd na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2638e-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="2638e-229">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="2638e-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="2638e-230">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="2638e-230">Displays the predicted results.</span></span>

<span data-ttu-id="2638e-231">Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `Evaluate` pod wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2638e-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="2638e-232">Użyj do przewidywania taryfy, dodając następujący kod do `TestSinglePrediction()`: `PredictionEngine`</span><span class="sxs-lookup"><span data-stu-id="2638e-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="2638e-233">[Klasa PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia przekazywanie pojedynczej instancji danych, a następnie przeprowadza prognozowanie.</span><span class="sxs-lookup"><span data-stu-id="2638e-233">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="2638e-234">Ten samouczek używa jednej podróży testowej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="2638e-234">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="2638e-235">Później możesz dodać inne scenariusze, aby eksperymentować z modelem.</span><span class="sxs-lookup"><span data-stu-id="2638e-235">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="2638e-236">Dodaj podróż, aby przetestować przeszkolony model kosztów w `TestSinglePrediction()` metodzie, tworząc `TaxiTrip`wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="2638e-236">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="2638e-237">Następnie należy przewidzieć opłaty za pośrednictwem jednego wystąpienia danych podróży z taksówką i przekazać je do programu `PredictionEngine` , dodając następujące elementy jako kolejne wiersze kodu `TestSinglePrediction()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="2638e-237">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="2638e-238">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="2638e-238">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="2638e-239">Aby wyświetlić przewidywaną opłatę za określoną podróż, Dodaj następujący kod do `TestSinglePrediction` metody:</span><span class="sxs-lookup"><span data-stu-id="2638e-239">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="2638e-240">Uruchom program, aby zobaczyć przewidywalną opłatę za taksówkę w przypadku testowym.</span><span class="sxs-lookup"><span data-stu-id="2638e-240">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="2638e-241">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="2638e-241">Congratulations!</span></span> <span data-ttu-id="2638e-242">Pomyślnie skompilowano model uczenia maszynowego na potrzeby przewidywania opłat za podróż z użyciem taksówki, oceny jego dokładności i używania go do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="2638e-242">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="2638e-243">Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) .</span><span class="sxs-lookup"><span data-stu-id="2638e-243">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2638e-244">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2638e-244">Next steps</span></span>

<span data-ttu-id="2638e-245">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2638e-245">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="2638e-246">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2638e-246">Prepare and understand the data</span></span>
> * <span data-ttu-id="2638e-247">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="2638e-247">Create a learning pipeline</span></span>
> * <span data-ttu-id="2638e-248">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="2638e-248">Load and transform the data</span></span>
> * <span data-ttu-id="2638e-249">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2638e-249">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2638e-250">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2638e-250">Train the model</span></span>
> * <span data-ttu-id="2638e-251">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2638e-251">Evaluate the model</span></span>
> * <span data-ttu-id="2638e-252">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2638e-252">Use the model for predictions</span></span>

<span data-ttu-id="2638e-253">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="2638e-253">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2638e-254">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="2638e-254">Iris clustering</span></span>](iris-clustering.md)
