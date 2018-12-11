---
title: Kwiatów iris klastra przy użyciu klastrowania uczeń - strukturze ML.NET
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klastrowania
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5bd73c774f60466daaf52215c34e7e17b5f5cc9c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145635"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="9b585-103">Samouczek: Kwiatów iris klastra przy użyciu klastrowania uczeń za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="9b585-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="9b585-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9b585-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="9b585-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9b585-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="9b585-106">W tym samouczku pokazano, jak za pomocą strukturze ML.NET tworzyć [model klastra](../resources/tasks.md#clustering) dla [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="9b585-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="9b585-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9b585-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9b585-108">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b585-108">Understand the problem</span></span>
> - <span data-ttu-id="9b585-109">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="9b585-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="9b585-110">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b585-110">Prepare the data</span></span>
> - <span data-ttu-id="9b585-111">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="9b585-111">Load and transform the data</span></span>
> - <span data-ttu-id="9b585-112">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="9b585-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="9b585-113">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b585-113">Train the model</span></span>
> - <span data-ttu-id="9b585-114">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="9b585-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b585-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9b585-115">Prerequisites</span></span>

- <span data-ttu-id="9b585-116">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="9b585-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="9b585-117">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b585-117">Understand the problem</span></span>

<span data-ttu-id="9b585-118">Ten problem dotyczy dzielenia zbiór kwiatów irysów w różnych grupach na podstawie funkcji Kwiatek.</span><span class="sxs-lookup"><span data-stu-id="9b585-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="9b585-119">Te funkcje są długość i szerokość słupka i długość i szerokość płatka.</span><span class="sxs-lookup"><span data-stu-id="9b585-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="9b585-120">Na potrzeby tego samouczka założono, że typ każdego Kwiatek jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="9b585-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="9b585-121">Chcesz poznać strukturę zestawu danych z funkcji i przewidzieć, jak wystąpienie danych dopasowuje tej struktury.</span><span class="sxs-lookup"><span data-stu-id="9b585-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="9b585-122">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="9b585-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="9b585-123">Nie wiesz, grupę, do której należy każdego Kwiatek, możesz wybrać [nienadzorowane uczenia maszynowego](../resources/glossary.md#unsupervised-machine-learning) zadania.</span><span class="sxs-lookup"><span data-stu-id="9b585-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="9b585-124">Aby podzielić zestawu danych w grupach w taki sposób, że elementy w tej samej grupie przypominają bardziej do innych niż w innych grupach, należy użyć [klastrowania](../resources/tasks.md#clustering) machine learning zadania.</span><span class="sxs-lookup"><span data-stu-id="9b585-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="9b585-125">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="9b585-125">Create a console application</span></span>

1. <span data-ttu-id="9b585-126">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9b585-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="9b585-127">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="9b585-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9b585-128">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="9b585-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="9b585-129">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="9b585-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="9b585-130">W **nazwa** pole tekstowe, wpisz "IrisClustering", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b585-130">In the **Name** text box, type "IrisClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="9b585-131">Utwórz katalog o nazwie *danych* w projekcie do przechowywania plików modelu i zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="9b585-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="9b585-132">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="9b585-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="9b585-133">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9b585-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="9b585-134">Zainstaluj **Microsoft.ML** pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="9b585-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="9b585-135">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9b585-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9b585-136">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b585-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="9b585-137">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="9b585-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="9b585-138">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b585-138">Prepare the data</span></span>

1. <span data-ttu-id="9b585-139">Pobierz [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) dane ustawić i zapisać go w celu *danych* folderu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="9b585-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="9b585-140">Aby uzyskać więcej informacji na temat zestawu danych iris zobacz [zbiór danych na temat irysów](https://en.wikipedia.org/wiki/Iris_flower_data_set) strony Wikipedii i [zestawu danych Iris](http://archive.ics.uci.edu/ml/datasets/Iris) strony, która jest źródłem zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9b585-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="9b585-141">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *iris.data* plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9b585-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="9b585-142">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="9b585-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="9b585-143">*Iris.data* plik zawiera pięć kolumn, które reprezentują:</span><span class="sxs-lookup"><span data-stu-id="9b585-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="9b585-144">Długość słupka w cm</span><span class="sxs-lookup"><span data-stu-id="9b585-144">sepal length in centimetres</span></span>
- <span data-ttu-id="9b585-145">Szerokość słupka w cm</span><span class="sxs-lookup"><span data-stu-id="9b585-145">sepal width in centimetres</span></span>
- <span data-ttu-id="9b585-146">Długość płatka w cm</span><span class="sxs-lookup"><span data-stu-id="9b585-146">petal length in centimetres</span></span>
- <span data-ttu-id="9b585-147">szerokość płatka w cm</span><span class="sxs-lookup"><span data-stu-id="9b585-147">petal width in centimetres</span></span>
- <span data-ttu-id="9b585-148">Typ kwiat irysa</span><span class="sxs-lookup"><span data-stu-id="9b585-148">type of iris flower</span></span>

<span data-ttu-id="9b585-149">Klastrowanie przykładach w tym samouczku ignoruje ostatniej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="9b585-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="9b585-150">Tworzenie klas danych</span><span class="sxs-lookup"><span data-stu-id="9b585-150">Create data classes</span></span>

<span data-ttu-id="9b585-151">Tworzenie klasy dla danych wejściowych i prognozy są tym:</span><span class="sxs-lookup"><span data-stu-id="9b585-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="9b585-152">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9b585-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9b585-153">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b585-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="9b585-154">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b585-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="9b585-155">Dodaj następujący kod `using` dyrektywy do nowego pliku:</span><span class="sxs-lookup"><span data-stu-id="9b585-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

<span data-ttu-id="9b585-156">Usuń istniejącą definicję klasy i Dodaj następujący kod, który określa klasy `IrisData` i `ClusterPrediction`, *IrisData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b585-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

<span data-ttu-id="9b585-157">`IrisData` jest klasą danych wejściowych i ma definicji dla każdej funkcji z zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9b585-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="9b585-158">Użyj [kolumny](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) atrybutu, aby określić indeksów kolumny źródłowe w pliku zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9b585-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="9b585-159">`ClusterPrediction` Klasa reprezentuje dane wyjściowe model klastrowania dotyczą `IrisData` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9b585-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="9b585-160">Użyj [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) atrybut do powiązania `PredictedClusterId` i `Distances` polom **PredictedLabel** i **wynik** kolumn odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9b585-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="9b585-161">W przypadku klastrowania zadania te kolumny mają następujące znaczenie:</span><span class="sxs-lookup"><span data-stu-id="9b585-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="9b585-162">**PredictedLabel** kolumna zawiera identyfikator przewidywane klastra.</span><span class="sxs-lookup"><span data-stu-id="9b585-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="9b585-163">**Wynik** kolumna zawiera tablicę z kwadratów euklidesowa odległości centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="9b585-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="9b585-164">Długość tablicy jest równa liczbie klastrów.</span><span class="sxs-lookup"><span data-stu-id="9b585-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="9b585-165">Użyj `float` typu do reprezentowania wartości zmiennoprzecinkowych w klasach danych wejściowych i prognozowania.</span><span class="sxs-lookup"><span data-stu-id="9b585-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="9b585-166">Zdefiniować dane oraz model ścieżki</span><span class="sxs-lookup"><span data-stu-id="9b585-166">Define data and model paths</span></span>

<span data-ttu-id="9b585-167">Wróć do *Program.cs* pliku i dodaj dwa pola, aby pomieścić ścieżki do pliku zestawu danych i plik, aby zapisać modelu:</span><span class="sxs-lookup"><span data-stu-id="9b585-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="9b585-168">`_dataPath` zawiera ścieżkę do pliku z zestawem danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="9b585-169">`_modelPath` zawiera ścieżkę do pliku, w którym przechowywany jest trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="9b585-170">Dodaj następujący kod nad `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="9b585-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

<span data-ttu-id="9b585-171">Aby powyższy kod, Kompiluj, Dodaj następujący kod `using` dyrektywy w górnej części *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b585-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="9b585-172">Tworzenie potoku uczenia</span><span class="sxs-lookup"><span data-stu-id="9b585-172">Create a learning pipeline</span></span>

<span data-ttu-id="9b585-173">Dodaj następujące dodatkowe `using` dyrektywy do góry *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b585-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

<span data-ttu-id="9b585-174">W `Main` metody, Zastąp `Console.WriteLine("Hello World!")` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9b585-174">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

<span data-ttu-id="9b585-175">`Train` Metoda szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-175">The `Train` method trains the model.</span></span> <span data-ttu-id="9b585-176">Tej metody Create, tuż poniżej `Main` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b585-176">Create that method just below the `Main` method, using the following code:</span></span>

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

<span data-ttu-id="9b585-177">Potok nauczania ładuje wszystkie dane i algorytmy niezbędne do nauczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-177">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="9b585-178">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="9b585-178">Add the following code into the `Train` method:</span></span>

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a><span data-ttu-id="9b585-179">Obciążenia i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="9b585-179">Load and transform data</span></span>

<span data-ttu-id="9b585-180">Pierwszym krokiem do wykonania jest ładowany zestaw danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="9b585-180">The first step to perform is to load the training data set.</span></span> <span data-ttu-id="9b585-181">W naszym przypadku szkoleniowy zestaw danych znajduje się w pliku tekstowym ze ścieżką definicją `_dataPath` pola.</span><span class="sxs-lookup"><span data-stu-id="9b585-181">In our case, the training data set is stored in the text file with a path defined by the `_dataPath` field.</span></span> <span data-ttu-id="9b585-182">Kolumny w pliku są oddzielone przecinkiem (",").</span><span class="sxs-lookup"><span data-stu-id="9b585-182">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="9b585-183">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="9b585-183">Add the following code into the `Train` method:</span></span>

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

<span data-ttu-id="9b585-184">Następnym krokiem jest łączenie wszystkich kolumn funkcji do **funkcji** przy użyciu kolumny <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> klasy przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="9b585-184">The next step is to combine all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="9b585-185">Domyślnie algorytmu uczenia przetwarza tylko funkcje z **funkcji** kolumny.</span><span class="sxs-lookup"><span data-stu-id="9b585-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="9b585-186">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="9b585-186">Add the following code:</span></span>

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="9b585-187">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="9b585-187">Choose a learning algorithm</span></span>

<span data-ttu-id="9b585-188">Po dodaniu danych z potokiem i przekształcane na poprawny format danych wejściowych, wybrać algorytm uczenia (**learner**).</span><span class="sxs-lookup"><span data-stu-id="9b585-188">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="9b585-189">Uczeń przygotowuje modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-189">The learner trains the model.</span></span> <span data-ttu-id="9b585-190">Strukturze ML.NET udostępnia <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner, który implementuje [algorytm k średnich](https://en.wikipedia.org/wiki/K-means_clustering) ulepszone metodę wyboru centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="9b585-190">ML.NET provides a <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner that implements [k-means algorithm](https://en.wikipedia.org/wiki/K-means_clustering) with an improved method for choosing the initial cluster centroids.</span></span>

<span data-ttu-id="9b585-191">Dodaj następujący kod do `Train` metoda przetwarzania danych kodzie dodanym w poprzednim kroku:</span><span class="sxs-lookup"><span data-stu-id="9b585-191">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

<span data-ttu-id="9b585-192">Użyj <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> właściwości w celu określenia liczby klastrów.</span><span class="sxs-lookup"><span data-stu-id="9b585-192">Use the <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> property to specify number of clusters.</span></span> <span data-ttu-id="9b585-193">Powyższy kod określa, że zestaw danych powinny być podzielone w trzech klastrów.</span><span class="sxs-lookup"><span data-stu-id="9b585-193">The code above specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="9b585-194">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b585-194">Train the model</span></span>

<span data-ttu-id="9b585-195">Kroki dodane w poprzednich sekcjach przygotowane potoku na potrzeby szkoleń, jednak nie zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="9b585-195">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="9b585-196">`pipeline.Train<TInput, TOutput>` Metoda tworzy model, który przyjmuje wystąpienie `TInput` typu, a następnie generuje wystąpienie `TOutput` typu.</span><span class="sxs-lookup"><span data-stu-id="9b585-196">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="9b585-197">Dodaj następujący kod do `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="9b585-197">Add the following code into the `Train` method:</span></span>

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a><span data-ttu-id="9b585-198">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="9b585-198">Save the model</span></span>

<span data-ttu-id="9b585-199">W tym momencie masz modelu, który można zintegrować wszystkich istniejących i nowych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="9b585-199">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="9b585-200">Aby zapisać swój model pliku .zip, Dodaj następujący kod do `Main` metoda poniżej wywołania `Train` metody:</span><span class="sxs-lookup"><span data-stu-id="9b585-200">To save your model to a .zip file, add the following code to the `Main` method below the call to the `Train` method:</span></span>

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

<span data-ttu-id="9b585-201">Za pomocą `await` w `Main` oznacza, że metoda `Main` metoda musi mieć `async` modyfikator i zwrócenie `Task`:</span><span class="sxs-lookup"><span data-stu-id="9b585-201">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

<span data-ttu-id="9b585-202">Musisz również dodać następujące `using` dyrektywę w górnej części *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="9b585-202">You also need to add the following `using` directive at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

<span data-ttu-id="9b585-203">Ponieważ `async Main` metodą jest funkcja, dodany w języku C# 7.1 i wersją języka domyślnego projektu języka C# 7.0, musisz zmienić wersję języka C# 7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9b585-203">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="9b585-204">Aby to zrobić, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9b585-204">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="9b585-205">Wybierz **kompilacji** kartę, a następnie wybierz pozycję **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b585-205">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="9b585-206">Z listy rozwijanej wybierz **języka C# 7.1** (lub nowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="9b585-206">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="9b585-207">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b585-207">Select the **OK** button.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="9b585-208">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="9b585-208">Use the model for predictions</span></span>

<span data-ttu-id="9b585-209">Utwórz `TestIrisData` klasy do domu badanie danych wystąpień:</span><span class="sxs-lookup"><span data-stu-id="9b585-209">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="9b585-210">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9b585-210">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9b585-211">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b585-211">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="9b585-212">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b585-212">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="9b585-213">Zmodyfikuj klasy, która ma być statyczne, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b585-213">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

<span data-ttu-id="9b585-214">Ten samouczek przedstawia jedno wystąpienie danych iris w ramach tej klasy.</span><span class="sxs-lookup"><span data-stu-id="9b585-214">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="9b585-215">Możesz dodać inne scenariusze, aby eksperymentować z modelu.</span><span class="sxs-lookup"><span data-stu-id="9b585-215">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="9b585-216">Dodaj następujący kod do `TestIrisData` klasy:</span><span class="sxs-lookup"><span data-stu-id="9b585-216">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

<span data-ttu-id="9b585-217">Aby dowiedzieć się, klastra, do którego należy określony element, wróć do obszaru *Program.cs* pliku i Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9b585-217">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

<span data-ttu-id="9b585-218">Uruchom program klastra, które zawiera wystąpienia określonych danych i kwadratów odległości od tego wystąpienia na centroids klastra.</span><span class="sxs-lookup"><span data-stu-id="9b585-218">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="9b585-219">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="9b585-219">Your results should be similar to the following.</span></span> <span data-ttu-id="9b585-220">Ponieważ przetwarza potoku, może zawierać ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="9b585-220">As the pipeline processes, it might display warnings or processing messages.</span></span> <span data-ttu-id="9b585-221">Zostały one usunięte z następujące dane wyjściowe w celu uściślenia.</span><span class="sxs-lookup"><span data-stu-id="9b585-221">These have been removed from the following output for clarity.</span></span>

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

<span data-ttu-id="9b585-222">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="9b585-222">Congratulations!</span></span> <span data-ttu-id="9b585-223">Usługi machine learning model iris klastrowania i użyto jej do prognozowania teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="9b585-223">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="9b585-224">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="9b585-224">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b585-225">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9b585-225">Next steps</span></span>

<span data-ttu-id="9b585-226">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9b585-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9b585-227">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="9b585-227">Understand the problem</span></span>
> - <span data-ttu-id="9b585-228">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="9b585-228">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="9b585-229">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="9b585-229">Prepare the data</span></span>
> - <span data-ttu-id="9b585-230">Ładowania i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="9b585-230">Load and transform the data</span></span>
> - <span data-ttu-id="9b585-231">Wybieranie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="9b585-231">Choose a learning algorithm</span></span>
> - <span data-ttu-id="9b585-232">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="9b585-232">Train the model</span></span>
> - <span data-ttu-id="9b585-233">Na użytek modelu prognozy</span><span class="sxs-lookup"><span data-stu-id="9b585-233">Use the model for predictions</span></span>

<span data-ttu-id="9b585-234">Zapoznaj się z naszym repozytorium GitHub, aby kontynuować zapoznawanie się z i znaleźć więcej przykładów.</span><span class="sxs-lookup"><span data-stu-id="9b585-234">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9b585-235">repozytorium DotNet/machinelearning w witrynie GitHub</span><span class="sxs-lookup"><span data-stu-id="9b585-235">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
