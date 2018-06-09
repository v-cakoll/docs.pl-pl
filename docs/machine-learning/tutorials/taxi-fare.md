---
title: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)
description: Dowiedz się, jak używać ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "35017292"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="92481-103">Samouczek: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)</span><span class="sxs-lookup"><span data-stu-id="92481-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="92481-104">W tym temacie odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, i materiały może być może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="92481-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="92481-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="92481-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="92481-106">W tym samouczku przedstawiono sposób wykorzystać do tworzenia ML.NET [modelu regresji](../resources/glossary.md#regression) do prognozowania opłat taksówki nowego Jorku.</span><span class="sxs-lookup"><span data-stu-id="92481-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="92481-107">Z tego samouczka, dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="92481-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="92481-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="92481-108">Understand the problem</span></span>
> * <span data-ttu-id="92481-109">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="92481-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="92481-110">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="92481-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="92481-111">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="92481-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="92481-112">Ładowanie i przekształcenia danych</span><span class="sxs-lookup"><span data-stu-id="92481-112">Load and transform your data</span></span>
> * <span data-ttu-id="92481-113">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="92481-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="92481-114">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="92481-114">Train the model</span></span>
> * <span data-ttu-id="92481-115">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="92481-115">Evaluate the model</span></span>
> * <span data-ttu-id="92481-116">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="92481-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92481-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="92481-117">Prerequisites</span></span>

* <span data-ttu-id="92481-118">[Visual Studio 2017 15,6 lub nowszym](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="92481-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="92481-119">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="92481-119">Understand the problem</span></span>

<span data-ttu-id="92481-120">Skupia się na ten problem **przewidywania opłatę taksówki rzeczy przed wyjazdem w Nowym Jorku**.</span><span class="sxs-lookup"><span data-stu-id="92481-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="92481-121">Na pierwszy rzut oka wydaje może po prostu zależą od dystans.</span><span class="sxs-lookup"><span data-stu-id="92481-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="92481-122">Jednak taksówki dostawców w Nowym Jorku naliczają opłaty zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płatności kartą kredytową zamiast gotówkowych.</span><span class="sxs-lookup"><span data-stu-id="92481-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="92481-123">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="92481-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="92481-124">Przewidywanie taryfy taksówki, najpierw wybierz zadanie learning odpowiednie maszyny.</span><span class="sxs-lookup"><span data-stu-id="92481-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="92481-125">Chcesz przewidzieć rzeczywistej wartości (wartość o podwójnej precyzji reprezentującą cen) na podstawie od innych czynników, w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="92481-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="92481-126">Możesz wybrać [ **regresji** ](../resources/glossary.md#regression) zadań.</span><span class="sxs-lookup"><span data-stu-id="92481-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="92481-127">Proces uczenia modelu określa, jakie czynniki w zestawie danych są najbardziej znaczenie w przypadku, gdy przewidywanie ceny końcowego taryfy.</span><span class="sxs-lookup"><span data-stu-id="92481-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="92481-128">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="92481-128">Create a console application</span></span>

1. <span data-ttu-id="92481-129">Otwórz program Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="92481-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="92481-130">Wybierz **pliku** > **nowy** > **projektu** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="92481-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="92481-131">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="92481-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="92481-132">Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="92481-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="92481-133">W **nazwa** polu tekstowym, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="92481-134">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="92481-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="92481-135">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="92481-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="92481-136">Wpisz "Dane" i naciśnij Enter.</span><span class="sxs-lookup"><span data-stu-id="92481-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="92481-137">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="92481-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="92481-138">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="92481-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="92481-139">Wybierz polecenie "nuget.org" jako źródło pakietu, wybierz kartę Przeglądaj, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="92481-140">Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.</span><span class="sxs-lookup"><span data-stu-id="92481-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="92481-141">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="92481-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="92481-142">Pobierz [taksówki taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówki taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folder utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="92481-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="92481-143">Zestaw danych podróży taksówki przygotowuje modelu uczenia maszynowego i może służyć do oceny, jak dokładny jest modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="92481-144">Te zestawy danych są początkowo z [zestawu danych w podróży taksówki TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="92481-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="92481-145">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*pliki CSV i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="92481-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="92481-146">W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.</span><span class="sxs-lookup"><span data-stu-id="92481-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="92481-147">Otwórz **taksówki taryfy train.csv** danych w edytorze kodu i przyjrzyj się nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="92481-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="92481-148">Spójrz na każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="92481-148">Take a look at each of the columns.</span></span> <span data-ttu-id="92481-149">Zrozumieć dane i zdecydować, które kolumny będą **funkcje** i **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="92481-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="92481-150">**Etykiety** jest identyfikator kolumny chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="92481-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="92481-151">Wskazywanego przez nią **funkcje** są używane do prognozowania etykiety.</span><span class="sxs-lookup"><span data-stu-id="92481-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="92481-152">**vendor_id:** identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="92481-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="92481-153">**rate_code:** typu szybkość podróży taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="92481-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="92481-154">**passenger_count:** liczba osób w podróży jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="92481-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="92481-155">**trip_time_in_secs:** trwało podróż ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="92481-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="92481-156">Aby dowiedzieć się, jak długo podróż przyjmuje dopiero po jego ukończeniu.</span><span class="sxs-lookup"><span data-stu-id="92481-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="92481-157">W tej kolumnie są wykluczone z modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="92481-158">**trip_distance:** odległość podróży jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="92481-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="92481-159">**payment_type:** formy płatności (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="92481-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="92481-160">**fare_amount:** taryfy całkowita taksówki płatnej jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="92481-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="92481-161">Tworzenie klas i zdefiniować ścieżki</span><span class="sxs-lookup"><span data-stu-id="92481-161">Create classes and define paths</span></span>

<span data-ttu-id="92481-162">Dodaj następujące dodatkowe `using` instrukcje na początku *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="92481-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="92481-163">Musisz utworzyć trzy zmienne globalne, aby zapisać modelu i do przechowywania ścieżek do ostatnio pobranych plików:</span><span class="sxs-lookup"><span data-stu-id="92481-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="92481-164">`_datapath` zawiera ścieżkę do danych używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="92481-165">`_testdatapath` zawiera ścieżkę do danych używany do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="92481-166">`_modelpath` zawiera ścieżkę, w której jest przechowywany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="92481-167">Dodaj następujący kod do prawej wiersz powyżej `Main` do określenia ostatnio pobranych plików:</span><span class="sxs-lookup"><span data-stu-id="92481-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="92481-168">Następnie należy utworzyć klasy dla danych wejściowych i prognozy:</span><span class="sxs-lookup"><span data-stu-id="92481-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="92481-169">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="92481-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="92481-170">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="92481-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="92481-171">Następnie wybierz opcję **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="92481-172">Dodaj następujące `using` instrukcje do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="92481-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="92481-173">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do *TaxiTrip.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="92481-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="92481-174">`TaxiTrip` jest to klasa wejściowy zestaw danych i zawiera definicje dla każdej kolumny zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="92481-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="92481-175">`TaxiTripFarePrediction` Klasa jest używana do przewidywania po zakończenia uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="92481-176">Ma ona zmiennoprzecinkowych pojedynczej precyzji (`FareAmount`) i `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut zastosowany.</span><span class="sxs-lookup"><span data-stu-id="92481-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="92481-177">Teraz przejdź wstecz do **Program.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="92481-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="92481-178">W `Main`, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="92481-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="92481-179">`Train` Metody przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-179">The `Train` method trains your model.</span></span> <span data-ttu-id="92481-180">Tworzenie tej funkcji tylko poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="92481-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="92481-181">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="92481-181">Create a learning pipeline</span></span>

<span data-ttu-id="92481-182">Potok learning ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="92481-183">Dodaj następujący kod do `Train()` metody:</span><span class="sxs-lookup"><span data-stu-id="92481-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="92481-184">Ładowanie i przekształcenia danych</span><span class="sxs-lookup"><span data-stu-id="92481-184">Load and transform your data</span></span>

<span data-ttu-id="92481-185">Następnie Załaduj dane do potoku.</span><span class="sxs-lookup"><span data-stu-id="92481-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="92481-186">Wskaż `_datapath` początkowo utworzony i ogranicznik plik CSV (,).</span><span class="sxs-lookup"><span data-stu-id="92481-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="92481-187">Dodaj następujący kod do `Train()` poniżej ostatni krok:</span><span class="sxs-lookup"><span data-stu-id="92481-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="92481-188">Będzie to odwołanie do kolumny bez podkreślenia w kodzie tworzonego.</span><span class="sxs-lookup"><span data-stu-id="92481-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="92481-189">Kopiuj `FareAmount` kolumny w nową kolumnę o nazwie "Etykieta" przy użyciu `ColumnCopier()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="92481-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="92481-190">Ta kolumna jest **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="92481-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="92481-191">Należy przeprowadzić niektóre **Inżynieria** do przekształcania danych, dzięki czemu można skutecznie do uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="92481-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="92481-192">Wymaga algorytmu, który przygotowuje modelu **liczbowych** funkcje, Przekształć dane podzielone na kategorie (`VendorId`, `RateCode`, i `PaymentType`) na liczby.</span><span class="sxs-lookup"><span data-stu-id="92481-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="92481-193">`CategoricalOneHotVectorizer()` Funkcja przypisuje kluczy numerycznych wartości w każdej z tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="92481-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="92481-194">Przekształcanie danych, dodając ten kod:</span><span class="sxs-lookup"><span data-stu-id="92481-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="92481-195">Ostatni etap przygotowywania danych łączy wszystkie Twoje **funkcje** do jednego za pomocą wektora `ColumnConcatenator()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="92481-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="92481-196">W tym kroku niezbędne pomaga algorytm łatwo przetworzyć funkcje.</span><span class="sxs-lookup"><span data-stu-id="92481-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="92481-197">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="92481-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="92481-198">Zwróć uwagę, że `trip_time_in_secs` kolumna nie jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="92481-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="92481-199">Już określone, że nie jest funkcją przydatne prognozowania.</span><span class="sxs-lookup"><span data-stu-id="92481-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="92481-200">Te kroki należy dodać do potoku w kolejności określonej powyżej do pomyślnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="92481-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="92481-201">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="92481-201">Choose a learning algorithm</span></span>

<span data-ttu-id="92481-202">Po dodaniu danych do potoku i przekształcenia go w poprawnym formacie wejściowych, wybrać algorytm uczenia (**uczeń**).</span><span class="sxs-lookup"><span data-stu-id="92481-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="92481-203">Algorytm uczenia przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="92481-204">Wybrano **zadań regresji** tego problemu, więc możesz dodać uczeń, nazywany `FastTreeRegressor()` do potoku, który używa **gradientu zwiększania**.</span><span class="sxs-lookup"><span data-stu-id="92481-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="92481-205">Zwiększanie wyniku gradientu jest technika problemów regresji uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="92481-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="92481-206">Zbudował każdego drzewa regresji w sposób stopniowy.</span><span class="sxs-lookup"><span data-stu-id="92481-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="92481-207">Funkcja wstępnie zdefiniowane utraty używa do mierzenia błąd w każdym kroku i popraw go w następnej.</span><span class="sxs-lookup"><span data-stu-id="92481-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="92481-208">Wynik jest modelu prognozowania, który jest rzeczywiście zespół słabszych modele predykcyjne.</span><span class="sxs-lookup"><span data-stu-id="92481-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="92481-209">Aby uzyskać więcej informacji na temat zwiększania gradientu, zobacz [Boosted regresji drzewa decyzyjnego](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="92481-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="92481-210">Dodaj następujący kod do `Train()` metody po kodzie przetwarzania danych dodanym w ostatnim kroku:</span><span class="sxs-lookup"><span data-stu-id="92481-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="92481-211">Dodano powyższych kroków do potoku jako pojedyncze instrukcje, ale C# zawiera przydatny zestaw Inicjalizacja składni, dzięki którym łatwiej Utwórz i zainicjuj potoku.</span><span class="sxs-lookup"><span data-stu-id="92481-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="92481-212">Zastąp kod zostały dodane do tej pory `Train()` metodę z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="92481-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="92481-213">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="92481-213">Train the model</span></span>

<span data-ttu-id="92481-214">Ostatnim krokiem jest do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-214">The final step is to train the model.</span></span> <span data-ttu-id="92481-215">Do tego momentu zostało wykonane żadne w potoku.</span><span class="sxs-lookup"><span data-stu-id="92481-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="92481-216">`pipeline.Train<T_Input, T_Output>()` Funkcja przyjmuje wstępnie zdefiniowane `TaxiTrip` typu klasy i dane wyjściowe `TaxiTripFarePrediction` typu.</span><span class="sxs-lookup"><span data-stu-id="92481-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="92481-217">Dodaj ten końcowy fragment kodu do `Train()` funkcji:</span><span class="sxs-lookup"><span data-stu-id="92481-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="92481-218">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="92481-218">And that's it!</span></span> <span data-ttu-id="92481-219">Pomyślnie zostały uczony model, który można przewidzieć taksówki opłat w NYC uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="92481-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="92481-220">Teraz zapoznaj się z informacjami, aby dowiedzieć się, jak dokładny modelu i Dowiedz się, jak pobrać go.</span><span class="sxs-lookup"><span data-stu-id="92481-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="92481-221">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="92481-221">Save the model</span></span>

<span data-ttu-id="92481-222">Przed przejściem do następnego kroku, Zapisz modelu w pliku zip, dodając następujący kod na końcu Twojej `Train()` funkcji:</span><span class="sxs-lookup"><span data-stu-id="92481-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="92481-223">Dodawanie `await` instrukcji `model.WriteAsync()` wywołania oznacza, że `Train()` metoda musi zostać zmieniona na to metoda asynchroniczna, która zwraca `Task`.</span><span class="sxs-lookup"><span data-stu-id="92481-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="92481-224">Modyfikowanie podpis `Train` zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="92481-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="92481-225">Zmiana typu zwracanego przez `Train` metody oznacza, że należy dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="92481-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="92481-226">Dodawanie `await` w Twojej `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i przywracać `Task`:</span><span class="sxs-lookup"><span data-stu-id="92481-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="92481-227">Należy również Dodaj następującą instrukcję using u góry pliku:</span><span class="sxs-lookup"><span data-stu-id="92481-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="92481-228">Ponieważ `async Main` metoda jest nową funkcją w C# 7.1 i domyślną wersję językową projektu jest 7.0 C#, musisz zmienić wersję języka C# 7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="92481-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="92481-229">W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="92481-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="92481-230">Wybierz **kompilacji** i wybierz **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="92481-231">Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="92481-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="92481-232">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="92481-233">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="92481-233">Evaluate the model</span></span>

<span data-ttu-id="92481-234">Obliczanie jest proces sprawdzania, jak działa modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="92481-235">Należy pamiętać, że model sprawia, że dobrej prognoz na danych, który nie był używany, gdy została ona uczony.</span><span class="sxs-lookup"><span data-stu-id="92481-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="92481-236">Aby zrobić to, Podziel dane na pociągu i testowania zestawów danych, tak jak w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="92481-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="92481-237">Teraz, gdy udało się nauczyć model danych pociągu, zobacz temat jak wykonuje na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="92481-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="92481-238">Wróć do Twojej `Main` funkcji i Dodaj następujący kod poniżej wywołania `Train()`metody:</span><span class="sxs-lookup"><span data-stu-id="92481-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="92481-239">`Evaluate()` Funkcja ocenia modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="92481-240">Tworzenie funkcji poniżej `Train()`.</span><span class="sxs-lookup"><span data-stu-id="92481-240">Create that function below `Train()`.</span></span> <span data-ttu-id="92481-241">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="92481-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="92481-242">Ładowanie danych test za pomocą `TextLoader()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="92481-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="92481-243">Dodaj następujący kod do `Evaluate()` metody:</span><span class="sxs-lookup"><span data-stu-id="92481-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="92481-244">Dodaj następujący kod, aby ocenić modelu oraz tworzenia metryki dla niej:</span><span class="sxs-lookup"><span data-stu-id="92481-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="92481-245">Usługi RMS jest jedna Metryka oceny problemów regresji.</span><span class="sxs-lookup"><span data-stu-id="92481-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="92481-246">Im niższa jest, tym lepiej modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-246">The lower it is, the better your model.</span></span> <span data-ttu-id="92481-247">Dodaj następujący kod do `Evaluate()` funkcji Drukowanie usługi RMS dla modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="92481-248">RSquared jest inny metryki oceny problemów regresji.</span><span class="sxs-lookup"><span data-stu-id="92481-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="92481-249">RSquared będzie wartość z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="92481-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="92481-250">Bliższe są 1, tym lepiej modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="92481-251">Dodaj następujący kod do `Evaluate()` funkcji Drukowanie wartość RSquared dla modelu.</span><span class="sxs-lookup"><span data-stu-id="92481-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="92481-252">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="92481-252">Use the model for predictions</span></span>

<span data-ttu-id="92481-253">Następnie należy utworzyć klasę, aby DOM scenariuszy testowania, których można użyć, aby upewnić się, że model działa poprawnie:</span><span class="sxs-lookup"><span data-stu-id="92481-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="92481-254">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="92481-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="92481-255">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="92481-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="92481-256">Następnie wybierz opcję **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="92481-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="92481-257">Modyfikowanie klasy statycznej, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="92481-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="92481-258">W tym samouczku korzysta z jednego podróży testu w ramach tej klasy.</span><span class="sxs-lookup"><span data-stu-id="92481-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="92481-259">Później można dodać inne scenariusze do eksperymentów z tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="92481-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="92481-260">Dodaj następujący kod do `TestTrips` klasy:</span><span class="sxs-lookup"><span data-stu-id="92481-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="92481-261">Rzeczywiste taryfy tego podróży jest 29.5, ale użyj wartości 0 jako symbol zastępczy.</span><span class="sxs-lookup"><span data-stu-id="92481-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="92481-262">Algorytmu uczenia maszynowego będzie prognozowania opłatę.</span><span class="sxs-lookup"><span data-stu-id="92481-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="92481-263">Dodaj następujący kod w Twojej `Main` funkcji.</span><span class="sxs-lookup"><span data-stu-id="92481-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="92481-264">Testowane się przy użyciu modelu `TestTrip` danych:</span><span class="sxs-lookup"><span data-stu-id="92481-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="92481-265">Uruchom program, aby zobaczyć taryfy przewidywane taksówki dla przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="92481-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="92481-266">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="92481-266">Congratulations!</span></span> <span data-ttu-id="92481-267">Zostały teraz pomyślnie skompilowane usługi machine learning model do przewidywania taksówki opłat, ocenić jego dokładność i przetestować go.</span><span class="sxs-lookup"><span data-stu-id="92481-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="92481-268">Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="92481-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="92481-269">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="92481-269">Next steps</span></span>

<span data-ttu-id="92481-270">W tym samouczku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="92481-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="92481-271">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="92481-271">Understand the problem</span></span>
> * <span data-ttu-id="92481-272">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="92481-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="92481-273">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="92481-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="92481-274">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="92481-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="92481-275">Ładowanie i przekształcenia danych</span><span class="sxs-lookup"><span data-stu-id="92481-275">Load and transform your data</span></span>
> * <span data-ttu-id="92481-276">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="92481-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="92481-277">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="92481-277">Train the model</span></span>
> * <span data-ttu-id="92481-278">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="92481-278">Evaluate the model</span></span>
> * <span data-ttu-id="92481-279">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="92481-279">Use the model for predictions</span></span>

<span data-ttu-id="92481-280">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i Znajdź więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="92481-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="92481-281">repozytorium GitHub DotNet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="92481-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
