---
title: 'Samouczek: Tworzenie zalecenia dotyczącego filmu — factorization macierzy'
description: W tym samouczku przedstawiono sposób tworzenia zalecenia dotyczącego filmu z ML.NET w aplikacji konsolowej .NET Core. Kroki używają C# i programu Visual Studio 2019.
author: briacht
ms.date: 08/26/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 97bdef3daa296dcb88cbb158a14668205df6fee3
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107253"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="40990-104">Samouczek: Tworzenie zalecenia dotyczącego filmu przy użyciu narzędzia Matrix factorizaton z ML.NET</span><span class="sxs-lookup"><span data-stu-id="40990-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="40990-105">W tym samouczku przedstawiono sposób tworzenia zalecenia dotyczącego filmu z ML.NET w aplikacji konsolowej .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40990-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="40990-106">Kroki używają C# i programu Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="40990-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="40990-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40990-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="40990-108">Wybierz algorytm uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="40990-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="40990-109">Przygotowywanie i ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="40990-109">Prepare and load your data</span></span>
> * <span data-ttu-id="40990-110">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="40990-110">Build and train a model</span></span>
> * <span data-ttu-id="40990-111">Oceń model</span><span class="sxs-lookup"><span data-stu-id="40990-111">Evaluate a model</span></span>
> * <span data-ttu-id="40990-112">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="40990-112">Deploy and consume a model</span></span>

<span data-ttu-id="40990-113">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="40990-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="40990-114">Przepływ pracy uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="40990-114">Machine learning workflow</span></span>

<span data-ttu-id="40990-115">Wykonaj następujące kroki, aby wykonać zadanie, a także inne zadania ML.NET:</span><span class="sxs-lookup"><span data-stu-id="40990-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="40990-116">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="40990-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="40990-117">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="40990-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="40990-118">Oceń model</span><span class="sxs-lookup"><span data-stu-id="40990-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="40990-119">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="40990-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="40990-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="40990-120">Prerequisites</span></span>

* <span data-ttu-id="40990-121">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40990-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="40990-122">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="40990-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="40990-123">Istnieje kilka sposobów podejścia do problemów z zaleceniami, takich jak zalecanie listy filmów lub zalecaną listę produktów pokrewnych, ale w tym przypadku można przewidzieć klasyfikację (1-5) użytkownika w określonym filmie i zalecać film, jeśli jest wyższy niż określony próg (im wyższa ocena, tym większe prawdopodobieństwo poniesienia określonego filmu przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="40990-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="40990-124">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="40990-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="40990-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="40990-125">Create a project</span></span>

1. <span data-ttu-id="40990-126">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="40990-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="40990-127">Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="40990-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="40990-128">W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="40990-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="40990-129">Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="40990-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="40990-130">W polu tekstowym **Nazwa** wpisz "MovieRecommender", a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="40990-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="40990-131">Utwórz katalog o nazwie *dane* w projekcie w celu zapisania zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="40990-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="40990-132">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **Nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="40990-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="40990-133">Wpisz "Data" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="40990-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="40990-134">Zainstaluj pakiety NuGet **Microsoft.ml** i **Microsoft. ml. zalecenia** :</span><span class="sxs-lookup"><span data-stu-id="40990-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="40990-135">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="40990-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="40990-136">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj** , wyszukaj pozycję **Microsoft.ml**, wybierz pakiet z listy, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="40990-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="40990-137">Wybierz przycisk **OK** w oknie dialogowym **Podgląd zmian** , a następnie wybierz przycisk Akceptuję w oknie dialogowym **akceptacji licencji** , jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="40990-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="40990-138">Powtórz te kroki dla **Microsoft. ml. zalecamy**.</span><span class="sxs-lookup"><span data-stu-id="40990-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="40990-139">Dodaj następujące `using` instrukcje w górnej części pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="40990-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="40990-140">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="40990-140">Download your data</span></span>

1. <span data-ttu-id="40990-141">Pobierz dwa zestawy danych i Zapisz je w utworzonym wcześniej folderze *danych* :</span><span class="sxs-lookup"><span data-stu-id="40990-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="40990-142">Kliknij prawym przyciskiem myszy plik [*Recommendation-ratings-Train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."</span><span class="sxs-lookup"><span data-stu-id="40990-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="40990-143">Kliknij prawym przyciskiem myszy plik [*Recommendation-ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz pozycję "Zapisz link (lub cel) jako..."</span><span class="sxs-lookup"><span data-stu-id="40990-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="40990-144">Upewnij \*się, że zapisano pliki CSV do folderu *danych* lub po jego zapisaniu w \*innym miejscu Przenieś pliki CSV do folderu *dane* .</span><span class="sxs-lookup"><span data-stu-id="40990-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="40990-145">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy z \*plików CSV i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="40990-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="40990-146">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="40990-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![Kopiuj, jeśli nowszy w programie VS](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="40990-148">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="40990-148">Load your data</span></span>

<span data-ttu-id="40990-149">Pierwszym krokiem w procesie ML.NET jest przygotowanie i załadowanie modelu szkolenia i testowanie danych.</span><span class="sxs-lookup"><span data-stu-id="40990-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="40990-150">Dane klasyfikacji rekomendacji są podzielone na `Train` i `Test` zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="40990-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="40990-151">`Train` Dane są używane do dopasowania do modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="40990-152">`Test` Dane służą do przeprowadzania prognoz z przeszkolonym modelem i oceny wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="40990-153">Często istnieje 80/20 podział z `Train` i `Test` danych.</span><span class="sxs-lookup"><span data-stu-id="40990-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="40990-154">Poniżej znajduje się podgląd danych z \*plików CSV:</span><span class="sxs-lookup"><span data-stu-id="40990-154">Below is a preview of the data from your \*.csv files:</span></span>

![Podgląd danych](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="40990-156">\*W plikach CSV znajdują się cztery kolumny:</span><span class="sxs-lookup"><span data-stu-id="40990-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="40990-157">W obszarze Uczenie maszynowe kolumny, które są używane do prognozowania, są nazywane [funkcjami](../resources/glossary.md#feature), a kolumna z zwróconym przewidywaniam nazywa się [etykietą](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="40990-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="40990-158">Chcesz przewidzieć klasyfikację filmów, aby kolumna Rating była `Label`kolumną.</span><span class="sxs-lookup"><span data-stu-id="40990-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="40990-159">Pozostałe trzy `userId`kolumny, `movieId`, i `timestamp` są `Features` używane do przewidywania `Label`.</span><span class="sxs-lookup"><span data-stu-id="40990-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="40990-160">Funkcje</span><span class="sxs-lookup"><span data-stu-id="40990-160">Features</span></span>      | <span data-ttu-id="40990-161">Etykieta</span><span class="sxs-lookup"><span data-stu-id="40990-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="40990-162">Jest to konieczne, aby określić, które `Features` są używane do `Label`przewidywania.</span><span class="sxs-lookup"><span data-stu-id="40990-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="40990-163">Możesz również użyć metod, takich jak [Funkcja Permutacja](../how-to-guides/determine-global-feature-importance-in-model.md) , aby ułatwić wybór najlepszych `Features`.</span><span class="sxs-lookup"><span data-stu-id="40990-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="40990-164">W takim przypadku należy wyeliminować `timestamp` kolumnę `Feature` jako, ponieważ sygnatura czasowa nie wpływa na to, jak użytkownik ocenia dany film i w związku z tym nie przyczynia się do dokładniejszego przewidywania:</span><span class="sxs-lookup"><span data-stu-id="40990-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="40990-165">Funkcje</span><span class="sxs-lookup"><span data-stu-id="40990-165">Features</span></span>      | <span data-ttu-id="40990-166">Etykieta</span><span class="sxs-lookup"><span data-stu-id="40990-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="40990-167">Następnie należy zdefiniować strukturę danych dla klasy wejściowej.</span><span class="sxs-lookup"><span data-stu-id="40990-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="40990-168">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="40990-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="40990-169">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj > nowy element**.</span><span class="sxs-lookup"><span data-stu-id="40990-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="40990-170">W **oknie dialogowym Dodaj nowy element**wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="40990-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="40990-171">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="40990-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="40990-172">Plik *MovieRatingData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="40990-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="40990-173">Dodaj następującą `using` instrukcję na początku *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40990-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="40990-174">Utwórz klasę o nazwie `MovieRating` , usuwając istniejącą definicję klasy i dodając następujący kod w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40990-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="40990-175">`MovieRating`Określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="40990-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="40990-176">Atrybut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane.</span><span class="sxs-lookup"><span data-stu-id="40990-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="40990-177">`Label` `Label`Kolumny `userId` i`movieId` są`Features` kolumnami (dane wejściowe będą nadawać modelowi przewidywanie), a kolumna oceny jest przewidywalna (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="40990-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="40990-178">Utwórz kolejną klasę, `MovieRatingPrediction`aby reprezentować przewidywane wyniki, dodając następujący kod `MovieRating` po klasie w *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="40990-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="40990-179">W *program.cs*, Zamień na `Console.WriteLine("Hello World!")` następujący kod `Main()`w:</span><span class="sxs-lookup"><span data-stu-id="40990-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="40990-180">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET, a inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="40990-181">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="40990-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="40990-182">Po `Main()`utworzeniu należy utworzyć metodę o `LoadData()`nazwie:</span><span class="sxs-lookup"><span data-stu-id="40990-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="40990-183">Ta metoda daje błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="40990-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="40990-184">Zainicjuj zmienne ścieżki \*danych, Załaduj dane z plików CSV i `Train` Zwróć dane oraz `Test` jako `IDataView` obiekty, dodając następujący kod jako następny wiersz kodu w `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="40990-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="40990-185">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="40990-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="40990-186">`IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="40990-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="40990-187">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="40990-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="40990-188">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="40990-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="40990-189">Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="40990-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="40990-190">W takim przypadku należy podać ścieżkę do `Test` plików i `Train` wskazać zarówno nagłówek pliku tekstowego (tak, aby można było poprawnie używać nazw kolumn), jak i separator danych znak przecinka (domyślny separator jest tabulatorem).</span><span class="sxs-lookup"><span data-stu-id="40990-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="40990-191">`Main()` Dodaj następujący kod w metodzie, aby `LoadData()` wywołać metodę i zwrócić `Train` dane i `Test` :</span><span class="sxs-lookup"><span data-stu-id="40990-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="40990-192">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="40990-192">Build and train your model</span></span>

<span data-ttu-id="40990-193">Istnieją trzy podstawowe koncepcje w ML.NET: [Dane](../resources/glossary.md#data), [Transformatory](../resources/glossary.md#transformer)i [szacowania](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="40990-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="40990-194">Algorytmy szkoleniowe dotyczące uczenia maszynowego wymagają danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="40990-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="40990-195">`Transformers`służy do przekształcania danych tabelarycznych w zgodny format.</span><span class="sxs-lookup"><span data-stu-id="40990-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![obraz transformatora](./media/movie-recommendation/transformer.png)

<span data-ttu-id="40990-197">Tworzysz w ml.NET, tworząc `Estimators`. `Transformers`</span><span class="sxs-lookup"><span data-stu-id="40990-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="40990-198">`Estimators`Zapoznaj się z danymi `Transformers`i wróć.</span><span class="sxs-lookup"><span data-stu-id="40990-198">`Estimators` take in data and return `Transformers`.</span></span>

![obraz szacowania](./media/movie-recommendation/estimator.png)

<span data-ttu-id="40990-200">Algorytm szkolenia rekomendacji, który będzie używany do uczenia modelu, jest przykładem `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="40990-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="40990-201">`Estimator` Wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="40990-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="40990-202">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `LoadData()` `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="40990-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="40990-203">Ta metoda daje błąd do momentu dodania instrukcji return w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="40990-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="40990-204">Zdefiniuj przekształcenia danych, dodając następujący kod do `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="40990-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="40990-205">Ponieważ `userId` i `Feature` `movieId` [](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) `userId` reprezentują użytkowników i tytuły filmów, a nie wartości rzeczywiste, należy użyć metody MapValueToKey () do przekształcania każdego i każdego z nich w kolumnę typu klucza numerycznego (zaakceptowano format `movieId` według algorytmów rekomendacji) i Dodaj je jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="40990-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="40990-206">userId</span><span class="sxs-lookup"><span data-stu-id="40990-206">userId</span></span> | <span data-ttu-id="40990-207">movieId</span><span class="sxs-lookup"><span data-stu-id="40990-207">movieId</span></span> | <span data-ttu-id="40990-208">Etykieta</span><span class="sxs-lookup"><span data-stu-id="40990-208">Label</span></span> | <span data-ttu-id="40990-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="40990-209">userIdEncoded</span></span> | <span data-ttu-id="40990-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="40990-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="40990-211">1</span><span class="sxs-lookup"><span data-stu-id="40990-211">1</span></span> | <span data-ttu-id="40990-212">1</span><span class="sxs-lookup"><span data-stu-id="40990-212">1</span></span> | <span data-ttu-id="40990-213">4</span><span class="sxs-lookup"><span data-stu-id="40990-213">4</span></span> | <span data-ttu-id="40990-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="40990-214">userKey1</span></span> | <span data-ttu-id="40990-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="40990-215">movieKey1</span></span> |
| <span data-ttu-id="40990-216">1</span><span class="sxs-lookup"><span data-stu-id="40990-216">1</span></span> | <span data-ttu-id="40990-217">3</span><span class="sxs-lookup"><span data-stu-id="40990-217">3</span></span> | <span data-ttu-id="40990-218">4</span><span class="sxs-lookup"><span data-stu-id="40990-218">4</span></span> | <span data-ttu-id="40990-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="40990-219">userKey1</span></span> | <span data-ttu-id="40990-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="40990-220">movieKey2</span></span> |
| <span data-ttu-id="40990-221">1</span><span class="sxs-lookup"><span data-stu-id="40990-221">1</span></span> | <span data-ttu-id="40990-222">6</span><span class="sxs-lookup"><span data-stu-id="40990-222">6</span></span> | <span data-ttu-id="40990-223">4</span><span class="sxs-lookup"><span data-stu-id="40990-223">4</span></span> | <span data-ttu-id="40990-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="40990-224">userKey1</span></span> | <span data-ttu-id="40990-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="40990-225">movieKey3</span></span> |

<span data-ttu-id="40990-226">Wybierz algorytm uczenia maszynowego i dołącz go do definicji transformacji danych, dodając następujący element jako następny wiersz kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="40990-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="40990-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytmem szkoleniowym rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="40990-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="40990-228">[Factorization macierzy](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest powszechnym podejściem do rekomendacji, gdy masz dane dotyczące sposobu, w jaki użytkownicy mają sklasyfikowane produkty w przeszłości, czyli w przypadku zestawów danych w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="40990-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="40990-229">Istnieją inne algorytmy rekomendacji, w których dostępne są różne dane (zobacz [inne algorytmy rekomendacji](#other-recommendation-algorithms) poniżej, aby dowiedzieć się więcej).</span><span class="sxs-lookup"><span data-stu-id="40990-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="40990-230">W tym przypadku `Matrix Factorization` algorytm używa metody zwanej "filtrowaniem do współpracy", która zakłada, że jeśli użytkownik 1 ma taką samą opinię co użytkownik 2 w przypadku pewnego problemu, wówczas użytkownik 1 będzie prawdopodobnie taki sam jak użytkownik 2, który ma inny problem.</span><span class="sxs-lookup"><span data-stu-id="40990-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="40990-231">Na przykład jeśli użytkownik 1 i użytkownik 2 oceniają szybkość filmów w podobny sposób, wówczas użytkownik 2 może korzystać z filmu, który użytkownik 1 zaobserwuje i ocenił:</span><span class="sxs-lookup"><span data-stu-id="40990-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="40990-232">Użytkownik 1</span><span class="sxs-lookup"><span data-stu-id="40990-232">User 1</span></span> | <span data-ttu-id="40990-233">Film obserwowany i Niemnie</span><span class="sxs-lookup"><span data-stu-id="40990-233">Watched and liked movie</span></span> | <span data-ttu-id="40990-234">Film obserwowany i Niemnie</span><span class="sxs-lookup"><span data-stu-id="40990-234">Watched and liked movie</span></span> | <span data-ttu-id="40990-235">Film obserwowany i Niemnie</span><span class="sxs-lookup"><span data-stu-id="40990-235">Watched and liked movie</span></span> |
| <span data-ttu-id="40990-236">Użytkownik 2</span><span class="sxs-lookup"><span data-stu-id="40990-236">User 2</span></span> | <span data-ttu-id="40990-237">Film obserwowany i Niemnie</span><span class="sxs-lookup"><span data-stu-id="40990-237">Watched and liked movie</span></span> | <span data-ttu-id="40990-238">Film obserwowany i Niemnie</span><span class="sxs-lookup"><span data-stu-id="40990-238">Watched and liked movie</span></span> | <span data-ttu-id="40990-239">Nie został obserwowany — ZALECAnym filmem</span><span class="sxs-lookup"><span data-stu-id="40990-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="40990-240">Trainer ma kilka [opcji](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), które można dowiedzieć się więcej o w poniższej sekcji [preparameters Algorithm](#algorithm-hyperparameters). `Matrix Factorization`</span><span class="sxs-lookup"><span data-stu-id="40990-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="40990-241">Dopasuj model do `Train` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu `BuildAndTrainModel()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="40990-242">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model z udostępnionym zestawem danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="40990-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="40990-243">Technicznie wykonuje `Estimator` definicje przez Przekształcanie danych i stosowanie szkoleń i zwraca z powrotem model szkolony, który `Transformer`jest.</span><span class="sxs-lookup"><span data-stu-id="40990-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="40990-244">Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `BuildAndTrainModel()` wywołać metodę i zwrócić szkolony model:</span><span class="sxs-lookup"><span data-stu-id="40990-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="40990-245">Oceń model</span><span class="sxs-lookup"><span data-stu-id="40990-245">Evaluate your model</span></span>

<span data-ttu-id="40990-246">Po przeprowadzeniu szkolenia modelu Użyj danych testowych, aby oszacować, jak działa model.</span><span class="sxs-lookup"><span data-stu-id="40990-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="40990-247">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `BuildAndTrainModel()` `EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="40990-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="40990-248">Przekształć `EvaluateModel()`dane, dodając następujący kod do: `Test`</span><span class="sxs-lookup"><span data-stu-id="40990-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="40990-249">Metoda [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) udostępnia prognozy dla wielu podanych danych wejściowych dla testu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="40990-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="40990-250">Oceń model poprzez dodanie następujących elementów jako następny wiersz kodu w `EvaluateModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="40990-251">Po zestawie prognoz Metoda [oceny ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowanym zestawie danych i zwraca metryki dotyczące sposobu działania modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="40990-252">Wydrukuj metryki oceny do konsoli, dodając następujący kod jako następny wiersz kodu w `EvaluateModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="40990-253">Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `EvaluateModel()` wywołać metodę:</span><span class="sxs-lookup"><span data-stu-id="40990-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="40990-254">Dane wyjściowe do tej pory powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="40990-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="40990-255">W tych danych wyjściowych występuje 20 iteracji.</span><span class="sxs-lookup"><span data-stu-id="40990-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="40990-256">W każdej iteracji miara błędów jest zmniejszana i zbieżna bliżej i bliższa 0.</span><span class="sxs-lookup"><span data-stu-id="40990-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="40990-257">`root of mean squared error` (RMS lub RMSE) służy do mierzenia różnic między wartościami przewidywanymi przez model i wartościami obserwowanymi testów zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="40990-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="40990-258">Jest to technicznie pierwiastek kwadratowy średniej kwadratów błędów.</span><span class="sxs-lookup"><span data-stu-id="40990-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="40990-259">Im niższa wartość, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="40990-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="40990-260">`R Squared`wskazuje, jak dobre dane pasują do modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="40990-261">Zakresy z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="40990-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="40990-262">Wartość 0 oznacza, że dane są losowo lub w przeciwnym razie nie można dopasować do modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="40990-263">Wartość 1 oznacza, że model dokładnie pasuje do danych.</span><span class="sxs-lookup"><span data-stu-id="40990-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="40990-264">Chcesz, aby `R Squared` wynik był możliwie blisko 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="40990-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="40990-265">Kompilowanie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="40990-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="40990-266">Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli.</span><span class="sxs-lookup"><span data-stu-id="40990-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="40990-267">Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi parametrami funkcji Hyper-Parameters dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="40990-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="40990-268">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Popraw model](#improve-your-model) poniżej.</span><span class="sxs-lookup"><span data-stu-id="40990-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="40990-269">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="40990-269">Use your model</span></span>

<span data-ttu-id="40990-270">Teraz można użyć Twojego przeszkolonego modelu do prognozowania nowych danych.</span><span class="sxs-lookup"><span data-stu-id="40990-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="40990-271">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `EvaluateModel()` `UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="40990-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="40990-272">Użyj do przewidywania klasyfikacji, dodając następujący kod do `UseModelForSinglePrediction()`: `PredictionEngine`</span><span class="sxs-lookup"><span data-stu-id="40990-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="40990-273">[Klasa PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia przekazywanie pojedynczej instancji danych, a następnie przeprowadza prognozowanie na tym pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="40990-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="40990-274">Utwórz wystąpienie o `MovieRating` nazwie `testInput` i przekaż je do aparatu przewidywania, dodając następujący element jako następny `UseModelForSinglePrediction()` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="40990-275">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczej kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="40990-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="40990-276">Następnie można użyć `Score`lub klasyfikacji przewidywanej, aby określić, czy chcesz zalecić film z movieId 10 do użytkownika 6.</span><span class="sxs-lookup"><span data-stu-id="40990-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="40990-277">Im wyższy poziom `Score`, tym większe prawdopodobieństwo, że użytkownik przydzieli określony film.</span><span class="sxs-lookup"><span data-stu-id="40990-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="40990-278">W tym przypadku Załóżmy, że zaleca się używanie filmów z przewidywaną klasyfikacją > 3,5.</span><span class="sxs-lookup"><span data-stu-id="40990-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="40990-279">Aby wydrukować wyniki, Dodaj następujący kod jako następny wiersz kodu w `UseModelForSinglePrediction()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="40990-280">Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `UseModelForSinglePrediction()` wywołać metodę:</span><span class="sxs-lookup"><span data-stu-id="40990-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="40990-281">Dane wyjściowe tej metody powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="40990-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="40990-282">Zapisz model</span><span class="sxs-lookup"><span data-stu-id="40990-282">Save your model</span></span>

<span data-ttu-id="40990-283">Aby używać modelu do prognozowania aplikacji użytkowników końcowych, należy najpierw zapisać model.</span><span class="sxs-lookup"><span data-stu-id="40990-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="40990-284">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `UseModelForSinglePrediction()` `SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="40990-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="40990-285">Zapisz swój przeszkolony model, dodając następujący kod w `SaveModel()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="40990-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="40990-286">Ta metoda zapisuje swój przeszkolony model do pliku zip (w folderze "dane"), który można następnie użyć w innych aplikacjach .NET do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="40990-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="40990-287">Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie, aby `SaveModel()` wywołać metodę:</span><span class="sxs-lookup"><span data-stu-id="40990-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="40990-288">Użyj zapisanego modelu</span><span class="sxs-lookup"><span data-stu-id="40990-288">Use your saved model</span></span>

<span data-ttu-id="40990-289">Po zapisaniu przeszkolonego modelu można korzystać z modelu w różnych środowiskach (zobacz [Przewodnik po poradniku](../how-to-guides/consuming-model-ml-net.md) ), aby dowiedzieć się, jak operacjonalizować model uczenia maszynowego w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="40990-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="40990-290">Wyniki</span><span class="sxs-lookup"><span data-stu-id="40990-290">Results</span></span>

<span data-ttu-id="40990-291">Po wykonaniu powyższych kroków uruchom aplikację konsolową (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="40990-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="40990-292">Wyniki z pojedynczej przewidywania powyżej powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="40990-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="40990-293">Mogą pojawić się ostrzeżenia lub komunikaty o przetwarzaniu, ale te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="40990-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="40990-294">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="40990-294">Congratulations!</span></span> <span data-ttu-id="40990-295">Pomyślnie skompilowano model uczenia maszynowego na potrzeby zalecanych filmów.</span><span class="sxs-lookup"><span data-stu-id="40990-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="40990-296">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) .</span><span class="sxs-lookup"><span data-stu-id="40990-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="40990-297">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="40990-297">Improve your model</span></span>

<span data-ttu-id="40990-298">Istnieje kilka sposobów na zwiększenie wydajności modelu, dzięki czemu można uzyskać dokładniejsze przewidywania.</span><span class="sxs-lookup"><span data-stu-id="40990-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="40990-299">Dane</span><span class="sxs-lookup"><span data-stu-id="40990-299">Data</span></span>

<span data-ttu-id="40990-300">Dodanie więcej danych szkoleniowych, które mają wystarczającą ilość próbek dla każdego użytkownika i identyfikatora filmu, może pomóc w ulepszeniu jakości modelu rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="40990-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="40990-301">[Krzyżowe sprawdzanie poprawności](../how-to-guides/train-cross-validation-ml-net.md) to technika służąca do oceniania modeli, które losowo dzielą dane na podzestawy (zamiast wyodrębniania danych testowych z zestawu danych, takiego jak w tym samouczku), a także niektóre grupy jako dane dotyczące uczenia i niektóre z tych grup.</span><span class="sxs-lookup"><span data-stu-id="40990-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="40990-302">Ta metoda prowadzi do podzielenia testu pociągowego pod względem jakości modelu.</span><span class="sxs-lookup"><span data-stu-id="40990-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="40990-303">Funkcje</span><span class="sxs-lookup"><span data-stu-id="40990-303">Features</span></span>

<span data-ttu-id="40990-304">W tym samouczku używane są tylko `Features` trzy (`user id`, `movie id`i `rating`), które są udostępniane przez zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="40990-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="40990-305">Chociaż jest to dobry początek, w rzeczywistości warto dodać inne atrybuty lub `Features` (na przykład wiek, płeć, lokalizację geograficzną itp.), jeśli są one zawarte w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="40990-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="40990-306">Dodanie bardziej istotnych `Features` informacji może pomóc w zwiększeniu wydajności modelu rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="40990-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="40990-307">Jeśli nie masz pewności, co `Features` może być najbardziej odpowiednie dla zadania uczenia maszynowego, możesz również skorzystać z funkcji obliczania udziałów funkcji (FCC) i znaczenia wartości [permutacji](../how-to-guides/determine-global-feature-importance-in-model.md), która ml.NET umożliwia odnajdywanie najbardziej wpływ `Features`.</span><span class="sxs-lookup"><span data-stu-id="40990-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="40990-308">Moje parametry algorytmu</span><span class="sxs-lookup"><span data-stu-id="40990-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="40990-309">Chociaż ML.NET zapewnia dobre domyślne algorytmy szkoleniowe, można dokładniej dostosować wydajność przez zmianę [parametrów](../resources/glossary.md#hyperparameter)algorytmu.</span><span class="sxs-lookup"><span data-stu-id="40990-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="40990-310">W `Matrix Factorization`przypadku programu można eksperymentować z parametrami, takimi jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , aby sprawdzić, czy daje on lepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="40990-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="40990-311">Na przykład w tym samouczku są dostępne następujące opcje algorytmu:</span><span class="sxs-lookup"><span data-stu-id="40990-311">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="40990-312">Inne algorytmy rekomendacji</span><span class="sxs-lookup"><span data-stu-id="40990-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="40990-313">Algorytm factorization Matrix z filtrowaniem do współpracy jest tylko jednym podejściem do wykonywania zaleceń dotyczących filmów.</span><span class="sxs-lookup"><span data-stu-id="40990-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="40990-314">W wielu przypadkach możesz nie mieć dostępnych danych klasyfikacji i mieć tylko historię filmów dostępną dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="40990-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="40990-315">W innych przypadkach może być więcej niż tylko dane oceny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40990-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="40990-316">Algorytm</span><span class="sxs-lookup"><span data-stu-id="40990-316">Algorithm</span></span>       | <span data-ttu-id="40990-317">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="40990-317">Scenario</span></span>           | <span data-ttu-id="40990-318">Przykład</span><span class="sxs-lookup"><span data-stu-id="40990-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="40990-319">Factorization macierzy klasy 1</span><span class="sxs-lookup"><span data-stu-id="40990-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="40990-320">Użyj tego, jeśli masz tylko userId i movieId.</span><span class="sxs-lookup"><span data-stu-id="40990-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="40990-321">Ten styl rekomendacji jest oparty na scenariuszu współsprzedaży lub produktów często kupowanych, co oznacza, że klient będzie polecał klientom zestaw produktów oparty na ich historii zakupów.</span><span class="sxs-lookup"><span data-stu-id="40990-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="40990-322">> Wypróbuj</span><span class="sxs-lookup"><span data-stu-id="40990-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="40990-323">Maszyny factorization z obsługą pól</span><span class="sxs-lookup"><span data-stu-id="40990-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="40990-324">Użyj tego do zaleceń, gdy masz więcej funkcji poza userId, productId i klasyfikacją (na przykład Opis produktu lub cena produktu).</span><span class="sxs-lookup"><span data-stu-id="40990-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="40990-325">Ta metoda używa również podejścia do filtrowania wspólnie.</span><span class="sxs-lookup"><span data-stu-id="40990-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="40990-326">> Wypróbuj</span><span class="sxs-lookup"><span data-stu-id="40990-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="40990-327">Nowy scenariusz użytkownika</span><span class="sxs-lookup"><span data-stu-id="40990-327">New user scenario</span></span>

<span data-ttu-id="40990-328">Jednym z typowych problemów w filtrowaniu do współpracy jest problem z zimnym rozpoczęciem, który jest przeznaczony dla nowego użytkownika, który nie ma żadnych poprzednich danych do rysowania wniosków z.</span><span class="sxs-lookup"><span data-stu-id="40990-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="40990-329">Ten problem jest często rozwiązywany przez zaproszenie nowych użytkowników o utworzenie profilu, a na przykład ocenianie filmów, które pojawiły się w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="40990-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="40990-330">Chociaż ta metoda nakłada pewne obciążenie dla użytkownika, zapewnia pewne dane wyjściowe dla nowych użytkowników bez historii klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="40990-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="40990-331">Zasoby</span><span class="sxs-lookup"><span data-stu-id="40990-331">Resources</span></span>

<span data-ttu-id="40990-332">Dane używane w tym samouczku pochodzą z [zestawu danych MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="40990-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="40990-333">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="40990-333">Next steps</span></span>

<span data-ttu-id="40990-334">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="40990-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="40990-335">Wybierz algorytm uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="40990-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="40990-336">Przygotowywanie i ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="40990-336">Prepare and load your data</span></span>
> * <span data-ttu-id="40990-337">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="40990-337">Build and train a model</span></span>
> * <span data-ttu-id="40990-338">Oceń model</span><span class="sxs-lookup"><span data-stu-id="40990-338">Evaluate a model</span></span>
> * <span data-ttu-id="40990-339">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="40990-339">Deploy and consume a model</span></span>

<span data-ttu-id="40990-340">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="40990-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="40990-341">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="40990-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
