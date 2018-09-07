---
title: Zastosowanie strukturze ML.NET do prognozowania cen biletów usługi New York taksówek (Regresja)
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 133b7ad17a98e4eea510f1704555b690b98e9091
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079805"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="70267-103">Samouczek: Używanie strukturze ML.NET do prognozowania cen biletów usługi New York taksówek (Regresja)</span><span class="sxs-lookup"><span data-stu-id="70267-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="70267-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="70267-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="70267-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="70267-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="70267-106">W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [modelu regresji](../resources/glossary.md#regression) do przewidywania taryf taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="70267-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="70267-107">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="70267-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="70267-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="70267-108">Understand the problem</span></span>
> * <span data-ttu-id="70267-109">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="70267-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="70267-110">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="70267-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="70267-111">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="70267-112">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="70267-112">Load and transform the data</span></span>
> * <span data-ttu-id="70267-113">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="70267-114">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="70267-114">Train the model</span></span>
> * <span data-ttu-id="70267-115">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="70267-115">Evaluate the model</span></span>
> * <span data-ttu-id="70267-116">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="70267-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70267-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="70267-117">Prerequisites</span></span>

* <span data-ttu-id="70267-118">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="70267-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="70267-119">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="70267-119">Understand the problem</span></span>

<span data-ttu-id="70267-120">Ten problem dotyczy Prognozowanie opłacie podróż taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="70267-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="70267-121">Na pierwszy rzut oka może wydawać się po prostu zależą dystans.</span><span class="sxs-lookup"><span data-stu-id="70267-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="70267-122">Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="70267-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="70267-123">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="70267-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="70267-124">Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="70267-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="70267-125">Aby zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.</span><span class="sxs-lookup"><span data-stu-id="70267-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="70267-126">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="70267-126">Create a console application</span></span>

1. <span data-ttu-id="70267-127">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="70267-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="70267-128">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="70267-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="70267-129">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="70267-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="70267-130">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="70267-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="70267-131">W **nazwa** pole tekstowe, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="70267-132">Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="70267-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="70267-133">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="70267-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="70267-134">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="70267-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="70267-135">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="70267-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="70267-136">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="70267-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="70267-137">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="70267-138">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="70267-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="70267-139">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="70267-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="70267-140">Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="70267-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="70267-141">Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="70267-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="70267-142">Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="70267-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="70267-143">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="70267-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="70267-144">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="70267-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="70267-145">Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="70267-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="70267-146">Przyjrzyj się każdej z kolumn.</span><span class="sxs-lookup"><span data-stu-id="70267-146">Take a look at each of the columns.</span></span> <span data-ttu-id="70267-147">Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="70267-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="70267-148">**Etykiety** to identyfikator kolumny, aby przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="70267-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="70267-149">Wskazywanego przez nią **funkcji** są używane do prognozowania etykiety.</span><span class="sxs-lookup"><span data-stu-id="70267-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="70267-150">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="70267-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="70267-151">**vendor_id:** identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="70267-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="70267-152">**rate_code:** Typ stawki podróży taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="70267-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="70267-153">**passenger_count:** liczba osób w ramach wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="70267-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="70267-154">**trip_time_in_secs:** trwało wyzwolenie ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="70267-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="70267-155">Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż.</span><span class="sxs-lookup"><span data-stu-id="70267-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="70267-156">W tym momencie nie wiesz, jak długo podróży zajęłoby.</span><span class="sxs-lookup"><span data-stu-id="70267-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="70267-157">Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="70267-158">**trip_distance:** odległość wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="70267-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="70267-159">**payment_type:** metodę płatności (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="70267-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="70267-160">**fare_amount:** taryfy taksówek łączna liczba płatnych jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="70267-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="70267-161">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="70267-161">Create data classes</span></span>

<span data-ttu-id="70267-162">Tworzenie klasy dla danych wejściowych i prognozy są tym:</span><span class="sxs-lookup"><span data-stu-id="70267-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="70267-163">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70267-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="70267-164">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="70267-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="70267-165">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="70267-166">Dodaj następujący kod `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="70267-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="70267-167">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="70267-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="70267-168">`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="70267-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="70267-169">Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="70267-169">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="70267-170">`TaxiTripFarePrediction` Klasa reprezentuje wyników.</span><span class="sxs-lookup"><span data-stu-id="70267-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="70267-171">Ma pola pojedynczego `FareAmount`, za pomocą `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) zastosowany.</span><span class="sxs-lookup"><span data-stu-id="70267-171">It has a single float field, `FareAmount`, with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="70267-172">W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.</span><span class="sxs-lookup"><span data-stu-id="70267-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="70267-173">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="70267-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="70267-174">Zdefiniować dane oraz model ścieżki</span><span class="sxs-lookup"><span data-stu-id="70267-174">Define data and model paths</span></span>

<span data-ttu-id="70267-175">Wróć do *Program.cs* pliku i Dodaj trzy pola do przechowywania ścieżek do plików z zestawami danych i plik, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="70267-175">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="70267-176">`_datapath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-176">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="70267-177">`_testdatapath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-177">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="70267-178">`_modelpath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-178">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="70267-179">Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="70267-179">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="70267-180">Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="70267-180">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="70267-181">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-181">Create a learning pipeline</span></span>

<span data-ttu-id="70267-182">Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="70267-182">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="70267-183">W `Main` metody, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="70267-183">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="70267-184">`Train` Metoda szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-184">The `Train` method trains the model.</span></span> <span data-ttu-id="70267-185">Tej metody Create, tuż poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="70267-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="70267-186">Potok nauczania ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="70267-187">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="70267-188">Obciążenia i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="70267-188">Load and transform data</span></span>

<span data-ttu-id="70267-189">Pierwszym krokiem do wykonania jest do ładowania danych z zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="70267-189">The first step to perform is to load data from the training data set.</span></span> <span data-ttu-id="70267-190">W naszym przypadku szkoleniowy zestaw danych znajduje się w pliku tekstowym ze ścieżką definicją `_datapath` pola.</span><span class="sxs-lookup"><span data-stu-id="70267-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="70267-191">Ten plik ma nagłówek z nazw kolumn, więc pierwszy wiersz powinien być ignorowane podczas ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="70267-191">That file has the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="70267-192">Kolumny w pliku są oddzielone przecinkiem (",").</span><span class="sxs-lookup"><span data-stu-id="70267-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="70267-193">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="70267-194">W następnych krokach nazywamy kolumny według nazw zdefiniowana w `TaxiTrip` klasy.</span><span class="sxs-lookup"><span data-stu-id="70267-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="70267-195">Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="70267-195">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="70267-196">Ponieważ chcemy przewidzieć taryfy taksówek w podróży, skopiuj `FareAmount` kolumny na **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="70267-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="70267-197">Aby to zrobić, należy użyć <xref:Microsoft.ML.Transforms.ColumnCopier> i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="70267-197">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="70267-198">Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby.</span><span class="sxs-lookup"><span data-stu-id="70267-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="70267-199">Aby to zrobić, użyj <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, co powoduje przypisanie różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="70267-199">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="70267-200">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny <xref:Microsoft.ML.Transforms.ColumnConcatenator> klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="70267-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="70267-201">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="70267-201">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="70267-202">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="70267-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="70267-203">Należy zauważyć, że `TripTime` kolumny, która odpowiada `trip_time_in_secs` kolumna w pliku zestawu danych nie jest uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="70267-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="70267-204">Już określone, że nie jest funkcją przydatne prognozowania.</span><span class="sxs-lookup"><span data-stu-id="70267-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="70267-205">Te kroki należy dodać do potoku w kolejności, w określonym powyżej pomyślne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="70267-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="70267-206">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-206">Choose a learning algorithm</span></span>

<span data-ttu-id="70267-207">Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, wybrać algorytm uczenia (**learner**).</span><span class="sxs-lookup"><span data-stu-id="70267-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="70267-208">Uczeń przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-208">The learner trains the model.</span></span> <span data-ttu-id="70267-209">Wybrano **regresji** zadań dla tego problemu, dzięki czemu używasz <xref:Microsoft.ML.Trainers.FastTreeRegressor> uczeń, który jest jednym z uczących regresji, dostarczone przez strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="70267-209">You chose a **regression** task for this problem, so you use a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="70267-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> Uczeń korzysta, wzrostu gradientu.</span><span class="sxs-lookup"><span data-stu-id="70267-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="70267-211">Ulepszanie gradientu jest techniką problemów regresji uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="70267-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="70267-212">Zbudował każdego drzewa regresji, w sposób stopniowy.</span><span class="sxs-lookup"><span data-stu-id="70267-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="70267-213">Aby zmierzyć błędów w każdym kroku i popraw go w ciągu następnych widoku jest używana funkcja utraty wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="70267-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="70267-214">Wynik jest model predykcyjny, który jest faktycznie zespołu słabszy modele predykcyjne.</span><span class="sxs-lookup"><span data-stu-id="70267-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="70267-215">Aby uzyskać więcej informacji na temat zwiększania wyniku gradientu zobacz [wzmocnione regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="70267-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="70267-216">Dodaj następujący kod do `Train` metoda przetwarzania danych kodzie dodanym w poprzednim kroku:</span><span class="sxs-lookup"><span data-stu-id="70267-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="70267-217">Powyższych kroków jest dodawane do potoku jako pojedyncze instrukcje, ale C# ma składnia inicjalizacji przydatny zestaw, który upraszcza tworzenie i Inicjowanie potoku.</span><span class="sxs-lookup"><span data-stu-id="70267-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="70267-218">Zastąp kod dodany do tej pory do `Train` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="70267-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="70267-219">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="70267-219">Train the model</span></span>

<span data-ttu-id="70267-220">Ostatnim krokiem jest do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-220">The final step is to train the model.</span></span> <span data-ttu-id="70267-221">Do tej pory została wykonana nic w potoku.</span><span class="sxs-lookup"><span data-stu-id="70267-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="70267-222">`pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienie `TInput` typu, a następnie generuje wystąpienie `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="70267-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="70267-223">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="70267-224">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="70267-224">And that's it!</span></span> <span data-ttu-id="70267-225">Zostały pomyślnie uczony model, który potrafi prognozować taryf taksówek w NYC uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="70267-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="70267-226">Teraz sklonujemy zapoznaj się z zrozumieć, jak dokładna jest model i Dowiedz się, jak go używać do prognozowania wartości taryfy taksówek.</span><span class="sxs-lookup"><span data-stu-id="70267-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="70267-227">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="70267-227">Save the model</span></span>

<span data-ttu-id="70267-228">W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="70267-228">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="70267-229">Aby zapisać model do pliku zip, Dodaj następujący kod na końcu `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-229">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="70267-230">Dodawanie `await` instrukcję, aby `model.WriteAsync` wywołanie oznacza, że `Train` metoda musi zostać zmieniona na metodzie asynchronicznej, która zwraca zadanie.</span><span class="sxs-lookup"><span data-stu-id="70267-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="70267-231">Zmodyfikuj podpis metody `Train` jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="70267-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="70267-232">Zmiana zwracanego typu `Train` metody oznacza, że trzeba dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="70267-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="70267-233">Za pomocą `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i zwrócenie `Task`:</span><span class="sxs-lookup"><span data-stu-id="70267-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="70267-234">Musisz również dodać następujące `using` dyrektywę w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="70267-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="70267-235">Ponieważ `async Main` metodą jest funkcja, dodany w języku C# 7.1 i wersją języka domyślnego projektu języka C# 7.0, musisz zmienić wersję języka C# 7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="70267-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="70267-236">Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="70267-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="70267-237">Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="70267-238">Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="70267-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="70267-239">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="70267-240">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="70267-240">Evaluate the model</span></span>

<span data-ttu-id="70267-241">Ocena jest procesem sprawdzania, jak model przewiduje wartości etykiet.</span><span class="sxs-lookup"><span data-stu-id="70267-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="70267-242">Należy pamiętać, że model sprawia, że dobry prognozy na danych, który nie był używany do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="70267-243">Jednym ze sposobów, w tym celu jest podzielenie danych na zestaw szkoleniowy i zestawami danych testowych, co jest wykonywane w ramach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="70267-243">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="70267-244">Skoro już uczony model na dane szkoleniowe, możesz zobaczyć, jak sprawdzi się na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="70267-244">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="70267-245">Wróć do `Main` metody i Dodaj następujący kod poniżej wywołania `Train`metody:</span><span class="sxs-lookup"><span data-stu-id="70267-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="70267-246">`Evaluate` Metoda ocenia modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="70267-247">Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="70267-248">Dodaj następujący kod do `Evaluate` metody instalacji ładowanie danych testowych:</span><span class="sxs-lookup"><span data-stu-id="70267-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="70267-249">Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:</span><span class="sxs-lookup"><span data-stu-id="70267-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="70267-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="70267-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="70267-251">Im niższa, w tym lepsze model jest.</span><span class="sxs-lookup"><span data-stu-id="70267-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="70267-252">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="70267-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="70267-253">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji.</span><span class="sxs-lookup"><span data-stu-id="70267-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="70267-254">RSquared przyjmuje wartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="70267-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="70267-255">Im bliżej jego wartość jest bliższa 1, tym lepiej jest model.</span><span class="sxs-lookup"><span data-stu-id="70267-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="70267-256">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="70267-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="70267-257">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="70267-257">Use the model for predictions</span></span>

<span data-ttu-id="70267-258">Utwórz klasę do domu badanie danych wystąpień:</span><span class="sxs-lookup"><span data-stu-id="70267-258">Create a class to house test data instances:</span></span>

1. <span data-ttu-id="70267-259">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70267-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="70267-260">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="70267-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="70267-261">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="70267-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="70267-262">Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="70267-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="70267-263">Ten samouczek używa test dwustronnej tej klasy.</span><span class="sxs-lookup"><span data-stu-id="70267-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="70267-264">Później możesz dodać inne scenariusze, aby eksperymentować z modelu.</span><span class="sxs-lookup"><span data-stu-id="70267-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="70267-265">Dodaj następujący kod do `TestTrips` klasy:</span><span class="sxs-lookup"><span data-stu-id="70267-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="70267-266">To podróż rzeczywiste taryfy jest 29,5.</span><span class="sxs-lookup"><span data-stu-id="70267-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="70267-267">Użyj wartości 0 jako symbolu zastępczego, zgodnie z modelu spowoduje przewidzieć opłacie.</span><span class="sxs-lookup"><span data-stu-id="70267-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="70267-268">Przewidywanie opłacie określonego podróży, wróć do *Program.cs* pliku i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="70267-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="70267-269">Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="70267-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="70267-270">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="70267-270">Congratulations!</span></span> <span data-ttu-id="70267-271">Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="70267-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="70267-272">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="70267-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="70267-273">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="70267-273">Next steps</span></span>

<span data-ttu-id="70267-274">W tym samouczku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="70267-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="70267-275">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="70267-275">Understand the problem</span></span>
> * <span data-ttu-id="70267-276">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="70267-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="70267-277">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="70267-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="70267-278">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="70267-279">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="70267-279">Load and transform the data</span></span>
> * <span data-ttu-id="70267-280">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="70267-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="70267-281">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="70267-281">Train the model</span></span>
> * <span data-ttu-id="70267-282">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="70267-282">Evaluate the model</span></span>
> * <span data-ttu-id="70267-283">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="70267-283">Use the model for predictions</span></span>

<span data-ttu-id="70267-284">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="70267-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="70267-285">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="70267-285">Iris clustering</span></span>](iris-clustering.md)
