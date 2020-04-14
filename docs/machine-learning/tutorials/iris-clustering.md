---
title: 'Samouczek: Kategoryzuj kwiaty tęczówki - k-oznacza klastrowanie'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 03ce1a5f3ef4d4da01f848cac0c520a5a6aaf4bf
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242793"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="d95f2-103">Poradnik: Kategoryzuj kwiaty tęczówki za pomocą k-oznacza klastrowanie z ML.NET</span><span class="sxs-lookup"><span data-stu-id="d95f2-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="d95f2-104">W tym samouczku pokazano, jak używać ML.NET do tworzenia [modelu klastrowania](../resources/tasks.md#clustering) dla [zestawu danych kwiatu tęczówki](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="d95f2-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="d95f2-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d95f2-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d95f2-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="d95f2-106">Understand the problem</span></span>
> - <span data-ttu-id="d95f2-107">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="d95f2-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="d95f2-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-108">Prepare the data</span></span>
> - <span data-ttu-id="d95f2-109">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-109">Load and transform the data</span></span>
> - <span data-ttu-id="d95f2-110">Wybieranie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="d95f2-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="d95f2-111">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="d95f2-111">Train the model</span></span>
> - <span data-ttu-id="d95f2-112">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="d95f2-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d95f2-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d95f2-113">Prerequisites</span></span>

- <span data-ttu-id="d95f2-114">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="d95f2-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="d95f2-115">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="d95f2-115">Understand the problem</span></span>

<span data-ttu-id="d95f2-116">Ten problem polega na podzieleniu zestawu kwiatów tęczówki w różnych grupach na podstawie cech kwiatowych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="d95f2-117">Cechy te to długość i szerokość działki oraz długość i szerokość płatka.</span><span class="sxs-lookup"><span data-stu-id="d95f2-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="d95f2-118">W tym samouczku załóżmy, że typ każdego kwiatu jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="d95f2-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="d95f2-119">Chcesz dowiedzieć się struktury zestawu danych z funkcji i przewidzieć, jak wystąpienie danych pasuje do tej struktury.</span><span class="sxs-lookup"><span data-stu-id="d95f2-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d95f2-120">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="d95f2-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d95f2-121">Ponieważ nie wiesz, do której grupy należy każdy kwiat, wybierz [zadanie uczenia maszynowego bez nadzoru.](../resources/glossary.md#unsupervised-machine-learning)</span><span class="sxs-lookup"><span data-stu-id="d95f2-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="d95f2-122">Aby podzielić zestaw danych w grupach w taki sposób, aby elementy w tej samej grupie były bardziej podobne do siebie niż w innych grupach, należy użyć zadania uczenia maszynowego [klastrowania.](../resources/tasks.md#clustering)</span><span class="sxs-lookup"><span data-stu-id="d95f2-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d95f2-123">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="d95f2-123">Create a console application</span></span>

1. <span data-ttu-id="d95f2-124">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d95f2-124">Open Visual Studio.</span></span> <span data-ttu-id="d95f2-125">Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="d95f2-126">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="d95f2-127">Następnie wybierz szablon projektu **aplikacji konsoli (net core).**</span><span class="sxs-lookup"><span data-stu-id="d95f2-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="d95f2-128">W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="d95f2-129">Utwórz katalog o nazwie *Dane* w projekcie, aby przechowywać zestaw danych i pliki modelu:</span><span class="sxs-lookup"><span data-stu-id="d95f2-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="d95f2-130">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="d95f2-131">Wpisz "Dane" i naciśnij enter.</span><span class="sxs-lookup"><span data-stu-id="d95f2-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="d95f2-132">Zainstaluj pakiet **Microsoft.ML** NuGet:</span><span class="sxs-lookup"><span data-stu-id="d95f2-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="d95f2-133">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d95f2-134">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="d95f2-135">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d95f2-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="d95f2-136">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-136">Prepare the data</span></span>

1. <span data-ttu-id="d95f2-137">Pobierz zestaw danych [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i zapisz go w folderze *Dane* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="d95f2-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="d95f2-138">Aby uzyskać więcej informacji na temat zestawu danych tęczówki, zobacz stronę Wikipedii [zestaw danych kwiatu tęczówki](https://en.wikipedia.org/wiki/Iris_flower_data_set) i stronę [Zestaw danych Iris,](http://archive.ics.uci.edu/ml/datasets/Iris) która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="d95f2-139">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *iris.data* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="d95f2-140">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="d95f2-141">Plik *iris.data* zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="d95f2-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="d95f2-142">długość działki w centymetrach</span><span class="sxs-lookup"><span data-stu-id="d95f2-142">sepal length in centimeters</span></span>
- <span data-ttu-id="d95f2-143">szerokość działki w centymetrach</span><span class="sxs-lookup"><span data-stu-id="d95f2-143">sepal width in centimeters</span></span>
- <span data-ttu-id="d95f2-144">długość płatka w centymetrach</span><span class="sxs-lookup"><span data-stu-id="d95f2-144">petal length in centimeters</span></span>
- <span data-ttu-id="d95f2-145">szerokość płatka w centymetrach</span><span class="sxs-lookup"><span data-stu-id="d95f2-145">petal width in centimeters</span></span>
- <span data-ttu-id="d95f2-146">rodzaj kwiatu tęczówki</span><span class="sxs-lookup"><span data-stu-id="d95f2-146">type of iris flower</span></span>

<span data-ttu-id="d95f2-147">Dla dobra przykładu klastrowania ten samouczek ignoruje ostatnią kolumnę.</span><span class="sxs-lookup"><span data-stu-id="d95f2-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="d95f2-148">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-148">Create data classes</span></span>

<span data-ttu-id="d95f2-149">Tworzenie klas dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="d95f2-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="d95f2-150">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d95f2-151">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d95f2-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="d95f2-152">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="d95f2-153">Dodaj następującą `using` dyrektywę do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="d95f2-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="d95f2-154">Usuń istniejącą definicję klasy i dodaj następujący `IrisData` kod, który definiuje klasy i `ClusterPrediction`, do *pliku IrisData.cs:*</span><span class="sxs-lookup"><span data-stu-id="d95f2-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="d95f2-155">`IrisData`jest klasą danych wejściowych i zawiera definicje dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="d95f2-156">Użyj [Atrybutu LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="d95f2-157">Klasa `ClusterPrediction` reprezentuje dane wyjściowe modelu klastrowania `IrisData` zastosowanego do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d95f2-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="d95f2-158">Użyj [columnname](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut powiązać `PredictedClusterId` `Distances` i pola do **PredictedLabel** i **Wynik** kolumny odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d95f2-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="d95f2-159">W przypadku zadania klastrowania kolumny te mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="d95f2-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="d95f2-160">**PredictedLabel** kolumna zawiera identyfikator przewidywanego klastra.</span><span class="sxs-lookup"><span data-stu-id="d95f2-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="d95f2-161">**Kolumna Wynik** zawiera tablicę z kwadratowymi odległościami euklidesowymi do centroidów klastra.</span><span class="sxs-lookup"><span data-stu-id="d95f2-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="d95f2-162">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="d95f2-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="d95f2-163">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywanie.</span><span class="sxs-lookup"><span data-stu-id="d95f2-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="d95f2-164">Definiowanie danych i ścieżek modelu</span><span class="sxs-lookup"><span data-stu-id="d95f2-164">Define data and model paths</span></span>

<span data-ttu-id="d95f2-165">Wróć do pliku *Program.cs* i dodaj dwa pola, aby przytrzymać ścieżki do pliku zestawu danych i do pliku, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="d95f2-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="d95f2-166">`_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="d95f2-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="d95f2-167">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="d95f2-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="d95f2-168">Dodaj następujący kod tuż `Main` nad metodą, aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="d95f2-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="d95f2-169">Aby skompilować poprzedni kod, `using` dodaj następujące dyrektywy u góry *pliku Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="d95f2-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="d95f2-170">Tworzenie kontekstu ML</span><span class="sxs-lookup"><span data-stu-id="d95f2-170">Create ML context</span></span>

<span data-ttu-id="d95f2-171">Dodaj następujące `using` dodatkowe dyrektywy w górnej części *pliku Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="d95f2-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="d95f2-172">W `Main` metodzie zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="d95f2-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="d95f2-173">Klasa <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> reprezentuje środowisko uczenia maszynowego i zapewnia mechanizmy rejestrowania i wprowadzania punktów do ładowania danych, szkolenia modelu, przewidywania i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="d95f2-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="d95f2-174">Jest to porównywalne koncepcyjnie do korzystania `DbContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="d95f2-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="d95f2-175">Konfigurowanie ładowania danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-175">Set up data loading</span></span>

<span data-ttu-id="d95f2-176">Dodaj następujący kod `Main` do metody, aby skonfigurować sposób ładowania danych:</span><span class="sxs-lookup"><span data-stu-id="d95f2-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="d95f2-177">Metoda [ `MLContext.Data.LoadFromTextFile` rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) ogólnego wnioskuje schemat zestawu danych `IrisData` z podanego typu i zwraca, <xref:Microsoft.ML.IDataView> który może służyć jako dane wejściowe dla transformatorów.</span><span class="sxs-lookup"><span data-stu-id="d95f2-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="d95f2-178">Tworzenie potoku nauki</span><span class="sxs-lookup"><span data-stu-id="d95f2-178">Create a learning pipeline</span></span>

<span data-ttu-id="d95f2-179">W tym samouczku potok uczenia się zadania klastrowania składa się z dwóch następujących kroków:</span><span class="sxs-lookup"><span data-stu-id="d95f2-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="d95f2-180">łączyć załadowane kolumny do jednej kolumny **Funkcje,** która jest używana przez trenera klastrowania;</span><span class="sxs-lookup"><span data-stu-id="d95f2-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="d95f2-181">użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> trenera, aby wyszkolić model za pomocą algorytmu klastrowania k-means++.</span><span class="sxs-lookup"><span data-stu-id="d95f2-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="d95f2-182">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="d95f2-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="d95f2-183">Kod określa, że zestaw danych powinny być podzielone na trzy klastry.</span><span class="sxs-lookup"><span data-stu-id="d95f2-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="d95f2-184">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="d95f2-184">Train the model</span></span>

<span data-ttu-id="d95f2-185">Kroki dodane w poprzednich sekcjach przygotował potok do szkolenia, jednak żaden nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="d95f2-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="d95f2-186">Dodaj następujący wiersz `Main` do metody, aby wykonać ładowanie danych i szkolenie modelu:</span><span class="sxs-lookup"><span data-stu-id="d95f2-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="d95f2-187">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="d95f2-187">Save the model</span></span>

<span data-ttu-id="d95f2-188">W tym momencie masz model, który można zintegrować z dowolnej istniejącej lub nowej aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="d95f2-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="d95f2-189">Aby zapisać model w pliku zip, dodaj do `Main` metody następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d95f2-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="d95f2-190">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="d95f2-190">Use the model for predictions</span></span>

<span data-ttu-id="d95f2-191">Aby prognoz, należy <xref:Microsoft.ML.PredictionEngine%602> użyć klasy, która przyjmuje wystąpienia typu wejściowego za pośrednictwem potoku transformatora i tworzy wystąpienia typu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d95f2-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="d95f2-192">Dodaj następujący wiersz `Main` do metody, aby utworzyć wystąpienie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="d95f2-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="d95f2-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="d95f2-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="d95f2-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="d95f2-195">Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="d95f2-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="d95f2-196">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d95f2-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="d95f2-197">Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="d95f2-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="d95f2-198">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="d95f2-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="d95f2-199">Utwórz `TestIrisData` klasę do domu wystąpienia danych testowych:</span><span class="sxs-lookup"><span data-stu-id="d95f2-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="d95f2-200">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d95f2-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="d95f2-201">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d95f2-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="d95f2-202">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="d95f2-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="d95f2-203">Zmodyfikuj klasę jako statyczną, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d95f2-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="d95f2-204">W tym samouczku przedstawiono jedno wystąpienie danych tęczówki w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="d95f2-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="d95f2-205">Można dodać inne scenariusze do eksperymentowania z modelem.</span><span class="sxs-lookup"><span data-stu-id="d95f2-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="d95f2-206">Dodaj następujący kod `TestIrisData` do klasy:</span><span class="sxs-lookup"><span data-stu-id="d95f2-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="d95f2-207">Aby dowiedzieć się, klaster, do którego należy *Program.cs* określony element, wróć do pliku `Main` Program.cs i dodaj następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="d95f2-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="d95f2-208">Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości od tego wystąpienia do centroidów klastra.</span><span class="sxs-lookup"><span data-stu-id="d95f2-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="d95f2-209">Wyniki powinny być podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="d95f2-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="d95f2-210">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="d95f2-210">Congratulations!</span></span> <span data-ttu-id="d95f2-211">Pomyślnie zbudowano model uczenia maszynowego do klastrowania tęczówki i użyto go do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="d95f2-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="d95f2-212">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub.</span><span class="sxs-lookup"><span data-stu-id="d95f2-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d95f2-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d95f2-213">Next steps</span></span>

<span data-ttu-id="d95f2-214">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d95f2-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d95f2-215">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="d95f2-215">Understand the problem</span></span>
> - <span data-ttu-id="d95f2-216">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="d95f2-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="d95f2-217">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-217">Prepare the data</span></span>
> - <span data-ttu-id="d95f2-218">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="d95f2-218">Load and transform the data</span></span>
> - <span data-ttu-id="d95f2-219">Wybieranie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="d95f2-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="d95f2-220">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="d95f2-220">Train the model</span></span>
> - <span data-ttu-id="d95f2-221">Użyj modelu do prognoz</span><span class="sxs-lookup"><span data-stu-id="d95f2-221">Use the model for predictions</span></span>

<span data-ttu-id="d95f2-222">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować naukę i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="d95f2-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d95f2-223">repozytorium Dotnet/machinelearning GitHub</span><span class="sxs-lookup"><span data-stu-id="d95f2-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
