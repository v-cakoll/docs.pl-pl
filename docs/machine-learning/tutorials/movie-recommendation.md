---
title: 'Samouczek: Tworzenie polecania filmu - factorization macierzy'
description: W tym samouczku dowiesz się, jak tworzyć polecania filmów za pomocą platformy ML.NET w aplikacji konsoli .NET Core. Użyj kroków C# i Visual Studio 2019 r.
author: briacht
ms.author: johalex
ms.date: 05/06/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 512c8d663835da77c05fb24926ff85c56afd11ca
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66725505"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="0c03f-104">Samouczek: Tworzenie polecania filmu, za pomocą factorizaton macierzy za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="0c03f-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="0c03f-105">W tym samouczku dowiesz się, jak tworzyć polecania filmów za pomocą platformy ML.NET w aplikacji konsoli .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c03f-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="0c03f-106">Użyj kroków C# i Visual Studio 2019 r.</span><span class="sxs-lookup"><span data-stu-id="0c03f-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="0c03f-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0c03f-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0c03f-108">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="0c03f-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="0c03f-109">Przygotowanie i ładowania danych</span><span class="sxs-lookup"><span data-stu-id="0c03f-109">Prepare and load your data</span></span>
> * <span data-ttu-id="0c03f-110">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-110">Build and train a model</span></span>
> * <span data-ttu-id="0c03f-111">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-111">Evaluate a model</span></span>
> * <span data-ttu-id="0c03f-112">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-112">Deploy and consume a model</span></span>

<span data-ttu-id="0c03f-113">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="0c03f-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="0c03f-114">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0c03f-114">Machine learning workflow</span></span>

<span data-ttu-id="0c03f-115">Poniższe kroki użyje do wykonywania zadań, a także inne zadanie w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="0c03f-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="0c03f-116">Załaduj dane</span><span class="sxs-lookup"><span data-stu-id="0c03f-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="0c03f-117">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="0c03f-118">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="0c03f-119">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="0c03f-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0c03f-120">Prerequisites</span></span>

* <span data-ttu-id="0c03f-121">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="0c03f-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="0c03f-122">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="0c03f-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="0c03f-123">Istnieje kilka sposobów podejście problemy zalecenie, takie jak polecanie listy filmów lub zalecania listę powiązanych z nimi produktów, ale w tym przypadku będzie przewidywania jakie oceny (1-5) użytkownika będą dawać do konkretnego filmu i zaleca się ten film, jeśli jest przekracza określoną wartość progową (wyższa ocenę, tym wyższe prawdopodobieństwo użytkownika liking konkretnego filmu).</span><span class="sxs-lookup"><span data-stu-id="0c03f-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0c03f-124">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="0c03f-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="0c03f-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="0c03f-125">Create a project</span></span>

1. <span data-ttu-id="0c03f-126">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0c03f-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="0c03f-127">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0c03f-128">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="0c03f-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0c03f-129">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0c03f-130">W **nazwa** pole tekstowe, wpisz "MovieRecommender", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0c03f-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="0c03f-131">Utwórz katalog o nazwie *danych* w projekcie do przechowywania zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="0c03f-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="0c03f-132">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0c03f-133">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="0c03f-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="0c03f-134">Zainstaluj **Microsoft.ML** i **Microsoft.ML.Recommender** pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="0c03f-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="0c03f-135">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0c03f-136">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, wybierz opcję **1.0.0** pakietu na liście, a następnie wybierz pozycję  **Zainstaluj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0c03f-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0c03f-137">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="0c03f-138">Powtórz te kroki dla **Microsoft.ML.Recommender v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-138">Repeat these steps for **Microsoft.ML.Recommender v0.12.0**.</span></span>

4. <span data-ttu-id="0c03f-139">Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="0c03f-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="0c03f-140">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="0c03f-140">Download your data</span></span>

1. <span data-ttu-id="0c03f-141">Pobierz dwa zestawy danych i zapisywanie ich *danych* wcześniej utworzony folder:</span><span class="sxs-lookup"><span data-stu-id="0c03f-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="0c03f-142">Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="0c03f-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="0c03f-143">Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="0c03f-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="0c03f-144">Upewnij się, albo zapisać \*plików CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*plików CSV *danych* folderu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="0c03f-145">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="0c03f-146">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Kopiuj Jeśli nowszy w programie VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="0c03f-148">Załaduj dane</span><span class="sxs-lookup"><span data-stu-id="0c03f-148">Load your data</span></span>

<span data-ttu-id="0c03f-149">Pierwszym krokiem w procesie strukturze ML.NET jest przygotowanie i obciążenia sieci szkolenia i modelu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="0c03f-150">Dane oceny zalecenie jest podzielony na `Train` i `Test` zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="0c03f-151">`Train` Danych służy do dopasowania modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="0c03f-152">`Test` Dane są używane do prognozowania za pomocą uczonego modelu i ocena wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="0c03f-153">Jest często mają 80/20, Podziel się `Train` i `Test` danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="0c03f-154">Poniżej znajduje się podgląd danych z usługi \*plików CSV:</span><span class="sxs-lookup"><span data-stu-id="0c03f-154">Below is a preview of the data from your \*.csv files:</span></span>

![Podgląd danych](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="0c03f-156">W \*plików CSV znajdują się cztery kolumny:</span><span class="sxs-lookup"><span data-stu-id="0c03f-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="0c03f-157">W usłudze machine learning, są nazywane kolumn, które są używane do prognozowania [funkcji](../resources/glossary.md#feature), i nosi nazwę kolumny z prognozowania zwracane [etykiety](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="0c03f-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="0c03f-158">Chcesz przewidzieć klasyfikacji filmów, więc kolumny ocenę `Label`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="0c03f-159">Pozostałe trzy kolumny `userId`, `movieId`, i `timestamp` wyświetlane są wszystkie `Features` używać do prognozowania `Label`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="0c03f-160">Funkcje</span><span class="sxs-lookup"><span data-stu-id="0c03f-160">Features</span></span>      | <span data-ttu-id="0c03f-161">Etykieta</span><span class="sxs-lookup"><span data-stu-id="0c03f-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="0c03f-162">To Ty decydujesz o tym, które `Features` są używane do prognozowania `Label`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="0c03f-163">Można również użyć metod, takich jak [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md) ułatwiające wybranie najlepszych `Features`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="0c03f-164">W takim przypadku można wyeliminować `timestamp` jako kolumny `Feature` ponieważ sygnatura czasowa naprawdę wpływa na sposób użytkownik ocenia danego filmu, a zatem nie przyczyni się do wprowadzania dokładniejszych prognoz:</span><span class="sxs-lookup"><span data-stu-id="0c03f-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="0c03f-165">Funkcje</span><span class="sxs-lookup"><span data-stu-id="0c03f-165">Features</span></span>      | <span data-ttu-id="0c03f-166">Etykieta</span><span class="sxs-lookup"><span data-stu-id="0c03f-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="0c03f-167">Następnie zdefiniuj strukturę danych wejściowych klasy.</span><span class="sxs-lookup"><span data-stu-id="0c03f-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="0c03f-168">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="0c03f-169">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0c03f-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="0c03f-170">W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="0c03f-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="0c03f-171">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0c03f-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="0c03f-172">*MovieRatingData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0c03f-173">Dodaj następujący kod `using` instrukcji na górze *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0c03f-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="0c03f-174">Utwórz klasę o nazwie `MovieRating` , usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0c03f-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="0c03f-175">`MovieRating` Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="0c03f-176">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane.</span><span class="sxs-lookup"><span data-stu-id="0c03f-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="0c03f-177">`userId` i `movieId` kolumny są usługi `Features` (dane wejściowe zostanie nadana model do przewidywania `Label`), i kolumna Ocena jest `Label` czy będzie przewidzieć (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="0c03f-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="0c03f-178">Tworzenie innej klasy `MovieRatingPrediction`, do reprezentowania wyników, dodając następujący kod po `MovieRating` klasy w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="0c03f-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="0c03f-179">W *Program.cs*, Zastąp `Console.WriteLine("Hello World!")` następujący kod wewnątrz `Main()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="0c03f-180">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="0c03f-181">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0c03f-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="0c03f-182">Po `Main()`, utworzyć metodę o nazwie `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="0c03f-183">Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="0c03f-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="0c03f-184">Inicjowanie zmiennych ścieżki danych, Załaduj dane z \*plików CSV i zwrócenie `Train` i `Test` dane jako `IDataView` obiektów przez dodanie poniższego jako następnego wiersza kodu w `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="0c03f-185">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="0c03f-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="0c03f-186">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="0c03f-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="0c03f-187">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="0c03f-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="0c03f-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="0c03f-189">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="0c03f-190">W tym przypadku podaj ścieżkę dla Twojego `Test` i `Train` pliki i wskazać nagłówka pliku tekstowego (tak, aby go prawidłowo używać nazwy kolumn) i przecinkami danych znak separatora (domyślnym separatorem jest karta).</span><span class="sxs-lookup"><span data-stu-id="0c03f-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="0c03f-191">Dodaj następujący kod jako następnych dwóch wierszach kodu w `Main()` metodę do wywołania usługi `LoadData()` metody i zwrócenie `Train` i `Test` danych:</span><span class="sxs-lookup"><span data-stu-id="0c03f-191">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="0c03f-192">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-192">Build and train your model</span></span>

<span data-ttu-id="0c03f-193">Istnieją trzy główne pojęcia w strukturze ML.NET: [Dane](../resources/glossary.md#data), [transformatory](../resources/glossary.md#transformer), i [aplikacjom](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="0c03f-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="0c03f-194">Uczenie maszynowe szkolenia algorytmów wymaganych danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="0c03f-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="0c03f-195">`Transformers` są używane do przekształcania danych tabelarycznych na format zgodny.</span><span class="sxs-lookup"><span data-stu-id="0c03f-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformer obrazu](./media/movie-recommendation/transformer.png)

<span data-ttu-id="0c03f-197">Możesz utworzyć `Transformers` w strukturze ML.NET, tworząc `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="0c03f-198">`Estimators` podjęcia w obszarach danych i zwrócenia `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-198">`Estimators` take in data and return `Transformers`.</span></span>

![Narzędzie do szacowania obrazu](./media/movie-recommendation/estimator.png)

<span data-ttu-id="0c03f-200">Zalecenie uczenie algorytmu, będą używane na potrzeby szkolenia modelu jest przykładem `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="0c03f-201">Tworzenie `Estimator` następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0c03f-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="0c03f-202">Tworzenie `BuildAndTrainModel()` metody tuż za `LoadData()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="0c03f-203">Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="0c03f-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="0c03f-204">Zdefiniować przekształceń danych, dodając następujący kod do `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="0c03f-205">Ponieważ `userId` i `movieId` reprezentują użytkowników i tytułów filmów, nie rzeczywiste wartości, użyj [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metoda przekształcania każdego `userId` i każdy `movieId` do klucza typu liczbowego `Feature`kolumny (formacie akceptowanym przez algorytmy zalecenie) i dodaj je jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="0c03f-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="0c03f-206">userId</span><span class="sxs-lookup"><span data-stu-id="0c03f-206">userId</span></span> | <span data-ttu-id="0c03f-207">movieId</span><span class="sxs-lookup"><span data-stu-id="0c03f-207">movieId</span></span> | <span data-ttu-id="0c03f-208">Etykieta</span><span class="sxs-lookup"><span data-stu-id="0c03f-208">Label</span></span> | <span data-ttu-id="0c03f-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="0c03f-209">userIdEncoded</span></span> | <span data-ttu-id="0c03f-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="0c03f-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="0c03f-211">1</span><span class="sxs-lookup"><span data-stu-id="0c03f-211">1</span></span> | <span data-ttu-id="0c03f-212">1</span><span class="sxs-lookup"><span data-stu-id="0c03f-212">1</span></span> | <span data-ttu-id="0c03f-213">4</span><span class="sxs-lookup"><span data-stu-id="0c03f-213">4</span></span> | <span data-ttu-id="0c03f-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="0c03f-214">userKey1</span></span> | <span data-ttu-id="0c03f-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="0c03f-215">movieKey1</span></span> |
| <span data-ttu-id="0c03f-216">1</span><span class="sxs-lookup"><span data-stu-id="0c03f-216">1</span></span> | <span data-ttu-id="0c03f-217">3</span><span class="sxs-lookup"><span data-stu-id="0c03f-217">3</span></span> | <span data-ttu-id="0c03f-218">4</span><span class="sxs-lookup"><span data-stu-id="0c03f-218">4</span></span> | <span data-ttu-id="0c03f-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="0c03f-219">userKey1</span></span> | <span data-ttu-id="0c03f-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="0c03f-220">movieKey2</span></span> |
| <span data-ttu-id="0c03f-221">1</span><span class="sxs-lookup"><span data-stu-id="0c03f-221">1</span></span> | <span data-ttu-id="0c03f-222">6</span><span class="sxs-lookup"><span data-stu-id="0c03f-222">6</span></span> | <span data-ttu-id="0c03f-223">4</span><span class="sxs-lookup"><span data-stu-id="0c03f-223">4</span></span> | <span data-ttu-id="0c03f-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="0c03f-224">userKey1</span></span> | <span data-ttu-id="0c03f-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="0c03f-225">movieKey3</span></span> |

<span data-ttu-id="0c03f-226">Wybieranie algorytmu uczenia maszynowego, a następnie dołącza je do definicji przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="0c03f-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia zalecenia.</span><span class="sxs-lookup"><span data-stu-id="0c03f-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="0c03f-228">[Macierz Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest typowym podejściem do zalecenia, gdy masz dane, w jaki użytkownicy, które oceniły produktów w przeszłości jest tak w przypadku zestawów danych w ramach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="0c03f-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="0c03f-229">Istnieją inne algorytmy zalecenie używane w przypadku różnych dostępnych danych (zobacz [inne algorytmy zalecenie](#other-recommendation-algorithms) sekcji poniżej, aby dowiedzieć się więcej).</span><span class="sxs-lookup"><span data-stu-id="0c03f-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="0c03f-230">W tym przypadku `Matrix Factorization` algorytm używa metodę o nazwie "współpracy filtering", która zakłada się, że jeśli 1 użytkownik ma ten sam opinia jako 2 użytkownika dotyczących niektórych problemów, a następnie 1 użytkownika jest bardziej prawdopodobne, że ten sam sposób jak 2 użytkowników o innym problemem.</span><span class="sxs-lookup"><span data-stu-id="0c03f-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="0c03f-231">Na przykład jeśli użytkownik 1 i 2 użytkownika podobnie szybkości filmy, następnie 2 użytkownika jest bardziej prawdopodobne cieszyć się filmu 1 użytkownik ma obserwowane i o wysokiej:</span><span class="sxs-lookup"><span data-stu-id="0c03f-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="0c03f-232">Użytkownik 1</span><span class="sxs-lookup"><span data-stu-id="0c03f-232">User 1</span></span> | <span data-ttu-id="0c03f-233">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-233">Watched and liked movie</span></span> | <span data-ttu-id="0c03f-234">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-234">Watched and liked movie</span></span> | <span data-ttu-id="0c03f-235">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-235">Watched and liked movie</span></span> |
| <span data-ttu-id="0c03f-236">Użytkownik 2</span><span class="sxs-lookup"><span data-stu-id="0c03f-236">User 2</span></span> | <span data-ttu-id="0c03f-237">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-237">Watched and liked movie</span></span> | <span data-ttu-id="0c03f-238">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-238">Watched and liked movie</span></span> | <span data-ttu-id="0c03f-239">Nie ma obserwowane--zaleca się filmu</span><span class="sxs-lookup"><span data-stu-id="0c03f-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="0c03f-240">`Matrix Factorization` Trainer ma kilka [opcje](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), której możesz przeczytać więcej na temat w [hiperparametrów algorytm](#algorithm-hyperparameters) poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0c03f-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="0c03f-241">Dopasuj do modelu `Train` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="0c03f-242">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu za pomocą podanego szkolenia zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="0c03f-243">Technicznie rzecz biorąc, wykonuje `Estimator` definicje, przekształcanie danych i stosując, szkolenia i zwraca kopię trenowanego modelu, który jest `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="0c03f-244">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `BuildAndTrainModel()` metody i zwrócenie uczonego modelu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="0c03f-245">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-245">Evaluate your model</span></span>

<span data-ttu-id="0c03f-246">Gdy masz uczony model, korzystanie z Twoich danych testu do oceny, jak działa model.</span><span class="sxs-lookup"><span data-stu-id="0c03f-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="0c03f-247">Tworzenie `EvaluateModel()` metody tuż za `BuildAndTrainModel()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="0c03f-248">Przekształcanie `Test` danych przez dodanie poniższego kodu `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span><span class="sxs-lookup"><span data-stu-id="0c03f-248">Transform the `Test` data by adding the following code to `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span></span>

<span data-ttu-id="0c03f-249">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda wykonuje prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="0c03f-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="0c03f-250">Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="0c03f-251">Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` w testowego zestawu danych i zwraca metryki dotyczące jak działa model.</span><span class="sxs-lookup"><span data-stu-id="0c03f-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="0c03f-252">Drukuj metryk oceny do konsoli, dodając następujące jako następnego wiersza kodu w `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="0c03f-253">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="0c03f-254">Do tej pory dane wyjściowe powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-254">The output so far should look similar to the following text:</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

<span data-ttu-id="0c03f-255">W poniższych danych wyjściowych istnieją 20 iteracjach.</span><span class="sxs-lookup"><span data-stu-id="0c03f-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="0c03f-256">W każdej iteracji miary błąd zmniejsza i zbieżna dla wartości bliżej i bliżej 0.</span><span class="sxs-lookup"><span data-stu-id="0c03f-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="0c03f-257">`root of mean squared error` (Usługi RMS lub RMSE) służy do mierzenia różnice między model przewiduje wartości i zestawy danych testowych zaobserwowane wartości.</span><span class="sxs-lookup"><span data-stu-id="0c03f-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="0c03f-258">Z technicznego punktu widzenia jest pierwiastek kwadratowy ze średniej kwadratów błędów.</span><span class="sxs-lookup"><span data-stu-id="0c03f-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="0c03f-259">Im niższa, w tym lepsze model jest.</span><span class="sxs-lookup"><span data-stu-id="0c03f-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="0c03f-260">`R Squared` Wskazuje, jak dobrze pasuje do modelu danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="0c03f-261">Z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="0c03f-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="0c03f-262">Wartość 0 oznacza, że dane są losowych lub w inny sposób nie można dopasować do modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="0c03f-263">Wartość 1 oznacza, że model dokładnie pasują do danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="0c03f-264">Chcesz, aby Twoje `R Squared` oceny być maksymalnie zbliżone do 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0c03f-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="0c03f-265">Tworzenie modeli pomyślne jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="0c03f-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="0c03f-266">Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="0c03f-267">Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, zapewniając większych zestawów danych szkoleniowych lub wybierając szkolenia różnych algorytmów przy użyciu różnych funkcji hyper parametrów dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="0c03f-268">Aby uzyskać więcej informacji, zapoznaj się z [poprawy modelu](#improve-your-model) poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0c03f-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="0c03f-269">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-269">Use your model</span></span>

<span data-ttu-id="0c03f-270">Teraz można użyć uczonego modelu do prognozowania na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="0c03f-271">Tworzenie `UseModelForSinglePrediction()` metody tuż za `EvaluateModel()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0c03f-272">Użyj `PredictionEngine` do prognozowania tę klasyfikację, dodając następujący kod do `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="0c03f-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="0c03f-273">[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać pojedyncze wystąpienie danych, a następnie wykonaj prognozę na to pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="0c03f-274">Utwórz wystąpienie obiektu `MovieRating` o nazwie `testInput` i przekaż go do aparatu prognozowania, dodając następujące jako z następującymi wierszami kodu w `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="0c03f-275">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozę na pojedynczej kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="0c03f-276">Następnie można użyć `Score`, lub przewidywane oceny, ustalenie, czy polecisz film z movieId 10 użytkownika 6.</span><span class="sxs-lookup"><span data-stu-id="0c03f-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="0c03f-277">Wyższe `Score`, tym większe prawdopodobieństwo użytkownika liking konkretnego filmu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="0c03f-278">W tym przypadku Załóżmy, że zalecane jest użycie filmów z oceną przewidywane > 3.5.</span><span class="sxs-lookup"><span data-stu-id="0c03f-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="0c03f-279">Aby wydrukować wyniki, należy dodać następujące porty jako dalej wiersze kodu `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="0c03f-280">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="0c03f-281">Dane wyjściowe tej metody powinien wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="0c03f-282">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="0c03f-282">Save your model</span></span>

<span data-ttu-id="0c03f-283">Aby użyć modelu do prognozowania w aplikacji użytkownika końcowego, należy najpierw zapisać modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="0c03f-284">Tworzenie `SaveModel()` metody tuż za `UseModelForSinglePrediction()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0c03f-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0c03f-285">Zapisania trenowanego modelu, dodając następujący kod w `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="0c03f-286">Ta metoda zapisuje uczonego modelu do pliku zip (w folderze "Dane"), które następnie mogą być używane w innych aplikacjach platformy .NET do przewidywania przyszłych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0c03f-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="0c03f-287">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="0c03f-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="0c03f-288">Użyj zapisanych modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-288">Use your saved model</span></span>

<span data-ttu-id="0c03f-289">Po zapisaniu uczonego modelu może zużywać model w różnych środowiskach (zobacz ["Poradnik"](../how-to-guides/consuming-model-ml-net.md) dowiesz się, jak do obsługi operacji modelu uczenia maszynowego uczonego w aplikacjach).</span><span class="sxs-lookup"><span data-stu-id="0c03f-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="0c03f-290">Wyniki</span><span class="sxs-lookup"><span data-stu-id="0c03f-290">Results</span></span>

<span data-ttu-id="0c03f-291">Po wykonaniu powyższych kroków, uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="0c03f-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="0c03f-292">Wyniki z jednej prognozowania powyżej powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="0c03f-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="0c03f-293">Może zostać wyświetlony, ostrzeżenia i przetwarzanie komunikatów, ale te komunikaty zostały usunięte z następujące wyniki dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="0c03f-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

<span data-ttu-id="0c03f-294">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="0c03f-294">Congratulations!</span></span> <span data-ttu-id="0c03f-295">Usługi machine learning model polecanie filmów teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="0c03f-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="0c03f-296">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="0c03f-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="0c03f-297">Poprawa modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-297">Improve your model</span></span>

<span data-ttu-id="0c03f-298">Istnieje kilka sposobów, że może poprawić wydajność modelu, dzięki czemu można uzyskać dokładniejszych prognoz.</span><span class="sxs-lookup"><span data-stu-id="0c03f-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="0c03f-299">Dane</span><span class="sxs-lookup"><span data-stu-id="0c03f-299">Data</span></span>

<span data-ttu-id="0c03f-300">Dodawanie większej ilości danych szkoleniowych, który ma wystarczającej liczby próbek dla każdego użytkownika i identyfikator filmu może zwiększyć jakość modelu zalecenia.</span><span class="sxs-lookup"><span data-stu-id="0c03f-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="0c03f-301">[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-cross-validation-ml-net.md) to technika, który losowo oceniania modeli są rozróżniane danych na podzestawy (zamiast wyodrębniania się dane testowe z zestawu danych, jak zrobiono to w ramach tego samouczka) i przyjmuje niektórych grup nauczenia danych, a niektóre z tych grup jako test dane.</span><span class="sxs-lookup"><span data-stu-id="0c03f-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="0c03f-302">Tej metody przewyższa przekształcania stosowane, dzięki czemu train-test podziału pod względem jakości modelu.</span><span class="sxs-lookup"><span data-stu-id="0c03f-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="0c03f-303">Funkcje</span><span class="sxs-lookup"><span data-stu-id="0c03f-303">Features</span></span>

<span data-ttu-id="0c03f-304">W tym samouczku używasz tylko trzy `Features` (`user id`, `movie id`, i `rating`) są dostarczane przez zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="0c03f-305">Gdy jest to dobry początek, w rzeczywistości możesz chcieć dodać inne atrybuty lub `Features` (na przykład, wiek, płeć, geolokalizacja itp.), jeśli są one uwzględnione w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="0c03f-306">Dodawanie istotniejsze `Features` może zwiększyć wydajność modelu zalecenia.</span><span class="sxs-lookup"><span data-stu-id="0c03f-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="0c03f-307">Jeśli nie wiesz o tym, które `Features` może być najbardziej istotne dla zadania machine learning, można również skorzystać z funkcji wkład obliczeń (FCC) i [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md), który zapewnia strukturze ML.NET Odkryj najbardziej duży wpływ `Features`.</span><span class="sxs-lookup"><span data-stu-id="0c03f-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="0c03f-308">Algorytm hiperparametrów</span><span class="sxs-lookup"><span data-stu-id="0c03f-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="0c03f-309">Strukturze ML.NET zapewnia dobre domyślne szkolenia algorytmów, jednocześnie można dodatkowo dostrajania wydajności przez zmianę tego algorytmu [hiperparametrów](../resources/glossary.md#hyperparameter).</span><span class="sxs-lookup"><span data-stu-id="0c03f-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="0c03f-310">Aby uzyskać `Matrix Factorization`, można eksperymentować hiperparametrów takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby zobaczyć, jeśli zapewnia to lepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="0c03f-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="0c03f-311">Na przykład w tym samouczku algorytm są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="0c03f-311">For instance, in this tutorial the algorithm options are:</span></span>

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="0c03f-312">Inne algorytmy zalecenia</span><span class="sxs-lookup"><span data-stu-id="0c03f-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="0c03f-313">Algorytm factorization macierzy za pomocą filtrowania z wykorzystaniem współpracy jest tylko jedno z podejść do wykonywania rekomendacji filmów.</span><span class="sxs-lookup"><span data-stu-id="0c03f-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="0c03f-314">W wielu przypadkach może nie ma dostępnych danych oceny i mieć tylko historii film dostępny od użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0c03f-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="0c03f-315">W innych przypadkach może mieć więcej niż tylko przez użytkownika klasyfikacji danych.</span><span class="sxs-lookup"><span data-stu-id="0c03f-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="0c03f-316">Algorytm</span><span class="sxs-lookup"><span data-stu-id="0c03f-316">Algorithm</span></span>       | <span data-ttu-id="0c03f-317">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="0c03f-317">Scenario</span></span>           | <span data-ttu-id="0c03f-318">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c03f-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="0c03f-319">Factorization macierzy jednej klasy</span><span class="sxs-lookup"><span data-stu-id="0c03f-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="0c03f-320">Użyj tego, jeśli masz tylko identyfikator użytkownika i movieId.</span><span class="sxs-lookup"><span data-stu-id="0c03f-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="0c03f-321">Ten styl zalecenie opiera się na scenariuszu wspólnej zakupu lub produktów często kupowane razem, co oznacza, że będzie zalecamy klientom zestaw produktów na podstawie własnych zakupu historii zamówień.</span><span class="sxs-lookup"><span data-stu-id="0c03f-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="0c03f-322">> wypróbuj działanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0c03f-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="0c03f-323">Pole pamiętać Factorization maszyn</span><span class="sxs-lookup"><span data-stu-id="0c03f-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="0c03f-324">Użyj tego zaleceń, gdy masz większą liczbą funkcji poza userId, identyfikator produktu i klasyfikacji (na przykład opis produktu lub cena produktu).</span><span class="sxs-lookup"><span data-stu-id="0c03f-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="0c03f-325">Ta metoda używa również wspólne podejście filtrowania.</span><span class="sxs-lookup"><span data-stu-id="0c03f-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="0c03f-326">> wypróbuj działanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0c03f-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="0c03f-327">Nowy scenariusz użytkownika</span><span class="sxs-lookup"><span data-stu-id="0c03f-327">New user scenario</span></span>

<span data-ttu-id="0c03f-328">Jeden powszechny problem związany z filtrowania z wykorzystaniem współpracy jest problem zimnego, czyli w przypadku nowego użytkownika bez poprzedniego danych do rysowania wniosków z.</span><span class="sxs-lookup"><span data-stu-id="0c03f-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="0c03f-329">To często problemu zadając nowych użytkowników, aby utworzyć profil i, na przykład filmy szybkość ich przejrzane w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="0c03f-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="0c03f-330">Gdy ta metoda powoduje niektórych obciążeń na użytkownika, zawiera dane wyjścia dla nowych użytkowników o Brak historii klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0c03f-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="0c03f-331">Zasoby</span><span class="sxs-lookup"><span data-stu-id="0c03f-331">Resources</span></span>

<span data-ttu-id="0c03f-332">Dane używane w tym samouczku jest tworzony na podstawie [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="0c03f-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c03f-333">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0c03f-333">Next steps</span></span>

<span data-ttu-id="0c03f-334">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0c03f-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0c03f-335">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="0c03f-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="0c03f-336">Przygotowanie i ładowania danych</span><span class="sxs-lookup"><span data-stu-id="0c03f-336">Prepare and load your data</span></span>
> * <span data-ttu-id="0c03f-337">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-337">Build and train a model</span></span>
> * <span data-ttu-id="0c03f-338">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-338">Evaluate a model</span></span>
> * <span data-ttu-id="0c03f-339">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="0c03f-339">Deploy and consume a model</span></span>

<span data-ttu-id="0c03f-340">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="0c03f-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0c03f-341">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="0c03f-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
