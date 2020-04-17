---
title: 'Samouczek: Zbuduj rekomendację filmu - faktoizacja macierzy'
description: W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core. Kroki używają języka C# i Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a1d7ef6226580fd3172b5714f9d7358298ba6668
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608000"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="412f6-104">Samouczek: Tworzenie programu rekomendacyjnego przy użyciu faktoryzacji macierzy z ML.NET</span><span class="sxs-lookup"><span data-stu-id="412f6-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="412f6-105">W tym samouczku pokazano, jak utworzyć program polecający film z ML.NET w aplikacji konsoli .NET Core.</span><span class="sxs-lookup"><span data-stu-id="412f6-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="412f6-106">Kroki używają języka C# i Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="412f6-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="412f6-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="412f6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="412f6-108">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="412f6-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="412f6-109">Przygotowanie i załadowanie danych</span><span class="sxs-lookup"><span data-stu-id="412f6-109">Prepare and load your data</span></span>
> * <span data-ttu-id="412f6-110">Tworzenie i szkolenie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-110">Build and train a model</span></span>
> * <span data-ttu-id="412f6-111">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-111">Evaluate a model</span></span>
> * <span data-ttu-id="412f6-112">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-112">Deploy and consume a model</span></span>

<span data-ttu-id="412f6-113">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)</span><span class="sxs-lookup"><span data-stu-id="412f6-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="412f6-114">Przepływ pracy uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="412f6-114">Machine learning workflow</span></span>

<span data-ttu-id="412f6-115">Aby wykonać zadanie, wykonasz następujące kroki, a także wszelkie inne ML.NET zadanie:</span><span class="sxs-lookup"><span data-stu-id="412f6-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="412f6-116">Załaduj swoje dane</span><span class="sxs-lookup"><span data-stu-id="412f6-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="412f6-117">Zbuduj i trenuj swój model</span><span class="sxs-lookup"><span data-stu-id="412f6-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="412f6-118">Ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="412f6-119">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="412f6-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="412f6-120">Prerequisites</span></span>

* <span data-ttu-id="412f6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowsze lub Visual Studio 2017 w wersji 15.6 lub nowszej z zainstalowanym obciążeniem ".NET Core rozwoju między platformami".</span><span class="sxs-lookup"><span data-stu-id="412f6-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="412f6-122">Wybierz odpowiednie zadanie uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="412f6-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="412f6-123">Istnieje kilka sposobów podejścia do problemów z rekomendacjami, takich jak zalecanie listy filmów lub polecanie listy powiązanych produktów, ale w tym przypadku można przewidzieć, jaką ocenę (1-5) użytkownik da konkretnemu filmowi i zalecić ten film, jeśli jest wyższy niż zdefiniowany próg (im wyższa ocena, tym większe prawdopodobieństwo polubienia konkretnego filmu przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="412f6-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="412f6-124">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="412f6-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="412f6-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="412f6-125">Create a project</span></span>

1. <span data-ttu-id="412f6-126">Otwórz program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="412f6-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="412f6-127">Z paska menu **wybierz pozycję Plik** > **nowy** > **projekt.**</span><span class="sxs-lookup"><span data-stu-id="412f6-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="412f6-128">W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#,** po którym następuje węzeł **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="412f6-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="412f6-129">Następnie wybierz szablon projektu **aplikacji konsoli (net core).**</span><span class="sxs-lookup"><span data-stu-id="412f6-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="412f6-130">W polu **tekstowym Nazwa** wpisz "MovieRecommender", a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="412f6-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="412f6-131">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="412f6-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="412f6-132">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **nowy folder**.</span><span class="sxs-lookup"><span data-stu-id="412f6-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="412f6-133">Wpisz "Dane" i naciśnij enter.</span><span class="sxs-lookup"><span data-stu-id="412f6-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="412f6-134">Zainstaluj **pakiety NuGet Microsoft.ML** i **Microsoft.ML.Recommender:**</span><span class="sxs-lookup"><span data-stu-id="412f6-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="412f6-135">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="412f6-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="412f6-136">Wybierz "nuget.org" jako źródło pakietu, wybierz kartę **Przeglądaj,** wyszukaj **Microsoft.ML**, wybierz pakiet na liście i wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="412f6-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="412f6-137">Wybierz przycisk **OK** w oknie **dialogowym Podgląd zmian,** a następnie wybierz przycisk **Akceptuję** w oknie dialogowym **Akceptacja licencji,** jeśli zgadzasz się z postanowieniami licencyjnymi dotyczącymi wymienionych pakietów.</span><span class="sxs-lookup"><span data-stu-id="412f6-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="412f6-138">Powtórz te kroki dla **programu Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="412f6-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="412f6-139">Dodaj następujące `using` instrukcje w górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="412f6-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="412f6-140">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="412f6-140">Download your data</span></span>

1. <span data-ttu-id="412f6-141">Pobierz dwa zestawy danych i zapisz je w folderze *Dane,* który został wcześniej utworzony:</span><span class="sxs-lookup"><span data-stu-id="412f6-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="412f6-142">Kliknij prawym przyciskiem myszy [*rekomendację-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) i wybierz "Zapisz link (lub cel) jako..."</span><span class="sxs-lookup"><span data-stu-id="412f6-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="412f6-143">Kliknij prawym przyciskiem myszy [*rekomendację-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) i wybierz "Zapisz link (lub cel) jako..."</span><span class="sxs-lookup"><span data-stu-id="412f6-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="412f6-144">Upewnij się, że \*pliki csv są zapisywane w folderze *Dane* lub \*po zapisaniu ich w innym miejscu, przenieś pliki csv do folderu *Dane.*</span><span class="sxs-lookup"><span data-stu-id="412f6-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="412f6-145">W Eksploratorze rozwiązań \*kliknij prawym przyciskiem myszy każdy z plików csv i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="412f6-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="412f6-146">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="412f6-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![GIF użytkownika wybierającego kopię, jeśli nowsza w programie VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="412f6-148">Załaduj swoje dane</span><span class="sxs-lookup"><span data-stu-id="412f6-148">Load your data</span></span>

<span data-ttu-id="412f6-149">Pierwszym krokiem w procesie ML.NET jest przygotowanie i załadowanie danych szkoleniowych i testowych modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="412f6-150">Dane klasyfikacji rekomendacji są `Train` `Test` dzielone na zestawy danych i.</span><span class="sxs-lookup"><span data-stu-id="412f6-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="412f6-151">Dane `Train` są używane do dopasowania modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="412f6-152">Dane `Test` są używane do tworzenia prognoz z przeszkolonym modelem i oceny wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="412f6-153">Często ma podział 80/20 z `Train` danymi `Test` i danymi.</span><span class="sxs-lookup"><span data-stu-id="412f6-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="412f6-154">Poniżej znajduje się podgląd \*danych z plików csv:</span><span class="sxs-lookup"><span data-stu-id="412f6-154">Below is a preview of the data from your \*.csv files:</span></span>

![Zrzut ekranu przedstawiający podgląd zestawu danych CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="412f6-156">W \*plikach csv znajdują się cztery kolumny:</span><span class="sxs-lookup"><span data-stu-id="412f6-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="412f6-157">W uczeniu maszynowym kolumny, które są używane do przewidywania są nazywane [Funkcje](../resources/glossary.md#feature), a kolumna z zwróconą przewidywaniem nosi nazwę [Label](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="412f6-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="412f6-158">Chcesz przewidzieć oceny filmów, więc kolumna `Label`klasyfikacji to .</span><span class="sxs-lookup"><span data-stu-id="412f6-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="412f6-159">Pozostałe trzy kolumny, `userId` `movieId`, `timestamp` i `Features` są używane `Label`do przewidywania .</span><span class="sxs-lookup"><span data-stu-id="412f6-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="412f6-160">Funkcje</span><span class="sxs-lookup"><span data-stu-id="412f6-160">Features</span></span>      | <span data-ttu-id="412f6-161">Label</span><span class="sxs-lookup"><span data-stu-id="412f6-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="412f6-162">To do Ciebie, aby `Features` zdecydować, które `Label`są używane do przewidywania .</span><span class="sxs-lookup"><span data-stu-id="412f6-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="412f6-163">Można również użyć metod, takich jak [znaczenie funkcji permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) aby pomóc w wyborze najlepszego `Features`.</span><span class="sxs-lookup"><span data-stu-id="412f6-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="412f6-164">W takim przypadku należy `timestamp` wyeliminować kolumnę jako, ponieważ sygnatura czasowa `Feature` nie ma wpływu na sposób, w jaki użytkownik ocenia dany film, a tym samym nie przyczyni się do dokładniejszej prognozowania:</span><span class="sxs-lookup"><span data-stu-id="412f6-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="412f6-165">Funkcje</span><span class="sxs-lookup"><span data-stu-id="412f6-165">Features</span></span>      | <span data-ttu-id="412f6-166">Label</span><span class="sxs-lookup"><span data-stu-id="412f6-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="412f6-167">Następnie należy zdefiniować strukturę danych dla klasy wejściowej.</span><span class="sxs-lookup"><span data-stu-id="412f6-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="412f6-168">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="412f6-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="412f6-169">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj > Nowy element**.</span><span class="sxs-lookup"><span data-stu-id="412f6-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="412f6-170">W **oknie dialogowym Dodawanie nowego elementu**wybierz pozycję **Klasa** i zmień pole **Nazwa** na *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="412f6-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="412f6-171">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="412f6-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="412f6-172">Plik *MovieRatingData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="412f6-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="412f6-173">Dodaj następującą `using` instrukcję do górnej części *MovieRatingData.cs:*</span><span class="sxs-lookup"><span data-stu-id="412f6-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="412f6-174">Utwórz klasę `MovieRating` wywoływaną przez usunięcie istniejącej definicji klasy i dodanie następującego kodu w *MovieRatingData.cs:*</span><span class="sxs-lookup"><span data-stu-id="412f6-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="412f6-175">`MovieRating`określa klasę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="412f6-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="412f6-176">[Atrybut LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) określa, które kolumny (według indeksu kolumn) w zestawie danych powinny zostać załadowane.</span><span class="sxs-lookup"><span data-stu-id="412f6-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="412f6-177">I `userId` `movieId` kolumny są `Features` twoje (dane wejściowe, które podasz modelowi do przewidzenia `Label`), a kolumna klasyfikacji jest `Label` tym, który będzie przewidywany (dane wyjściowe modelu).</span><span class="sxs-lookup"><span data-stu-id="412f6-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="412f6-178">Utwórz inną `MovieRatingPrediction`klasę , aby reprezentować przewidywane `MovieRating` wyniki, dodając następujący kod po klasie w *MovieRatingData.cs:*</span><span class="sxs-lookup"><span data-stu-id="412f6-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="412f6-179">W *Program.cs*, wymienić `Console.WriteLine("Hello World!")` na następujący `Main()`kod wewnątrz:</span><span class="sxs-lookup"><span data-stu-id="412f6-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="412f6-180">Klasa [MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET, a inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="412f6-181">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="412f6-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="412f6-182">Po `Main()`, utwórz `LoadData()`metodę o nazwie :</span><span class="sxs-lookup"><span data-stu-id="412f6-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="412f6-183">Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="412f6-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="412f6-184">Inicjuj zmienne ścieżki danych, \*ładuj dane z `Train` plików `Test` csv i zwracaj dane jako `IDataView` obiekty, dodając następujące elementy jako następny wiersz kodu w `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="412f6-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="412f6-185">Dane w ML.NET są reprezentowane jako [klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="412f6-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="412f6-186">`IDataView`jest elastycznym, skutecznym sposobem opisywania danych tabelaryjskich (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="412f6-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="412f6-187">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="412f6-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="412f6-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="412f6-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="412f6-189">Przyjmuje zmienne ścieżki danych i `IDataView`zwraca plik .</span><span class="sxs-lookup"><span data-stu-id="412f6-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="412f6-190">W takim przypadku należy podać `Test` ścieżkę dla i `Train` plików i wskazać zarówno nagłówek pliku tekstowego (dzięki czemu można użyć nazwy kolumny poprawnie) i separator danych znaków przecinka (domyślny separator jest kartę).</span><span class="sxs-lookup"><span data-stu-id="412f6-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="412f6-191">Dodaj następujący kod `Main()` w metodzie, aby wywołać metodę `LoadData()` i zwrócić `Train` dane i: `Test`</span><span class="sxs-lookup"><span data-stu-id="412f6-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="412f6-192">Zbuduj i trenuj swój model</span><span class="sxs-lookup"><span data-stu-id="412f6-192">Build and train your model</span></span>

<span data-ttu-id="412f6-193">Istnieją trzy główne pojęcia w ML.NET: [Dane,](../resources/glossary.md#data) [Transformatory](../resources/glossary.md#transformer)i [Estymatory.](../resources/glossary.md#estimator)</span><span class="sxs-lookup"><span data-stu-id="412f6-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="412f6-194">Algorytmy szkoleniowe uczenia maszynowego wymagają danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="412f6-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="412f6-195">`Transformers`są używane do przekształcania danych tabelaryczne do zgodnego formatu.</span><span class="sxs-lookup"><span data-stu-id="412f6-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Diagram przepływu danych transformatora.](./media/movie-recommendation/data-transformer-transformed.png)

<span data-ttu-id="412f6-197">Tworzenie `Transformers` w ML.NET przez utworzenie `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="412f6-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="412f6-198">`Estimators`danych i zwrócić `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="412f6-198">`Estimators` take in data and return `Transformers`.</span></span>

![Diagram przepływu danych estymatora.](./media/movie-recommendation/data-estimator-transformer.png)

<span data-ttu-id="412f6-200">Algorytm szkolenia rekomendacji, który będzie używany do `Estimator`szkolenia modelu jest przykładem .</span><span class="sxs-lookup"><span data-stu-id="412f6-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="412f6-201">Stwórz z `Estimator` następujących kroków:</span><span class="sxs-lookup"><span data-stu-id="412f6-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="412f6-202">Utwórz `BuildAndTrainModel()` metodę, zaraz `LoadData()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="412f6-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="412f6-203">Ta metoda daje błąd, dopóki nie dodasz return instrukcji w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="412f6-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="412f6-204">Zdefiniuj przekształcenia danych, dodając następujący kod do: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="412f6-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="412f6-205">Ponieważ `userId` `movieId` i reprezentują użytkowników i tytuły filmów, a nie wartości rzeczywiste, używasz `userId` Metody `movieId` [MapValueToKey(),](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) aby przekształcić każdą i każdą kolumnę o typie `Feature` klucza numerycznego (format akceptowany przez algorytmy rekomendacji) i dodać je jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="412f6-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="412f6-206">userId</span><span class="sxs-lookup"><span data-stu-id="412f6-206">userId</span></span> | <span data-ttu-id="412f6-207">movieId (ida)</span><span class="sxs-lookup"><span data-stu-id="412f6-207">movieId</span></span> | <span data-ttu-id="412f6-208">Label</span><span class="sxs-lookup"><span data-stu-id="412f6-208">Label</span></span> | <span data-ttu-id="412f6-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="412f6-209">userIdEncoded</span></span> | <span data-ttu-id="412f6-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="412f6-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="412f6-211">1</span><span class="sxs-lookup"><span data-stu-id="412f6-211">1</span></span> | <span data-ttu-id="412f6-212">1</span><span class="sxs-lookup"><span data-stu-id="412f6-212">1</span></span> | <span data-ttu-id="412f6-213">4</span><span class="sxs-lookup"><span data-stu-id="412f6-213">4</span></span> | <span data-ttu-id="412f6-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="412f6-214">userKey1</span></span> | <span data-ttu-id="412f6-215">filmKey1</span><span class="sxs-lookup"><span data-stu-id="412f6-215">movieKey1</span></span> |
| <span data-ttu-id="412f6-216">1</span><span class="sxs-lookup"><span data-stu-id="412f6-216">1</span></span> | <span data-ttu-id="412f6-217">3</span><span class="sxs-lookup"><span data-stu-id="412f6-217">3</span></span> | <span data-ttu-id="412f6-218">4</span><span class="sxs-lookup"><span data-stu-id="412f6-218">4</span></span> | <span data-ttu-id="412f6-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="412f6-219">userKey1</span></span> | <span data-ttu-id="412f6-220">filmKey2</span><span class="sxs-lookup"><span data-stu-id="412f6-220">movieKey2</span></span> |
| <span data-ttu-id="412f6-221">1</span><span class="sxs-lookup"><span data-stu-id="412f6-221">1</span></span> | <span data-ttu-id="412f6-222">6</span><span class="sxs-lookup"><span data-stu-id="412f6-222">6</span></span> | <span data-ttu-id="412f6-223">4</span><span class="sxs-lookup"><span data-stu-id="412f6-223">4</span></span> | <span data-ttu-id="412f6-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="412f6-224">userKey1</span></span> | <span data-ttu-id="412f6-225">filmKey3</span><span class="sxs-lookup"><span data-stu-id="412f6-225">movieKey3</span></span> |

<span data-ttu-id="412f6-226">Wybierz algorytm uczenia maszynowego i dołącz go do definicji transformacji danych, dodając `BuildAndTrainModel()`następujące elementy jako następny wiersz kodu w:</span><span class="sxs-lookup"><span data-stu-id="412f6-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="412f6-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) jest algorytm szkolenia rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="412f6-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="412f6-228">[Macierz Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) jest wspólne podejście do zalecenia, gdy masz dane na temat sposobu, w jaki użytkownicy ocenili produkty w przeszłości, co ma miejsce w przypadku zestawów danych w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="412f6-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="412f6-229">Istnieją inne algorytmy rekomendacji, gdy masz różne dane dostępne (zobacz [inne algorytmy rekomendacji](#other-recommendation-algorithms) poniżej, aby dowiedzieć się więcej).</span><span class="sxs-lookup"><span data-stu-id="412f6-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="412f6-230">W takim przypadku `Matrix Factorization` algorytm używa metody o nazwie "filtrowanie współpracy", która zakłada, że jeśli użytkownik 1 ma taką samą opinię jak Użytkownik 2 w pewnym problemie, użytkownik 1 jest bardziej prawdopodobne, aby czuć się tak samo jak Użytkownik 2 o innym problemie.</span><span class="sxs-lookup"><span data-stu-id="412f6-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="412f6-231">Na przykład, jeśli użytkownik 1 i Użytkownik 2 oceniają filmy w podobny sposób, użytkownik 2 jest bardziej skłonny do korzystania z filmu, który użytkownik 1 oglądał i wysoko ocenił:</span><span class="sxs-lookup"><span data-stu-id="412f6-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="412f6-232">Użytkownik 1</span><span class="sxs-lookup"><span data-stu-id="412f6-232">User 1</span></span> | <span data-ttu-id="412f6-233">Oglądany i lubiany film</span><span class="sxs-lookup"><span data-stu-id="412f6-233">Watched and liked movie</span></span> | <span data-ttu-id="412f6-234">Oglądany i lubiany film</span><span class="sxs-lookup"><span data-stu-id="412f6-234">Watched and liked movie</span></span> | <span data-ttu-id="412f6-235">Oglądany i lubiany film</span><span class="sxs-lookup"><span data-stu-id="412f6-235">Watched and liked movie</span></span> |
| <span data-ttu-id="412f6-236">Użytkownik 2</span><span class="sxs-lookup"><span data-stu-id="412f6-236">User 2</span></span> | <span data-ttu-id="412f6-237">Oglądany i lubiany film</span><span class="sxs-lookup"><span data-stu-id="412f6-237">Watched and liked movie</span></span> | <span data-ttu-id="412f6-238">Oglądany i lubiany film</span><span class="sxs-lookup"><span data-stu-id="412f6-238">Watched and liked movie</span></span> | <span data-ttu-id="412f6-239">Nie oglądałem -- POLECAM film</span><span class="sxs-lookup"><span data-stu-id="412f6-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="412f6-240">Trener `Matrix Factorization` ma kilka [opcji](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), o których można przeczytać więcej w [hiperparametrach algorytm](#algorithm-hyperparameters) poniżej.</span><span class="sxs-lookup"><span data-stu-id="412f6-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="412f6-241">Dopasuj `Train` model do danych i zwróć przeszkolony model, dodając następujący `BuildAndTrainModel()` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="412f6-242">[Metoda Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) trenuje model z dostarczonym zestawem danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="412f6-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="412f6-243">Technicznie wykonuje `Estimator` definicje, przekształcając dane i stosując szkolenie, i zwraca z powrotem przeszkolony `Transformer`model, który jest .</span><span class="sxs-lookup"><span data-stu-id="412f6-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="412f6-244">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę `BuildAndTrainModel()` i zwrócić przeszkolony model:</span><span class="sxs-lookup"><span data-stu-id="412f6-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="412f6-245">Ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-245">Evaluate your model</span></span>

<span data-ttu-id="412f6-246">Po przeszkoleniu modelu użyj danych testowych, aby ocenić, jak model działa.</span><span class="sxs-lookup"><span data-stu-id="412f6-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="412f6-247">Utwórz `EvaluateModel()` metodę, zaraz `BuildAndTrainModel()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="412f6-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="412f6-248">Przekształć `Test` dane, `EvaluateModel()`dodając następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="412f6-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="412f6-249">Metoda [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) sprawia, że prognoz dla wielu wierszy wejściowych dostarczonych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="412f6-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="412f6-250">Oceń model, dodając następujące jako następny wiersz `EvaluateModel()` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="412f6-251">Po ustawieniu prognozowania metoda [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) ocenia model, który porównuje przewidywane wartości `Labels` z rzeczywistym w zestawie danych testowych i zwraca metryki dotyczące wykonywania modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="412f6-252">Wydrukuj metryki oceny w konsoli, dodając następujące elementy `EvaluateModel()` jako następny wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="412f6-253">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="412f6-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="412f6-254">Dane wyjściowe do tej pory powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="412f6-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="412f6-255">W tym wyjściu istnieje 20 iteracji.</span><span class="sxs-lookup"><span data-stu-id="412f6-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="412f6-256">W każdej iteracji miara błędu zmniejsza się i zbiega się coraz bliżej 0.</span><span class="sxs-lookup"><span data-stu-id="412f6-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="412f6-257">(RMS `root of mean squared error` lub RMSE) służy do pomiaru różnic między wartościami przewidywanymi modelami a obserwowanymi wartościami testowego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="412f6-258">Technicznie jest to pierwiastek kwadratowy średniej kwadratów błędów.</span><span class="sxs-lookup"><span data-stu-id="412f6-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="412f6-259">Im niższy, tym lepszy jest model.</span><span class="sxs-lookup"><span data-stu-id="412f6-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="412f6-260">`R Squared`wskazuje, jak dobrze dane pasują do modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="412f6-261">Waha się od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="412f6-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="412f6-262">Wartość 0 oznacza, że dane są losowe lub w inny sposób nie mogą być dostosowane do modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="412f6-263">Wartość 1 oznacza, że model dokładnie pasuje do danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="412f6-264">Chcesz, `R Squared` aby twój wynik był jak najbliżej 1, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="412f6-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="412f6-265">Tworzenie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="412f6-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="412f6-266">Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="412f6-267">Jeśli nie jesteś zadowolony z jakości modelu, można spróbować go poprawić, zapewniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi hiper-parametrów dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="412f6-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="412f6-268">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Ulepszanie modelu](#improve-your-model) poniżej.</span><span class="sxs-lookup"><span data-stu-id="412f6-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="412f6-269">Korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-269">Use your model</span></span>

<span data-ttu-id="412f6-270">Teraz można użyć przeszkolonego modelu do przewidywania na nowe dane.</span><span class="sxs-lookup"><span data-stu-id="412f6-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="412f6-271">Utwórz `UseModelForSinglePrediction()` metodę, zaraz `EvaluateModel()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="412f6-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="412f6-272">Służy `PredictionEngine` do przewidywania klasyfikacji przez dodanie `UseModelForSinglePrediction()`następującego kodu do:</span><span class="sxs-lookup"><span data-stu-id="412f6-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="412f6-273">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="412f6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="412f6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="412f6-275">Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="412f6-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="412f6-276">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="412f6-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="412f6-277">Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="412f6-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="412f6-278">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="412f6-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="412f6-279">Utwórz wystąpienie wywoływane `MovieRating` `testInput` i przekazać go do aparatu przewidywania, dodając `UseModelForSinglePrediction()` następujące jako następne wiersze kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="412f6-280">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie na jednej kolumnie danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="412f6-281">Następnie można użyć `Score`, lub przewidywanej klasyfikacji, aby określić, czy chcesz polecić film z movieId 10 do użytkownika 6.</span><span class="sxs-lookup"><span data-stu-id="412f6-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="412f6-282">Im `Score`wyższe, tym większe prawdopodobieństwo polubienia konkretnego filmu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="412f6-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="412f6-283">W takim przypadku załóżmy, że polecasz filmy o przewidywanej ocenie > 3,5.</span><span class="sxs-lookup"><span data-stu-id="412f6-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="412f6-284">Aby wydrukować wyniki, dodaj następujące wiersze jako `UseModelForSinglePrediction()` następne wiersze kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="412f6-285">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="412f6-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="412f6-286">Dane wyjściowe tej metody powinny wyglądać podobnie do następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="412f6-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="412f6-287">Zapisywanie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-287">Save your model</span></span>

<span data-ttu-id="412f6-288">Aby użyć modelu do prognozowania w aplikacjach użytkowników końcowych, należy najpierw zapisać model.</span><span class="sxs-lookup"><span data-stu-id="412f6-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="412f6-289">Utwórz `SaveModel()` metodę, zaraz `UseModelForSinglePrediction()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="412f6-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="412f6-290">Zapisz przeszkolony model, dodając następujący `SaveModel()` kod w metodzie:</span><span class="sxs-lookup"><span data-stu-id="412f6-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="412f6-291">Ta metoda zapisuje przeszkolony model do pliku zip (w folderze "Dane"), który może być następnie używany w innych aplikacjach .NET do tworzenia prognoz.</span><span class="sxs-lookup"><span data-stu-id="412f6-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="412f6-292">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie, aby wywołać metodę: `SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="412f6-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="412f6-293">Korzystanie z zapisanego modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-293">Use your saved model</span></span>

<span data-ttu-id="412f6-294">Po zapisaniu przeszkolonego modelu można korzystać z modelu w różnych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="412f6-294">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="412f6-295">Zobacz [Zapisywanie i ładowanie wyszkolonych modeli,](../how-to-guides/save-load-machine-learning-models-ml-net.md) aby dowiedzieć się, jak operacjonalizacji wyszkolonego modelu uczenia maszynowego w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="412f6-295">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="412f6-296">Wyniki</span><span class="sxs-lookup"><span data-stu-id="412f6-296">Results</span></span>

<span data-ttu-id="412f6-297">Po wykonać powyższe czynności uruchom aplikację konsoli (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="412f6-297">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="412f6-298">Wyniki z pojedynczej prognozy powyżej powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="412f6-298">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="412f6-299">Możesz zobaczyć ostrzeżenia lub przetwarzania wiadomości, ale te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="412f6-299">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="412f6-300">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="412f6-300">Congratulations!</span></span> <span data-ttu-id="412f6-301">Pomyślnie skompilowano model uczenia maszynowego do polecania filmów.</span><span class="sxs-lookup"><span data-stu-id="412f6-301">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="412f6-302">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation)</span><span class="sxs-lookup"><span data-stu-id="412f6-302">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="412f6-303">Ulepszanie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-303">Improve your model</span></span>

<span data-ttu-id="412f6-304">Istnieje kilka sposobów, które można poprawić wydajność modelu, dzięki czemu można uzyskać dokładniejsze prognoz.</span><span class="sxs-lookup"><span data-stu-id="412f6-304">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="412f6-305">Dane</span><span class="sxs-lookup"><span data-stu-id="412f6-305">Data</span></span>

<span data-ttu-id="412f6-306">Dodanie większej liczby danych szkoleniowych, które mają wystarczającą liczbę próbek dla każdego użytkownika i identyfikator filmu, może poprawić jakość modelu rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="412f6-306">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="412f6-307">[Sprawdzanie poprawności krzyżowej](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) jest techniką oceny modeli, która losowo dzieli dane na podzbiory (zamiast wyodrębniania danych testowych z zestawu danych, tak jak to miało miejsce w tym samouczku) i przyjmuje niektóre grupy jako dane pociągu, a niektóre grupy jako dane testowe.</span><span class="sxs-lookup"><span data-stu-id="412f6-307">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="412f6-308">Ta metoda przewyższa dokonywanie podziału testu pociągu pod względem jakości modelu.</span><span class="sxs-lookup"><span data-stu-id="412f6-308">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="412f6-309">Funkcje</span><span class="sxs-lookup"><span data-stu-id="412f6-309">Features</span></span>

<span data-ttu-id="412f6-310">W tym samouczku używasz `Features` `user id`tylko `movie id`trzech `rating`( , i ), które są dostarczane przez zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-310">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="412f6-311">Chociaż jest to dobry początek, w rzeczywistości można `Features` dodać inne atrybuty lub (na przykład wiek, płeć, geolokalię itp.), jeśli są one zawarte w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="412f6-311">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="412f6-312">Dodanie bardziej `Features` istotne może pomóc poprawić wydajność modelu rekomendacji.</span><span class="sxs-lookup"><span data-stu-id="412f6-312">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="412f6-313">Jeśli nie masz `Features` pewności, które z nich może być najbardziej istotne dla twojego zadania uczenia maszynowego, możesz również skorzystać z obliczania `Features`wkładu funkcji (FCC) i znaczenia funkcji [permutacji,](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)które ML.NET zapewnia, aby odkryć najbardziej wpływowe.</span><span class="sxs-lookup"><span data-stu-id="412f6-313">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="412f6-314">Algorytm hiperparametry</span><span class="sxs-lookup"><span data-stu-id="412f6-314">Algorithm hyperparameters</span></span>

<span data-ttu-id="412f6-315">Chociaż ML.NET zapewnia dobre domyślne algorytmy szkoleniowe, można dodatkowo dostosować wydajność, zmieniając [hiperparametry algorytmu.](../resources/glossary.md#hyperparameter)</span><span class="sxs-lookup"><span data-stu-id="412f6-315">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="412f6-316">For `Matrix Factorization`, można eksperymentować z hiperparametrów, takich jak [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) i [ApproximationRank,](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) aby sprawdzić, czy to daje lepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="412f6-316">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="412f6-317">Na przykład w tym samouczku opcje algorytmu są:</span><span class="sxs-lookup"><span data-stu-id="412f6-317">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="412f6-318">Inne algorytmy rekomendacji</span><span class="sxs-lookup"><span data-stu-id="412f6-318">Other Recommendation Algorithms</span></span>

<span data-ttu-id="412f6-319">Algorytm faktoryzacji macierzy z filtrowania współpracy jest tylko jedno podejście do wykonywania zaleceń filmowych.</span><span class="sxs-lookup"><span data-stu-id="412f6-319">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="412f6-320">W wielu przypadkach dane ocen mogą nie być dostępne i mieć dostępną tylko historię filmów od użytkowników.</span><span class="sxs-lookup"><span data-stu-id="412f6-320">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="412f6-321">W innych przypadkach możesz mieć więcej niż tylko dane ratingowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="412f6-321">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="412f6-322">Algorytm</span><span class="sxs-lookup"><span data-stu-id="412f6-322">Algorithm</span></span>       | <span data-ttu-id="412f6-323">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="412f6-323">Scenario</span></span>           | <span data-ttu-id="412f6-324">Przykład</span><span class="sxs-lookup"><span data-stu-id="412f6-324">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="412f6-325">Faktoryzacja macierzy jednej klasy</span><span class="sxs-lookup"><span data-stu-id="412f6-325">One Class Matrix Factorization</span></span> | <span data-ttu-id="412f6-326">Użyj tego, gdy masz tylko identyfikator użytkownika i identyfikator movieId.</span><span class="sxs-lookup"><span data-stu-id="412f6-326">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="412f6-327">Ten styl rekomendacji opiera się na scenariuszu współskupu lub produktach często kupowanych razem, co oznacza, że poleci klientom zestaw produktów opartych na ich własnej historii zamówień zakupu.</span><span class="sxs-lookup"><span data-stu-id="412f6-327">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="412f6-328">>Wypróbuj</span><span class="sxs-lookup"><span data-stu-id="412f6-328">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="412f6-329">Maszyny faktoryzacji z uwzględnieniem pola</span><span class="sxs-lookup"><span data-stu-id="412f6-329">Field Aware Factorization Machines</span></span> | <span data-ttu-id="412f6-330">Użyj tego, aby sformułować zalecenia, gdy masz więcej funkcji poza identyfikatorem użytkownika, identyfikatorem produktu i oceną (na przykład opis produktu lub cenę produktu).</span><span class="sxs-lookup"><span data-stu-id="412f6-330">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="412f6-331">Ta metoda używa również podejścia do filtrowania współpracy.</span><span class="sxs-lookup"><span data-stu-id="412f6-331">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="412f6-332">>Wypróbuj</span><span class="sxs-lookup"><span data-stu-id="412f6-332">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="412f6-333">Nowy scenariusz użytkownika</span><span class="sxs-lookup"><span data-stu-id="412f6-333">New user scenario</span></span>

<span data-ttu-id="412f6-334">Jednym z typowych problemów w filtrowaniu współpracy jest problem zimnego rozruchu, który jest, gdy masz nowego użytkownika bez poprzednich danych do wyciągnięcia wniosków z.</span><span class="sxs-lookup"><span data-stu-id="412f6-334">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="412f6-335">Ten problem jest często rozwiązywany przez prośbę nowych użytkowników o utworzenie profilu i, na przykład, ocenę filmów, które widzieli w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="412f6-335">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="412f6-336">Chociaż ta metoda nakłada pewne obciążenie na użytkownika, zapewnia pewne dane początkowe dla nowych użytkowników bez historii klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="412f6-336">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="412f6-337">Zasoby</span><span class="sxs-lookup"><span data-stu-id="412f6-337">Resources</span></span>

<span data-ttu-id="412f6-338">Dane użyte w tym samouczku pochodzą z [movielens dataset](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="412f6-338">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="412f6-339">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="412f6-339">Next steps</span></span>

<span data-ttu-id="412f6-340">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="412f6-340">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="412f6-341">Wybieranie algorytmu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="412f6-341">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="412f6-342">Przygotowanie i załadowanie danych</span><span class="sxs-lookup"><span data-stu-id="412f6-342">Prepare and load your data</span></span>
> * <span data-ttu-id="412f6-343">Tworzenie i szkolenie modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-343">Build and train a model</span></span>
> * <span data-ttu-id="412f6-344">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-344">Evaluate a model</span></span>
> * <span data-ttu-id="412f6-345">Wdrażanie i korzystanie z modelu</span><span class="sxs-lookup"><span data-stu-id="412f6-345">Deploy and consume a model</span></span>

<span data-ttu-id="412f6-346">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="412f6-346">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="412f6-347">Analiza tonacji</span><span class="sxs-lookup"><span data-stu-id="412f6-347">Sentiment Analysis</span></span>](sentiment-analysis.md)
