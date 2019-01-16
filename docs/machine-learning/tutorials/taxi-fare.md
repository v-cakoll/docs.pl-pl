---
title: Przewidywanie, Nowy Jork taksówek opłaty za pomocą uczeń regresji za pomocą platformy ML.NET
description: Przewidywanie opłaty za pomocą platformy ML.NET przy użyciu uczeń regresji.
author: aditidugar
ms.author: johalex
ms.date: 01/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b17b4e31a60d6eaf432577281004bcf2c7ca1da2
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333788"
---
# <a name="tutorial-predict-new-york-taxi-fares-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="5f079-103">Samouczek: Przewidywanie, Nowy Jork taksówek opłaty za pomocą uczeń regresji za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="5f079-103">Tutorial: Predict New York taxi fares using a regression learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="5f079-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="5f079-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="5f079-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5f079-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="5f079-106">W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [modelu regresji](../resources/glossary.md#regression) do przewidywania taryf taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="5f079-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="5f079-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5f079-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5f079-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5f079-108">Understand the problem</span></span>
> * <span data-ttu-id="5f079-109">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="5f079-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="5f079-110">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="5f079-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="5f079-111">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="5f079-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="5f079-112">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="5f079-112">Load and transform the data</span></span>
> * <span data-ttu-id="5f079-113">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="5f079-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="5f079-114">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-114">Train the model</span></span>
> * <span data-ttu-id="5f079-115">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-115">Evaluate the model</span></span>
> * <span data-ttu-id="5f079-116">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="5f079-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f079-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5f079-117">Prerequisites</span></span>

* <span data-ttu-id="5f079-118">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="5f079-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="5f079-119">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5f079-119">Understand the problem</span></span>

<span data-ttu-id="5f079-120">Ten problem dotyczy Prognozowanie opłacie podróż taksówek w Nowym Jorku.</span><span class="sxs-lookup"><span data-stu-id="5f079-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="5f079-121">Na pierwszy rzut oka może wydawać się po prostu zależą dystans.</span><span class="sxs-lookup"><span data-stu-id="5f079-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="5f079-122">Jednak dostawców taksówek w Nowym Jorku jest opłata w wysokości zmiennych ilości dla innych czynników, takich jak dodatkowe osób lub płacenia kartą kredytową zamiast środków pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="5f079-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="5f079-123">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="5f079-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="5f079-124">Chcesz przewidzieć wartość ceny, który jest wartością rzeczywistego na podstawie innych czynników, w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="5f079-125">Aby zrobić, możesz wybrać [regresji](../resources/glossary.md#regression) machine learning zadania.</span><span class="sxs-lookup"><span data-stu-id="5f079-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5f079-126">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="5f079-126">Create a console application</span></span>

1. <span data-ttu-id="5f079-127">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5f079-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="5f079-128">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="5f079-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="5f079-129">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="5f079-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="5f079-130">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="5f079-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5f079-131">W **nazwa** pole tekstowe, wpisz "TaxiFarePrediction", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5f079-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="5f079-132">Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="5f079-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="5f079-133">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="5f079-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="5f079-134">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="5f079-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="5f079-135">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="5f079-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="5f079-136">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5f079-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="5f079-137">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5f079-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="5f079-138">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="5f079-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="5f079-139">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="5f079-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="5f079-140">Pobierz [taksówek taryfy train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) i [taksówek taryfy test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) danych ustawia i zapisywanie ich *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="5f079-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="5f079-141">Używamy tych zestawów danych do nauczenia modelu uczenia maszynowego, a następnie ocenę, jak dokładna jest model.</span><span class="sxs-lookup"><span data-stu-id="5f079-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="5f079-142">Te zestawy danych są pierwotnie z [zestawu danych podróży taksówek TLC NYC](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="5f079-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="5f079-143">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5f079-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="5f079-144">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="5f079-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="5f079-145">Otwórz **taksówek taryfy train.csv** dane ustawić i spójrz na nagłówki kolumn w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="5f079-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="5f079-146">Przyjrzyj się każdej z kolumn.</span><span class="sxs-lookup"><span data-stu-id="5f079-146">Take a look at each of the columns.</span></span> <span data-ttu-id="5f079-147">Zrozumieć dane i zdecydować, które kolumny są **funkcji** i który z nich jest **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="5f079-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="5f079-148">**Etykiety** to identyfikator kolumny, aby przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="5f079-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="5f079-149">Wskazywanego przez nią **funkcji** są używane do prognozowania etykiety.</span><span class="sxs-lookup"><span data-stu-id="5f079-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="5f079-150">Podany zestaw danych zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="5f079-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="5f079-151">**vendor_id:** Identyfikator dostawcy taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="5f079-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="5f079-152">**rate_code:** Typ stawki podróży taksówek jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="5f079-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="5f079-153">**passenger_count:** Liczba osób w ramach wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="5f079-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="5f079-154">**trip_time_in_secs:** Ilość czasu trwania podróży.</span><span class="sxs-lookup"><span data-stu-id="5f079-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="5f079-155">Chcesz przewidzieć opłacie wyzwolenie przed zakończeniem podróż.</span><span class="sxs-lookup"><span data-stu-id="5f079-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="5f079-156">W tym momencie nie wiesz, jak długo podróży zajęłoby.</span><span class="sxs-lookup"><span data-stu-id="5f079-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="5f079-157">Dlatego czas podróży nie jest funkcją i będzie Wyklucz tę kolumnę z modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="5f079-158">**trip_distance:** Odległość wyzwolenie jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="5f079-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="5f079-159">**payment_type:** Sposób zapłaty (pieniężnych lub karta kredytowa) jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="5f079-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="5f079-160">**fare_amount:** Taryfy taksówek łączna liczba płatnych jest etykieta.</span><span class="sxs-lookup"><span data-stu-id="5f079-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="5f079-161">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="5f079-161">Create data classes</span></span>

<span data-ttu-id="5f079-162">Tworzenie klasy dla danych wejściowych i prognozy są tym:</span><span class="sxs-lookup"><span data-stu-id="5f079-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="5f079-163">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5f079-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="5f079-164">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="5f079-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="5f079-165">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5f079-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="5f079-166">Dodaj następujący kod `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="5f079-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="5f079-167">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `TaxiTrip` i `TaxiTripFarePrediction`, *TaxiTrip.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="5f079-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="5f079-168">`TaxiTrip` jest klasą danych wejściowych i ma definicje dla każdej z kolumn w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="5f079-169">Użyj <xref:Microsoft.ML.Data.ColumnAttribute> atrybutu, aby określić indeksów kolumny źródłowe w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-169">Use the <xref:Microsoft.ML.Data.ColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="5f079-170">`TaxiTripFarePrediction` Klasa reprezentuje wyników.</span><span class="sxs-lookup"><span data-stu-id="5f079-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="5f079-171">Ma pola pojedynczego `FareAmount`, za pomocą `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> zastosowany.</span><span class="sxs-lookup"><span data-stu-id="5f079-171">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="5f079-172">W przypadku zadań regresji **wynik** kolumna zawiera wartości prognozowanej etykiet.</span><span class="sxs-lookup"><span data-stu-id="5f079-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="5f079-173">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="5f079-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="5f079-174">Zdefiniować dane oraz model ścieżki</span><span class="sxs-lookup"><span data-stu-id="5f079-174">Define data and model paths</span></span>

<span data-ttu-id="5f079-175">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="5f079-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="5f079-176">Musisz utworzyć trzy pola do przechowywania ścieżek do plików z zestawami danych i plik Aby zapisać model i zmienną globalną, uzyskać `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="5f079-176">You need to create three fields to hold the paths to the files with data sets and the file to save the model, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="5f079-177">`_trainDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-177">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="5f079-178">`_testDataPath` zawiera ścieżkę do pliku z zestawem danych, używane do oceny modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-178">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="5f079-179">`_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-179">`_modelPath` contains the path to the file where the trained model is stored.</span></span>
* <span data-ttu-id="5f079-180">`_textLoader` jest <xref:Microsoft.ML.Data.TextLoader> używany do ładowania i przekształcić zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-180">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="5f079-181">Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek i `_textLoader` zmiennej:</span><span class="sxs-lookup"><span data-stu-id="5f079-181">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="5f079-182">Podczas tworzenia modelu za pomocą platformy ML.NET rozpoczyna się od utworzenia kontekście uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5f079-182">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="5f079-183">To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="5f079-183">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="5f079-184">Środowisko dostarcza kontekst dla zadania uczenia maszyny używanej dla wyjątku, śledzenia i rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5f079-184">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="5f079-185">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="5f079-185">Initialize variables in Main</span></span>

<span data-ttu-id="5f079-186">Utwórz zmienną o nazwie `mlContext` i zainicjuj ją o nowe wystąpienie klasy `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="5f079-186">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="5f079-187">Zastąp `Console.WriteLine("Hello World!")` wiersz poniższym kodem w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-187">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="5f079-188">Następnie do Instalatora w celu załadowania zainicjować danych `_textLoader` zmienna globalna, aby można było użyć go ponownie.</span><span class="sxs-lookup"><span data-stu-id="5f079-188">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="5f079-189">Należy zauważyć, że użyto `TextReader`.</span><span class="sxs-lookup"><span data-stu-id="5f079-189">Notice that we are using a `TextReader`.</span></span> <span data-ttu-id="5f079-190">Po utworzeniu `TextLoader` przy użyciu `TextReader`, są przekazywane w kontekście potrzebne i <xref:Microsoft.ML.Data.TextLoader.Arguments> klasy, która umożliwia dostosowanie.</span><span class="sxs-lookup"><span data-stu-id="5f079-190">When you create a `TextLoader` using a `TextReader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span> <span data-ttu-id="5f079-191">Określ schemat danych, przekazując tablicę <xref:Microsoft.ML.Data.TextLoader.Column> obiekty do `TextReader` zawierająca wszystkie nazwy kolumn i ich typy.</span><span class="sxs-lookup"><span data-stu-id="5f079-191">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the `TextReader` containing all the column names and their types.</span></span> <span data-ttu-id="5f079-192">Zdefiniowany schemat danych wcześniej podczas tworzenia naszej `TaxiTrip` klasy.</span><span class="sxs-lookup"><span data-stu-id="5f079-192">We defined the data schema previously when we created our `TaxiTrip` class.</span></span>

<span data-ttu-id="5f079-193">`TextReader` Klasa zwraca w pełni zainicjowane <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="5f079-193">The `TextReader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="5f079-194">Aby zainicjować `_textLoader` zmienna globalna, aby można było użyć go ponownie w przypadku wymaganych zestawów danych, Dodaj następujący kod po `mlContext` inicjowania:</span><span class="sxs-lookup"><span data-stu-id="5f079-194">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="5f079-195">Dodaj następujący kod jako następnego wiersza kodu w `Main` metodę do wywołania `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-195">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="5f079-196">`Train` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5f079-196">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="5f079-197">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-197">Loads the data.</span></span>
* <span data-ttu-id="5f079-198">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="5f079-198">Extracts and transforms the data.</span></span>
* <span data-ttu-id="5f079-199">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-199">Trains the model.</span></span>
* <span data-ttu-id="5f079-200">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="5f079-200">Saves the model as .zip file.</span></span>
* <span data-ttu-id="5f079-201">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-201">Returns the model.</span></span>

<span data-ttu-id="5f079-202">`Train` Metoda szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-202">The `Train` method trains the model.</span></span> <span data-ttu-id="5f079-203">Tej metody Create, tuż poniżej `Main`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-203">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="5f079-204">Firma Microsoft kończy się sukcesem dwa parametry do `Train` metoda; `MLContext` kontekstu (`mlContext`) i ciągu dla ścieżki zestawu danych (`dataPath`).</span><span class="sxs-lookup"><span data-stu-id="5f079-204">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="5f079-205">Zamierzamy ponownie użyć tej metody do ładowania zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-205">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="5f079-206">Obciążenia i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="5f079-206">Load and transform data</span></span>

<span data-ttu-id="5f079-207">Firma Microsoft będzie załadować dane przy użyciu `_textLoader` zmienna globalna z `dataPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="5f079-207">We'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="5f079-208">Zwraca <xref:Microsoft.ML.Data.IDataView>.</span><span class="sxs-lookup"><span data-stu-id="5f079-208">It returns a <xref:Microsoft.ML.Data.IDataView>.</span></span> <span data-ttu-id="5f079-209">Jako dane wejściowe i wyjściowe transformacji `DataView` jest typem potoku danych podstawowych porównywalne do `IEnumerable` dla `LINQ`.</span><span class="sxs-lookup"><span data-stu-id="5f079-209">As the input and output of Transforms, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="5f079-210">W strukturze ML.NET dane są podobne do widoku SQL.</span><span class="sxs-lookup"><span data-stu-id="5f079-210">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="5f079-211">Jest opóźnieniem ocenianą informatycznych i heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="5f079-211">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="5f079-212">Obiekt jest pierwszą częścią potoku i służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-212">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="5f079-213">W tym samouczku ładuje zestaw danych taksówek podróży informacje przydatne do prognozowania cen biletów.</span><span class="sxs-lookup"><span data-stu-id="5f079-213">For this tutorial, it loads a dataset with taxi trip information useful to predict fares.</span></span> <span data-ttu-id="5f079-214">Służy do tworzenia modelu i szkoleń.</span><span class="sxs-lookup"><span data-stu-id="5f079-214">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="5f079-215">Dodaj następujący kod jako pierwsza linia `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-215">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="5f079-216">W następnych krokach nazywamy kolumny według nazw zdefiniowana w `TaxiTrip` klasy.</span><span class="sxs-lookup"><span data-stu-id="5f079-216">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="5f079-217">Gdy wiedzę i oceniane, domyślne wartości w modelu **etykiety** kolumny będą traktowane jako prawidłowe wartości do można przewidzieć.</span><span class="sxs-lookup"><span data-stu-id="5f079-217">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="5f079-218">Ponieważ chcemy przewidzieć taryfy taksówek w podróży, skopiuj `FareAmount` kolumny na **etykiety** kolumny.</span><span class="sxs-lookup"><span data-stu-id="5f079-218">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="5f079-219">Aby to zrobić, należy użyć `CopyColumnsEstimator` przekształcania klasy, a następnie dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5f079-219">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="5f079-220">Algorytm, który przygotowuje model wymaga **liczbowych** funkcji, więc do przekształcania danych podzielonych na kategorie (`VendorId`, `RateCode`, i `PaymentType`) wartości jako liczby.</span><span class="sxs-lookup"><span data-stu-id="5f079-220">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="5f079-221">Aby to zrobić, należy użyć `OneHotEncodingEstimator` klasy transformacji, która przypisuje różnych liczbowe wartości różne wartości w każdej z kolumn klucza i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5f079-221">To do that, use the `OneHotEncodingEstimator` transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="5f079-222">Ostatnim krokiem w przygotowaniu danych łączy wszystkie kolumny funkcji do **funkcji** przy użyciu kolumny `ColumnConcatenatingEstimator` klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="5f079-222">The last step in data preparation combines all of the feature columns into the **Features** column using the `ColumnConcatenatingEstimator` transformation class.</span></span> <span data-ttu-id="5f079-223">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="5f079-223">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="5f079-224">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5f079-224">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="5f079-225">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="5f079-225">Choose a learning algorithm</span></span>

<span data-ttu-id="5f079-226">Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, możemy wybrać algorytm uczenia (**learner**).</span><span class="sxs-lookup"><span data-stu-id="5f079-226">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="5f079-227">Uczeń przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-227">The learner trains the model.</span></span> <span data-ttu-id="5f079-228">Wybraliśmy **regresji** zadań dla tego problemu, więc używana `FastTreeRegressionTrainer` uczeń, który jest jednym z uczących regresji, dostarczone przez strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5f079-228">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="5f079-229">`FastTreeRegressionTrainer` Uczeń korzysta, wzrostu gradientu.</span><span class="sxs-lookup"><span data-stu-id="5f079-229">The `FastTreeRegressionTrainer` learner utilizes gradient boosting.</span></span> <span data-ttu-id="5f079-230">Ulepszanie gradientu jest techniką problemów regresji uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5f079-230">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="5f079-231">Zbudował każdego drzewa regresji, w sposób stopniowy.</span><span class="sxs-lookup"><span data-stu-id="5f079-231">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="5f079-232">Aby zmierzyć błędów w każdym kroku i popraw go w ciągu następnych widoku jest używana funkcja utraty wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="5f079-232">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="5f079-233">Wynik jest model predykcyjny, który jest faktycznie zespołu słabszy modele predykcyjne.</span><span class="sxs-lookup"><span data-stu-id="5f079-233">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="5f079-234">Aby uzyskać więcej informacji na temat zwiększania wyniku gradientu zobacz [wzmocnione regresji drzewa decyzyjnego](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span><span class="sxs-lookup"><span data-stu-id="5f079-234">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="5f079-235">Dodaj następujący kod do `Train` metody w celu dodania `FastTreeRegressionTrainer` kodowi przetwarzania danych dodane w poprzednim kroku:</span><span class="sxs-lookup"><span data-stu-id="5f079-235">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="5f079-236">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-236">Train the model</span></span>

<span data-ttu-id="5f079-237">Ostatnim krokiem jest do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-237">The final step is to train the model.</span></span> <span data-ttu-id="5f079-238">Uczenie modelu, <xref:Microsoft.ML.Data.TransformerChain>zgodnie z zestawu danych, który został załadowany i przekształcone.</span><span class="sxs-lookup"><span data-stu-id="5f079-238">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="5f079-239">Po zdefiniowaniu estymatora uczenie modelu przy użyciu <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> przy jednoczesnym zapewnieniu dane szkoleniowe już załadowana.</span><span class="sxs-lookup"><span data-stu-id="5f079-239">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="5f079-240">Spowoduje to zwrócenie modelu na potrzeby prognozy.</span><span class="sxs-lookup"><span data-stu-id="5f079-240">This returns a model to use for predictions.</span></span> <span data-ttu-id="5f079-241">`pipeline.Fit()` szkolenie modeli potoku i zwraca `Transformer` na podstawie `DataView` przekazany.</span><span class="sxs-lookup"><span data-stu-id="5f079-241">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="5f079-242">Eksperyment nie jest wykonywane, dopóki nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="5f079-242">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="5f079-243">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="5f079-243">And that's it!</span></span> <span data-ttu-id="5f079-244">Zostały pomyślnie uczony model, który potrafi prognozować taryf taksówek w NYC uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="5f079-244">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="5f079-245">Teraz sklonujemy zapoznaj się z zrozumieć, jak dokładna jest model i Dowiedz się, jak go używać do prognozowania wartości taryfy taksówek.</span><span class="sxs-lookup"><span data-stu-id="5f079-245">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="5f079-246">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="5f079-246">Save the model</span></span>

<span data-ttu-id="5f079-247">W tym momencie masz model typu <xref:Microsoft.ML.Data.TransformerChain> , można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5f079-247">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="5f079-248">Aby zapisać model do pliku zip, Dodaj następujący kod na końcu `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-248">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="5f079-249">Zapisz model jako plik .zip</span><span class="sxs-lookup"><span data-stu-id="5f079-249">Save the model as a .zip file</span></span>

<span data-ttu-id="5f079-250">Tworzenie `SaveModelAsFile` metody tuż za `Train` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-250">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="5f079-251">`SaveModelAsFile` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5f079-251">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="5f079-252">Zapisuje modelu w postaci pliku zip.</span><span class="sxs-lookup"><span data-stu-id="5f079-252">Saves the model as a .zip file.</span></span>

<span data-ttu-id="5f079-253">Musimy utworzyć metodę, aby zapisać modelu mogą być używane ponownie i używane w innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="5f079-253">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="5f079-254">`ITransformer` Ma <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> metodę, która przyjmuje `_modelPath` globalne pola i <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="5f079-254">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="5f079-255">Ponieważ chcemy zapisać ten element jako plik zip, utworzymy `FileStream` bezpośrednio przed wywołaniem `SaveTo` metody.</span><span class="sxs-lookup"><span data-stu-id="5f079-255">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="5f079-256">Dodaj następujący kod do `SaveModelAsFile` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="5f079-256">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="5f079-257">Firma Microsoft może także wyświetlać, której plik został zapisany przy pisaniu komunikatu konsoli, za pomocą `_modelPath`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-257">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="5f079-258">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-258">Evaluate the model</span></span>

<span data-ttu-id="5f079-259">Ocena jest procesem sprawdzania, jak model przewiduje wartości etykiet.</span><span class="sxs-lookup"><span data-stu-id="5f079-259">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="5f079-260">Należy pamiętać, że model sprawia, że dobry prognozy na danych, który nie był używany do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-260">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="5f079-261">Jednym ze sposobów, w tym celu jest podzielenie danych na zestaw szkoleniowy i zestawami danych testowych, co jest wykonywane w ramach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="5f079-261">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="5f079-262">Skoro już uczony model na dane szkoleniowe, możesz zobaczyć, jak sprawdzi się na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5f079-262">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="5f079-263">`Evaluate` Metoda ocenia modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-263">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="5f079-264">Aby utworzyć tę metodę, Dodaj następujący kod poniżej `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-264">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="5f079-265">`Evaluate` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5f079-265">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="5f079-266">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5f079-266">Loads the test dataset.</span></span>
* <span data-ttu-id="5f079-267">Tworzy ewaluatora regresji.</span><span class="sxs-lookup"><span data-stu-id="5f079-267">Creates the regression evaluator.</span></span>
* <span data-ttu-id="5f079-268">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="5f079-268">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="5f079-269">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="5f079-269">Displays the metrics.</span></span>

<span data-ttu-id="5f079-270">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Train` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-270">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="5f079-271">Załadujemy zestawu danych testowych za pomocą wcześniej zainicjowane `_textLoader` zmienna globalna z `_testDataPath` globalne pole.</span><span class="sxs-lookup"><span data-stu-id="5f079-271">We'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="5f079-272">Możesz ocenić modelu przy użyciu tego zestawu danych w celu sprawdzenia jakości.</span><span class="sxs-lookup"><span data-stu-id="5f079-272">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="5f079-273">Dodaj następujący kod do `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-273">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="5f079-274">Następnie użyjemy usługi machine learning `model` parametru (transformatora), aby dane wejściowe funkcji i zwracają prognozy.</span><span class="sxs-lookup"><span data-stu-id="5f079-274">Next, we'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="5f079-275">Dodaj następujący kod do `Evaluate` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="5f079-275">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="5f079-276">`RegressionContext.Evaluate` Metoda oblicza metryk jakości `PredictionModel` przy użyciu określonego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-276">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="5f079-277">Zwraca <xref:Microsoft.ML.Data.RegressionMetrics> obiekt, który zawiera metryki ogólną obliczone przez ewaluatory regresji.</span><span class="sxs-lookup"><span data-stu-id="5f079-277">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="5f079-278">Aby je wyświetlić, aby określić jakość modelu, należy pobrać pierwszy metryki.</span><span class="sxs-lookup"><span data-stu-id="5f079-278">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="5f079-279">Dodaj następujący kod w następnym wierszu `Evaluate` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-279">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="5f079-280">Dodaj następujący kod do ewaluacji modelu i generować metryk oceny:</span><span class="sxs-lookup"><span data-stu-id="5f079-280">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="5f079-281">[RSquared](../resources/glossary.md#coefficient-of-determination) jest kolejną metrykę oceny, modele regresji.</span><span class="sxs-lookup"><span data-stu-id="5f079-281">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="5f079-282">RSquared przyjmuje wartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="5f079-282">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="5f079-283">Im bliżej jego wartość jest bliższa 1, tym lepiej jest model.</span><span class="sxs-lookup"><span data-stu-id="5f079-283">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="5f079-284">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RSquared:</span><span class="sxs-lookup"><span data-stu-id="5f079-284">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="5f079-285">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) jest jedną z metryk oceny modelu regresji.</span><span class="sxs-lookup"><span data-stu-id="5f079-285">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="5f079-286">Im niższa, w tym lepsze model jest.</span><span class="sxs-lookup"><span data-stu-id="5f079-286">The lower it is, the better the model is.</span></span> <span data-ttu-id="5f079-287">Dodaj następujący kod do `Evaluate` metodę, aby wyświetlić wartość RMS:</span><span class="sxs-lookup"><span data-stu-id="5f079-287">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="5f079-288">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="5f079-288">Use the model for predictions</span></span>


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="5f079-289">Przewidywanie wyników danych testu za pomocą modelu i pojedynczego komentarza</span><span class="sxs-lookup"><span data-stu-id="5f079-289">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="5f079-290">Tworzenie `TestSinglePrediction` metody tuż za `Evaluate` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-290">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="5f079-291">`TestSinglePrediction` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5f079-291">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="5f079-292">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5f079-292">Creates a single comment of test data.</span></span>
* <span data-ttu-id="5f079-293">Prognozuje kwota taryfy oparte na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="5f079-293">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="5f079-294">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="5f079-294">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="5f079-295">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="5f079-295">Displays the predicted results.</span></span>

<span data-ttu-id="5f079-296">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `Evaluate` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f079-296">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="5f079-297">Ponieważ chcemy, aby załadować modelu z pliku zip wcześniej zapisany, utworzymy `FileStream` bezpośrednio przed wywołaniem `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="5f079-297">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="5f079-298">Dodaj następujący kod do `TestSinglePrediction` metodę jako następny wiersz:</span><span class="sxs-lookup"><span data-stu-id="5f079-298">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="5f079-299">Gdy `model` jest `transformer` który operuje na wiele wierszy danych, to bardzo typowy scenariusz w środowisku produkcyjnym jest na potrzeby prognoz na poszczególne przykłady.</span><span class="sxs-lookup"><span data-stu-id="5f079-299">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="5f079-300"><xref:Microsoft.ML.PredictionEngine%602> Jest otoką, który jest zwracany z `CreatePredictionEngine` metody.</span><span class="sxs-lookup"><span data-stu-id="5f079-300">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="5f079-301">Możemy dodać następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz w `Predict` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-301">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="5f079-302">Ten samouczek używa test dwustronnej tej klasy.</span><span class="sxs-lookup"><span data-stu-id="5f079-302">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="5f079-303">Później możesz dodać inne scenariusze, aby eksperymentować z modelu.</span><span class="sxs-lookup"><span data-stu-id="5f079-303">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="5f079-304">Dodaj podróży do testowania uczonego modelu prognozowania kosztu `Predict` metody przez utworzenie wystąpienia `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="5f079-304">Add a trip to test the trained model's prediction of cost in the `Predict` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="5f079-305">Firma Microsoft może używać, aby przewidzieć opłatę, w oparciu o jedno wystąpienie danych taksówek w podróży.</span><span class="sxs-lookup"><span data-stu-id="5f079-305">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="5f079-306">Aby uzyskać prognozę, użyj <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> na danych.</span><span class="sxs-lookup"><span data-stu-id="5f079-306">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="5f079-307">Należy pamiętać, że dane wejściowe to ciąg, a model zawiera cechowania.</span><span class="sxs-lookup"><span data-stu-id="5f079-307">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="5f079-308">Potok jest zsynchronizowany podczas uczenia i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="5f079-308">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="5f079-309">Nie trzeba napisać kod przetwarzania wstępnego cechowania specjalnie dla prognoz i zajmuje się tego samego interfejsu API i usługi batch jednorazowe prognozy.</span><span class="sxs-lookup"><span data-stu-id="5f079-309">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="5f079-310">Aby wyświetlić przewidywane opłacie określonego podróży, Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="5f079-310">To display the predicted fare of the specified trip, add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="5f079-311">Uruchom program, aby zobaczyć taryfy przewidywane taksówek dla przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="5f079-311">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="5f079-312">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="5f079-312">Congratulations!</span></span> <span data-ttu-id="5f079-313">Już teraz pomyślnie wbudowany model uczenia maszynowego do przewidywania taksówek podróży opłaty, ocenić jego dokładności i używana do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="5f079-313">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="5f079-314">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="5f079-314">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5f079-315">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5f079-315">Next steps</span></span>

<span data-ttu-id="5f079-316">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5f079-316">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5f079-317">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="5f079-317">Understand the problem</span></span>
> * <span data-ttu-id="5f079-318">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="5f079-318">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="5f079-319">Przygotuj i zrozumieć dane</span><span class="sxs-lookup"><span data-stu-id="5f079-319">Prepare and understand the data</span></span>
> * <span data-ttu-id="5f079-320">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="5f079-320">Create a learning pipeline</span></span>
> * <span data-ttu-id="5f079-321">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="5f079-321">Load and transform the data</span></span>
> * <span data-ttu-id="5f079-322">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="5f079-322">Choose a learning algorithm</span></span>
> * <span data-ttu-id="5f079-323">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-323">Train the model</span></span>
> * <span data-ttu-id="5f079-324">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="5f079-324">Evaluate the model</span></span>
> * <span data-ttu-id="5f079-325">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="5f079-325">Use the model for predictions</span></span>

<span data-ttu-id="5f079-326">Przejdź do następnego samouczka, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="5f079-326">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5f079-327">Klastrowanie zestawu danych Iris</span><span class="sxs-lookup"><span data-stu-id="5f079-327">Iris clustering</span></span>](iris-clustering.md)
