---
title: 'Samouczek: Kategoryzacja przesłony kwiaty-k-oznacza klastrowanie'
description: Dowiedz się, jak używać ML.NET w scenariuszu klastrowania
author: pkulikov
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: e2aaeb8abc6981b420329f194aa7b82c90cae00a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929099"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="951cb-103">Samouczek: Klasyfikowanie kwiatów z użyciem tęczówki przy użyciu k-oznacza klastrowanie z ML.NET</span><span class="sxs-lookup"><span data-stu-id="951cb-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="951cb-104">W tym samouczku pokazano, jak za pomocą ML.NET utworzyć [Model klastrowania](../resources/tasks.md#clustering) dla [zestawu danych dla elementu pokwiatowego Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="951cb-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="951cb-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="951cb-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="951cb-106">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="951cb-106">Understand the problem</span></span>
> - <span data-ttu-id="951cb-107">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="951cb-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="951cb-108">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="951cb-108">Prepare the data</span></span>
> - <span data-ttu-id="951cb-109">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="951cb-109">Load and transform the data</span></span>
> - <span data-ttu-id="951cb-110">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="951cb-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="951cb-111">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="951cb-111">Train the model</span></span>
> - <span data-ttu-id="951cb-112">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="951cb-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="951cb-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="951cb-113">Prerequisites</span></span>

- <span data-ttu-id="951cb-114">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="951cb-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="951cb-115">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="951cb-115">Understand the problem</span></span>

<span data-ttu-id="951cb-116">Ten problem polega na rozdzieleniu zestawu zakwiatek Iris w różnych grupach w oparciu o funkcje kwiatowe.</span><span class="sxs-lookup"><span data-stu-id="951cb-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="951cb-117">Te funkcje to długość i szerokość słupka oraz długość i szerokość płatne.</span><span class="sxs-lookup"><span data-stu-id="951cb-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="951cb-118">W tym samouczku przyjęto założenie, że typ każdego kwiatu jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="951cb-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="951cb-119">Chcesz poznać strukturę zestawu danych z funkcji i przewidywania, jak wystąpienie danych pasuje do tej struktury.</span><span class="sxs-lookup"><span data-stu-id="951cb-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="951cb-120">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="951cb-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="951cb-121">Ponieważ nie wiesz, do której grupy należą każdy kwiat, wybierz zadanie [nienadzorowane Uczenie maszynowe](../resources/glossary.md#unsupervised-machine-learning) .</span><span class="sxs-lookup"><span data-stu-id="951cb-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="951cb-122">Aby podzielić zestaw danych w grupach w taki sposób, że elementy w tej samej grupie są bardziej podobne do siebie, niż w przypadku innych grup, Użyj zadania uczenia [maszynowego](../resources/tasks.md#clustering) .</span><span class="sxs-lookup"><span data-stu-id="951cb-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="951cb-123">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="951cb-123">Create a console application</span></span>

1. <span data-ttu-id="951cb-124">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="951cb-124">Open Visual Studio.</span></span> <span data-ttu-id="951cb-125">Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="951cb-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="951cb-126">W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="951cb-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="951cb-127">Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="951cb-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="951cb-128">W polu tekstowym **Nazwa** wpisz "IrisFlowerClustering", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="951cb-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="951cb-129">Utwórz katalog o nazwie *dane* w projekcie do przechowywania zestawu danych i plików modeli:</span><span class="sxs-lookup"><span data-stu-id="951cb-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="951cb-130">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="951cb-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="951cb-131">Wpisz "Data" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="951cb-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="951cb-132">Zainstaluj pakiet NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="951cb-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="951cb-133">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="951cb-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="951cb-134">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet **v 1.0.0** na liście, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="951cb-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="951cb-135">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie **Wybierz przycisk** Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="951cb-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="951cb-136">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="951cb-136">Prepare the data</span></span>

1. <span data-ttu-id="951cb-137">Pobierz zestaw danych [Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) i Zapisz go w folderze *danych* utworzonym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="951cb-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="951cb-138">Aby uzyskać więcej informacji na temat zestawu danych Iris, zapoznaj się ze stroną sieci Web dotyczącą [zestawu danych kwitnienia Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set) oraz stroną [zestawu danych Iris](https://archive.ics.uci.edu/ml/datasets/Iris) , która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="951cb-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="951cb-139">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Iris. Data* i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="951cb-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="951cb-140">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="951cb-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="951cb-141">Plik *Iris. Data* zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="951cb-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="951cb-142">słupka długość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="951cb-142">sepal length in centimetres</span></span>
- <span data-ttu-id="951cb-143">słupka szerokość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="951cb-143">sepal width in centimetres</span></span>
- <span data-ttu-id="951cb-144">płatna długość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="951cb-144">petal length in centimetres</span></span>
- <span data-ttu-id="951cb-145">Wysokość i szerokość w centymetrach</span><span class="sxs-lookup"><span data-stu-id="951cb-145">petal width in centimetres</span></span>
- <span data-ttu-id="951cb-146">Typ kwitnienia tęczówki</span><span class="sxs-lookup"><span data-stu-id="951cb-146">type of iris flower</span></span>

<span data-ttu-id="951cb-147">W ramach przykładu klastrowania ten samouczek ignoruje ostatnią kolumnę.</span><span class="sxs-lookup"><span data-stu-id="951cb-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="951cb-148">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="951cb-148">Create data classes</span></span>

<span data-ttu-id="951cb-149">Utwórz klasy dla danych wejściowych i prognoz:</span><span class="sxs-lookup"><span data-stu-id="951cb-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="951cb-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="951cb-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="951cb-151">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="951cb-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="951cb-152">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="951cb-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="951cb-153">Dodaj następującą `using` dyrektywę do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="951cb-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="951cb-154">Usuń istniejącą definicję klasy i Dodaj następujący kod, który definiuje klasy `IrisData` i `ClusterPrediction`, do pliku *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="951cb-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="951cb-155">`IrisData`jest klasą danych wejściowych i zawiera definicje dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="951cb-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="951cb-156">Użyj atrybutu [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) , aby określić indeksy kolumn źródłowych w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="951cb-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="951cb-157">Klasa reprezentuje dane wyjściowe modelu klastrowania zastosowanego `IrisData` do wystąpienia. `ClusterPrediction`</span><span class="sxs-lookup"><span data-stu-id="951cb-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="951cb-158">Użyj atrybutu [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) , aby powiązać `PredictedClusterId` pola `Distances` i z kolumnami **PredictedLabel** i **Score** odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="951cb-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="951cb-159">W przypadku zadania klastrowania te kolumny mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="951cb-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="951cb-160">Kolumna **PredictedLabel** zawiera identyfikator przewidywanego klastra.</span><span class="sxs-lookup"><span data-stu-id="951cb-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="951cb-161">Kolumna **punktacji** zawiera tablicę z kwadratową Euclideaną odległości do centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="951cb-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="951cb-162">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="951cb-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="951cb-163">Użyj typu `float` , aby reprezentować wartości zmiennoprzecinkowe w klasach danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="951cb-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="951cb-164">Definiowanie ścieżek danych i modeli</span><span class="sxs-lookup"><span data-stu-id="951cb-164">Define data and model paths</span></span>

<span data-ttu-id="951cb-165">Wróć do pliku *program.cs* i Dodaj dwa pola do przechowywania ścieżek do pliku zestawu danych i do pliku, aby zapisać model:</span><span class="sxs-lookup"><span data-stu-id="951cb-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="951cb-166">`_dataPath`zawiera ścieżkę do pliku z zestawem danych używanym do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="951cb-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="951cb-167">`_modelPath`zawiera ścieżkę do pliku, w którym jest przechowywany przeszkolony model.</span><span class="sxs-lookup"><span data-stu-id="951cb-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="951cb-168">Dodaj następujący kod bezpośrednio powyżej metody, `Main` aby określić te ścieżki:</span><span class="sxs-lookup"><span data-stu-id="951cb-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="951cb-169">Aby wykonać poprzednią kompilację kodu, Dodaj następujące `using` dyrektywy w górnej części pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="951cb-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="951cb-170">Tworzenie kontekstu ML</span><span class="sxs-lookup"><span data-stu-id="951cb-170">Create ML context</span></span>

<span data-ttu-id="951cb-171">Dodaj następujące dodatkowe `using` dyrektywy na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="951cb-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="951cb-172">W metodzie Zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem: `Main`</span><span class="sxs-lookup"><span data-stu-id="951cb-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="951cb-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Klasa reprezentuje środowisko uczenia maszynowego i udostępnia mechanizmy rejestrowania i punktów wejścia na potrzeby ładowania danych, szkoleń modeli, prognozowania i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="951cb-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="951cb-174">Jest to porównywalne koncepcje dotyczące `DbContext` korzystania z programu w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="951cb-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="951cb-175">Ładowanie danych konfiguracyjnych</span><span class="sxs-lookup"><span data-stu-id="951cb-175">Setup data loading</span></span>

<span data-ttu-id="951cb-176">Dodaj następujący kod do `Main` metody, aby skonfigurować sposób ładowania danych:</span><span class="sxs-lookup"><span data-stu-id="951cb-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="951cb-177">Ogólna `IrisData` [ `MLContext.Data.LoadFromTextFile` Metoda rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) wnioskuje schemat zestawu danych z dostarczonego typu i zwraca <xref:Microsoft.ML.IDataView> , który może być używany jako dane wejściowe dla transformatorów.</span><span class="sxs-lookup"><span data-stu-id="951cb-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="951cb-178">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="951cb-178">Create a learning pipeline</span></span>

<span data-ttu-id="951cb-179">W tym samouczku potok uczenia zadania klastra składa się z dwóch następujących kroków:</span><span class="sxs-lookup"><span data-stu-id="951cb-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="951cb-180">Połącz załadowane kolumny w jedną kolumnę **funkcji** , która jest używana przez Trainer klastrowania;</span><span class="sxs-lookup"><span data-stu-id="951cb-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="951cb-181"><xref:Microsoft.ML.Trainers.KMeansTrainer> Użyj Trainer, aby nauczyć model przy użyciu algorytmu klastrowanie k-oznaczanie + +.</span><span class="sxs-lookup"><span data-stu-id="951cb-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="951cb-182">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="951cb-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="951cb-183">Kod określa, że zestaw danych powinien być podzielony na trzy klastry.</span><span class="sxs-lookup"><span data-stu-id="951cb-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="951cb-184">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="951cb-184">Train the model</span></span>

<span data-ttu-id="951cb-185">Kroki dodane w poprzednich sekcjach przygotowano potok do szkolenia, jednak żadne nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="951cb-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="951cb-186">Dodaj następujący wiersz do `Main` metody w celu wykonania ładowania danych i szkolenia modelu:</span><span class="sxs-lookup"><span data-stu-id="951cb-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="951cb-187">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="951cb-187">Save the model</span></span>

<span data-ttu-id="951cb-188">W tym momencie masz model, który można zintegrować z dowolnymi istniejącymi lub nowymi aplikacjami platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="951cb-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="951cb-189">Aby zapisać model w pliku zip, Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="951cb-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="951cb-190">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="951cb-190">Use the model for predictions</span></span>

<span data-ttu-id="951cb-191">Aby dokonać prognoz, użyj <xref:Microsoft.ML.PredictionEngine%602> klasy, która pobiera wystąpienia typu wejściowego za pomocą potoku transformatora i tworzy wystąpienia typu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="951cb-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="951cb-192">Dodaj następujący wiersz do `Main` metody, aby utworzyć wystąpienie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="951cb-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="951cb-193">`TestIrisData` Utwórz klasę z wystąpieniami danych testowych:</span><span class="sxs-lookup"><span data-stu-id="951cb-193">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="951cb-194">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="951cb-194">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="951cb-195">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="951cb-195">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="951cb-196">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="951cb-196">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="951cb-197">Zmodyfikuj klasę jako statyczną, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="951cb-197">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="951cb-198">W tym samouczku wprowadzono jedno wystąpienie danych Iris w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="951cb-198">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="951cb-199">Możesz dodać inne scenariusze, aby eksperymentować z modelem.</span><span class="sxs-lookup"><span data-stu-id="951cb-199">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="951cb-200">Dodaj następujący kod do `TestIrisData` klasy:</span><span class="sxs-lookup"><span data-stu-id="951cb-200">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="951cb-201">Aby sprawdzić klaster, do którego należy określony element, Wróć do pliku *program.cs* i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="951cb-201">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="951cb-202">Uruchom program, aby zobaczyć, który klaster zawiera określone wystąpienie danych i kwadratowe odległości z tego wystąpienia do klastra centroids.</span><span class="sxs-lookup"><span data-stu-id="951cb-202">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="951cb-203">Wyniki powinny wyglądać podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="951cb-203">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="951cb-204">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="951cb-204">Congratulations!</span></span> <span data-ttu-id="951cb-205">Pomyślnie skompilowano model uczenia maszynowego na potrzeby klastrowania Iris i użył go do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="951cb-205">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="951cb-206">Kod źródłowy dla tego samouczka można znaleźć w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) .</span><span class="sxs-lookup"><span data-stu-id="951cb-206">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="951cb-207">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="951cb-207">Next steps</span></span>

<span data-ttu-id="951cb-208">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="951cb-208">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="951cb-209">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="951cb-209">Understand the problem</span></span>
> - <span data-ttu-id="951cb-210">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="951cb-210">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="951cb-211">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="951cb-211">Prepare the data</span></span>
> - <span data-ttu-id="951cb-212">Załaduj i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="951cb-212">Load and transform the data</span></span>
> - <span data-ttu-id="951cb-213">Wybierz algorytm uczenia</span><span class="sxs-lookup"><span data-stu-id="951cb-213">Choose a learning algorithm</span></span>
> - <span data-ttu-id="951cb-214">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="951cb-214">Train the model</span></span>
> - <span data-ttu-id="951cb-215">Używanie modelu dla prognoz</span><span class="sxs-lookup"><span data-stu-id="951cb-215">Use the model for predictions</span></span>

<span data-ttu-id="951cb-216">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować uczenie i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="951cb-216">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="951cb-217">repozytorium dotnet/machinelearning w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="951cb-217">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
