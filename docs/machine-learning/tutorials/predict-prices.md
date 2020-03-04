---
title: 'Samouczek: prognozowanie cen przy użyciu regresji'
description: W tym samouczku przedstawiono sposób tworzenia modelu regresji przy użyciu ML.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 51cef97178c2dbc6a5b572a7045bdad4bc382ba0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240990"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="2f981-103">Samouczek: prognozowanie cen przy użyciu regresji z ML.NET</span><span class="sxs-lookup"><span data-stu-id="2f981-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="2f981-104">W tym samouczku przedstawiono sposób tworzenia [modelu regresji](../resources/glossary.md#regression) przy użyciu ml.NET do przewidywania cen, w oddziałach, w oddziałach, w oddziałach</span><span class="sxs-lookup"><span data-stu-id="2f981-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="2f981-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2f981-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2f981-106">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2f981-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="2f981-107">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="2f981-107">Load and transform the data</span></span>
> * <span data-ttu-id="2f981-108">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2f981-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2f981-109">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2f981-109">Train the model</span></span>
> * <span data-ttu-id="2f981-110">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2f981-110">Evaluate the model</span></span>
> * <span data-ttu-id="2f981-111">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2f981-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f981-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2f981-112">Prerequisites</span></span>

* <span data-ttu-id="2f981-113">[Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core".</span><span class="sxs-lookup"><span data-stu-id="2f981-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2f981-114">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="2f981-114">Create a console application</span></span>

1. <span data-ttu-id="2f981-115">Utwórz **aplikację konsolową .NET Core** o nazwie "TaxiFarePrediction".</span><span class="sxs-lookup"><span data-stu-id="2f981-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="2f981-116">Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli.</span><span class="sxs-lookup"><span data-stu-id="2f981-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="2f981-117">Zainstaluj pakiet NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="2f981-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="2f981-118">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2f981-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2f981-119">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="2f981-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2f981-120">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="2f981-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="2f981-121">Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="2f981-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2f981-122">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2f981-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="2f981-123">Pobierz zestawy danych [Taxi-Fare-Train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [Taxi-Fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) i Zapisz je w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="2f981-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="2f981-124">Te zestawy danych są używane do uczenia modelu uczenia maszynowego, a następnie szacowania dokładnego modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="2f981-125">Te zestawy danych pierwotnie pochodzą z [zestawu danych o podróży NYC TLC](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="2f981-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="2f981-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy każdy z plików \*. csv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2f981-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="2f981-127">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="2f981-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="2f981-128">Otwórz zestaw danych **Taxi-Fare-Train. csv** i sprawdź nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="2f981-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="2f981-129">Zapoznaj się z każdą kolumną.</span><span class="sxs-lookup"><span data-stu-id="2f981-129">Take a look at each of the columns.</span></span> <span data-ttu-id="2f981-130">Zrozumienie danych i decydowanie o tym, które kolumny są **funkcjami** , a które są takie same jak **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="2f981-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="2f981-131">`label` to kolumna, która ma zostać przewidywalna.</span><span class="sxs-lookup"><span data-stu-id="2f981-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="2f981-132">Zidentyfikowane `Features`są danymi wejściowymi, które umożliwiają modelowi przewidywanie `Label`.</span><span class="sxs-lookup"><span data-stu-id="2f981-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="2f981-133">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="2f981-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="2f981-134">**vendor_id:** Identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="2f981-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="2f981-135">**rate_code:** Typ szybkości podróży z taksówką jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="2f981-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="2f981-136">**passenger_count:** Liczba pasażerów w podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2f981-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="2f981-137">**trip_time_in_secs:** Czas trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="2f981-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="2f981-138">Chcesz przewidzieć przejazd podróży przed ukończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="2f981-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="2f981-139">W tej chwili nie wiesz, jak długo trwa podróż.</span><span class="sxs-lookup"><span data-stu-id="2f981-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="2f981-140">W ten sposób czas podróży nie jest funkcją, a ta kolumna zostanie wykluczona z modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="2f981-141">**trip_distance:** Odległość podróży to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2f981-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="2f981-142">**payment_type:** Forma płatności (karta kasowa lub kredytowa) to funkcja.</span><span class="sxs-lookup"><span data-stu-id="2f981-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="2f981-143">**fare_amount:** Łączna liczba płatnych opłat za taksówkę to etykieta.</span><span class="sxs-lookup"><span data-stu-id="2f981-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="2f981-144">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="2f981-144">Create data classes</span></span>

<span data-ttu-id="2f981-145">Utwórz klasy dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="2f981-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="2f981-146">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="2f981-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2f981-147">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f981-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="2f981-148">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="2f981-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2f981-149">Dodaj następujące dyrektywy `using` do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="2f981-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="2f981-150">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do pliku *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="2f981-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="2f981-151">`TaxiTrip` jest klasą danych wejściowych i zawiera definicje dla każdej z kolumn zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="2f981-152">Użyj atrybutu <xref:Microsoft.ML.Data.LoadColumnAttribute>, aby określić indeksy kolumn źródłowych w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="2f981-153">Klasa `TaxiTripFarePrediction` reprezentuje przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="2f981-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="2f981-154">Ma pojedyncze pole zmiennoprzecinkowe `FareAmount`z zastosowanym atrybutem `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2f981-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="2f981-155">W przypadku zadania regresji kolumna **Score** zawiera wartości przewidywanych etykiet.</span><span class="sxs-lookup"><span data-stu-id="2f981-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="2f981-156">Użyj typu `float`, aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="2f981-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="2f981-157">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="2f981-157">Define data and model paths</span></span>

<span data-ttu-id="2f981-158">Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2f981-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="2f981-159">Należy utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="2f981-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="2f981-160">`_trainDataPath` zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="2f981-161">`_testDataPath` zawiera ścieżkę do pliku z zestawem danych używanym do szacowania modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="2f981-162">`_modelPath` zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="2f981-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="2f981-163">Dodaj następujący kod bezpośrednio powyżej metody `Main`, aby określić te ścieżki i dla zmiennej `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="2f981-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="2f981-164">Wszystkie operacje ML.NET są uruchamiane w [klasie MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="2f981-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="2f981-165">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2f981-166">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2f981-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2f981-167">Inicjuj zmienne w głównym</span><span class="sxs-lookup"><span data-stu-id="2f981-167">Initialize variables in Main</span></span>

<span data-ttu-id="2f981-168">Zastąp wiersz `Console.WriteLine("Hello World!")` w metodzie `Main` następującym kodem, aby zadeklarować i zainicjować zmienną `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="2f981-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="2f981-169">Dodaj następujący kod jako następny wiersz kodu w metodzie `Main`, aby wywołać metodę `Train`:</span><span class="sxs-lookup"><span data-stu-id="2f981-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="2f981-170">Metoda `Train()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2f981-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="2f981-171">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="2f981-171">Loads the data.</span></span>
* <span data-ttu-id="2f981-172">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="2f981-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="2f981-173">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="2f981-173">Trains the model.</span></span>
* <span data-ttu-id="2f981-174">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="2f981-174">Returns the model.</span></span>

<span data-ttu-id="2f981-175">Metoda `Train` przeciąga model.</span><span class="sxs-lookup"><span data-stu-id="2f981-175">The `Train` method trains the model.</span></span> <span data-ttu-id="2f981-176">Utwórz tę metodę tuż poniżej `Main`przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f981-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="2f981-177">Ładowanie i Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="2f981-177">Load and transform data</span></span>

<span data-ttu-id="2f981-178">ML.NET używa [klasy IDataView](xref:Microsoft.ML.IDataView) jako elastycznej, wydajnej metody opisywania danych tabelarycznych lub tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="2f981-179">`IDataView` może ładować pliki tekstowe lub w czasie rzeczywistym (na przykład bazy danych SQL lub pliki dzienników).</span><span class="sxs-lookup"><span data-stu-id="2f981-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="2f981-180">Dodaj następujący kod jako pierwszy wiersz metody `Train()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="2f981-181">W miarę jak ma być przewidywana taryfa za podróż, kolumna `FareAmount` jest `Label`, który zostanie przewidywalny (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="2f981-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="2f981-182">Użyj klasy transformacji `CopyColumnsEstimator`, aby skopiować `FareAmount`, i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2f981-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="2f981-183">Algorytm łączący model wymaga funkcji **liczbowych** , dlatego należy przekształcić wartości kategorii (`VendorId`, `RateCode`i `PaymentType`) na liczby (`VendorIdEncoded`, `RateCodeEncoded`i `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="2f981-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="2f981-184">W tym celu należy użyć klasy transformacji [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) , która przypisuje różne wartości klucza liczbowego do różnych wartości w każdej z kolumn, a następnie Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2f981-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="2f981-185">Ostatnim krokiem w przygotowaniu danych jest połączenie wszystkich kolumn funkcji w kolumnie **funkcje** przy użyciu klasy transformacji `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="2f981-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="2f981-186">Domyślnie algorytm uczenia przetwarza tylko funkcje z kolumny **Features** .</span><span class="sxs-lookup"><span data-stu-id="2f981-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="2f981-187">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2f981-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="2f981-188">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2f981-188">Choose a learning algorithm</span></span>

<span data-ttu-id="2f981-189">Ten problem polega na przewidywaniu opłaty za podróż z taksówką w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="2f981-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="2f981-190">Na pierwszy rzut oka może wydawać się, że zależy tylko od podróży.</span><span class="sxs-lookup"><span data-stu-id="2f981-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="2f981-191">Jednak dostawcy taksówki w Nowym Jorku naliczane są różne kwoty dla innych czynników, takich jak dodatkowe pasażerowie lub płacisz kartą kredytową zamiast gotówki.</span><span class="sxs-lookup"><span data-stu-id="2f981-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="2f981-192">Chcesz przewidzieć wartość ceny, która jest wartością rzeczywistą, opartą na innych czynnikach w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="2f981-193">W tym celu należy wybrać zadanie uczenia [maszynowego](../resources/glossary.md#regression) .</span><span class="sxs-lookup"><span data-stu-id="2f981-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="2f981-194">Dołącz zadanie uczenia maszynowego [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `Train()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="2f981-195">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2f981-195">Train the model</span></span>

<span data-ttu-id="2f981-196">Dopasuj model do `dataview` szkoleniowego i zwróć przeszkolony model, dodając następujący wiersz kodu do metody `Train()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="2f981-197">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="2f981-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="2f981-198">Zwróć przeszkolony model z następującym wierszem kodu w metodzie `Train()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="2f981-199">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2f981-199">Evaluate the model</span></span>

<span data-ttu-id="2f981-200">Następnie Oceń wydajność modelu z danymi testowymi w celu zapewnienia jakości i weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="2f981-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="2f981-201">Utwórz metodę `Evaluate()`, zaraz po `Train()`, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f981-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="2f981-202">Metoda `Evaluate` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2f981-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="2f981-203">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-203">Loads the test dataset.</span></span>
* <span data-ttu-id="2f981-204">Tworzy ewaluatora regresji.</span><span class="sxs-lookup"><span data-stu-id="2f981-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="2f981-205">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="2f981-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="2f981-206">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="2f981-206">Displays the metrics.</span></span>

<span data-ttu-id="2f981-207">Dodaj wywołanie do nowej metody z metody `Main`, bezpośrednio pod wywołaniem metody `Train`, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f981-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="2f981-208">Załaduj zestaw danych testowych przy użyciu metody [LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) .</span><span class="sxs-lookup"><span data-stu-id="2f981-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="2f981-209">Oceń model przy użyciu tego zestawu danych jako sprawdzenie jakości, dodając następujący kod w metodzie `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="2f981-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="2f981-210">Następnie Przekształć `Test` dane, dodając następujący kod do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="2f981-211">Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) umożliwia prognozowanie wierszy wejściowych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="2f981-212">Metoda `RegressionContext.Evaluate` oblicza metryki jakości dla `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="2f981-213">Zwraca obiekt <xref:Microsoft.ML.Data.RegressionMetrics>, który zawiera metryki ogólne obliczone przez oszacowania regresji.</span><span class="sxs-lookup"><span data-stu-id="2f981-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="2f981-214">Aby wyświetlić je w celu określenia jakości modelu, należy najpierw uzyskać metryki.</span><span class="sxs-lookup"><span data-stu-id="2f981-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="2f981-215">Dodaj następujący kod jako następny wiersz w `Evaluate` metodzie:</span><span class="sxs-lookup"><span data-stu-id="2f981-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="2f981-216">Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z rzeczywistym `Labels` w testowym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.</span><span class="sxs-lookup"><span data-stu-id="2f981-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="2f981-217">Dodaj następujący kod, aby ocenić model i utworzyć metryki oceny:</span><span class="sxs-lookup"><span data-stu-id="2f981-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="2f981-218">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metryką oceny dla modeli regresji.</span><span class="sxs-lookup"><span data-stu-id="2f981-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="2f981-219">RSquared przyjmuje wartości z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2f981-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="2f981-220">Im bliżej wartości jest 1, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="2f981-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="2f981-221">Dodaj następujący kod do metody `Evaluate`, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="2f981-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="2f981-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="2f981-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="2f981-223">Im niższa wartość, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="2f981-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="2f981-224">Dodaj następujący kod do metody `Evaluate`, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="2f981-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="2f981-225">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2f981-225">Use the model for predictions</span></span>

<span data-ttu-id="2f981-226">Utwórz metodę `TestSinglePrediction` po prostu po metodzie `Evaluate`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f981-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="2f981-227">Metoda `TestSinglePrediction` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2f981-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="2f981-228">Tworzy pojedynczy komentarz dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="2f981-229">Przewiduje wartość opłaty za przejazd na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="2f981-230">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="2f981-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="2f981-231">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="2f981-231">Displays the predicted results.</span></span>

<span data-ttu-id="2f981-232">Dodaj wywołanie do nowej metody z metody `Main`, bezpośrednio pod wywołaniem metody `Evaluate`, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f981-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="2f981-233">Użyj `PredictionEngine` do przewidywania taryfy, dodając następujący kod do `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="2f981-234">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2f981-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczna wątkowo.</span><span class="sxs-lookup"><span data-stu-id="2f981-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2f981-236">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="2f981-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2f981-237">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f981-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2f981-238">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="2f981-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="2f981-239">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="2f981-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="2f981-240">Ten samouczek używa jednej podróży testowej w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="2f981-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="2f981-241">Później możesz dodać inne scenariusze, aby eksperymentować z modelem.</span><span class="sxs-lookup"><span data-stu-id="2f981-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="2f981-242">Dodaj podróż w celu przetestowania przeszkolonego modelu kosztów w metodzie `TestSinglePrediction()` przez utworzenie wystąpienia `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="2f981-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="2f981-243">Następnie należy przewidzieć opłaty za pośrednictwem jednego wystąpienia danych podróży z taksówką i przekazać je do `PredictionEngine` przez dodanie następujących elementów jako następnych wierszy kodu w metodzie `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="2f981-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="2f981-244">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="2f981-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="2f981-245">Aby wyświetlić przewidywaną opłatę za określoną podróż, Dodaj następujący kod do metody `TestSinglePrediction`:</span><span class="sxs-lookup"><span data-stu-id="2f981-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="2f981-246">Uruchom program, aby zobaczyć przewidywalną opłatę za taksówkę w przypadku testowym.</span><span class="sxs-lookup"><span data-stu-id="2f981-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="2f981-247">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="2f981-247">Congratulations!</span></span> <span data-ttu-id="2f981-248">Pomyślnie skompilowano model uczenia maszynowego na potrzeby przewidywania opłat za podróż z użyciem taksówki, oceny jego dokładności i używania go do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="2f981-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="2f981-249">Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) .</span><span class="sxs-lookup"><span data-stu-id="2f981-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f981-250">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2f981-250">Next steps</span></span>

<span data-ttu-id="2f981-251">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2f981-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="2f981-252">Przygotuj i poznanie danych</span><span class="sxs-lookup"><span data-stu-id="2f981-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="2f981-253">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="2f981-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="2f981-254">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="2f981-254">Load and transform the data</span></span>
> * <span data-ttu-id="2f981-255">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="2f981-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="2f981-256">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="2f981-256">Train the model</span></span>
> * <span data-ttu-id="2f981-257">Oceń model</span><span class="sxs-lookup"><span data-stu-id="2f981-257">Evaluate the model</span></span>
> * <span data-ttu-id="2f981-258">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="2f981-258">Use the model for predictions</span></span>

<span data-ttu-id="2f981-259">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="2f981-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f981-260">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="2f981-260">Iris clustering</span></span>](iris-clustering.md)
