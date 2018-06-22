---
title: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)
description: Dowiedz się, jak używać ML.NET w scenariuszu regresji.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0bd92317b1cc6d708b44b4f2e8d2b226460a6706
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298269"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="b7e20-103">Samouczek: Użyj ML.NET do prognozowania opłat taksówki nowego Jorku (Regresja)</span><span class="sxs-lookup"><span data-stu-id="b7e20-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="b7e20-104">W tym temacie odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, i materiały może być może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="b7e20-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b7e20-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b7e20-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b7e20-106">W tym samouczku przedstawiono sposób wykorzystać do tworzenia ML.NET [modelu regresji](../resources/glossary.md#regression) do prognozowania opłat taksówki nowego Jorku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="b7e20-107">Z tego samouczka, dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="b7e20-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b7e20-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="b7e20-108">Understand the problem</span></span>
> * <span data-ttu-id="b7e20-109">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="b7e20-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="b7e20-110">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="b7e20-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="b7e20-111">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="b7e20-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="b7e20-112">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="b7e20-112">Load and transform the data</span></span>
> * <span data-ttu-id="b7e20-113">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="b7e20-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b7e20-114">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-114">Train the model</span></span>
> * <span data-ttu-id="b7e20-115">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-115">Evaluate the model</span></span>
> * <span data-ttu-id="b7e20-116">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="b7e20-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b7e20-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b7e20-117">Prerequisites</span></span>

* <span data-ttu-id="b7e20-118">[Visual Studio 2017 15,6 lub nowszym](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b7e20-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b7e20-119">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="b7e20-119">Understand the problem</span></span>

<span data-ttu-id="b7e20-120">Skupia się na ten problem **przewidywania opłatę taksówki rzeczy przed wyjazdem w Nowym Jorku**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="b7e20-121">Na pierwszy rzut oka wydaje może po prostu zależą od dystans.</span><span class="sxs-lookup"><span data-stu-id="b7e20-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="b7e20-122">Jednak taksówki dostawców w Nowym Jorku naliczają opłaty zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płatności kartą kredytową zamiast gotówkowych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="b7e20-123">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="b7e20-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="b7e20-124">Przewidywanie taryfy taksówki, najpierw wybierz zadanie learning odpowiednie maszyny.</span><span class="sxs-lookup"><span data-stu-id="b7e20-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="b7e20-125">Chcesz przewidzieć rzeczywistej wartości (wartość o podwójnej precyzji reprezentującą cen) na podstawie od innych czynników, w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="b7e20-126">Możesz wybrać [ **regresji** ](../resources/glossary.md#regression) zadań.</span><span class="sxs-lookup"><span data-stu-id="b7e20-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b7e20-127">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="b7e20-127">Create a console application</span></span>

1. <span data-ttu-id="b7e20-128">Otwórz program Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="b7e20-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="b7e20-129">Wybierz **pliku** > **nowy** > **projektu** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b7e20-130">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="b7e20-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b7e20-131">Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b7e20-132">W **nazwa** polu tekstowym, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="b7e20-133">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać plik zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="b7e20-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="b7e20-134">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b7e20-135">Wpisz "Dane" i naciśnij Enter.</span><span class="sxs-lookup"><span data-stu-id="b7e20-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="b7e20-136">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b7e20-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b7e20-137">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b7e20-138">Wybierz "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** karcie, wyszukaj **Microsoft.ML**, wybierz z listy tego pakietu i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b7e20-139">Wybierz **OK** znajdującego się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdującego się na **akceptacji licencji** okna dialogowego jeśli użytkownik Akceptuję warunki licencji dla pakietów na liście.</span><span class="sxs-lookup"><span data-stu-id="b7e20-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b7e20-140">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="b7e20-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="b7e20-141">Pobierz [taksówki taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówki taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folder utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b7e20-142">Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładny jest modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="b7e20-143">Te zestawy danych są początkowo z [zestawu danych w podróży taksówki TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="b7e20-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="b7e20-144">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*pliki CSV i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="b7e20-145">W obszarze **zaawansowane**, zmień wartość **Kopiuj do katalogu wyjściowego** do **zawsze**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="b7e20-146">Otwórz **taksówki taryfy train.csv** danych ustaw i przyjrzyj się nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="b7e20-147">Spójrz na każdej kolumny.</span><span class="sxs-lookup"><span data-stu-id="b7e20-147">Take a look at each of the columns.</span></span> <span data-ttu-id="b7e20-148">Zrozumieć dane i zdecydować, które kolumny będą **funkcje** i która jest **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="b7e20-149">**Etykiety** jest identyfikator kolumny chcesz przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="b7e20-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="b7e20-150">Wskazywanego przez nią **funkcje** są używane do prognozowania etykiety.</span><span class="sxs-lookup"><span data-stu-id="b7e20-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="b7e20-151">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="b7e20-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="b7e20-152">**vendor_id:** identyfikator dostawcy taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="b7e20-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="b7e20-153">**rate_code:** typu szybkość podróży taksówki jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="b7e20-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="b7e20-154">**passenger_count:** liczba osób w podróży jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="b7e20-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="b7e20-155">**trip_time_in_secs:** trwało podróż ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="b7e20-156">Chcesz przewidzieć taryfy podróży przed zakończeniem podróży.</span><span class="sxs-lookup"><span data-stu-id="b7e20-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="b7e20-157">W tym momencie nie wiadomo, jak długo podróży zajmie.</span><span class="sxs-lookup"><span data-stu-id="b7e20-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="b7e20-158">W związku z tym podczas podróży nie jest funkcją i będzie wykluczyć tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="b7e20-159">**trip_distance:** odległość podróży jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="b7e20-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="b7e20-160">**payment_type:** formy płatności (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="b7e20-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="b7e20-161">**fare_amount:** taryfy całkowita taksówki płatnej jest etykietą.</span><span class="sxs-lookup"><span data-stu-id="b7e20-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b7e20-162">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="b7e20-162">Create data classes</span></span>

<span data-ttu-id="b7e20-163">Tworzenie klasy dla danych wejściowych i prognozy:</span><span class="sxs-lookup"><span data-stu-id="b7e20-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b7e20-164">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b7e20-165">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="b7e20-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="b7e20-166">Następnie wybierz opcję **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b7e20-167">Dodaj następujące `using` instrukcje do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="b7e20-167">Add the following `using` statements to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="b7e20-168">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, do *TaxiTrip.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="b7e20-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="b7e20-169">`TaxiTrip` jest to klasa danych wejściowych i zawiera definicje dla każdej kolumny zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="b7e20-170">Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić wskaźników źródłowych kolumn w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="b7e20-171">`TaxiTripFarePrediction` Klasa jest używana do reprezentowania wyniki przewidywane.</span><span class="sxs-lookup"><span data-stu-id="b7e20-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="b7e20-172">Ma ona zmiennoprzecinkowych pojedynczej precyzji (`FareAmount`) pole z `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut zastosowany.</span><span class="sxs-lookup"><span data-stu-id="b7e20-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="b7e20-173">**Wynik** kolumna jest kolumną specjalne w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b7e20-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="b7e20-174">Model danych wyjściowych przewidywane wartości w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="b7e20-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="b7e20-175">Zdefiniuj ścieżki danych i modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-175">Define data and model paths</span></span>

<span data-ttu-id="b7e20-176">Wróć do *Program.cs* plików i Utwórz trzy stałe globalne do przechowywania ścieżki do plików z zestawami danych i zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="b7e20-176">Go back to the *Program.cs* file and create three global constants to hold the paths to the files with data sets and to save the model:</span></span>

* <span data-ttu-id="b7e20-177">`_datapath` zawiera ścieżkę do danych używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-177">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="b7e20-178">`_testdatapath` zawiera ścieżkę do danych używany do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-178">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="b7e20-179">`_modelpath` zawiera ścieżkę, w której jest przechowywany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-179">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="b7e20-180">Dodaj następujący kod do prawej wiersz powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="b7e20-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="b7e20-181">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="b7e20-181">Create a learning pipeline</span></span>

<span data-ttu-id="b7e20-182">Dodaj następujące dodatkowe `using` instrukcje na początku *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="b7e20-182">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="b7e20-183">W `Main`, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b7e20-183">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="b7e20-184">`Train` Metody przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-184">The `Train` method trains the model.</span></span> <span data-ttu-id="b7e20-185">Tworzenie tej metody tylko poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="b7e20-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="b7e20-186">Potok learning ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="b7e20-187">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="b7e20-188">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="b7e20-188">Load and transform data</span></span>

<span data-ttu-id="b7e20-189">Pierwszym krokiem, który wykonuje potoku learning ładuje dane z zestawu danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-189">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="b7e20-190">W tym przypadku szkoleniowy zestaw danych są przechowywane w pliku tekstowym ze ścieżką zdefiniowane przez `_datapath` stałej.</span><span class="sxs-lookup"><span data-stu-id="b7e20-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` constant.</span></span> <span data-ttu-id="b7e20-191">Ten plik zawiera nagłówek z nazwami kolumn, w związku z czym pierwszy wiersz powinien być ignorowane podczas ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-191">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="b7e20-192">Kolumny w pliku są oddzielone przecinkiem (",").</span><span class="sxs-lookup"><span data-stu-id="b7e20-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="b7e20-193">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="b7e20-194">W następnych krokach możemy odwoływać się do kolumn za pomocą nazw zdefiniowana w `TaxiTrip` klasy.</span><span class="sxs-lookup"><span data-stu-id="b7e20-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="b7e20-195">Gdy model jest uczony i obliczone wartości w **etykiety** kolumny są traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="b7e20-195">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="b7e20-196">Ponieważ chcemy przewidzieć taksówki taryfy podróży, skopiuj `FareAmount` kolumny do **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="b7e20-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="b7e20-197">Aby to zrobić, użyj <xref:Microsoft.ML.Transforms.ColumnCopier> i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b7e20-197">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="b7e20-198">Wymaga algorytmu, który przygotowuje modelu **liczbowych** funkcji, dlatego należy przekształcić dane podzielone na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby.</span><span class="sxs-lookup"><span data-stu-id="b7e20-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="b7e20-199">Aby to zrobić, użyj <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, co powoduje przypisanie liczbowe różnych wartości różne wartości w każdej kolumny klucza i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b7e20-199">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="b7e20-200">Ostatni etap przygotowywania danych łączy wszystkich kolumn funkcji do **funkcje** przy użyciu kolumny <xref:Microsoft.ML.Transforms.ColumnConcatenator> klasy transformacji.</span><span class="sxs-lookup"><span data-stu-id="b7e20-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="b7e20-201">Ten krok jest niezbędny, ponieważ uczeń przetwarza tylko funkcje z **funkcje** kolumny.</span><span class="sxs-lookup"><span data-stu-id="b7e20-201">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="b7e20-202">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b7e20-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="b7e20-203">Zwróć uwagę, że `TripTime` kolumny, która odpowiada `trip_time_in_secs` kolumny w pliku zestawu danych nie jest uwzględniana.</span><span class="sxs-lookup"><span data-stu-id="b7e20-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="b7e20-204">Już określone, że nie jest funkcją przydatne prognozowania.</span><span class="sxs-lookup"><span data-stu-id="b7e20-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="b7e20-205">Te kroki należy dodać do potoku w kolejności określonej powyżej do pomyślnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="b7e20-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b7e20-206">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="b7e20-206">Choose a learning algorithm</span></span>

<span data-ttu-id="b7e20-207">Po dodaniu danych do potoku i przekształcenia go w poprawnym formacie wejściowych, wybrać algorytm uczenia (**uczeń**).</span><span class="sxs-lookup"><span data-stu-id="b7e20-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="b7e20-208">Uczeń przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-208">The learner trains the model.</span></span> <span data-ttu-id="b7e20-209">Wybrano **zadań regresji** tego problemu, więc możesz dodać <xref:Microsoft.ML.Trainers.FastTreeRegressor> uczeń, które jest jednym z uczących regresji dostarczonych przez ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b7e20-209">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="b7e20-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> Uczeń wykorzystuje zwiększania gradientu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-210"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="b7e20-211">Zwiększanie wyniku gradientu jest technika problemów regresji uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="b7e20-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="b7e20-212">Zbudował każdego drzewa regresji w sposób stopniowy.</span><span class="sxs-lookup"><span data-stu-id="b7e20-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="b7e20-213">Funkcja wstępnie zdefiniowane utraty używa do mierzenia błąd w każdym kroku i popraw go w następnej.</span><span class="sxs-lookup"><span data-stu-id="b7e20-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="b7e20-214">Wynik jest modelu prognozowania, który jest rzeczywiście zespół słabszych modele predykcyjne.</span><span class="sxs-lookup"><span data-stu-id="b7e20-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="b7e20-215">Aby uzyskać więcej informacji na temat zwiększania gradientu, zobacz [Boosted regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="b7e20-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="b7e20-216">Dodaj następujący kod do `Train` metody po kodzie przetwarzania danych dodanym w poprzednim kroku:</span><span class="sxs-lookup"><span data-stu-id="b7e20-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="b7e20-217">Dodano powyższych kroków do potoku jako pojedyncze instrukcje, ale C# zawiera przydatny zestaw Inicjalizacja składni, dzięki którym łatwiej Utwórz i zainicjuj potoku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="b7e20-218">Zastąp kod zostały dodane do tej pory `Train` metodę z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b7e20-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="b7e20-219">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-219">Train the model</span></span>

<span data-ttu-id="b7e20-220">Ostatnim krokiem jest do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-220">The final step is to train the model.</span></span> <span data-ttu-id="b7e20-221">Do tego momentu zostało wykonane żadne w potoku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="b7e20-222">`pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienia `TInput` wpisz i wyświetla wystąpienia `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="b7e20-223">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="b7e20-224">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="b7e20-224">And that's it!</span></span> <span data-ttu-id="b7e20-225">Pomyślnie zostały uczony model, który można przewidzieć taksówki opłat w NYC uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="b7e20-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="b7e20-226">Teraz załóżmy podglądu, aby zrozumieć, jak dokładny model jest i Dowiedz się, jak używać go do prognozowania wartości taryfy taksówki.</span><span class="sxs-lookup"><span data-stu-id="b7e20-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="b7e20-227">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="b7e20-227">Save the model</span></span>

<span data-ttu-id="b7e20-228">Przed przejściem do następnego kroku, Zapisz modelu w pliku zip, dodając następujący kod na końcu `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-228">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="b7e20-229">Dodawanie `await` instrukcji `model.WriteAsync` wywołania oznacza, że `Train` metoda musi zostać zmieniona na to metoda asynchroniczna, która zwraca zadanie.</span><span class="sxs-lookup"><span data-stu-id="b7e20-229">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="b7e20-230">Modyfikowanie podpis `Train` zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="b7e20-230">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="b7e20-231">Zmiana typu zwracanego przez `Train` metody oznacza, że należy dodać `await` do kodu, który wywołuje `Train` w `Main` metody, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="b7e20-231">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="b7e20-232">Przy użyciu `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i przywracać `Task`:</span><span class="sxs-lookup"><span data-stu-id="b7e20-232">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="b7e20-233">Należy również dodać następujące `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="b7e20-233">You also need to add the following `using` statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="b7e20-234">Ponieważ `async Main` metody jest funkcją dodane w języku C# 7.1 i domyślną wersję językową projektu jest 7.0 C#, musisz zmienić wersję języka C# 7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="b7e20-234">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="b7e20-235">W tym celu kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-235">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="b7e20-236">Wybierz **kompilacji** i wybierz **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-236">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b7e20-237">Na liście rozwijanej wybierz **C# 7.1** (lub nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="b7e20-237">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="b7e20-238">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-238">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="b7e20-239">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-239">Evaluate the model</span></span>

<span data-ttu-id="b7e20-240">Obliczanie jest proces sprawdzania, jak model przewiduje wartości etykiet.</span><span class="sxs-lookup"><span data-stu-id="b7e20-240">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="b7e20-241">Należy pamiętać, że model sprawia, że dobrej prognoz na danych, który nie był używany do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-241">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="b7e20-242">Jednym ze sposobów jest podzielić dane na pociągu i testowania zestawów danych, co jest wykonywane w ramach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="b7e20-242">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="b7e20-243">Teraz, gdy udało się nauczyć model danych pociągu, zobacz temat jak wykonuje na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="b7e20-243">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="b7e20-244">Wróć do `Main` — metoda i Dodaj następujący kod poniżej wywołania `Train`metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-244">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="b7e20-245">`Evaluate` Metody ocenia modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-245">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="b7e20-246">Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-246">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="b7e20-247">Dodaj następujący kod do `Evaluate` metody instalacji ładowania danych testowych:</span><span class="sxs-lookup"><span data-stu-id="b7e20-247">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="b7e20-248">Dodaj następujący kod, aby ocenić modelu oraz tworzenia metryki oceny:</span><span class="sxs-lookup"><span data-stu-id="b7e20-248">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="b7e20-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jednym z metryki oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="b7e20-249">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="b7e20-250">Im niższa, tym lepiej model jest.</span><span class="sxs-lookup"><span data-stu-id="b7e20-250">The lower it is, the better the model is.</span></span> <span data-ttu-id="b7e20-251">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="b7e20-251">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="b7e20-252">[RSquared](../resources/glossary.md#coefficient-of-determination) jest inny metryki oceny modeli regresji.</span><span class="sxs-lookup"><span data-stu-id="b7e20-252">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="b7e20-253">RSquared przyjmuje wartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="b7e20-253">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="b7e20-254">Jego wartość jest bliższa 1, tym lepiej jest modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-254">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="b7e20-255">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="b7e20-255">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b7e20-256">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="b7e20-256">Use the model for predictions</span></span>

<span data-ttu-id="b7e20-257">Następnie należy utworzyć klasę, aby DOM scenariuszy testowania, których można użyć, aby upewnić się, że model działa poprawnie:</span><span class="sxs-lookup"><span data-stu-id="b7e20-257">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="b7e20-258">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b7e20-258">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b7e20-259">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmienić **nazwa** do *TestTrips.cs*.</span><span class="sxs-lookup"><span data-stu-id="b7e20-259">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="b7e20-260">Następnie wybierz opcję **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b7e20-260">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b7e20-261">Modyfikowanie klasy statycznej, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b7e20-261">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="b7e20-262">W tym samouczku korzysta z jednego podróży testu w ramach tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b7e20-262">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="b7e20-263">Później można dodać inne scenariusze do eksperymentów z modelu.</span><span class="sxs-lookup"><span data-stu-id="b7e20-263">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b7e20-264">Dodaj następujący kod do `TestTrips` klasy:</span><span class="sxs-lookup"><span data-stu-id="b7e20-264">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="b7e20-265">Rzeczywiste taryfy tego podróży jest 29.5.</span><span class="sxs-lookup"><span data-stu-id="b7e20-265">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="b7e20-266">Użyj wartości 0 jako symbolu zastępczego, jak model zostanie prognozowania opłatę.</span><span class="sxs-lookup"><span data-stu-id="b7e20-266">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="b7e20-267">Przewidywanie taryfy określonego podróży, przejdź wstecz do *Program.cs* i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="b7e20-267">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="b7e20-268">Uruchom program, aby zobaczyć taryfy przewidywane taksówki dla przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="b7e20-268">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="b7e20-269">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="b7e20-269">Congratulations!</span></span> <span data-ttu-id="b7e20-270">Zostały teraz pomyślnie skompilowane usługi machine learning model do przewidywania taksówki podróży opłat, obliczone dokładność i używana do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="b7e20-270">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="b7e20-271">Kod źródłowy można znaleźć w tym samouczku w [dotnet/przykłady](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="b7e20-271">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7e20-272">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b7e20-272">Next steps</span></span>

<span data-ttu-id="b7e20-273">W tym samouczku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="b7e20-273">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b7e20-274">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="b7e20-274">Understand the problem</span></span>
> * <span data-ttu-id="b7e20-275">Wybierz zadanie learning odpowiednie maszyny</span><span class="sxs-lookup"><span data-stu-id="b7e20-275">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="b7e20-276">Przygotowanie i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="b7e20-276">Prepare and understand the data</span></span>
> * <span data-ttu-id="b7e20-277">Tworzenie potoku learning</span><span class="sxs-lookup"><span data-stu-id="b7e20-277">Create a learning pipeline</span></span>
> * <span data-ttu-id="b7e20-278">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="b7e20-278">Load and transform the data</span></span>
> * <span data-ttu-id="b7e20-279">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="b7e20-279">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b7e20-280">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-280">Train the model</span></span>
> * <span data-ttu-id="b7e20-281">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="b7e20-281">Evaluate the model</span></span>
> * <span data-ttu-id="b7e20-282">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="b7e20-282">Use the model for predictions</span></span>

<span data-ttu-id="b7e20-283">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i Znajdź więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="b7e20-283">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b7e20-284">repozytorium GitHub DotNet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="b7e20-284">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
