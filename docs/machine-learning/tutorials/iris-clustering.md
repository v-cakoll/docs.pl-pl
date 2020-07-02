---
title: 'Samouczek: kategoryzowanie kwiatów'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 0cc42a196589a7ffe77300c9f2cd9cb28229a0a9
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803979"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="52007-103">Samouczek: kategoryzowanie kwiatów w ramach Iris przy użyciu k-oznacza klastrowanie z ML.NET</span><span class="sxs-lookup"><span data-stu-id="52007-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="52007-104">W tym samouczku pokazano, jak za pomocą ML.NET utworzyć [Model klastrowania](../resources/tasks.md#clustering) dla [zestawu danych dla elementu pokwiatowego Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="52007-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="52007-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="52007-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="52007-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="52007-106">Understand the problem</span></span>
> - <span data-ttu-id="52007-107">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="52007-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="52007-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="52007-108">Prepare the data</span></span>
> - <span data-ttu-id="52007-109">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="52007-109">Load and transform the data</span></span>
> - <span data-ttu-id="52007-110">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="52007-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="52007-111">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="52007-111">Train the model</span></span>
> - <span data-ttu-id="52007-112">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="52007-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52007-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="52007-113">Prerequisites</span></span>

- <span data-ttu-id="52007-114">[Program Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszy albo program visual Studio 2017 w wersji 15,6 lub nowszej z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52007-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="52007-115">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="52007-115">Understand the problem</span></span>

<span data-ttu-id="52007-116">Ten problem polega na rozdzieleniu zestawu zakwiatek Iris w różnych grupach w oparciu o funkcje kwiatowe.</span><span class="sxs-lookup"><span data-stu-id="52007-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="52007-117">Te funkcje to długość i szerokość słupka oraz długość i szerokość płatne.</span><span class="sxs-lookup"><span data-stu-id="52007-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="52007-118">W tym samouczku przyjęto założenie, że typ każdego kwiatu jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="52007-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="52007-119">Chcesz poznać strukturę zestawu danych z funkcji i przewidywania, jak wystąpienie danych pasuje do tej struktury.</span><span class="sxs-lookup"><span data-stu-id="52007-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="52007-120">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="52007-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="52007-121">Ponieważ nie wiesz, do której grupy należą każdy kwiat, wybierz zadanie [nienadzorowane Uczenie maszynowe](../resources/glossary.md#unsupervised-machine-learning) .</span><span class="sxs-lookup"><span data-stu-id="52007-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="52007-122">Aby podzielić zestaw danych w grupach w taki sposób, że elementy w tej samej grupie są bardziej podobne do siebie, niż w przypadku innych grup, Użyj zadania uczenia [maszynowego](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="52007-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="52007-123">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="52007-123">Create a console application</span></span>

1. <span data-ttu-id="52007-124">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52007-124">Open Visual Studio.</span></span> <span data-ttu-id="52007-125">Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** .</span><span class="sxs-lookup"><span data-stu-id="52007-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="52007-126">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#** , a następnie węzeł **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="52007-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="52007-127">Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="52007-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="52007-128">W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="52007-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="52007-129">Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli:</span><span class="sxs-lookup"><span data-stu-id="52007-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="52007-130">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj**  >  **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="52007-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="52007-131">Wpisz "Data" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="52007-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="52007-132">Zainstaluj pakiet NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="52007-132">Install the **Microsoft.ML** NuGet package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="52007-133">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="52007-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="52007-134">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml** i wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="52007-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="52007-135">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="52007-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="52007-136">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="52007-136">Prepare the data</span></span>

1. <span data-ttu-id="52007-137">Pobierz zestaw danych [Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i Zapisz go w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="52007-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="52007-138">Aby uzyskać więcej informacji na temat zestawu danych Iris, zapoznaj się ze stroną sieci Web dotyczącą [zestawu danych kwitnienia Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) oraz stroną [zestawu danych Iris](http://archive.ics.uci.edu/ml/datasets/Iris) , która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="52007-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="52007-139">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Iris. Data* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="52007-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="52007-140">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="52007-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="52007-141">Plik *Iris. Data* zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="52007-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="52007-142">słupka długość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="52007-142">sepal length in centimeters</span></span>
- <span data-ttu-id="52007-143">słupka szerokość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="52007-143">sepal width in centimeters</span></span>
- <span data-ttu-id="52007-144">płatna długość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="52007-144">petal length in centimeters</span></span>
- <span data-ttu-id="52007-145">połówkowe szerokości w centymetrach</span><span class="sxs-lookup"><span data-stu-id="52007-145">petal width in centimeters</span></span>
- <span data-ttu-id="52007-146">Typ kwitnienia tęczówki</span><span class="sxs-lookup"><span data-stu-id="52007-146">type of iris flower</span></span>

<span data-ttu-id="52007-147">W ramach przykładu klastrowania ten samouczek ignoruje ostatnią kolumnę.</span><span class="sxs-lookup"><span data-stu-id="52007-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="52007-148">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="52007-148">Create data classes</span></span>

<span data-ttu-id="52007-149">Utwórz klasy dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="52007-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="52007-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="52007-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="52007-151">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="52007-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="52007-152">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="52007-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="52007-153">Dodaj następującą `using` dyrektywę do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="52007-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="52007-154">Usuń istniejącą definicję klasy i Dodaj następujący kod, który definiuje klasy `IrisData` i `ClusterPrediction` , do pliku *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="52007-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="52007-155">`IrisData`jest klasą danych wejściowych i zawiera definicje dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="52007-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="52007-156">Użyj atrybutu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="52007-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="52007-157">`ClusterPrediction`Klasa reprezentuje dane wyjściowe modelu klastrowania zastosowanego do `IrisData` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="52007-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="52007-158">Użyj atrybutu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) , aby powiązać `PredictedClusterId` pola i z `Distances` kolumnami **PredictedLabel** i **Score** odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="52007-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="52007-159">W przypadku zadania klastrowania te kolumny mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="52007-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="52007-160">Kolumna **PredictedLabel** zawiera identyfikator przewidywanego klastra.</span><span class="sxs-lookup"><span data-stu-id="52007-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="52007-161">Kolumna **punktacji** zawiera tablicę z kwadratową Euclideaną odległości do centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="52007-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="52007-162">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="52007-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="52007-163">Użyj `float` typu, aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="52007-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="52007-164">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="52007-164">Define data and model paths</span></span>

<span data-ttu-id="52007-165">Wróć do pliku *program.cs* i Dodaj dwa pola do przechowywania ścieżek do pliku zestawu danych i do pliku, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="52007-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="52007-166">`_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="52007-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="52007-167">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="52007-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="52007-168">Dodaj następujący kod bezpośrednio powyżej metody, `Main` Aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="52007-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="52007-169">Aby wykonać poprzednią kompilację kodu, Dodaj następujące `using` dyrektywy w górnej części pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="52007-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="52007-170">Tworzenie kontekstu ML</span><span class="sxs-lookup"><span data-stu-id="52007-170">Create ML context</span></span>

<span data-ttu-id="52007-171">Dodaj następujące dodatkowe `using` dyrektywy na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="52007-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="52007-172">W `Main` metodzie Zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="52007-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="52007-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType>Klasa reprezentuje środowisko uczenia maszynowego i udostępnia mechanizmy rejestrowania i punktów wejścia na potrzeby ładowania danych, szkoleń modeli, prognozowania i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="52007-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="52007-174">Jest to porównywalne koncepcje dotyczące korzystania `DbContext` z programu w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="52007-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="52007-175">Konfigurowanie ładowania danych</span><span class="sxs-lookup"><span data-stu-id="52007-175">Set up data loading</span></span>

<span data-ttu-id="52007-176">Dodaj następujący kod do metody, `Main` Aby skonfigurować sposób ładowania danych:</span><span class="sxs-lookup"><span data-stu-id="52007-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="52007-177">Ogólna [ `MLContext.Data.LoadFromTextFile` Metoda rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) wnioskuje schemat zestawu danych z dostarczonego `IrisData` typu i zwraca, <xref:Microsoft.ML.IDataView> który może być używany jako dane wejściowe dla transformatorów.</span><span class="sxs-lookup"><span data-stu-id="52007-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="52007-178">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="52007-178">Create a learning pipeline</span></span>

<span data-ttu-id="52007-179">W tym samouczku potok uczenia zadania klastra składa się z dwóch następujących kroków:</span><span class="sxs-lookup"><span data-stu-id="52007-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="52007-180">Połącz załadowane kolumny w jedną kolumnę **funkcji** , która jest używana przez Trainer klastrowania;</span><span class="sxs-lookup"><span data-stu-id="52007-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="52007-181">Użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> Trainer, aby nauczyć model przy użyciu algorytmu klastrowanie k-oznaczanie + +.</span><span class="sxs-lookup"><span data-stu-id="52007-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="52007-182">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="52007-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="52007-183">Kod określa, że zestaw danych powinien być podzielony na trzy klastry.</span><span class="sxs-lookup"><span data-stu-id="52007-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="52007-184">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="52007-184">Train the model</span></span>

<span data-ttu-id="52007-185">Kroki dodane w poprzednich sekcjach przygotowano potok do szkolenia, jednak żadne nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="52007-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="52007-186">Dodaj następujący wiersz do `Main` metody w celu wykonania ładowania danych i szkolenia modelu:</span><span class="sxs-lookup"><span data-stu-id="52007-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="52007-187">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="52007-187">Save the model</span></span>

<span data-ttu-id="52007-188">W tym momencie masz model, który można zintegrować z dowolnymi istniejącymi lub nowymi aplikacjami platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="52007-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="52007-189">Aby zapisać model w pliku zip, Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="52007-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="52007-190">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="52007-190">Use the model for predictions</span></span>

<span data-ttu-id="52007-191">Aby dokonać prognoz, użyj <xref:Microsoft.ML.PredictionEngine%602> klasy, która pobiera wystąpienia typu wejściowego za pomocą potoku transformatora i tworzy wystąpienia typu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="52007-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="52007-192">Dodaj następujący wiersz do metody, `Main` Aby utworzyć wystąpienie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="52007-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="52007-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="52007-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="52007-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="52007-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="52007-195">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="52007-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="52007-196">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, należy użyć `PredictionEnginePool` usługi, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiekty do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52007-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="52007-197">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania `PredictionEnginePool` z programu w ASP.NET Core INTERNETowym interfejsie API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="52007-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="52007-198">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="52007-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="52007-199">Utwórz `TestIrisData` klasę z wystąpieniami danych testowych:</span><span class="sxs-lookup"><span data-stu-id="52007-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="52007-200">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="52007-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="52007-201">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="52007-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="52007-202">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="52007-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="52007-203">Zmodyfikuj klasę jako statyczną, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="52007-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="52007-204">W tym samouczku wprowadzono jedno wystąpienie danych Iris w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="52007-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="52007-205">Możesz dodać inne scenariusze, aby eksperymentować z modelem.</span><span class="sxs-lookup"><span data-stu-id="52007-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="52007-206">Dodaj następujący kod do `TestIrisData` klasy:</span><span class="sxs-lookup"><span data-stu-id="52007-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="52007-207">Aby sprawdzić klaster, do którego należy określony element, Wróć do pliku *program.cs* i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="52007-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="52007-208">Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości z tego wystąpienia do klastra centroids.</span><span class="sxs-lookup"><span data-stu-id="52007-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="52007-209">Wyniki powinny wyglądać podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="52007-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="52007-210">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="52007-210">Congratulations!</span></span> <span data-ttu-id="52007-211">Pomyślnie skompilowano model uczenia maszynowego na potrzeby klastrowania Iris i użył go do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="52007-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="52007-212">Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) .</span><span class="sxs-lookup"><span data-stu-id="52007-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="52007-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="52007-213">Next steps</span></span>

<span data-ttu-id="52007-214">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="52007-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="52007-215">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="52007-215">Understand the problem</span></span>
> - <span data-ttu-id="52007-216">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="52007-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="52007-217">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="52007-217">Prepare the data</span></span>
> - <span data-ttu-id="52007-218">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="52007-218">Load and transform the data</span></span>
> - <span data-ttu-id="52007-219">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="52007-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="52007-220">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="52007-220">Train the model</span></span>
> - <span data-ttu-id="52007-221">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="52007-221">Use the model for predictions</span></span>

<span data-ttu-id="52007-222">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="52007-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="52007-223">repozytorium dotnet/machinelearning w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="52007-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
