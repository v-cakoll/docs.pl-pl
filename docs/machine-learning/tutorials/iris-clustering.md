---
title: 'Samouczek: Kategoryzuj kwiaty iris - k-oznacza klastrowanie'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 174907adac5741d5cc7d02cb134921debc586061
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241094"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="98f42-103">Samouczek: Kategoryzuj kwiaty przysiadów za pomocą k-oznacza klastrowanie z ML.NET</span><span class="sxs-lookup"><span data-stu-id="98f42-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="98f42-104">W tym samouczku przedstawiono sposób używania ML.NET do tworzenia [modelu klastrowania](../resources/tasks.md#clustering) dla [zestawu danych kwiatu przysłonki](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="98f42-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="98f42-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="98f42-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="98f42-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="98f42-106">Understand the problem</span></span>
> - <span data-ttu-id="98f42-107">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="98f42-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="98f42-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="98f42-108">Prepare the data</span></span>
> - <span data-ttu-id="98f42-109">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="98f42-109">Load and transform the data</span></span>
> - <span data-ttu-id="98f42-110">Wybierz algorytm uczenia się</span><span class="sxs-lookup"><span data-stu-id="98f42-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="98f42-111">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="98f42-111">Train the model</span></span>
> - <span data-ttu-id="98f42-112">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="98f42-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98f42-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="98f42-113">Prerequisites</span></span>

- <span data-ttu-id="98f42-114">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="98f42-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="98f42-115">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="98f42-115">Understand the problem</span></span>

<span data-ttu-id="98f42-116">Ten problem polega na podzieleniu zestawu kwiatów iris w różnych grupach w oparciu o cechy kwiatu.</span><span class="sxs-lookup"><span data-stu-id="98f42-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="98f42-117">Cechy te są długość i szerokość działka oraz długość i szerokość płatka.</span><span class="sxs-lookup"><span data-stu-id="98f42-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="98f42-118">W tym samouczku załóżmy, że typ każdego kwiatu jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="98f42-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="98f42-119">Chcesz poznać strukturę zestawu danych z funkcji i przewidzieć, jak wystąpienie danych pasuje do tej struktury.</span><span class="sxs-lookup"><span data-stu-id="98f42-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="98f42-120">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="98f42-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="98f42-121">Ponieważ nie wiesz, do której grupy należy każdy kwiat, wybierasz [zadanie uczenia maszynowego bez nadzoru.](../resources/glossary.md#unsupervised-machine-learning)</span><span class="sxs-lookup"><span data-stu-id="98f42-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="98f42-122">Aby podzielić zestaw danych w grupach w taki sposób, że elementy w tej samej grupie są bardziej podobne do siebie niż w innych grupach, należy użyć zadania uczenia maszynowego [klastrowania.](../resources/tasks.md#clustering)</span><span class="sxs-lookup"><span data-stu-id="98f42-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="98f42-123">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="98f42-123">Create a console application</span></span>

1. <span data-ttu-id="98f42-124">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98f42-124">Open Visual Studio.</span></span> <span data-ttu-id="98f42-125">Wybierz **pozycję Plik** > **nowy** > **projekt** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="98f42-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="98f42-126">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="98f42-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="98f42-127">Następnie wybierz szablon projektu **aplikacji konsoli (.NET Core).**</span><span class="sxs-lookup"><span data-stu-id="98f42-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="98f42-128">W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="98f42-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="98f42-129">Utwórz katalog o nazwie *Dane* w projekcie w celu przechowywania zestawu danych i plików modelu:</span><span class="sxs-lookup"><span data-stu-id="98f42-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="98f42-130">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="98f42-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="98f42-131">Wpisz "Dane" i naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="98f42-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="98f42-132">Zainstaluj pakiet **Microsoft.ML** NuGet:</span><span class="sxs-lookup"><span data-stu-id="98f42-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="98f42-133">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="98f42-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="98f42-134">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML** i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="98f42-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="98f42-135">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z warunkami licencyjnymi dla wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="98f42-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="98f42-136">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="98f42-136">Prepare the data</span></span>

1. <span data-ttu-id="98f42-137">Pobierz zestaw danych [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i zapisz go w folderze *Dane* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="98f42-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="98f42-138">Aby uzyskać więcej informacji na temat zestawu danych przysłonki, zobacz [zestaw danych kwiatów iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia strony i [iris data set](https://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="98f42-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="98f42-139">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *iris.data* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="98f42-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="98f42-140">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="98f42-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="98f42-141">Plik *iris.data* zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="98f42-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="98f42-142">długość sepal w centymetrach</span><span class="sxs-lookup"><span data-stu-id="98f42-142">sepal length in centimetres</span></span>
- <span data-ttu-id="98f42-143">szerokość działka w centymetrach</span><span class="sxs-lookup"><span data-stu-id="98f42-143">sepal width in centimetres</span></span>
- <span data-ttu-id="98f42-144">długość płatka w centymetrach</span><span class="sxs-lookup"><span data-stu-id="98f42-144">petal length in centimetres</span></span>
- <span data-ttu-id="98f42-145">szerokość płatka w centymetrach</span><span class="sxs-lookup"><span data-stu-id="98f42-145">petal width in centimetres</span></span>
- <span data-ttu-id="98f42-146">rodzaj kwiatu przysłania</span><span class="sxs-lookup"><span data-stu-id="98f42-146">type of iris flower</span></span>

<span data-ttu-id="98f42-147">Ze względu na przykład klastrowania ten samouczek ignoruje ostatnią kolumnę.</span><span class="sxs-lookup"><span data-stu-id="98f42-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="98f42-148">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="98f42-148">Create data classes</span></span>

<span data-ttu-id="98f42-149">Tworzenie klas dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="98f42-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="98f42-150">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="98f42-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="98f42-151">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="98f42-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="98f42-152">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="98f42-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="98f42-153">Dodaj następującą `using` dyrektywę do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="98f42-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="98f42-154">Usuń istniejącą definicję klasy i dodaj następujący `IrisData` kod, który definiuje klasy i `ClusterPrediction`, do *pliku IrisData.cs:*</span><span class="sxs-lookup"><span data-stu-id="98f42-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="98f42-155">`IrisData`jest klasą danych wejściowych i ma definicje dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="98f42-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="98f42-156">Użyj [atrybutu LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute) aby określić indeksy kolumn źródłowych w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="98f42-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="98f42-157">Klasa `ClusterPrediction` reprezentuje dane wyjściowe modelu klastrowania zastosowane `IrisData` do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="98f42-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="98f42-158">Użyj [Atrybutcolumnname,](xref:Microsoft.ML.Data.ColumnNameAttribute) aby `PredictedClusterId` `Distances` powiązać i pola odpowiednio **predictedlabel** i **score** kolumn.</span><span class="sxs-lookup"><span data-stu-id="98f42-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="98f42-159">W przypadku zadania klastrowania kolumny te mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="98f42-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="98f42-160">**Kolumna PredictedLabel** zawiera identyfikator przewidywanego klastra.</span><span class="sxs-lookup"><span data-stu-id="98f42-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="98f42-161">**Kolumna Wynik** zawiera tablicę z kwadratowymi odległościami euklidesa do centroidklastra.</span><span class="sxs-lookup"><span data-stu-id="98f42-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="98f42-162">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="98f42-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="98f42-163">Typ `float` służy do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i przewidywania.</span><span class="sxs-lookup"><span data-stu-id="98f42-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="98f42-164">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="98f42-164">Define data and model paths</span></span>

<span data-ttu-id="98f42-165">Wróć do *pliku Program.cs* i dodaj dwa pola, aby przytrzymać ścieżki do pliku zestawu danych i do pliku, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="98f42-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="98f42-166">`_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="98f42-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="98f42-167">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="98f42-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="98f42-168">Dodaj następujący kod tuż `Main` nad metodą, aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="98f42-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="98f42-169">Aby skompilować poprzedni kod, dodaj `using` następujące dyrektywy u góry *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="98f42-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="98f42-170">Tworzenie kontekstu ml</span><span class="sxs-lookup"><span data-stu-id="98f42-170">Create ML context</span></span>

<span data-ttu-id="98f42-171">Dodaj następujące `using` dodatkowe dyrektywy w górnej części *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="98f42-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="98f42-172">W `Main` metodzie zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="98f42-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="98f42-173">Klasa <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> reprezentuje środowisko uczenia maszynowego i zapewnia mechanizmy rejestrowania i punkty wejścia do ładowania danych, szkolenia modelu, przewidywania i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="98f42-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="98f42-174">Jest to porównywalne koncepcyjnie do używania `DbContext` w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="98f42-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="98f42-175">Konfigurowanie ładowania danych</span><span class="sxs-lookup"><span data-stu-id="98f42-175">Set up data loading</span></span>

<span data-ttu-id="98f42-176">Dodaj następujący kod `Main` do metody, aby skonfigurować sposób ładowania danych:</span><span class="sxs-lookup"><span data-stu-id="98f42-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="98f42-177">Metoda [ `MLContext.Data.LoadFromTextFile` rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) ogólnego wnioskuje schemat zestawu danych `IrisData` z <xref:Microsoft.ML.IDataView> podanego typu i zwraca, które mogą być używane jako dane wejściowe dla transformatorów.</span><span class="sxs-lookup"><span data-stu-id="98f42-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="98f42-178">Tworzenie potoku uczenia się</span><span class="sxs-lookup"><span data-stu-id="98f42-178">Create a learning pipeline</span></span>

<span data-ttu-id="98f42-179">W tym samouczku potok uczenia się zadania klastrowania składa się z dwóch następujących kroków:</span><span class="sxs-lookup"><span data-stu-id="98f42-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="98f42-180">łączenie załadowanych kolumn w jedną **kolumnę Funkcji,** która jest używana przez trenera klastrowania;</span><span class="sxs-lookup"><span data-stu-id="98f42-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="98f42-181">użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> trenera do szkolenia modelu przy użyciu algorytmu klastrowania k-means++.</span><span class="sxs-lookup"><span data-stu-id="98f42-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="98f42-182">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="98f42-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="98f42-183">Kod określa, że zestaw danych powinien być podzielony na trzy klastry.</span><span class="sxs-lookup"><span data-stu-id="98f42-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="98f42-184">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="98f42-184">Train the model</span></span>

<span data-ttu-id="98f42-185">Kroki dodane w poprzednich sekcjach przygotowały potok do szkolenia, jednak żadne nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="98f42-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="98f42-186">Dodaj następujący wiersz `Main` do metody, aby wykonać ładowanie danych i szkolenie modelu:</span><span class="sxs-lookup"><span data-stu-id="98f42-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="98f42-187">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="98f42-187">Save the model</span></span>

<span data-ttu-id="98f42-188">W tym momencie masz model, który można zintegrować z dowolnym z istniejących lub nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="98f42-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="98f42-189">Aby zapisać model w pliku zip, dodaj do `Main` metody następujący kod:</span><span class="sxs-lookup"><span data-stu-id="98f42-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="98f42-190">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="98f42-190">Use the model for predictions</span></span>

<span data-ttu-id="98f42-191">Aby przewidywań, należy <xref:Microsoft.ML.PredictionEngine%602> użyć klasy, która przyjmuje wystąpień typu wejściowego za pośrednictwem potoku transformatora i tworzy wystąpienia typu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="98f42-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="98f42-192">Dodaj następujący wiersz `Main` do metody, aby utworzyć wystąpienie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="98f42-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="98f42-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="98f42-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="98f42-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="98f42-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="98f42-195">Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="98f42-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="98f42-196">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98f42-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="98f42-197">Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="98f42-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="98f42-198">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="98f42-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="98f42-199">Utwórz `TestIrisData` klasę do umieszczenia wystąpień danych testowych:</span><span class="sxs-lookup"><span data-stu-id="98f42-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="98f42-200">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="98f42-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="98f42-201">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="98f42-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="98f42-202">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="98f42-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="98f42-203">Zmodyfikuj klasę, aby była statyczna, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="98f42-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="98f42-204">W tym samouczku przedstawiono jedno wystąpienie danych przysłonki w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="98f42-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="98f42-205">Można dodać inne scenariusze do eksperymentowania z modelem.</span><span class="sxs-lookup"><span data-stu-id="98f42-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="98f42-206">Dodaj następujący kod `TestIrisData` do klasy:</span><span class="sxs-lookup"><span data-stu-id="98f42-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="98f42-207">Aby dowiedzieć się klastra, do którego należy określony element, wróć do *pliku* Program.cs `Main` i dodaj następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="98f42-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="98f42-208">Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości od tego wystąpienia do centroidów klastra.</span><span class="sxs-lookup"><span data-stu-id="98f42-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="98f42-209">Wyniki powinny być podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="98f42-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="98f42-210">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="98f42-210">Congratulations!</span></span> <span data-ttu-id="98f42-211">Teraz pomyślnie skonstruowano model uczenia maszynowego do klastrowania przysłonek i użyto go do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="98f42-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="98f42-212">Kod źródłowy tego samouczka można znaleźć w repozytorium GitHub [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering)</span><span class="sxs-lookup"><span data-stu-id="98f42-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="98f42-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="98f42-213">Next steps</span></span>

<span data-ttu-id="98f42-214">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="98f42-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="98f42-215">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="98f42-215">Understand the problem</span></span>
> - <span data-ttu-id="98f42-216">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="98f42-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="98f42-217">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="98f42-217">Prepare the data</span></span>
> - <span data-ttu-id="98f42-218">Ładowanie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="98f42-218">Load and transform the data</span></span>
> - <span data-ttu-id="98f42-219">Wybierz algorytm uczenia się</span><span class="sxs-lookup"><span data-stu-id="98f42-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="98f42-220">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="98f42-220">Train the model</span></span>
> - <span data-ttu-id="98f42-221">Użyj modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="98f42-221">Use the model for predictions</span></span>

<span data-ttu-id="98f42-222">Sprawdź nasze repozytorium GitHub, aby kontynuować naukę i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="98f42-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="98f42-223">repozytorium GitHub dotnet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="98f42-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
