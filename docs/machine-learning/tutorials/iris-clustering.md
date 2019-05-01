---
title: Kwiatów iris klastra przy użyciu klastrowania uczeń - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klastrowania
author: pkulikov
ms.author: johalex
ms.date: 04/08/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 86eba0c7a3eaeed008d41ff950bf2fd7e0e5fb57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019051"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="66282-103">Samouczek: Kwiatów iris klastra przy użyciu klastrowania uczeń za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="66282-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="66282-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="66282-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="66282-105">Aby uzyskać więcej informacji, zobacz [Wprowadzenie do struktury ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="66282-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="66282-106">Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET 1.0 RC (w wersji Release Candidate) (wersja `1.0.0-preview`)**.</span><span class="sxs-lookup"><span data-stu-id="66282-106">This tutorial and related sample are currently using **ML.NET 1.0 RC (Release Candidate) (version `1.0.0-preview`)**.</span></span> <span data-ttu-id="66282-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="66282-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="66282-108">W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [model klastra](../resources/tasks.md#clustering) dla [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="66282-108">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="66282-109">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="66282-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="66282-110">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="66282-110">Understand the problem</span></span>
> - <span data-ttu-id="66282-111">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="66282-111">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="66282-112">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="66282-112">Prepare the data</span></span>
> - <span data-ttu-id="66282-113">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="66282-113">Load and transform the data</span></span>
> - <span data-ttu-id="66282-114">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="66282-114">Choose a learning algorithm</span></span>
> - <span data-ttu-id="66282-115">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="66282-115">Train the model</span></span>
> - <span data-ttu-id="66282-116">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="66282-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66282-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="66282-117">Prerequisites</span></span>

- <span data-ttu-id="66282-118">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="66282-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="66282-119">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="66282-119">Understand the problem</span></span>

<span data-ttu-id="66282-120">Ten problem dotyczy dzielenia zbiór kwiatów irysów w różnych grupach na podstawie funkcji Kwiatek.</span><span class="sxs-lookup"><span data-stu-id="66282-120">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="66282-121">Te funkcje są długość i szerokość słupka i długość i szerokość płatka.</span><span class="sxs-lookup"><span data-stu-id="66282-121">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="66282-122">Na potrzeby tego samouczka założono, że typ każdego Kwiatek jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="66282-122">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="66282-123">Chcesz poznać strukturę zestawu danych z funkcji i przewidzieć, jak wystąpienie danych dopasowuje tej struktury.</span><span class="sxs-lookup"><span data-stu-id="66282-123">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="66282-124">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="66282-124">Select the appropriate machine learning task</span></span>

<span data-ttu-id="66282-125">Nie wiesz, grupę, do której należy każdego Kwiatek, możesz wybrać [nienadzorowane uczenia maszynowego](../resources/glossary.md#unsupervised-machine-learning) zadania.</span><span class="sxs-lookup"><span data-stu-id="66282-125">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="66282-126">Aby podzielić zestawu danych w grupach w taki sposób, że elementy w tej samej grupie przypominają bardziej do innych niż w innych grupach, należy użyć [klastrowania](../resources/tasks.md#clustering) machine learning zadania.</span><span class="sxs-lookup"><span data-stu-id="66282-126">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="66282-127">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="66282-127">Create a console application</span></span>

1. <span data-ttu-id="66282-128">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="66282-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="66282-129">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="66282-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="66282-130">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="66282-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="66282-131">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="66282-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="66282-132">W **nazwa** pole tekstowe, wpisz "IrisFlowerClustering", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="66282-132">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="66282-133">Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="66282-133">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="66282-134">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="66282-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="66282-135">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="66282-135">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="66282-136">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="66282-136">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="66282-137">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="66282-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="66282-138">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="66282-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="66282-139">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="66282-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="66282-140">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="66282-140">Prepare the data</span></span>

1. <span data-ttu-id="66282-141">Pobierz [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="66282-141">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="66282-142">Aby uzyskać więcej informacji na temat zestawu danych iris zobacz [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set) strony Wikipedii i [zestawu danych Iris](https://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="66282-142">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="66282-143">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *iris.data* plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="66282-143">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="66282-144">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="66282-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="66282-145">*Iris.data* plik zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="66282-145">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="66282-146">Długość słupka w cm</span><span class="sxs-lookup"><span data-stu-id="66282-146">sepal length in centimetres</span></span>
- <span data-ttu-id="66282-147">Szerokość słupka w cm</span><span class="sxs-lookup"><span data-stu-id="66282-147">sepal width in centimetres</span></span>
- <span data-ttu-id="66282-148">Długość płatka w cm</span><span class="sxs-lookup"><span data-stu-id="66282-148">petal length in centimetres</span></span>
- <span data-ttu-id="66282-149">szerokość płatka w cm</span><span class="sxs-lookup"><span data-stu-id="66282-149">petal width in centimetres</span></span>
- <span data-ttu-id="66282-150">Typ kwiat irysa</span><span class="sxs-lookup"><span data-stu-id="66282-150">type of iris flower</span></span>

<span data-ttu-id="66282-151">Klastrowanie przykładach w tym samouczku ignoruje ostatniej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="66282-151">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="66282-152">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="66282-152">Create data classes</span></span>

<span data-ttu-id="66282-153">Tworzenie klasy dla danych wejściowych i prognozy są tym:</span><span class="sxs-lookup"><span data-stu-id="66282-153">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="66282-154">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="66282-154">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="66282-155">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="66282-155">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="66282-156">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="66282-156">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="66282-157">Dodaj następujący kod `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="66282-157">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="66282-158">Usuń istniejącą definicję klasy i Dodaj następujący kod, który określa klasy `IrisData` i `ClusterPrediction`, *IrisData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="66282-158">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="66282-159">`IrisData` jest klasą danych wejściowych i ma definicji dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="66282-159">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="66282-160">Użyj [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="66282-160">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="66282-161">`ClusterPrediction` Klasa reprezentuje dane wyjściowe model klastrowania dotyczą `IrisData` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="66282-161">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="66282-162">Użyj [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut do powiązania `PredictedClusterId` i `Distances` polom **PredictedLabel** i **wynik** kolumn odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="66282-162">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="66282-163">W przypadku klastrowania zadania te kolumny mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="66282-163">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="66282-164">**PredictedLabel** kolumna zawiera identyfikator przewidywane klastra.</span><span class="sxs-lookup"><span data-stu-id="66282-164">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="66282-165">**Wynik** kolumna zawiera tablicę z kwadratów euklidesowa odległości centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="66282-165">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="66282-166">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="66282-166">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="66282-167">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="66282-167">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="66282-168">Zdefiniować dane oraz model ścieżki</span><span class="sxs-lookup"><span data-stu-id="66282-168">Define data and model paths</span></span>

<span data-ttu-id="66282-169">Wróć do *Program.cs* pliku i dodaj dwa pola, aby pomieścić ścieżki do pliku zestawu danych i plik, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="66282-169">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="66282-170">`_dataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="66282-170">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="66282-171">`_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="66282-171">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="66282-172">Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="66282-172">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="66282-173">Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="66282-173">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="66282-174">Utwórz kontekst ML</span><span class="sxs-lookup"><span data-stu-id="66282-174">Create ML context</span></span>

<span data-ttu-id="66282-175">Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="66282-175">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="66282-176">W `Main` metody, Zastąp `Console.WriteLine("Hello World!");` wiersz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="66282-176">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="66282-177"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Klasa reprezentuje środowiska usługi machine learning i udostępnia mechanizmy punkty wejścia i rejestrowania dla ładowania danych, szkoleń modelowych, prognozowania i innych zadań.</span><span class="sxs-lookup"><span data-stu-id="66282-177">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="66282-178">To jest porównywalna koncepcyjnie za pomocą `DbContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="66282-178">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="66282-179">Ustawienia ładowania danych</span><span class="sxs-lookup"><span data-stu-id="66282-179">Setup data loading</span></span>

<span data-ttu-id="66282-180">Dodaj następujący kod do `Main` metodę, aby skonfigurować sposób ładowania danych:</span><span class="sxs-lookup"><span data-stu-id="66282-180">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="66282-181">Ogólny [ `MLContext.Data.LoadFromTextFile` — metoda rozszerzenia](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) wnioskuje schemat zestawu danych z dostarczonego `IrisData` typu i zwraca <xref:Microsoft.ML.IDataView> który może służyć jako dane wejściowe do transformatory.</span><span class="sxs-lookup"><span data-stu-id="66282-181">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="66282-182">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="66282-182">Create a learning pipeline</span></span>

<span data-ttu-id="66282-183">W tym samouczku potok nauczania klastrowania zadania obejmuje dwa następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="66282-183">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="66282-184">łączenie kolumn załadowanych w jednym **funkcji** kolumny, która jest używana przez trainer klastrowania.</span><span class="sxs-lookup"><span data-stu-id="66282-184">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="66282-185">Użyj <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer do nauczenia modelu, używając k — oznacza, że ++ algorytmu klastrowania.</span><span class="sxs-lookup"><span data-stu-id="66282-185">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="66282-186">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="66282-186">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="66282-187">Kod ten określa, że zestaw danych powinny być podzielone w trzech klastrów.</span><span class="sxs-lookup"><span data-stu-id="66282-187">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="66282-188">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="66282-188">Train the model</span></span>

<span data-ttu-id="66282-189">Kroki dodane w poprzednich sekcjach przygotowane potoku na potrzeby szkoleń, jednak nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="66282-189">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="66282-190">Dodaj następujący wiersz do `Main` metodę w celu ładowania danych i szkolenie modelu:</span><span class="sxs-lookup"><span data-stu-id="66282-190">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="66282-191">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="66282-191">Save the model</span></span>

<span data-ttu-id="66282-192">W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="66282-192">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="66282-193">Aby zapisać swój model pliku .zip, Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="66282-193">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="66282-194">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="66282-194">Use the model for predictions</span></span>

<span data-ttu-id="66282-195">Aby tworzyć prognozy, należy użyć <xref:Microsoft.ML.PredictionEngine%602> klasy, która pobiera wystąpienia typu danych wejściowych przez potok przekształcania i tworzy wystąpienia typu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="66282-195">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="66282-196">Dodaj następujący wiersz do `Main` metodę, aby utworzyć wystąpienie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="66282-196">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="66282-197">Utwórz `TestIrisData` klasy do domu badanie danych wystąpień:</span><span class="sxs-lookup"><span data-stu-id="66282-197">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="66282-198">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="66282-198">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="66282-199">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="66282-199">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="66282-200">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="66282-200">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="66282-201">Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="66282-201">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="66282-202">Ten samouczek przedstawia jedno wystąpienie danych iris w ramach tej klasy.</span><span class="sxs-lookup"><span data-stu-id="66282-202">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="66282-203">Możesz dodać inne scenariusze, aby eksperymentować z modelu.</span><span class="sxs-lookup"><span data-stu-id="66282-203">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="66282-204">Dodaj następujący kod do `TestIrisData` klasy:</span><span class="sxs-lookup"><span data-stu-id="66282-204">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="66282-205">Aby dowiedzieć się, klastra, do którego należy określony element, wróć do obszaru *Program.cs* pliku i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="66282-205">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="66282-206">Uruchom program klastra, które zawiera wystąpienia określonych danych i kwadratów odległości od tego wystąpienia na centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="66282-206">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="66282-207">Wyniki powinny wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="66282-207">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="66282-208">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="66282-208">Congratulations!</span></span> <span data-ttu-id="66282-209">Usługi machine learning model iris klastrowania i użyto jej do prognozowania teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="66282-209">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="66282-210">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="66282-210">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="66282-211">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="66282-211">Next steps</span></span>

<span data-ttu-id="66282-212">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="66282-212">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="66282-213">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="66282-213">Understand the problem</span></span>
> - <span data-ttu-id="66282-214">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="66282-214">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="66282-215">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="66282-215">Prepare the data</span></span>
> - <span data-ttu-id="66282-216">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="66282-216">Load and transform the data</span></span>
> - <span data-ttu-id="66282-217">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="66282-217">Choose a learning algorithm</span></span>
> - <span data-ttu-id="66282-218">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="66282-218">Train the model</span></span>
> - <span data-ttu-id="66282-219">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="66282-219">Use the model for predictions</span></span>

<span data-ttu-id="66282-220">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować zapoznawanie się z i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="66282-220">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="66282-221">repozytorium DotNet/machinelearning w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="66282-221">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
