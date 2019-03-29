---
title: Użyj strukturze ML.NET w scenariuszu zaleceń filmu
description: Dowiedz się, jak na potrzeby strukturze ML.NET w scenariuszu rekomendacji zaleca się filmy dla użytkowników.
author: briacht
ms.author: johalex
ms.date: 03/08/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: e78772df1cf7e5f8999305a1b726a7085f94601b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410072"
---
# <a name="tutorial-create-a-movie-recommender-with-mlnet"></a><span data-ttu-id="321d0-103">Samouczek: Utwórz polecania filmów za pomocą platformy ML.NET</span><span class="sxs-lookup"><span data-stu-id="321d0-103">Tutorial: Create a Movie Recommender with ML.NET</span></span>

<span data-ttu-id="321d0-104">Ten przykładowy samouczek przedstawia tworzenie polecania filmu, za pośrednictwem używany aplikację konsoli .NET Core za pomocą strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="321d0-104">This sample tutorial illustrates using ML.NET to build a movie recommender via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="321d0-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="321d0-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="321d0-106">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="321d0-106">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="321d0-107">Przygotowanie i ładowania danych</span><span class="sxs-lookup"><span data-stu-id="321d0-107">Prepare and load your data</span></span>
> * <span data-ttu-id="321d0-108">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-108">Build and train a model</span></span>
> * <span data-ttu-id="321d0-109">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-109">Evaluate a model</span></span>
> * <span data-ttu-id="321d0-110">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-110">Deploy and consume a model</span></span>

> [!NOTE]
> <span data-ttu-id="321d0-111">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="321d0-111">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="321d0-112">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="321d0-112">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="321d0-113">Obecnie używasz tego samouczka, a powiązane próbki **strukturze ML.NET wersji 0,11**.</span><span class="sxs-lookup"><span data-stu-id="321d0-113">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="321d0-114">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="321d0-114">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="321d0-115">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="321d0-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="321d0-116">Maszyny uczenie się przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="321d0-116">Machine learning workflow</span></span>
<span data-ttu-id="321d0-117">Poniższe kroki użyje do wykonywania zadań, a także inne zadanie w strukturze ML.NET:</span><span class="sxs-lookup"><span data-stu-id="321d0-117">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="321d0-118">Załaduj dane</span><span class="sxs-lookup"><span data-stu-id="321d0-118">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="321d0-119">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-119">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="321d0-120">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-120">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="321d0-121">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-121">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="321d0-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="321d0-122">Prerequisites</span></span>

* <span data-ttu-id="321d0-123">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="321d0-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="321d0-124">Wybierz zadanie uczenia odpowiedniej maszyny</span><span class="sxs-lookup"><span data-stu-id="321d0-124">Select the appropriate machine learning task</span></span>

<span data-ttu-id="321d0-125">Istnieje kilka sposobów podejście problemy zalecenie, takie jak polecanie listy filmów lub zalecania listę powiązanych z nimi produktów, ale w tym przypadku będzie przewidywania jakie oceny (1-5) użytkownika będą dawać do konkretnego filmu i zaleca się ten film, jeśli jest przekracza określoną wartość progową (wyższa ocenę, tym wyższe prawdopodobieństwo użytkownika liking konkretnego filmu).</span><span class="sxs-lookup"><span data-stu-id="321d0-125">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="321d0-126">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="321d0-126">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="321d0-127">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="321d0-127">Create a project</span></span>

1. <span data-ttu-id="321d0-128">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="321d0-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="321d0-129">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="321d0-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="321d0-130">W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="321d0-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="321d0-131">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="321d0-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="321d0-132">W **nazwa** pole tekstowe, wpisz "MovieRecommender", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="321d0-132">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="321d0-133">Utwórz katalog o nazwie *danych* w projekcie do przechowywania zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="321d0-133">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="321d0-134">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy Folder**.</span><span class="sxs-lookup"><span data-stu-id="321d0-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="321d0-135">Wpisz "Dane", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="321d0-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="321d0-136">Zainstaluj **Microsoft.ML** i **Microsoft.ML.Recommender** pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="321d0-136">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="321d0-137">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="321d0-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="321d0-138">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz opcję **Przeglądaj** kartę, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="321d0-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="321d0-139">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="321d0-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="321d0-140">Powtórz te kroki dla **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="321d0-140">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

  > [!NOTE]
  > <span data-ttu-id="321d0-141">W tym samouczku **Microsoft.ML v0.11.0** i **Microsoft.ML.Recommender v0.11.0**.</span><span class="sxs-lookup"><span data-stu-id="321d0-141">This tutorial uses **Microsoft.ML v0.11.0** and **Microsoft.ML.Recommender v0.11.0**.</span></span>
    
4. <span data-ttu-id="321d0-142">Dodaj następujący kod `using` instrukcji w górnej części Twojej *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="321d0-142">Add the following `using` statements at the top of your *Program.cs* file:</span></span>
    
    [!code-csharp[UsingStatements](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="321d0-143">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="321d0-143">Download your data</span></span>

1. <span data-ttu-id="321d0-144">Pobierz dwa zestawy danych i zapisywanie ich *danych* wcześniej utworzony folder:</span><span class="sxs-lookup"><span data-stu-id="321d0-144">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

*   <span data-ttu-id="321d0-145">Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="321d0-145">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
*   <span data-ttu-id="321d0-146">Kliknij prawym przyciskiem myszy [ *zalecenie klasyfikacje — test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz pozycję "Zapisz jako łącza (lub docelowego)..."</span><span class="sxs-lookup"><span data-stu-id="321d0-146">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="321d0-147">Upewnij się, albo zapisać \*plików CSV *danych* folderu lub po jego zapisaniu innym miejscu, Przenieś \*plików CSV *danych* folderu.</span><span class="sxs-lookup"><span data-stu-id="321d0-147">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="321d0-148">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików CSV, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="321d0-148">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="321d0-149">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="321d0-149">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Kopiuj Jeśli nowszy w programie VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="321d0-151">Załaduj dane</span><span class="sxs-lookup"><span data-stu-id="321d0-151">Load your data</span></span>

<span data-ttu-id="321d0-152">Pierwszym krokiem w procesie strukturze ML.NET jest przygotowanie i obciążenia sieci szkolenia i modelu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="321d0-152">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="321d0-153">Dane oceny zalecenie jest podzielony na `Train` i `Test` zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-153">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="321d0-154">`Train` Danych służy do dopasowania modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-154">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="321d0-155">`Test` Dane są używane do prognozowania za pomocą uczonego modelu i ocena wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-155">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="321d0-156">Jest często mają 80/20, Podziel się `Train` i `Test` danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-156">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="321d0-157">Poniżej znajduje się podgląd danych z usługi \*plików CSV:</span><span class="sxs-lookup"><span data-stu-id="321d0-157">Below is a preview of the data from your \*.csv files:</span></span>

![Podgląd danych](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="321d0-159">W \*plików CSV znajdują się cztery kolumny:</span><span class="sxs-lookup"><span data-stu-id="321d0-159">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="321d0-160">W usłudze machine learning, są nazywane kolumn, które są używane do prognozowania [funkcji](../resources/glossary.md#feature), i nosi nazwę kolumny z prognozowania zwracane [etykiety](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="321d0-160">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="321d0-161">Chcesz przewidzieć klasyfikacji filmów, więc kolumny ocenę `Label`.</span><span class="sxs-lookup"><span data-stu-id="321d0-161">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="321d0-162">Pozostałe trzy kolumny `userId`, `movieId`, i `timestamp` wyświetlane są wszystkie `Features` używać do prognozowania `Label`.</span><span class="sxs-lookup"><span data-stu-id="321d0-162">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="321d0-163">Funkcje</span><span class="sxs-lookup"><span data-stu-id="321d0-163">Features</span></span>      | <span data-ttu-id="321d0-164">Etykieta</span><span class="sxs-lookup"><span data-stu-id="321d0-164">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="321d0-165">To Ty decydujesz o tym, które `Features` są używane do prognozowania `Label`.</span><span class="sxs-lookup"><span data-stu-id="321d0-165">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="321d0-166">Można również użyć metod, takich jak [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md) ułatwiające wybranie najlepszych `Features`.</span><span class="sxs-lookup"><span data-stu-id="321d0-166">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="321d0-167">W takim przypadku można wyeliminować `timestamp` jako kolumny `Feature` ponieważ sygnatura czasowa naprawdę wpływa na sposób użytkownik ocenia danego filmu, a zatem nie przyczyni się do wprowadzania dokładniejszych prognoz:</span><span class="sxs-lookup"><span data-stu-id="321d0-167">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="321d0-168">Funkcje</span><span class="sxs-lookup"><span data-stu-id="321d0-168">Features</span></span>      | <span data-ttu-id="321d0-169">Etykieta</span><span class="sxs-lookup"><span data-stu-id="321d0-169">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="321d0-170">Następnie zdefiniuj strukturę danych wejściowych klasy.</span><span class="sxs-lookup"><span data-stu-id="321d0-170">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="321d0-171">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="321d0-171">Add a new class to your project:</span></span>

1. <span data-ttu-id="321d0-172">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="321d0-172">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="321d0-173">W **okno dialogowe Dodaj nowy element**, wybierz opcję **klasy** i zmień **nazwa** pole *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="321d0-173">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="321d0-174">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="321d0-174">Then, select the **Add** button.</span></span>

<span data-ttu-id="321d0-175">*MovieRatingData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="321d0-175">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="321d0-176">Dodaj następujący kod `using` instrukcji na górze *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="321d0-176">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="321d0-177">Utwórz klasę o nazwie `MovieRating` , usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="321d0-177">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="321d0-178">`MovieRating` Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="321d0-178">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="321d0-179">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybut określa, które kolumny (według indeksu kolumny) w zestawie danych, które powinny być załadowane.</span><span class="sxs-lookup"><span data-stu-id="321d0-179">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="321d0-180">`userId` i `movieId` kolumny są usługi `Features` (dane wejściowe zostanie nadana model do przewidywania `Label`), i kolumna Ocena jest `Label` czy będzie przewidzieć (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="321d0-180">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="321d0-181">Tworzenie innej klasy `MovieRatingPrediction`, do reprezentowania wyników, dodając następujący kod po `MovieRating` klasy w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="321d0-181">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](../../../samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="321d0-182">W *Program.cs*, Zastąp `Console.WriteLine("Hello World!")` następujący kod wewnątrz `Main()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-182">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="321d0-183">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-183">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="321d0-184">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="321d0-184">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="321d0-185">Po `Main()`, utworzyć metodę o nazwie `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-185">After `Main()`, create a method called `LoadData()`:</span></span>
```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{


}
```

> [!NOTE]
> <span data-ttu-id="321d0-186">Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="321d0-186">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="321d0-187">Inicjowanie zmiennych ścieżki danych, Załaduj dane z plików \*.csv i zwróć `Train` i `Test` dane jako `IDataView` obiektów przez dodanie poniższego jako następnego wiersza kodu w `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-187">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="321d0-188">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.Data.DataView.IDataView).</span><span class="sxs-lookup"><span data-stu-id="321d0-188">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.Data.DataView.IDataView).</span></span> <span data-ttu-id="321d0-189">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="321d0-189">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="321d0-190">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="321d0-190">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="321d0-191">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="321d0-191">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="321d0-192">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="321d0-192">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="321d0-193">W tym przypadku podaj ścieżkę dla Twojego `Test` i `Train` pliki i wskazać nagłówka pliku tekstowego (tak, aby go prawidłowo używać nazwy kolumn) i przecinkami danych znak separatora (domyślnym separatorem jest karta).</span><span class="sxs-lookup"><span data-stu-id="321d0-193">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="321d0-194">Dodaj następujący kod jako następnych dwóch wierszach kodu w `Main()` metodę do wywołania usługi `LoadData()` metody i zwrócenie `Train` i `Test` danych:</span><span class="sxs-lookup"><span data-stu-id="321d0-194">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]


## <a name="build-and-train-your-model"></a><span data-ttu-id="321d0-195">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-195">Build and train your model</span></span>

<span data-ttu-id="321d0-196">Istnieją trzy główne pojęcia w strukturze ML.NET: [Dane](../basic-concepts-model-training-in-mldotnet.md#data), [transformatory](../basic-concepts-model-training-in-mldotnet.md#transformer), i [aplikacjom](../basic-concepts-model-training-in-mldotnet.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="321d0-196">There are three major concepts in ML.NET: [Data](../basic-concepts-model-training-in-mldotnet.md#data), [Transformers](../basic-concepts-model-training-in-mldotnet.md#transformer), and [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).</span></span>

<span data-ttu-id="321d0-197">Uczenie maszynowe szkolenia algorytmów wymaganych danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="321d0-197">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="321d0-198">`Transformers` są używane do przekształcania danych tabelarycznych na format zgodny.</span><span class="sxs-lookup"><span data-stu-id="321d0-198">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformer obrazu](./media/movie-recommendation/transformer.png)

<span data-ttu-id="321d0-200">Możesz utworzyć `Transformers` w strukturze ML.NET, tworząc `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="321d0-200">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="321d0-201">`Estimators` podjęcia w obszarach danych i zwrócenia `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="321d0-201">`Estimators` take in data and return `Transformers`.</span></span>

![Narzędzie do szacowania obrazu](./media/movie-recommendation/estimator.png)

<span data-ttu-id="321d0-203">Zalecenie uczenie algorytmu, będą używane na potrzeby szkolenia modelu jest przykładem `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="321d0-203">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="321d0-204">Tworzenie `Estimator` następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="321d0-204">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="321d0-205">Tworzenie `BuildAndTrainModel()` metody tuż za `LoadData()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="321d0-205">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>
```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{


}
```
> [!NOTE]
> <span data-ttu-id="321d0-206">Ta metoda zapewni błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="321d0-206">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="321d0-207">Zdefiniować przekształceń danych, dodając następujący kod do `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-207">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>
   
[!code-csharp[DataTransformations](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="321d0-208">Ponieważ `userId` i `movieId` reprezentują użytkowników i tytułów filmów, nie rzeczywiste wartości, użyj [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) metoda przekształcania każdego `userId` i każdy `movieId` do klucza typu liczbowego `Feature`kolumny (formacie akceptowanym przez algorytmy zalecenie) i dodaj je jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="321d0-208">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="321d0-209">userId</span><span class="sxs-lookup"><span data-stu-id="321d0-209">userId</span></span> | <span data-ttu-id="321d0-210">movieId</span><span class="sxs-lookup"><span data-stu-id="321d0-210">movieId</span></span> | <span data-ttu-id="321d0-211">Etykieta</span><span class="sxs-lookup"><span data-stu-id="321d0-211">Label</span></span> | <span data-ttu-id="321d0-212">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="321d0-212">userIdEncoded</span></span> | <span data-ttu-id="321d0-213">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="321d0-213">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="321d0-214">1</span><span class="sxs-lookup"><span data-stu-id="321d0-214">1</span></span> | <span data-ttu-id="321d0-215">1</span><span class="sxs-lookup"><span data-stu-id="321d0-215">1</span></span> | <span data-ttu-id="321d0-216">4</span><span class="sxs-lookup"><span data-stu-id="321d0-216">4</span></span> | <span data-ttu-id="321d0-217">userKey1</span><span class="sxs-lookup"><span data-stu-id="321d0-217">userKey1</span></span> | <span data-ttu-id="321d0-218">movieKey1</span><span class="sxs-lookup"><span data-stu-id="321d0-218">movieKey1</span></span> |
| <span data-ttu-id="321d0-219">1</span><span class="sxs-lookup"><span data-stu-id="321d0-219">1</span></span> | <span data-ttu-id="321d0-220">3</span><span class="sxs-lookup"><span data-stu-id="321d0-220">3</span></span> | <span data-ttu-id="321d0-221">4</span><span class="sxs-lookup"><span data-stu-id="321d0-221">4</span></span> | <span data-ttu-id="321d0-222">userKey1</span><span class="sxs-lookup"><span data-stu-id="321d0-222">userKey1</span></span> | <span data-ttu-id="321d0-223">movieKey2</span><span class="sxs-lookup"><span data-stu-id="321d0-223">movieKey2</span></span> |
| <span data-ttu-id="321d0-224">1</span><span class="sxs-lookup"><span data-stu-id="321d0-224">1</span></span> | <span data-ttu-id="321d0-225">6</span><span class="sxs-lookup"><span data-stu-id="321d0-225">6</span></span> | <span data-ttu-id="321d0-226">4</span><span class="sxs-lookup"><span data-stu-id="321d0-226">4</span></span> | <span data-ttu-id="321d0-227">userKey1</span><span class="sxs-lookup"><span data-stu-id="321d0-227">userKey1</span></span> | <span data-ttu-id="321d0-228">movieKey3</span><span class="sxs-lookup"><span data-stu-id="321d0-228">movieKey3</span></span> |


<span data-ttu-id="321d0-229">Wybieranie algorytmu uczenia maszynowego, a następnie dołącza je do definicji przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-229">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="321d0-230">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia zalecenia.</span><span class="sxs-lookup"><span data-stu-id="321d0-230">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="321d0-231">[Macierz Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest typowym podejściem do zalecenia, gdy masz dane, w jaki użytkownicy, które oceniły produktów w przeszłości jest tak w przypadku zestawów danych w ramach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="321d0-231">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="321d0-232">Istnieją inne algorytmy zalecenie używane w przypadku różnych dostępnych danych (zobacz [inne algorytmy zalecenie](#other-recommendation-algorithms) sekcji poniżej, aby dowiedzieć się więcej).</span><span class="sxs-lookup"><span data-stu-id="321d0-232">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span> 

<span data-ttu-id="321d0-233">W tym przypadku `Matrix Factorization` algorytm używa metodę o nazwie "współpracy filtering", która zakłada się, że jeśli 1 użytkownik ma ten sam opinia jako 2 użytkownika dotyczących niektórych problemów, a następnie 1 użytkownika jest bardziej prawdopodobne, że ten sam sposób jak 2 użytkowników o innym problemem.</span><span class="sxs-lookup"><span data-stu-id="321d0-233">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="321d0-234">Na przykład jeśli użytkownik 1 i 2 użytkownika podobnie szybkości filmy, następnie 2 użytkownika jest bardziej prawdopodobne cieszyć się filmu 1 użytkownik ma obserwowane i o wysokiej:</span><span class="sxs-lookup"><span data-stu-id="321d0-234">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="321d0-235">Użytkownik 1</span><span class="sxs-lookup"><span data-stu-id="321d0-235">User 1</span></span> | <span data-ttu-id="321d0-236">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-236">Watched and liked movie</span></span> | <span data-ttu-id="321d0-237">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-237">Watched and liked movie</span></span> | <span data-ttu-id="321d0-238">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-238">Watched and liked movie</span></span> |
| <span data-ttu-id="321d0-239">Użytkownik 2</span><span class="sxs-lookup"><span data-stu-id="321d0-239">User 2</span></span> | <span data-ttu-id="321d0-240">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-240">Watched and liked movie</span></span> | <span data-ttu-id="321d0-241">Monitorowane i zbędne filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-241">Watched and liked movie</span></span> | <span data-ttu-id="321d0-242">Nie ma obserwowane--zaleca się filmu</span><span class="sxs-lookup"><span data-stu-id="321d0-242">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="321d0-243">`Matrix Factorization` Trainer ma kilka [opcje](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), której możesz przeczytać więcej na temat w [hiperparametrów algorytm](#algorithm-hyperparameters) poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="321d0-243">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="321d0-244">Dopasuj do modelu `Train` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-244">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="321d0-245">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) metoda szkolenie modeli modelu za pomocą podanego szkolenia zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-245">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.Data.DataView.IDataView,Microsoft.Data.DataView.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="321d0-246">Technicznie rzecz biorąc, wykonuje `Estimator` definicje, przekształcanie danych i stosując, szkolenia i zwraca kopię trenowanego modelu, który jest `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="321d0-246">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="321d0-247">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `BuildAndTrainModel()` metody i zwrócenie uczonego modelu:</span><span class="sxs-lookup"><span data-stu-id="321d0-247">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="321d0-248">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-248">Evaluate your model</span></span>

<span data-ttu-id="321d0-249">Gdy masz uczony model, korzystanie z Twoich danych testu do oceny, jak działa model.</span><span class="sxs-lookup"><span data-stu-id="321d0-249">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span> 

<span data-ttu-id="321d0-250">Tworzenie `EvaluateModel()` metody tuż za `BuildAndTrainModel()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="321d0-250">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>
```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{


}
```

<span data-ttu-id="321d0-251">Przekształcanie `Test` danych przez dodanie poniższego kodu `EvaluateModel()`: [!code-csharp[Transform](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span><span class="sxs-lookup"><span data-stu-id="321d0-251">Transform the `Test` data by adding the following code to `EvaluateModel()`: [!code-csharp[Transform](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span></span>

<span data-ttu-id="321d0-252">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda wykonuje prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="321d0-252">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="321d0-253">Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-253">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="321d0-254">Po utworzeniu prognozowania ustawiona, [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` w testowego zestawu danych i zwraca metryki dotyczące jak działa model.</span><span class="sxs-lookup"><span data-stu-id="321d0-254">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="321d0-255">Drukuj metryk oceny do konsoli, dodając następujące jako następnego wiersza kodu w `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-255">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="321d0-256">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `EvaluateModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-256">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="321d0-257">Do tej pory dane wyjściowe powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="321d0-257">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="321d0-258">W poniższych danych wyjściowych istnieją 20 iteracjach.</span><span class="sxs-lookup"><span data-stu-id="321d0-258">In this output, there are 20 iterations.</span></span> <span data-ttu-id="321d0-259">W każdej iteracji miary błąd zmniejsza i zbieżna dla wartości bliżej i bliżej 0.</span><span class="sxs-lookup"><span data-stu-id="321d0-259">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="321d0-260">`root of mean squared error` (Usługi RMS lub RMSE) jest często używane do mierzenia różnice między wartości prognozowane przez model i wartościami odczytanymi w zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="321d0-260">The `root of mean squared error` (RMS or RMSE) is frequently used to measure the differences between values predicted by a model and the values observed in a test dataset.</span></span> <span data-ttu-id="321d0-261">Z technicznego punktu widzenia jest pierwiastek kwadratowy ze średniej kwadratów błędów.</span><span class="sxs-lookup"><span data-stu-id="321d0-261">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="321d0-262">Chcesz, aby Twój wynik RMSE sposób maksymalnie zbliżony 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="321d0-262">You want your RMSE score to be as close to 1 as possible.</span></span>

<span data-ttu-id="321d0-263">`R Squared` jest wartością procentową zmiany w przewidywane wartości wyjaśnione przy użyciu modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-263">`R Squared` is the variation percentage in the predicted values explained by your model.</span></span> <span data-ttu-id="321d0-264">Jest wartością z zakresu od 0 do 1, a im bliżej wartość to 0, tym lepsze model jest.</span><span class="sxs-lookup"><span data-stu-id="321d0-264">It's a value between 0 and 1, and the closer the value is to 0, the better the model is.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="321d0-265">Użyj modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-265">Use your model</span></span>

<span data-ttu-id="321d0-266">Teraz można użyć uczonego modelu do prognozowania na nowych danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-266">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="321d0-267">Tworzenie `UseModelForSinglePrediction()` metody tuż za `EvaluateModel()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="321d0-267">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>
```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="321d0-268">Użyj `PredictionEngine` do prognozowania tę klasyfikację, dodając następujący kod do `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="321d0-268">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="321d0-269">[Klasy PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać pojedyncze wystąpienie danych, a następnie wykonaj prognozę na to pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-269">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="321d0-270">Utwórz wystąpienie obiektu `MovieRating` o nazwie `testInput` i przekaż go do aparatu prognozowania, dodając następujące jako z następującymi wierszami kodu w `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-270">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="321d0-271">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognozę na pojedynczej kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-271">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="321d0-272">Następnie można użyć `Score`, lub przewidywane oceny, ustalenie, czy polecisz film z movieId 10 użytkownika 6.</span><span class="sxs-lookup"><span data-stu-id="321d0-272">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="321d0-273">Wyższe `Score`, tym większe prawdopodobieństwo użytkownika liking konkretnego filmu.</span><span class="sxs-lookup"><span data-stu-id="321d0-273">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="321d0-274">W tym przypadku Załóżmy, że zalecane jest użycie filmów z oceną przewidywane > 3.5.</span><span class="sxs-lookup"><span data-stu-id="321d0-274">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="321d0-275">Aby wydrukować wyniki, należy dodać następujące porty jako dalej wiersze kodu `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-275">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="321d0-276">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `UseModelForSinglePrediction()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-276">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="321d0-277">Dane wyjściowe tej metody powinien wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="321d0-277">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="321d0-278">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="321d0-278">Save your model</span></span>
<span data-ttu-id="321d0-279">Aby użyć modelu do prognozowania w aplikacji użytkownika końcowego, należy najpierw zapisać modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-279">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="321d0-280">Tworzenie `SaveModel()` metody tuż za `UseModelForSinglePrediction()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="321d0-280">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>
```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{


}
```

<span data-ttu-id="321d0-281">Zapisania trenowanego modelu, dodając następujący kod w `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-281">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="321d0-282">Ta metoda zapisuje uczonego modelu do pliku zip (w folderze "Dane"), które następnie mogą być używane w innych aplikacjach platformy .NET do przewidywania przyszłych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="321d0-282">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="321d0-283">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metodę do wywołania usługi `SaveModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="321d0-283">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](../../../samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="321d0-284">Użyj zapisanych modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-284">Use your saved model</span></span>
<span data-ttu-id="321d0-285">Po zapisaniu uczonego modelu może zużywać model w różnych środowiskach (zobacz ["Poradnik"](../how-to-guides/consuming-model-ml-net.md) dowiesz się, jak do obsługi operacji modelu uczenia maszynowego uczonego w aplikacjach).</span><span class="sxs-lookup"><span data-stu-id="321d0-285">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="321d0-286">Wyniki</span><span class="sxs-lookup"><span data-stu-id="321d0-286">Results</span></span>

<span data-ttu-id="321d0-287">Po wykonaniu powyższych kroków, uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="321d0-287">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="321d0-288">Wyniki z jednej prognozowania powyżej powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="321d0-288">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="321d0-289">Może zostać wyświetlony, ostrzeżenia i przetwarzanie komunikatów, ale te komunikaty zostały usunięte z następujące wyniki dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="321d0-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="321d0-290">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="321d0-290">Congratulations!</span></span> <span data-ttu-id="321d0-291">Usługi machine learning model polecanie filmów teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="321d0-291">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="321d0-292">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="321d0-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="321d0-293">Poprawa modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-293">Improve your model</span></span>

<span data-ttu-id="321d0-294">Istnieje kilka sposobów, że może poprawić wydajność modelu, dzięki czemu można uzyskać dokładniejszych prognoz.</span><span class="sxs-lookup"><span data-stu-id="321d0-294">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="321d0-295">Dane</span><span class="sxs-lookup"><span data-stu-id="321d0-295">Data</span></span> 

<span data-ttu-id="321d0-296">Dodawanie większej ilości danych szkoleniowych, który ma wystarczającej liczby próbek dla każdego użytkownika i identyfikator filmu może zwiększyć jakość modelu zalecenia.</span><span class="sxs-lookup"><span data-stu-id="321d0-296">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="321d0-297">[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-cross-validation-ml-net.md) to technika, który losowo oceniania modeli są rozróżniane danych na podzestawy (zamiast wyodrębniania się dane testowe z zestawu danych, jak zrobiono to w ramach tego samouczka) i przyjmuje niektórych grup nauczenia danych, a niektóre z tych grup jako test dane.</span><span class="sxs-lookup"><span data-stu-id="321d0-297">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="321d0-298">Tej metody przewyższa przekształcania stosowane, dzięki czemu train-test podziału pod względem jakości modelu.</span><span class="sxs-lookup"><span data-stu-id="321d0-298">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="321d0-299">Funkcje</span><span class="sxs-lookup"><span data-stu-id="321d0-299">Features</span></span>

<span data-ttu-id="321d0-300">W tym samouczku używasz tylko trzy `Features` (`user id`, `movie id`, i `rating`) są dostarczane przez zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-300">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span> 

<span data-ttu-id="321d0-301">Gdy jest to dobry początek, w rzeczywistości możesz chcieć dodać inne atrybuty lub `Features` (na przykład, wiek, płeć, geolokalizacja itp.), jeśli są one uwzględnione w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-301">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="321d0-302">Dodawanie istotniejsze `Features` może zwiększyć wydajność modelu zalecenia.</span><span class="sxs-lookup"><span data-stu-id="321d0-302">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span> 

<span data-ttu-id="321d0-303">Jeśli nie wiesz o tym, które `Features` może być najbardziej istotne dla zadania machine learning, można również skorzystać z funkcji wkład obliczeń (FCC) i [znaczenie permutacji funkcji](../how-to-guides/determine-global-feature-importance-in-model.md), który zapewnia strukturze ML.NET Odkryj najbardziej duży wpływ `Features`.</span><span class="sxs-lookup"><span data-stu-id="321d0-303">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="321d0-304">Algorytm hiperparametrów</span><span class="sxs-lookup"><span data-stu-id="321d0-304">Algorithm hyperparameters</span></span>

<span data-ttu-id="321d0-305">Strukturze ML.NET zapewnia dobre domyślne szkolenia algorytmów, jednocześnie można dodatkowo dostrajania wydajności przez zmianę tego algorytmu [hiperparametrów](../resources/glossary.md#hyperparameter).</span><span class="sxs-lookup"><span data-stu-id="321d0-305">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="321d0-306">Aby uzyskać `Matrix Factorization`, można eksperymentować hiperparametrów takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby zobaczyć, jeśli zapewnia to lepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="321d0-306">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="321d0-307">Na przykład w tym samouczku algorytm są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="321d0-307">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="321d0-308">Inne algorytmy zalecenia</span><span class="sxs-lookup"><span data-stu-id="321d0-308">Other Recommendation Algorithms</span></span>
<span data-ttu-id="321d0-309">Algorytm factorization macierzy za pomocą filtrowania z wykorzystaniem współpracy jest tylko jedno z podejść do wykonywania rekomendacji filmów.</span><span class="sxs-lookup"><span data-stu-id="321d0-309">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="321d0-310">W wielu przypadkach może nie ma dostępnych danych oceny i mieć tylko historii film dostępny od użytkowników.</span><span class="sxs-lookup"><span data-stu-id="321d0-310">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="321d0-311">W innych przypadkach może mieć więcej niż tylko przez użytkownika klasyfikacji danych.</span><span class="sxs-lookup"><span data-stu-id="321d0-311">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="321d0-312">Algorytm</span><span class="sxs-lookup"><span data-stu-id="321d0-312">Algorithm</span></span>       | <span data-ttu-id="321d0-313">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="321d0-313">Scenario</span></span>           | <span data-ttu-id="321d0-314">Przykład</span><span class="sxs-lookup"><span data-stu-id="321d0-314">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="321d0-315">Factorization macierzy jednej klasy</span><span class="sxs-lookup"><span data-stu-id="321d0-315">One Class Matrix Factorization</span></span> | <span data-ttu-id="321d0-316">Użyj tego, jeśli masz tylko identyfikator użytkownika i movieId.</span><span class="sxs-lookup"><span data-stu-id="321d0-316">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="321d0-317">Ten styl zalecenie opiera się na scenariuszu wspólnej zakupu lub produktów często kupowane razem, co oznacza, że będzie zalecamy klientom zestaw produktów na podstawie własnych zakupu historii zamówień.</span><span class="sxs-lookup"><span data-stu-id="321d0-317">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="321d0-318">> wypróbuj działanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="321d0-318">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="321d0-319">Pole pamiętać Factorization maszyn</span><span class="sxs-lookup"><span data-stu-id="321d0-319">Field Aware Factorization Machines</span></span> | <span data-ttu-id="321d0-320">Użyj tego zaleceń, gdy masz większą liczbą funkcji poza userId, identyfikator produktu i klasyfikacji (na przykład opis produktu lub cena produktu).</span><span class="sxs-lookup"><span data-stu-id="321d0-320">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="321d0-321">Ta metoda używa również wspólne podejście filtrowania.</span><span class="sxs-lookup"><span data-stu-id="321d0-321">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="321d0-322">> wypróbuj działanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="321d0-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="321d0-323">Nowy scenariusz użytkownika</span><span class="sxs-lookup"><span data-stu-id="321d0-323">New user scenario</span></span>
<span data-ttu-id="321d0-324">Jeden powszechny problem związany z filtrowania z wykorzystaniem współpracy jest problem zimnego, czyli w przypadku nowego użytkownika bez poprzedniego danych do rysowania wniosków z.</span><span class="sxs-lookup"><span data-stu-id="321d0-324">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="321d0-325">To często problemu zadając nowych użytkowników, aby utworzyć profil i, na przykład filmy szybkość ich przejrzane w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="321d0-325">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="321d0-326">Gdy ta metoda powoduje niektórych obciążeń na użytkownika, zawiera dane wyjścia dla nowych użytkowników o Brak historii klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="321d0-326">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="321d0-327">Zasoby</span><span class="sxs-lookup"><span data-stu-id="321d0-327">Resources</span></span>
<span data-ttu-id="321d0-328">Dane używane w tym samouczku jest tworzony na podstawie [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="321d0-328">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="321d0-329">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="321d0-329">Next steps</span></span>
<span data-ttu-id="321d0-330">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="321d0-330">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="321d0-331">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="321d0-331">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="321d0-332">Przygotowanie i ładowania danych</span><span class="sxs-lookup"><span data-stu-id="321d0-332">Prepare and load your data</span></span>
> * <span data-ttu-id="321d0-333">Tworzenie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-333">Build and train a model</span></span>
> * <span data-ttu-id="321d0-334">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-334">Evaluate a model</span></span>
> * <span data-ttu-id="321d0-335">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="321d0-335">Deploy and consume a model</span></span>

<span data-ttu-id="321d0-336">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="321d0-336">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="321d0-337">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="321d0-337">Sentiment Analysis</span></span>](sentiment-analysis.md)